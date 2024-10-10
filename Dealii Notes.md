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

\section {Introduction}
The time-dependent, dimensionless, viscoresistive, incompressible Navier-Stokes equations for computing the homogeneous Newtonian fluid flow is given by the following non-linear stochastic PDEs: 
$$\begin{align}
    \mathbf {u_t} +\mathbf{u} \cdot \nabla \mathbf{u} - \nabla \cdot (\nu(\mathbf{x}, \omega)\nabla \mathbf{u})&+ \nabla p=\mathbf{f}(\mathbf{x},t,\omega)  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T] \\
    \nabla \cdot \mathbf{u}& = 0  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T]\\
    \mathbf{u}(\mathbf{x},0,\omega)&=u^0(\mathbf{x}), \hspace{0.5cm} \mathbf{x} \in \mathcal{D}
\end{align}$$

Here, the vector $\mathbf{u}_t$ represents the unknown time derivative of the velocity field $\mathbf{u}$ at some future time, t. The scalar pressure is given by p and the external force, $\mathbf{f}(\mathbf{x},t,\omega)$. Viscosity, $\nu(\mathbf{x}, \omega)$ is a continuous equation that depends on a position vector $\mathbf{x}$, and a random variable $\omega$ that is taken from a random field $\Omega$. The complete probability measure space is given by $(\Omega,\mathcal{F},P)$, where $\Omega$ is the set or probability space, $F \subset 2^\Omega$ is the $\sigma$-algebra, and P represents all possible values for $F$, namely the probability measure, $P: F \to [0,1]$. 

The vector-valued function for velocity, $\mathbf{u}$ is on $\mathcal{D} \times (0,T] \times \Omega \in \mathbb{R}^3$ and the scalar-valued pressure function, $p$ is on $\mathcal{D} \times (0,T] \times \Omega \in \mathbb{R}$. Specifically, we know that $\textbf{u}$ is square integrable, that is, $\text{L}^2(\mathcal{D})$ such that $\int_\Omega ||\mathbf{u}||^2 d\Omega < \infty$. The velocity vector space is given by: $$\mathbf{X} : H_o^1(\mathcal{D})=\{\mathbf{u} \in \text{L}^2(\Omega)^d ~|~ \nabla \mathbf{u} \in \text{L}^2, u = 0 ~~\text{on} ~~\delta \mathcal{D}\}$$ The pressure function domain is given by:
$$\text{Q}: \text{L}^2_o = \{q \in L^2(\mathcal{D}) ~|~ \int_\Omega q~ d\Omega =0\}$$
The stochastic space by which we take our random variable, $\Omega$ is given by:  $$\text{W} = L^2_\rho (\Omega)$$
Let the inner product, $\text{L}^2(\mathcal{D})$, be denoted by $(\cdot, \cdot)$. In order to arrive at the weak formulation of our equation, we must multiply by test functions, $\mathbf v$ and perform integration over the domain $\Omega$. We will take $\mathbf v$ from the vector space X such that $\mathbf v \in X$, with the same properties as $\textbf{u}$ on the boundary. The weak formulation can be thought of as finding a $\mathbf{u} \in \mathbf{X} \otimes \mathbf{W}$ and  $p\in \mathbf{Q} \otimes \mathbf{W}$ such that:

$$\begin{align}
(\mathbf{u_t},\mathbf{v})+(u \cdot \nabla u, v)+&(\nu\nabla\mathbf{u}, \nabla\mathbf{v}) + (p,\nabla \cdot \mathbf{v})=(\mathbf{f},\mathbf{v})\\
(\nabla \cdot \mathbf{u},q)&=0
\end{align}$$

 Because we have taken the variables from the stochastic space, let us take the expectation of both sides:
$$\begin{align}
\mathbb{E}[(\mathbf{u_t},\mathbf{v})]+\mathbb{E}[(u \cdot \nabla u, v)]+&\mathbb{E}[(\nu\nabla\mathbf{u}, \nabla\mathbf{v})] - \mathbb{E}[(p,\nabla \cdot \mathbf{v})]=\mathbb{E}[(\mathbf{f},\mathbf{v})]\\
\mathbb{E}[(\nabla \cdot \mathbf{u},q)]&=0
\end{align}$$

Because viscosity is a continuous function, we take a random sample of viscosities, and compute their mean. To model the current $\nu(\mathbf{x}, \omega)$ equation, we will use a d-dimensional random variable $\mathbf{y}(\omega) = (y_1(\omega), y_2(\omega), ..., y_d(\omega))$ with the assumption that $\mathbb{E}[\mathbf{y}]=0, \text{Variance}[\mathbf{y}]=I_d$. Using standard integration as Expectation our problem becomes: 

```$$\begin{align}
\begin{split}
\int_\Gamma (\mathbf{u_t},\mathbf{v})\rho(\mathbf{y}) d\mathbf{y}+\int_\Gamma (\mathbf{u} \cdot \nabla \mathbf{u}, \mathbf{v})\rho(\mathbf{y}) d\mathbf{y}+&\int_\Gamma (\nu(\mathbf{x},\mathbf{y} )\nabla \mathbf{u}, \nabla \mathbf{v})\rho(\mathbf{y}) d\mathbf{y}  \\- \int_\Gamma (p,\nabla \cdot \mathbf{v})\rho(\mathbf{y}) d\mathbf{y}=&\int_\Gamma (\mathbf{f},\mathbf{v})\rho(\mathbf{y}) d\mathbf{y} \hspace{1cm} \forall \mathbf{x}\in \mathbf{X}\otimes \mathbf{Y}\\
\end{split}
\end{align}
\begin{align}
\int_\Gamma (\nabla \cdot \mathbf{u},q)\rho(\mathbf{y}) d\mathbf{y}&=0 \hspace{1.5cm} \forall q \in \mathbf{Q}\otimes \mathbf{Y}
\end{align}$$
```
In our viscosity assumption, we have $\nu(\mathbf{x},\mathbf{y})=\nu_o(\mathbf{x})+\displaystyle{\sum_{\mathscr{l}=1}^N} \nu_\mathscr{l}(\mathbf{x})y_\mathscr{l}$ and assume affline dependence of the random variables for viscosity. 

