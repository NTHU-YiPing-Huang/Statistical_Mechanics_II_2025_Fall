# The Ginsburg Landau theory


We will introduce the Ginsburg Landau theory which is a theory that describes the definition of phases and the transitions between them. The theory heavily relies on the principle of symmetry which will become more clear as we introduce the postulates and the structure of the theory. Before everything, let's understand what is the problem and what kind of tools we have at hands.

## Motivation -- Phases and phase transitions

Phases characterizes the pattern of collective behavior of a many-body system. When the pattern changes, we have a phase transition. In the equilibrium statistical mechanics, we learned that phases and phase transitions could be understood by the partition function. The key to have a well-defined notion of phase transition is to study the question at the thermodynamic limit where we could have non-analytic behavior from the combination of infinite many analytic functions.

The partition function for a system can be formally expressed as

$$
Z(N,\beta)=\sum_{c\in \mathcal{C}} e^{-\beta E(c)}\text{.}
$$
Here, $N$ is the number of degrees of freedom, $\beta=(k_B T)^{-1}$, $c$ represent an arbitrary configuration of the system in the configuration space $\mathcal{C}$ and $E(c)$ is the energy of the corresponding configuration $c$.

With the partition function defined, the probability of the configuration $c$ can be expressed as

$$
P(c)=\frac{1}{Z}e^{-\beta E(c)}; \sum_{c\in\mathcal{C}} P(c)=1\text{(The normalization condition).}
$$

The partition function is related to the free energy by a simple change of variable.

$$
Z(N,\beta)&=\sum_{c\in \mathcal{C}} e^{-\beta E(c)}=\sum_{E}\sum_{c\in \mathcal{C}}\delta_{E,E(c)} e^{-\beta E(c)}\\
&=\sum_{E} \underbrace{w(E)}_{\text{number of configurations at the specific energy } E} e^{-\beta E(c)}\\
&=\sum_E e^{-\beta E+\ln[w(E)]}=e^{-\beta F(N,\beta)}\text{.}
$$

The competition between energetics and the entropy can be observed clearly by taking derivative with respect to $\beta$ to the normalization condition above.

$$
\sum_{c\in\mathcal{C}} e^{\beta[F(N,\beta)-E(c)]}\left\{ \left[F(N,\beta)-E(c)\right]+\beta\left(\frac{\partial F}{\partial \beta}\right)_N\right\}=0
$$

The above equality leads to

$$
F(N,\beta)=\sum_{c\in\mathcal{C}}P(c)E(c)-\beta\sum_{c\in\mathcal{C}}P(c)\left(\frac{\partial F}{\partial \beta}\right)_N=\langle H\rangle -T \langle \left(-\partial_T F\right)_N\rangle\text{.}
$$

Adjusting temperature changes the weighting of $\langle H\rangle$ and $T \langle \left(-\partial_T F\right)_N\rangle$.  At low temperature limit, the first term dominates. At the high temperature limit, the latter dominates.

### Mean-field theory for Ising model

To have a more specific picture about the above abstract idea. Let's take the simplest non-trivial model for the study of phases-- the ferromagnetic Ising model.

The model is defined by interacting binary variables $\sigma_i=\{+1,-1\}$ on lattice site $i$. The Hamiltonian for the system $\Omega$ is

$$
H_{\Omega}=-J\sum_{\langle i,j\rangle} \sigma_i\sigma_j, J>0\text{.}
$$

Here, the binary variables prefer to have the same sign as dictated by the energy scale $J$. 

The system has the global Ising symmetry, $\sigma_i\to-\sigma_i$, which keep the Hamiltonian invariant. There are other symmetries such as the lattice symmetry which we will see does not play an important role for the discussion of the phase transition.

The probability of a spin configuration $P(c=\{\sigma_1,\sigma_2,\cdots,\sigma_N\})$ factorizes under the mean-field theory assumption. *i.e.* $P(c=\{\sigma_1,\sigma_2,\cdots,\sigma_N\})\xrightarrow{MFT} \prod_{i=1}^N P_{MFT}(\sigma_i)$. The corresponding probability $P_{MFT}(\sigma_i)$ is then determined in a self-consistent fashion.

The formal procedure is to replace the spin spin coupling using the expectation value that is determined by $P_{MFT}(\sigma_i)$. The replacement is valid when we assume the fluctuation $\delta \sigma \equiv \sigma_i-\langle \sigma_i\rangle_{MFT}$ is small and we only include terms up to $\mathcal{O}(\delta \sigma)$. The replacement

