```
\documentclass{article}
\usepackage{array}
\usepackage{multicol}
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{mathrsfs}
\input{notation-siam}
\begin{document}
```
\numberwithin{equation}{section}

\section {Introduction}
 The time-dependent, dimensionless, viscoresistive, incompressible Navier-Stokes equations for computing the homogeneous Newtonian fluid flow is given by the following non-linear stochastic PDEs: 

```
\begin{align}
    \bu_t +\bu \cdot \nabla \bu - \nabla \cdot (\nu(\bx, \omega)\nabla \bu)&+ \nabla p=\bif(\bx,t,\omega)  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T] \\
    \nabla \cdot \bu& = 0  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T]\\
    \bu(\bx,0,\omega)&=\bu^0(\bx), \hspace{0.5cm} \bx \in \mathcal{D}
\end{align}
```

Here, the vector $\bu_t$ represents the unknown time derivative of the velocity field $\bu$ at some future time, t. The scalar pressure is given by p and the external force, $\bf(\bx,t,\omega)$. Viscosity, $\nu(\bx, \omega)$ is a continuous equation that depends on a position vector $\bx$, and a random variable $\omega$ that is taken from a random field $\Omega$. The complete probability measure space is given by $(\Omega,\mathcal{f},P)$, where $\Omega$ is the set or probability space, $F \subset 2^\Omega$ is the $\sigma$-algebra, and P represents all possible values for $F$, namely the probability measure, $P: F \to [0,1]$. 

The vector-valued function for velocity, $\bu$ is on $\mathcal{D} \times (0,T] \times \Omega \in \mathbb{R}^3$ and the scalar-valued pressure function, $p$ is on $\mathcal{D} \times (0,T] \times \Omega \in \mathbb{R}$. Specifically, we know that $\bu$ is square integrable, that is, $\text{L}^2(\mathcal{D})$ such that $\int_\Omega ||\bu||^2 d\Omega < \infty$. In addition, the vector-valued velocity belongs to the Hilbert space given by $\bX : H_0^1(\mathcal{D})$, the pressure space is given by $Q: \text{L}^2_0$ and the stochastic space by which we take our random variable, $\Omega$ is $\bW= L^2_\rho (\Omega)$.
Let the inner product, $\text{L}^2(\mathcal{D})$, be denoted by $(\cdot, \cdot)$. In order to arrive at the weak formulation of our equation, we must multiply by test functions, $\bv$ and perform integration over the domain $\Omega$. We will take $\bv$ from the vector space $\bX$, that is, $\bv \in X$, with the same properties as $\bu$ on the boundary. The weak formulation can be thought of as finding a $\bu \in \bX \otimes \bW$ and  $p\in \bf{Q} \otimes \bW$ such that:

```
\begin{align}
(\bu_t,\bv)+(u \cdot \nabla u, v)+&(\nu\nabla\bu, \nabla\bv) + (p,\nabla \cdot \bv)=(\bf,\bv)\\
(\nabla \cdot \bu,q)&=0
\end{align}
```
 Because we have taken the variables from the stochastic space, let us take the expectation of both sides:
```
\begin{align}
\mathbb{E}[(\bu_t,\bv)]+\mathbb{E}[(u \cdot \nabla u, v)]+&\mathbb{E}[(\nu\nabla\bu, \nabla\bv)] - \mathbb{E}[(p,\nabla \cdot \bv)]=\mathbb{E}[(\bf,\bv)]\\
\mathbb{E}[(\nabla \cdot \bu,q)]&=0
\end{align}
```

Because viscosity is a continuous function, we take a random sample of viscosities, and compute their mean. To model the current $\nu(\bx, \omega)$ equation, we will use a d-dimensional random variable $\by(\omega) = (y_1(\omega), y_2(\omega), ..., y_d(\omega))$ with the assumption that $\mathbb{E}[\by]=0, \text{Var}[\by]=I_d$ and, using standard integration as Expectation our problem becomes: 
```
\begin{align}
\begin{split}
\int_\Gamma (\bu_t,\bv)\rho(\by) d\by+\int_\Gamma (\bu \cdot \nabla \bu, \bv)\rho(\by) d\by+&\int_\Gamma (\nu(\bx,\by )\nabla \bu, \nabla \bv)\rho(\by) d\by  \\- \int_\Gamma (p,\nabla \cdot \bv)\rho(\by) d\by=&\int_\Gamma (\bf,\bv)\rho(\by) d\by \hspace{1cm} \forall \bx\in \bX\otimes \bY\\
\end{split}
\end{align}
\begin{align}
\int_\Gamma (\nabla \cdot \bu,q)\rho(\by) d\by&=0 \hspace{1.5cm} \forall q \in \bf{Q}\otimes \bY
\end{align}
```
In our viscosity assumption, we have $$\nu(\bx,\by)=\nu_0(\bx)+\displaystyle{\sum_{l=1}^N} \nu_l(\bx)y_l$$ and assume affline dependence of the random variables for viscosity. 

Let $\textit{J}$ be the number of realizations -- that is, number of solutions, for equation.  We can rewrite the strong form as: We want to find $(u_j, p_j)$ such that  
```
\begin{align}
    \b u_{j,t} +\bu_j \cdot \nabla \bu_j - \nabla \cdot (\nu_j(\bx)\nabla \bu_j)&+ \nabla p_j=\bf_j(\bx,t)  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T] \\
    \nabla \cdot \bu_j& = 0  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T]
\end{align}
```
Where $\bu_j$ and $p_j$ are the velocity and pressure solutions, for each realization $j = 1,2,...\mathit{J}$ , each corresponding to a kinematic viscosity $\nu_j$, for a forcing function $\bf_j$. We use Dirichlet boundary conditions $\bu_j(\bx,t)=\b0$ at the $j^{th}$ realization. Assuming $\nu_j(\bx )\in L^\infty(\mathcal{D})$ and the supremum over this domain will be bounded. Also $\nu$ has a minimum, namely $\nu_j(\bx)\ge \nu_{j,\text{min}}>0$ where $\nu_{j,\text{min}} = \displaystyle{\min_{\bx\in \mathcal{D}}}\nu_j(\bx)$. 