When computing Navier Stokes flow ensembles, even in regular scenarios, a single sample can call for many iterations with $\mathit{J}$ different realizations. We want to develop an algorithm that will solve this simple case, as well as the case of multiple samples with J different realizations. "In numerical simulation of flows with incomplete data, quantification of uncertainty, increased forecasting skill, quantification of flow sensitivities and other issues lead to the problem of computing ensembles $u_j, p_j$ of solutions of the Navier Stokes equations."[1] 

Let \textit{J} be the number of realizations -- that is, number of solutions, for equation.  We can rewrite the strong form as: We want to find $(u_j, p_j)$ such that  $$\begin{align}
    \mathbf {u}_{j,t} +\mathbf{u}_j \cdot \nabla \mathbf{u}_j - \nabla \cdot (\nu_j(\mathbf{x})\nabla \mathbf{u}_j)&+ \nabla p_j=\mathbf{f}_j(\mathbf{x},t)  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T] \\
    \nabla \cdot \mathbf{u}_j& = 0  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T]
\end{align}$$
Where $\mathbf{u}_j$ and $p_j$ are the velocity and pressure solutions, for each realization $j = 1,2,...\mathit{J}$ , each corresponding to a kinematic viscosity $\nu_j$, for a forcing function $\mathbf{f}_j$. We use Dirichlet boundary conditions, 

Assuming $\nu_j(\mathbf{x} )\in L^\infty(\mathcal{D})$ and the supremum over this domain will be bounded. Also $\nu$ has a minimum, namely $\nu_j(\mathbf{x})\ge \nu_{j,\text{min}}>0$ where $\nu_{j,\text{min}} = \displaystyle{\min_{\mathbf{x}\in \mathcal{D}}}\nu_j(\mathbf{x})$. 

We are primarily concerned with the computational complexity for the calculation, and we will discretize in such a way that avoids undue computational cost. \textbf{{insert more discussion here}} Small change in viscosity will result in a large change in the velocity. The problem is ill conditioned. The algorithm is an efficient algorithm, but not straightforward. 

 
---
\section{Notation and Preliminaries}

The functional space for $\mathbf{u}$ and p are given by:
$$\begin{align}\mathbf{X}=H^1_o(\mathcal{D})=\{\mathbf{u} \in L^2(\Omega)^d ~&| ~\nabla u \in L^2(\mathit{D})^{d\times d}, ~~u = 0 \text{~on~} \delta \mathit{D}\}\\
Q=L^2_o(\mathcal{D})=\{q\in L^2(\mathcal{D})~&|~ \int_\Omega q ~~d\Omega =0\}\end{align}$$

We take $H_o$: on the boundary, where velocity is equal 0.


\section{Numerical Experiments}
In this section, we present a series of numerical tests that verify the predicted convergence rates and show the performance of the scheme on some benchmark problems. In all experiments, we consider $\mathbf{x}=(x_1,x_2)$ for 2D problems, pointwise-divergence free $(\mathbb{P}_2,\mathbb{P}_1^{disc})$ Scott-Vogelius element for the BESCoupled scheme, and $(\mathbb{P}_2,\mathbb{P}_1)$ Taylor-hood element for the BESProj scheme on a barycenter refined triangular meshes.
  

\subsection{Convergence Rates Verification}

In the first experiment, we verify the theoretically found convergence rates beginning with the following analytical solution:
\[ {u}=\left(\begin{array}{c} \cos x_2+(1+e^t)\sin x_2 \\ \sin x_1+(1+e^t)\cos x_1 \end{array} \right),\;\;\text{and}\;\; \ p =\sin(x_1+x_2)(1+e^t),
\]
on domain $\mathcal{D}=[0,1]^2$. Then, we introduce noise as $u_j=(1+k_j\epsilon)u$, and $p_j=(1+k_j\epsilon)p$, where $\epsilon$ is a perturbation parameter, $k_j:=(-1)^{j+1}4\lceil j/2\rceil/J$, $j=1,2,\cdots, J$, and $J=20$. We consider $\epsilon=0.01$, this will introduce $10\%$ noise in the initial condition, boundary condition, and the forcing functions. The forcing function $/\bif_j$ is computed using the above synthetic data into \eqref{gov1}. We assume the viscosity $\nu$ is a continuous uniform random variable, and consider three random samples of size $J$ as $\nu\sim
\mathcal{U}(0.009, 0.011)$ with $E[\nu]=0.01$,  $\nu\sim
\mathcal{U}(0.0009, 0.0011)$ with $E[\nu]=0.001$, and $\nu\sim
\mathcal{U}(0.00009, 0.00011)$ with $E[\nu]=0.0001$. The initial and boundary conditions are $\bu_{j,h}^0=\bu_{j}(\bx,0)$, and $\bu_{j,h}|_{\partial\cD}=\bu_j$, respectively. 

\section*{Viscosity = 0.01}
We run the program nse-spatial- with a viscosity  of $\nu= 0.01$, and a random sample of 20 viscosities. The output is as follows:\vskip12pt


We run the program nse-tem-092624.cc with a viscosity of $\nu= 0.01$, and a random sample of 20 viscosities. The output is as follows:\vskip12pt
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






\end{document}