$$
\sigma_i\sigma_j\to \langle \sigma_i \rangle_{MFT} \sigma_j+\sigma_i\langle \sigma_j\rangle_{MFT}-\langle \sigma_i\rangle_{MFT}\langle \sigma_j\rangle_{MFT}
$$

effectively reduce the problem into a single particle problem with an effective magnetic field, $h_{eff,i}=\sum_{j\neq i} J_{ij}\langle \sigma_j\rangle_{MFT}$, applied on a single spin. For those who are not familiar with the mean-field theory approach, please check the lecture note of statistical mechanics (I).

We can stand back and ask what is the key assumption in the mean-field theory? It turns out the assumption that $\delta \sigma\approx0$ is the key for the mean-field theory to work. If the statement is true, then we can drop the fluctuation. This situation happened when the system is deep in a specific phase. On the other hand, when the system is near the transition, the fluctuation is not small, then the approach will be problematic. We will revisit this issue later. For now, let's pretend the mean-field theory is valid for all temperature range and move on to do the corresponding calculation.

The key equation for us to solve is the self-consistency equation. At this step, I will put back the coupling with the external magnetic field, $h$, to remind ourselves about how to use the mean-field theory to calculate the critical exponents. The self-consistency equation is

$$
\langle \sigma_i\rangle_{MFT}=m=\tanh\left[ \beta (h+m k_B T_c)\right]; T_c=\frac{2dJ}{k_B}\text{.}
$$

Once $m$ is determined, we can construct the effective magnetic field and recover $P_{MFT}(\sigma_i)$. With these information, we can calculate the critical exponents by expanding the self-consistency equation near the critical temperature. Can we generalize this process? If yes, what can we learn from the generalization scheme?


## The "Landau free energy"

### Concept of order parameter

One can immediate notice that $\langle \sigma_i\rangle_{MFT}$ plays an important role in the above approach. It is actually the parameter that specifies the corresponding order. When $\langle \sigma_i\rangle_{MFT}\neq0$, it specifies the system is ordered. However, the quantity is defined within the mean-field theory. Why not promoting this idea to a more general setting beyond the mean-field theory. After all, the mean-field theory is just a theory for us to approximate the $P(\{\sigma_1,\sigma_2,\cdots,\sigma_N\})$.

We can take the idea and define an observable $\mathcal{O}$. When $\langle \mathcal{O}\rangle \neq0$, the probability distribution develop some kind of collective pattern that is specified by $\langle \mathcal{O}\rangle$, so we call it the *order parameter*. The order parameter can be a scalar, a vector, a tensor or even a function. We will focus on the simple case for now. For the Ising model, it is just the magnitude of $m$.

### A little bit of reverse engineering...

Now we know the idea of the mean-field theory and the order parameter. For different problems, we will need to run the same machinery again and again. Can we find the common features between those mean-field theories? The key equation seems to be the self-consistency equation. Can we make some physical arguments and directly get the essential information of the self-consistency equation?

Let's first define what do we mean by the essential information. In the study of critical phenomena, we basically look for the so-called critical exponents. When the temperature is near the critical temperature, the order parameter will be small and we might expand the self-consistency equation and solve them approximately. In the case of Ising model, we essentially can do the analysis by sending $T\to T_c$ and $m\approx0$ at small external field $h$. The self-consistency equation becomes

$$
\frac{h}{k_B T}\approx (1-\tau)m+\left[\tau-\tau^2+\frac{\tau^3}{3}\right]m^3+\cdots\\
\text{or equivalently}\\
(1-\tau)m+\left[\tau-\tau^2+\frac{\tau^3}{3}\right]m^3-\frac{h}{k_B T}\approx
$$ (critical-equation)

here, $\tau=\frac{T_c}{T}$ and we can get all the critical exponents starting from this equation.

So the question is: can we define some kind of concept that is similar to the free energy in thermodynamics and minimize it to get the above self-consistency equation near the critical temperature? If we can do that, that concept will be useful. Then we can go back and ask how to justify this seemly *ad hoc* free energy on a physical ground.

Let's just try to do the exercise for our Ising model problem with equation [](critical-equation). If we define some kind of "free energy" $\Gamma(T,J,h,m)$. We can always devide it into parts that are independent of $m$ completely and parts that depends on $m$ implicitly. We would like to have the part that has implcit dependence on $m$ provides the minimization equation which is equivalent to [](critical-equation). The following construction will work.