When computing Navier Stokes flow ensembles, even in regular scenarios, a single sample can call for many iterations with $\mathit{J}$ different realizations. We want to develop an algorithm that will solve this simple case, as well as the case of multiple samples with J different realizations. "In numerical simulation of flows with incomplete data, quantification of uncertainty, increased forecasting skill, quantification of flow sensitivities and other issues lead to the problem of computing ensembles $u_j, p_j$ of solutions of the Navier Stokes equations."\cite{jiang2015higher} We are primarily concerned with the computational complexity for the calculation, and we will discretize in such a way that avoids undue computational cost. \textbf{{insert more discussion here}} 

Utilizing backward Euler method to approximate $\bu_j,t$ we have: 
```
u_{j,t}=\dfrac{u_j(t^{n+1})-u_{j,h}(t^n)}{\Delata t}
```
Here we use $\bu_{j,h}-\bu_j^n$ as an approximation for u_j(t^{n+1}, which is the present, unknown solution.


 
---
\section{Notation and Preliminaries}

The functional space for $\bu$ and p are given by:
```
\begin{align}\bX=H^1_0(\mathcal{D})=\{\bu \in L^2(\Omega)^d ~&| ~\nabla u \in L^2(\mathit{D})^{d\times d}, ~~u = 0 \text{~on~} \delta \mathit{D}\}\\
Q=L^2_0(\mathcal{D})=\{q\in L^2(\mathcal{D})~&|~ \int_\Omega q ~~d\Omega =0\}\end{align}
```
We take $H_0$: on the boundary, where velocity is equal 0.


\section{Numerical Experiments}
In this section, we present a series of numerical tests that verify the predicted convergence rates and show the performance of the scheme on some benchmark problems. In all experiments, we consider $\bx=(x_1,x_2)$ for 2D problems, pointwise-divergence free $(\mathbb{P}_2,\mathbb{P}_1^{disc})$ Scott-Vogelius element for the BESCoupled scheme, and $(\mathbb{P}_2,\mathbb{P}_1)$ Taylor-hood element for the BESProj scheme on a barycentxer refined triangular meshes.
  

\subsection{Convergence Rates Verification}

In the first experiment, we verify the theoretically found convergence rates beginning with the following analytical solution:
\[ u=\left(\begin{array}{c} \cos x_2+(1+e^t)\sin x_2 \\ \sin x_1+(1+e^t)\cos x_1 \end{array} \right),\;\;\text{and}\;\; \ p =\sin(x_1+x_2)(1+e^t),
\]
on domain $\mathcal{D}=[0,1]^2$. Then, we introduce noise as $u_j=(1+k_j\epsilon)u$, and $p_j=(1+k_j\epsilon)p$, where $\epsilon$ is a perturbation parameter, $k_j:=(-1)^{j+1}4\lceil j/2\rceil/J$, $j=1,2,\cdots, J$, and $J=20$. We consider $\epsilon=0.01$, this will introduce $10\%$ noise in the initial condition, boundary condition, and the forcing functions. The forcing function $/\bif_j$ is computed using the above synthetic data into \eqref{gov1}. We assume the viscosity $\nu$ is a continuous uniform random variable, and consider three random samples of size $J$ as $\nu\sim
\mathcalu(0.009, 0.011)$ with $E[\nu]=0.01$,  $\nu\sim
\mathcalu(0.0009, 0.0011)$ with $E[\nu]=0.001$, and $\nu\sim
\mathcalu(0.00009, 0.00011)$ with $E[\nu]=0.0001$. The initial and boundary conditions are $\bu_{j,h}^0=\bu_{j}(\bx,0)$, and $\bu_{j,h}|_{\partial\cD}=\bu_j$, respectively. 

\section*{Viscosity = 0.01}
We run the program nse-spatial- with a viscosity  of $\nu= 0.01$, and a random sample of 20 viscosities. The output is as follows:\vskip12pt


We run the program nse-tem-092624.cc with a viscosity of $\nu= 0.01$, and a random sample of 20 viscosities. The output is as follows:
```
\vskip12pt
\begin{table}[h!]
    \centering
    \begin{tabular}{|l|l|l|l|l|l|l|}
    \hline
    $\Delta t$& dim($X_h$) & $||u-u_h||_{2,1}$& Rate$_u$ & dim($Q_h$)& $||p-p_h||_{2,2}$ &Rate$_p$\\
    \hline
    2& 33282 & 0.290031 &  & 4225 & 0.615951 &  \\
    \hline
    4& 33282 & 0.126205 & 1.20 & 4225 & 0.291304 & 1.08 \\
    \hline
    8& 33282 & 0.05919 & 1.09 & 4225 & 0.140391 & 1.05 \\
    \hline
    16& 33282 & 0.0286108 & 1.05 & 4225 & 0.0687603 & 1.03 \\
    \hline
    32& 33282 & 0.0140699 & 1.02 & 4225 & 0.0340082 & 1.02 \\\hline
    \end{tabular}
    \caption{Temporal convergence with $\mathbb{E}[\nu]=0.001$ }
    \label{tab:my_label}
\end{table}
```




\bibliographystyle{plain}
% mike
\bibliography{snse}

\end{document}