$$
\Gamma(T,J,h,m)\equiv \Gamma_0(T,J,h)+\underbrace{U[\Gamma_0(T,J,h)]}_{\text{To make sure the expression has the right unit.}}\int dm K(T,J,h,m)\text{.}
$$

The minimization condition is

$$
\frac{\partial \Gamma}{\partial m}=0=(1-\tau)m+\left[\tau-\tau^2+\frac{\tau^3}{3}\right]m^3-\frac{h}{k_B T}\text{.}
$$

So we can see the idea is very tempting! It is indeed possible at least formally. If we perform the last integral, we can see

$$
\Gamma(T,J,h,m)\equiv \Gamma_0(T,J,h)+U[\Gamma_0(T,J,h)]\left\{(1-\tau)\frac{m^2}{2}+\left[\tau-\tau^2+\frac{\tau^3}{3}\right]\frac{m^4}{4}-\frac{h}{k_BT}m\right\}\text{.}
$$

All the important information is hidden in the last term. The question is: can we have a theoretical argument to construct it directly? It turns out, it is the Landau theory.

### The postulates

Here we discuss the postulates for the Landau theory. The key step toward the physical argument of the Landau theory is to identify the transformation property of the order parameter under the symmetry of the system. We will discuss the postulates first and apply it to the Ising model and see what we can learn during the procedure.

1. We can construct the Landau free energy, $L$, as
   
   $$
   L\left[\left\{K_i\right\},\eta\right]
   $$
   with the order parameter $\eta$ and couplings $\{K_i\}$.
2. How to construct $L$? 
   1. $\eta$ transforms under the symmetry of the system.
   2. $L$ is invariant under the symmetry transformation.
   
   Taking the Ising model as an example, the order parameter $\eta=\langle \sigma_i\rangle\xrightarrow{\text{Ising symmetry}}-\eta$. As the temperature is below the critical temperature, $\eta\neq0$. The symmetry is spontaneously broken. When the temperature is above the critical temperature $\eta=0$ the symmetry is preserved.
3. $L$ is analytic in $\eta$ around $\eta=0$. We will see that it is convenient to discuss the density of $L$ defined as
   
   $$
   \mathcal{L}=\frac{L}{V}=\sum_{p=0}^{\infty}a_p(\{K_i\})\eta^p\text{ when } \eta\approx0\text{.}
   $$
4. For inhomogeneous system, we require $\mathcal{L}$ to be a local function of $\eta(\textbf{r})$ and $\nabla^q \eta(\textbf{r})$ with $q$ finite.
5. When $T>T_c$, the solution of the minimization equation of $\mathcal{L}$ is $\eta=0$. When $T<T_c$, the solution is $\eta\neq0$.

```{admonition} Beyond Landau?
:class: tip
An interesting question to ask is: How to go beyond Landau's phenomenlogical theory? Before we claim something is beyond Landau's paradigm, we should learn what is Landau theory. Now we know what is the spirit and the assumptions of Landau theory. There are several ways that people found that is not included in Landau's paradigm.

1. Non-equilibrium physics: Once we are not in equlibrium, the fundation of free energy like concept is questionalble. In this sense, it is a trivial case that is beyond Landau's paradigm.
2. Equilibrium physics: If we are discussing equilibrium phases, it is more challenging to find other general mechanism beyond Landau's approach. I will mention two of them, which is related to the [2016 Nobel prize in Physics](https://www.nobelprize.org/uploads/2018/06/advanced-physicsprize2016-1.pdf)。The key question is related to the concept of order parameter. The conventional order parameter contains only local information. Are there collective pattern that is invisible to local information, but requires global informaiton of the system to identify the collective pattern?
```

### Phenomenological Landau theory for the Ising model

Let's try to construct the phenomenological Landau theory for the Ising model. 

$$
H=-J\sum_{\langle i,j\rangle}S_iS_j; J>0\text{.}
$$

The important object is the order parameter. In this case, the symmetry of the Hamiltonian is the Ising symmetry $S_i\to-S_i$. The simplest observable that breaks the symmetry is $\langle S_i\rangle\equiv \eta$. We will use it to be the order parameter and construct the corresponding Landau free energy. 

#### Constructing the Landau free energy

We start our process by considering the homogeneous case where $\eta(\textbf{r})=\eta$ and $\nabla \eta(\textbf{r})=0$. From the postulate 3 we know

$$
\mathcal{L}=a_0(J,T)+a_1(J,T)\eta+a_2(J,T)\eta^2+a_3(J,T)\eta^3+a_4(J,T)\eta^4+\cdots
$$

From postulate 2, the Ising symmetry requires $\mathcal{L}(\eta)=\mathcal{L}(-\eta)$. Therefore, we only keep the even power terms.

$$
\mathcal{L}=a_0(J,T)+a_2(J,T)\eta^2+a_4(J,T)\eta^4+\cdots
$$
To avoid the cluttering notation, we will supress the $(J,T)$ dependence. But we should keep in mind that those coeficients all depends on $J$ and $T$ implicitly.

We will use postulate 5 to determine the behavior of the phenomenological constants across the critical temperature $T_c$. We first notice the minimization condition of the Landau free energy has two solutions

$$
\frac{\partial \mathcal{L}}{\partial \eta}=2a_2\eta+4a_4\eta^3=0
$$

with two solutions

$$
\eta=
\left\{
\begin{array}{c}
0\\
\pm \sqrt{-\frac{a_2}{2a_4}}\equiv \pm \eta_{SB}
\end{array}
\right.
\text{.}
$$

Our goal is to have $\eta=0$ to be the stable solution for the Landau free energy when $T>T_c$ and $\eta=\pm\eta_{SB}$ when $T<T_c$. How to achieve our goal? We can make the following observation, the functional form of the Landau free energy is essentially a quadratic equation in disguise. That is, we can rewrite the free energy in the form of $A_1(\eta^2+A_2)^2$. To have a well defined minimum, we need to have $A_1>0$. If $A_2>0$, the free energy is minimized when $\eta^2=\eta=0$. If $A_2<0$, the free energy is minimized when $\eta^2=-A_2>0$. Therefore, we can reverse engineer the properties we want. That is, we require $a_4(J,T)>0$ and $a_2(J,T)$ to change sign accordingly at $T=T_c$! With these information, we could find the leading order behavior of $a_0(J,T),a_2(J,T)$ and $a_4(J,T)$ in temperature.

$$
a_0(J,T)&\simeq a_0(J)+\cdots\\
a_2(J,T)&\simeq a\left(\frac{T-T_c}{T_c}\right)+\cdots\equiv at+\cdots\\
a_4(J,T)&\simeq \frac{b}{2}+\cdots\text{ with $b>0$.}
$$

The $a_0(J)$ term is not going to play an essential role, so we drop it in later discussion. When we include coupling with external field, the Landau free energy should have the form

$$
\mathcal{L}=at\eta^2+\frac{b}{2}\eta^4-h\eta\text{.}
$$

The schematic behavior of the Landau free energy is ploted in {numref}`Landau_free_energy_Ising`.

```{figure} /images/Landau_free_energy_simple.pdf
---
width: 950 px
name: Landau_free_energy_Ising
---
Schematic behavior of the Landau free energy for Ising model.
```

When $h=0$, the system has the Ising symmetry and the symmetry is spontaneously broken at the continuous phase transition point.
When $t<0$ and we tune the external field from postive value to negative value, we have a jump of the order parameter at $h=0$. We have a discontinuous phase transition at $h=0$.

#### The critical exponents

For the corresponding Landau free energy, we can easily derive 

$$
\eta(t)=
\left\{
\begin{array}{cc}
\sqrt{\frac{-at}{b}}\propto t^{\beta}; \beta=\frac{1}{2} &\text{when $t<0$,h=0}\\
0 &\text{when $t>0$,h=0}
\end{array}
\right.
\text{.}
$$

Using this informaiton, we can derive $\mathcal{L}(\eta=0)$ and $\mathcal{L}{\eta=\sqrt{\frac{-at}{b}}}$ and calculate the corresponding specific heat near $T_c$. We find there is a jump. So the critical exponent is $\alpha=0$.

$$
C_v=T^2\frac{\partial^2 \mathcal{L}}{\partial T^2}=
\left\{
\begin{array}{cc}
0 &t>0\\
\frac{a^2}{b T_c} &t\lesssim 0
\end{array}
\right.
\text{.}
$$

When $t=0$ and $h\neq0$, we have

$$
(\cdots)\frac{b}{2}\eta^3=h, h\propto \eta^{\delta}; \delta=3\text{.}
$$

For the susceptibility, we have

$$
\chi_T=\left.\frac{\partial \eta(h)}{\partial h}\right|_T\sim
\left\{
\begin{array}{cc}
\frac{1}{at} \sim t^{-\gamma^+} &t>0,\eta=0
\frac{1}{-4at} \sim t^{-\gamma^-} &t<0,\eta=\sqrt{\frac{-at}{b}}
\end{array}
\right.
$$

with $\gamma^+=\gamma^-=1$.

#### Effects of higher order terms

Once we include the external field that breaks the symmetry, we should allow terms with odd power of $\eta$. In the previous discussion, we found the linear term will tilt the free energy landscape and demonstrate the discontinuous transition across $h=0$. However, in the simple free energy expression, we found there will be no discontinuous phase transition when we tune the temperature! It is actually an artifact of the simple free energy structure. It does not mean the Landau theory cannot capture finite temperature discontinuous phase transition. Now we would like to understand what happend if we include higher order terms of $\eta$. Will that give us some understanding about the discontinuous phase transition at finite temperature?

Let's consider the term proportional with $\eta^3$. The corresponding free energy looks like

$$
\mathcal{L}=at\eta^2+\frac{b}{2}\eta^4-h\eta+C\eta^3\text{.}
$$

As before, we would like to identify the configuration that minimize the Landau free energy.

$$
\frac{\partial \mathcal{L}}{\partial \eta}=0=2at\eta+2b\eta^3-h+3C\eta^2\text{.}
$$

We roughly know the effect of the linear term. So let's set $h=0$ and focus on the effect of the $\eta^3$ term. At the $h=0$ point, we have

$$
\eta=
\left\{
\begin{array}{c}
0\\
-\frac{3C}{4b}\pm\sqrt{\left(\frac{3C}{4b}\right)^2-\frac{at}{b}}\equiv \eta_{\pm}
\end{array}
\right.
\text{.}
$$
To get real $\eta_{\pm}$, we require

$$
\left(\frac{3C}{4b}\right)^2-\frac{at}{b}\ge0\text{.}
$$

That sets a range of the temperture given by the temperature scale $t^*$. $\eta$ is real if

$$
t<t^*\equiv \frac{b}{a}\left(\frac{3C}{4b}\right)^2 \text{.}
$$

That is, only below this temperature, we could have non-trivial local extrema for $\eta=\eta_{\pm}$. Otherwise, the only local extrema is the minuma at $\eta=0$.

When we are below the temperature scale $t^*$, the two minimum will compete with each other. The critical temperature, $t_1$, that the two minimum switch roles, is the point where the discontinuous phase transition happened.

## The Landau free energy with inhomogeneous order parameter field

The whole discussion till now focus on the homogeneous case where $\nabla \eta(\boldsymbol{r})=0$. If the order parameter field is "piecewise flat", we can simply add the contribution of the Landau free energy for each position with a local homogeneous order parameter field. So the challenge to go from homogeneous one to the inhomogeneous one is how to deal with the situation when the order parameter changes as a function of space. That is the point where $\nabla \eta(\boldsymbol{r})$ kicks in. In principle we could have very complicate order parameter field, but let's assume we would like to focus on the case that the order parameter field varies smoothly on the scale that we care about. What that means is we don't want to have the field configuration with large $\nabla \eta(\boldsymbol{r})$ value, a simple way to supress such configuration is to give it a free energy penalty. So our Landau free enegy will look like

$$
L\left[\eta(\boldsymbol{r})\right]=\int d^d\boldsymbol{r}\frac{\gamma}{2}\left(\nabla \eta(\boldsymbol{r})\right)^2 +\mathcal{L}_0\left[\eta(\boldsymbol{r})\right]\equiv \int d^d\boldsymbol{r}\mathcal{L}^{(g)}\left[\eta(\boldsymbol{r})\right]\text{.}
$$

Here, $\mathcal{L}^{(g)}$ represent the generalized Landau free energy density. Phenomenological wise, we know that $\gamma$ is related to how difficult it is to modify the order parameter field. When the coupling is stronger, or the range of the interaction, $R$, is larger, the order parameter gets stiffer. From the dimension analysis, we should know $\gamma\propto J\frac{R^2}{a^d}$.

## The functional integral representation of Landau theory

Next, we are going to introduce the functional integral representation of Landau theory. In the above phenomenological description, we should notice that the introduction of the $\frac{\gamma}{2}\left(\nabla \eta(\boldsymbol{r})\right)^2$ term introduces a length scale to the problem. It will become clear that the length scale is the correlation length, $\xi$. On the other hand, the microscopic model has an intrinsic length scale given by the lattice constant $a$. The differentiation cannot be well defined at the length scale of $\mathcal{O}(a)$. So we should be more careful about the description. Especially in this description, all the observable defined on the lattice is now promoted into a field. The techniques that are developed to analyse field like this is part of the big research subject of field theory. Formulating statistical mechanics problem into field theory is sometimes known as "statistical field theory". One of the first step to describe Landau theory in the statistical field theory framework is the coarse graining process. What exactly do we mean by $\eta(\boldsymbol{r})$?

### Coarse graining

In the Ising model, we use binary variables to describe the configurations. Consider a random configuration on a two-dimensional lattice, schematically it looks like {numref}`random_Ising`.

```{figure} /images/random_conf.pdf
---
width: 950 px
name: random_Ising
---
A random configuration of binary variables on a two-dimensional lattice.
```

The {numref}`random_Ising` contains the full information about the configuration. However, it is also difficult to work in this representation since everything is discrete and we cannot apply the approximations that we are familiar with in the continuous description (e.g. No Taylor expansion). Can we have some approximate version of {numref}`random_Ising` but that is smooth enough for us to develop continuous description on top of that? The coarse graining process essentially is designed for that. If we replace the exact binary configurations within a length scale using the average value within the length scale, the average values will vary slower on the space. For example, if we took {numref}`random_Ising` and average over a $5\times 5$ block and define a new variable at the center of such block, the new configuration looks like {numref}`random_Ising_cg_l_5`.

```{figure} /images/random_conf_cg_1_l_5.pdf
---
width: 520 px
name: random_Ising_cg_l_5
---
A random configuration of binary variables on a two-dimensional lattice after we coarse grain on a $5\times 5$ block. Blue/Red regions are the regions below/above the average value of $0.5$
```

Now we can see the variation in space is reduced (at least not of $O(1)$). But still, it is not as smooth as we considered as continuous in space.

We can perform the coarse graining on a bigger block, say $15\times 15$, it looks like {numref}`random_Ising_cg_l_15`. 

```{figure} /images/random_conf_cg_1_l_15.pdf
---
width: 520 px
name: random_Ising_cg_l_15
---
A random configuration of binary variables on a two-dimensional lattice after we coarse grain on a $15\times 15$ block.
```

We can also coarse grain the coarse grained ones, it looks like {numref}`random_Ising_cg_6_l_5` after we iteratively coarse grain the configuration on $5\times 5$ blocks six times.

```{figure} /images/random_conf_cg_6_l_5.pdf
---
width: 520 px
name: random_Ising_cg_6_l_5
---
A random configuration of binary variables on a two-dimensional lattice after we coarse grain on a $5\times 5$ block iteratively 6 times.
```

The point is, we loose some information after coarse graining, but the corresponding configuration looks smoother (comparing {numref}`random_Ising`, {numref}`random_Ising_cg_l_15` and {numref}`random_Ising_cg_6_l_5`). So it makes more sense for us to use a continuous function to describe the coarse grained configuration and develop the corresponding field theory.

But we should also be careful about what have been dropped. After some thinking, we know the size of the block for coarse graining is important.  After we average the spin configurations within that block, the detailed informaiton inside that block is sacrificed. So we need to choose the length scale for the coarse grainning blocks wisely such that we can still access the relevant information of our original problem.

On the otherhand, we cannot coarse grain our system too little such that the field description does not make sense. If we use $\Lambda^{-1}$ to represent the length scale of the coarse graining, we would like to have the following relation.

$$
a\ll \Lambda^{-1}\lesssim \xi(t)
$$

Here $\Lambda^{-1}$ is the inverse of the wave vector cutoff which will be convenient for our later discussion. The coarse grained field is constructed by

$$
m_{\Lambda}(\boldsymbol{r})\equiv \frac{1}{N_{\Lambda}(\boldsymbol{r})} \sum_{i\in \mathcal{B}(\boldsymbol{r},\Lambda)} \langle \sigma_i\rangle\text{.}
$$
Now, we would like to discuss the theory of $m_{\Lambda}(\boldsymbol{r})$.

### The functional integral form of the Landau free energy and functional derivatives

More specifically, the previous expression of the Landau free energy should be understood with the coarse grained length scale $\Lambda^{-1}$ and the corresponding Landau free energy can be expressed as

$$
L\left[m_{\Lambda}(\boldsymbol{r})\right]&=\int d^d\boldsymbol{r}\left\{\mathcal{L}\left[m_{\Lambda}(\boldsymbol{r})\right]+\frac{\gamma}{2}\left(\nabla m_{\Lambda}(\boldsymbol{r})\right)^2\right\}\\
&\equiv\int d^d\boldsymbol{r}\mathcal{L}^{(g)}\left[m_{\Lambda}(\boldsymbol{r})\right]
$$

where the dependence on the coarse graining process is shown explicitly. 

The microscopic partition function can be formally related to the Landau free energy through the coarse grain process as

$$
Z&=\sum_{ \left\{\sigma_i\right\}}e^{-\beta H(\left\{\sigma_i\right\})}=\sum_{j}\sum_{m_{\Lambda}(\boldsymbol{x}_j)}\sum_{ \left\{\sigma_i\right\}}\delta_{m_{\Lambda}(\boldsymbol{x}_j)N_{\Lambda}(\boldsymbol{x}_j), \sum_{i\in\mathcal{B}(\boldsymbol{x}_j,\Lambda)}\sigma_i}e^{-\beta H(\left\{\sigma_i\right\})}\\
&\xrightarrow{\text{continuous limit}} \int \mathcal{D}\left[m_{\Lambda}(\boldsymbol{r})\right] e^{-\beta \int d^d\boldsymbol{r} \mathcal{L}^{(g)}\left[m_{\Lambda}(\boldsymbol{r})\right]}
$$

Keep writing the dependence on $\Lambda$ make the expression lengthy. So we usually supress the $\Lambda$ dependence but we should always remember the existence of the coarse grain length scale in our expression.

What do we mean by the continuous limit? We take $a\to0$ but we want to keep the physical volume to be invariant, that is $V=N(\Omega)a^d$ is kept fixed as we send $a\to0$. The formal expression $\int \mathcal{D}\left[m_{\Lambda}(\boldsymbol{r})\right]$ can therefore beening understood as

$$
\int \mathcal{D}\left[\eta(\boldsymbol{r})\right]\equiv \lim_{a\to0 , N(\Omega)\to\infty \atop V\to const} \int d{\eta_1}\int d{\eta_2}\cdots \int d{\eta_{N(\Omega)}}\equiv Tr_{ \eta(\boldsymbol{r})}
\text{.}
$$

Here, we use $\eta(\boldsymbol{r})$ to restore the generality of the theory.
Usually, we would like to work in the momentum space. For real $\eta(\boldsymbol{r})$, the Fourier components are not independent, therefore, we have 

$$
Tr_{ \eta(\boldsymbol{r})}=\int \prod_{\boldsymbol{k}<\Lambda\atop k_z>0} d(Re[\eta_{\boldsymbol{k}}]) d(Im[\eta_{\boldsymbol{k}}])\text{.}
$$

The $k_z>0$ take care of the double counting issue of the constraint due to the realness of the order parameter field. The $\boldsymbol{k}<\Lambda$ is to remind us that the validity of the field theory is based on a valid coarse grain process.

Now we would like to do some calculation using the functional integral representation of the Landau free energy. It is useful to know how to make the corresponding generalization by consulting the discrete version of the problem.

$$
Z_D[\left\{h_i\right\}]\leftrightarrow Z_C[h(\boldsymbol{r})]\text{.}
$$

Here

$$
Z_D[\left\{h_i\right\}]=Tr_{ \left\{\eta_i\right\}}\left\{\exp\left[-\beta(H_{\Omega}-\sum_i h_i\eta_i)\right]\right\}
$$

with the lattice Hamiltonian $H_{\Omega}$.

$$
Z_C[h(\boldsymbol{r})]=Tr_{ \eta(\boldsymbol{r})}\left\{\exp\left[-\beta\int d^d\boldsymbol{r} \left\{\mathcal{H}_{\Omega}-h(\boldsymbol{r})\eta(\boldsymbol{r})\right\}\right]\right\}
$$

with the Hamiltonian density $\mathcal{H}_{\Omega}$.

The corresponding correlators can be constructed as

$$
\langle \eta_i\eta_j\rangle_D&= \beta^{-2}Z_D[\left\{h_l\right\}]^{-1} \frac{\partial}{\partial h_i}\frac{\partial}{\partial h_j}Z_D[\left\{h_l\right\}]\\
\langle \eta(\boldsymbol{r}_i)\eta(\boldsymbol{r}_j)\rangle_C&=\beta^{-2}Z_C[h(\boldsymbol{r})]^{-1} \frac{\delta }{\delta h(\boldsymbol{r}_i)}\frac{\delta }{\delta h(\boldsymbol{r}_j)}Z_C[h(\boldsymbol{r})]\text{.}
$$

Here, we introduce the notion of functional derivative which means the notion of differential is now extended to the functional space. A function $f$ is a mapping of a vector $\boldsymbol{r}$ to a value $f(\boldsymbol{r})$. A functional $F$ is a mapping of a function $f(\boldsymbol{r})$ to a value of $F[f(\boldsymbol{r})]$. 

We can therefore again make the correspondence explicit

$$
\frac{\partial}{\partial x}&\equiv \lim_{\epsilon\to0} \frac{1}{\epsilon} \left[f(x+\epsilon)-f(x)\right]\\
\frac{\delta}{\delta \eta(\boldsymbol{x}')}&\equiv \lim_{\epsilon\to0}\frac{1}{\epsilon}\left\{F[\eta(\boldsymbol{x})+\epsilon\delta(\boldsymbol{x}'-\boldsymbol{x})]-F[\eta(\boldsymbol{x})]\right\}\text{.}
$$

Using this definition, we should be able to show
* $\frac{\delta}{\delta \eta(\boldsymbol{r})}\left[\int d^d\boldsymbol{r}' \eta(\boldsymbol{r}')\right]=1$
* $\frac{\delta}{\delta \eta(\boldsymbol{r})}\left[\eta(\boldsymbol{r}')\right]=\delta(\boldsymbol{r}-\boldsymbol{r}')$
* $\frac{\delta}{\delta \eta(\boldsymbol{r})}\left[\int d^d\boldsymbol{r}' \frac{1}{2}\left[\nabla \eta(\boldsymbol{r}')\right]^2\right]=-\nabla^2 \eta(\boldsymbol{r})$

We will leave the proof for the readers and using them for later discussion.

Now we should be able to notice the similarity between the discrete discription and the continuous description. So we expect to have

$$
\langle \eta(\boldsymbol{r})\rangle&=-\frac{\delta}{\delta h(\boldsymbol{r})} F[\eta(\boldsymbol{r})]\\
\chi_T(\boldsymbol{r},\boldsymbol{r}')&=\frac{\delta}{\delta h(\boldsymbol{r}')}\langle\eta(\boldsymbol{r})\rangle=-\frac{\delta}{\delta h(\boldsymbol{r}')}\frac{\delta}{\delta h(\boldsymbol{r})} F[\eta(\boldsymbol{r})]\\
&=\beta\left[\underbrace{\langle\eta(\boldsymbol{r})\eta(\boldsymbol{r}')\rangle-\langle \eta(\boldsymbol{r})\rangle\langle\eta(\boldsymbol{r}')\rangle}_{\text{connected correlation function}}\right]=\beta G(\boldsymbol{r},\boldsymbol{r}')\text{.}
$$

Now, let's see how to calculate the connected correlation function and the susceptibility from the functional representation of the Landau free energy. We copy the free energy here for our convenience.

$$
L=\int d^d\boldsymbol{r}\left[\frac{\gamma}{2}(\nabla \eta)^2+at\eta^2+\frac{b}{2}\eta^4-h(\boldsymbol{r})\eta(\boldsymbol{r})\right]\text{.}
$$

The first step is to find the formal expression of field $\eta^*(\boldsymbol{r})$ such that $\left.\frac{\delta L}{\delta \eta(\boldsymbol{r})}\right|_{\eta(\boldsymbol{r})=\eta^*(\boldsymbol{r})}=0$. The minimization condition gives

$$
-\gamma \nabla^2\eta^*+2at\eta^*+2b(\eta^*)^3-h(\boldsymbol{r})=0\text{.}
$$

With this equaiton, we can derive the formal expression of susceptibility by taking functional derivative with respect to $h(\boldsymbol{r}')$ on both side of the above equation.

$$
\chi_T(\boldsymbol{r},\boldsymbol{r}')&=\frac{\delta}{\delta h(\boldsymbol{r}')}\eta^*(\boldsymbol{r})\\
\left[-\gamma\nabla^2+2at+6b(\eta^*)^2\right]\underbrace{\chi_T(\boldsymbol{r},\boldsymbol{r}')}_{\beta G(\boldsymbol{r},\boldsymbol{r}')}&=\delta(\boldsymbol{r}-\boldsymbol{r}')\text{.}
$$

We can get $G(\boldsymbol{r},\boldsymbol{r}')$ by solving the above equations. 

In principle, we should solve the differential equation directly and find $\eta*(\boldsymbol{r})$. However, we will assume that we are studying the physics near the homogeneous solution.
