
# Terms and Symbols
1. change in velocity wrt time, $\mathbf{u}_t = \dfrac{\partial \mathbf{u}}{\partial t}$
2. Laplacian, $\nabla^2$
3. density, $\rho$
4. Pressure (scalar), $p$
5. kinematic viscosity, $\nu$
6. dynamic viscosity, $\mu$
# Background and Research Motivation
- From a mathematical perspective, the behaviors of different physical phenomena can all be described through a class of equations known as Partial Differential Equations (PDEs). For example, the governing equations that describe wave-like behavior can be applied to any physical phenomena that has wavelike motion. Finding the exact solution for a PDE provides a model for how state variables such as pressure, velocity, or temperature change, within a system, over space and time.  One such are the Navier-Stokes Equations (NSEs). Navier-Stokes Equations are a system of three-dimensional, 2nd order of PDEs that serve as the governing equations for the conservation of momentum, mass, and energy within a fluid. They operate as an extension of Netwon's Second Law of Motion, where the equations are comprised of terms to account for the internal and external forces that affect fluid flow.
- $$\rho(\dfrac{\partial \mathbf{u}}{\partial t}+\mathbf{u}\cdot\nabla\mathbf{u})=-\nabla p+\mu\nabla^2\mathbf{u}$$
-  Here, $\rho\frac{\partial \mathbf{u}}{\partial t}$, represents the inertial term, and shows the change in momentum of the fluid with respect to time.  The convection term, $\rho(\mathbf{u} \cdot \nabla \mathbf{u})$, represents the movement of the fluid due to the velocity vector field within the fluid. The pressure gradient term $-\nabla p$ is to account for the force exerted by pressure changes within the fluid. 
   - Represents the transport of momentum due to the fluid's velocity field.
   - This term is nonlinear and accounts for the advection of fluid particles, which is a key source of complexity in fluid dynamics.

2. **Pressure Gradient Term: $(-\nabla p$)**
   - Represents the force exerted by pressure differences within the fluid.
   - Drives the fluid flow from regions of high pressure to low pressure.

3. **Viscous Term: $(\mu \nabla^2 \mathbf{u})$**
   - Represents the diffusion of momentum due to viscosity.
   - Accounts for the internal friction within the fluid, which tends to smooth out velocity gradients.

4. **External Force Term: (\mathbf{f})**
   - Represents any external forces acting on the fluid, such as gravity or electromagnetic forces.
   - These forces can influence the motion and behavior of the fluid.
- Each component of velocity varies in every direction, with respect to time. The pressure solution is a scalar vector function  
- Finding the exact solution for NSEs analytically has proven difficult because of the nonlinear term \mathbf{u} \cdot \nabla \mathbf{u} within the formulation. In addition, the equations themselves involve functions of multiple variables, interacting together simultaneously.  Since an analytic solution is not always attainable, several numerical methods have been developed to approximate solutions for the NSEs so that observations can lead to some quantitative result.  
- 
- The equations that we have developed are for "ideal" scenarios that do not mimic the real world conditions. 
- It is easier to describe the changes throughout a system than it is to pinpoint the exact state of the system at a point in time. 
- In general, when a solution to a PDE is sought, numerical methods are often employed.  

Partial Derivatives
partial derivative of position wrt = 
 
 Add motivation at the beginning. 
  What is incompressible flow?
- [ ] What is the viscosity?
- [x] What are the Navier-Stokes Equations? ✅ 2025-03-01
- [ ] Why are you doing this? What is the significant? Why do we need to do it? Why is it important?
What is the uncertainty quantification? Why do we need to quantify the uncertainty?

- Eddy viscosity models are used with the NSEs to accurately model turbulence within a system. 
- ensemble averages - the purpose is to 
## Problem derivation - Intro to Navier-Stokes Eqs
- The flow variables of the Navier-Stokes equations, density $\rho$, velocity $u$, and pressure $p$, etc. are considered as continuous functions of space and time. These functions are fields. 
	-  **Fields:** how to represent a field on the computer in such a fashion that we can perform operations with them
	- $\mathbf{u}(\mathbf{x},t)$ represents the velocity of a particle within the fluid at a specific vector position $\mathbf{x}$, as time progresses, $t$. 
- **Assumptions**: When studying a physical process or investigating phenomena, it is customary to make assumptions about the physical setting or the equation parameters. This is to focus on the governing equations, relationships between state variables, and the properties of the phenomena itself. 
	- The equations that we have developed are for "ideal" scenarios that do not mimic the real world conditions. 
	- Negligible effects of a variable or some physical assumption
		- incompressibility is an assumption we make for the system -> requires that the divergence of the velocity field is zero everywhere.
		- we can make this assumption because compression is negligible
- to use these formulations for accurate analysis we need to add additional terms, factors to account for these
- In addition, these additional factors make the formulations nigh impossible to solve with traditional methods...enter computational analysis

- **development of an efficient, accurate, and robust computation for turbulent fluid flow is ongoing, and is the focus of this work.** 
- **Why Numerical Methods:** Since they are Partial Differential Equations, and analytic solutions for these are not always analytically feasible, numerical methods have been developed to approximate solutions, and are the focus of this work. 

For an incompressible fluid, the Navier-Stokes equations can be written as:
$$\dfrac{\partial \mathbf{u}}{\partial t}=-\mathbf{u}\cdot\nabla\mathbf{u}+\alpha\nabla^2\mathbf{u}-\dfrac{\nabla p}{\rho}$$
with the requirement that $\nabla \cdot u = 0$
Where 
1. advection is covered by the $-\mathbf{u} \cdot \nabla \mathbf{u}$ term
2. diffusion is covered by the $\alpha \nabla^2 \mathbf{u}=\alpha \nabla \cdot \nabla \mathbf{u}$ term
3. pressure is covered by the $\nabla p/\rho$ term

- $(\mathbf{u})$ is the velocity vector field of the fluid.
- $(t)$ is time.
- $(\rho)$ is the fluid density.
- $(p)$ is the pressure field.
- $(\mu)$ is the dynamic viscosity of the fluid.
- $(\mathbf{f})$ represents external forces (e.g., gravity).
### Boundary and Initial Conditions
 
## Numerical Analysis of Incompressible Fluid Flow

### Method of Manufactured Solutions
The Method of Manufactured Solutions (MMS) is a testing method used in verifying that our numerical scheme is performing properly. For our given PDE, a solution of the appropriate order is assumed for the equation. This solution allows for the computation of the spatial and temporal derivatives for the problem. For the spatial study, the temporal finite difference scheme will represent the solution exactly, while the spatial solution is not exactly represented by finite element shape functions. Conversely, during the temporal study, the spatial solution is exactly represented, and the temporal solution is not. In the context of our problem, we assume an exact solution for velocity, and 

 used to validate the numerical implementation of the EEV scheme
- The backward Euler method would then be used to compute the future values of the solution based on the current state, and these computed values can be compared against the manufactured solution to check for accuracy.
- We will use the finite element method within the dealii library to construct the individual elements over which we will approximate the state variables of the fluid. 

### EEV and the uses of ensemble data in numerical schemes

Viscosity is not constant in real world scenarios. In practice viscosity involves noise. Our arrays introduce noise. 

visocisty causes randomness and ill conditions - enter stochasticity 


From Backward Euler to EEV scheme
$y'(t_{i-1}) = \lambda y(t_{i+1})$


To accurately model the effects of variable viscosity, we take a random sample of viscosities, and compute their mean. 

# Introduction
We propose an algorithm to compute the homogeneous Newtonian fluid flow that is governed by the non-linear stochastic PDE,  $$\begin{align}
\mathbf{u_t}+\mathbf{u}\cdot \nabla \mathbf{u}-\nabla \cdot (\nu(\mathbf{x},\omega) \nabla \mathbf{u})& + \nabla p = f(\mathbf{x},t,\omega)\\
\nabla \cdot \mathbf{u} &= 0\\
\end{align}$$
Here, the vector $\mathbf{u}_t$ represents the unknown time derivative of the velocity field $\mathbf{u}$ at some future time, t. The scalar pressure is given by $p$ and the external force, $\mathbf{f}(\mathbf{x},t,\omega)$. Viscosity, $ν(\mathbf{x},ω)$ is a random field that depends on a spatial variable, the position vector $\mathbf{x}(t)$, and a random variable $ω$ that is taken from a random field, Ω.

We define a complex polyhedral physical domain, $\mathcal{D}⊂R^d$ (d = 2,3) with $∂\mathcal{D}$ on the boundary, where the simulation end-time is represented by T > 0. The vector-valued time derivative for velocity, $\mathbf{u}_t$, is on $\mathcal{D}×(0,T]×Ω ∈R^d$, and the scalar-valued pressure function, p is on D×(0,T] ×Ω ∈R. Specifically, we know that $\mathbf{u}_t$ is square integrable, that is, L2(D) such that Ω ||ut||2dΩ < ∞.
Velocity belongs to the Hilbert space given by $X := H^1_0(\mathcal{D})$, pressure to the pressure space given by $Q = L^2_0(\mathcal{D})$, and Ω within the stochastic space from which we will select our random variable, $W := L^2_P(Ω)$

Let the inner product in L2(D), be denoted by (·,·). In order to arrive at the weak formulation of our equation, we must multiply by test functions, $ϕ = (v,q)$, and perform integration over the domain Ω. We will take v ∈X and q∈Q. The weak formulation can be thought of as finding u ∈X ⊗W and p∈Q⊗W such that:
$$(u_t,v) + (u ·∇u,v)+(ν∇u,∇v) + (p,∇·v) = (f,v), $$
$$(∇·u,q) = 0.$$

Let $\textit{J}$ be the number of realizations -- that is, the number of solutions, for the equations.  We can rewrite the strong form as: We want to find $(\mathbf{u}_j, p_j)$ such that  

$$\begin{align}
\mathbf{u}_{j,t} +\mathbf{u}_j \cdot \nabla \mathbf{u}_j - \nabla \cdot (\nu_j(\mathbf{x})\nabla \mathbf{u}_j)&+ \nabla p_j=\mathbf{f}_j(\mathbf{x},t),  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T], \\
    \nabla \cdot \mathbf{u}_j& = 0,  \hspace{0.5cm} \text{in~} \mathcal{D} \times (0,T].
\end{align}$$

Where $\mathbf{u}_j$ and $p_j$ are the velocity and pressure solutions, respectively. For each realization $j = 1,2,...\mathit{J},$ each corresponding to a kinematic viscosity $\nu_j$, a forcing function $\mathbf{f}_j$. Assuming $\nu_j(\mathbf{x} )\in L^\infty(\mathcal{D})$ and a bounded supremum over this domain. Also $\nu$ has a minimum, namely $\nu_j(\mathbf{x})\ge \nu_{j,\text{min}}>0$ where $\nu_{j,\text{min}} = \displaystyle{\min_{\mathbf{x}\in \mathcal{D}}}\nu_j(\mathbf{x})$. 

When computing Navier Stokes flow ensembles, even in regular scenarios, a single sample can call for many iterations with $\mathit{J}$ different realizations. We want to develop an algorithm that will solve this simple case, as well as the case of multiple samples, with $J$ different realizations. In numerical simulation of flows with incomplete data, quantification of uncertainty, increased forecasting skill, quantification of flow sensitivities and other issues lead to the problem of computing ensembles $\mathbf{u}_j, p_j$ of solutions of the Navier Stokes equations. \say{We are primarily concerned with the computational complexity for the calculation, and we will discretize in such a way that avoids undue computational cost. \cite{jiang2015higher}} Using an implicit-explicit time discretization and keeping the resulting coefficient matrix independent of the ensemble member, leads to the method:

Utilizing the linearized backward Euler method, we propose the following discrete scheme of 

For $j=1,2,\cdots,J$, find $(\mathbf{u}_{j,h}^{n+1},p_{j,h}^{n+1})$:

$$\begin{align}
\frac{\mathbf{u}_{j,h}^{n+1}}{\Delta t} + <\mathbf{u}_h>^n \cdot &\nabla \mathbf{u}_{j,h}^{n+1}-\nabla \cdot (\bar{\nu}\nabla \mathbf{u}_{j,h}^{n+1}) - \gamma\nabla(\nabla \cdot\mathbf{u}_{j,h}^{n+1})-\nabla \cdot (2\nu_{T}(\mathbf{u}^{'}_{h},t^n)\nabla \mathbf{u}_{j,h}^{n+1}) \nonumber\\
&+\nabla p_{j,h}^{n+1}=\mathbf{f}_{j,h}(t^{n+1})+\frac{\mathbf{u}_{j,h}^n}{\Delta t}-\mathbf{u}_{j,h}^{'n}\cdot\nabla \mathbf{u}_{j,h}^n+\nabla\cdot\left(\nu_{j,h}^{'}\nabla \mathbf{u}_{j,h}^{n}\right),\\
&\hspace{3.0cm} \nabla \cdot \mathbf{u}_j^{n+1}=0.
\end{align}$$

Here $\mathbf{u}_{j,h}^{n+1}$ as an approximation for $\mathbf{u}_j(t^{n+1})$, the present unknown solution, and $h$ is the maximum mesh width.


With some algebra, we have moved the present solution to the RHS, added an eddy viscosity term $\nu_T$, which is of $\mathcal{O}(\Delta t)$, having been defined using mixing length phenomenology. We define the ensemble mean as: 
$$\begin{align}
<\mathbf{u}_h>^n:=\frac{1}{J}\sum_{j=1}^{n}\mathbf{u}^n_{j,h},\hspace{0.5cm} \mathbf{u}'^n_{j,h} :=\mathbf{u}_{j,h}^n-<\mathbf{u}>^n \end{align}$$

where u

Here, the eddy viscosity, $\nu_T$ is defined as 

$$\begin{align}
    \nu_t(\mathbf{u}'_h, t^n):=\mu\Delta t(l^n)^2, \text{where}~(l^n)^2 =\sum^J_{j=1} |\mathbf{u}'^n_j|^2.
\end{align}$$

### Jiang Motivations -> Carati sections 2,3

**To accurately model the effects of variable viscosity, we take a random sample of viscosities, and compute their mean.** 

# Notation and Preliminaries

## Taylor Hood Element
The Taylor-Hood element is a mixed finite element method that uses a higher-order polynomial for the velocity field and a lower-order polynomial for the pressure field. This combination helps satisfy the Ladyzhenskaya-Babuška-Brezzi (LBB) condition, ensuring stability and convergence of the solution.

the Taylor-Hood element is used to approximate the velocity and pressure fields in the Navier-Stokes equations. The velocity is typically approximated using a $(Q_{degree+1}^d)$ polynomial, while the pressure is approximated using a $(Q_{degree})$ polynomial.

# Theorem and Proof

# Deal.II implementation
There are many libraries, software, and packages that have code implementations for utilizing finite elements to find computational solutions for PDEs. Many of these libraries, however, tend to be for use within a specific problem area or physical phenomena, and have not been constructed for a more general, abstracted use. \say{Most available software tools would either be tuned to performance, but be specialized to one class of applications, while others offered flexibility and generality at a significant waste of memory and computing power.} [cite deal.II] deal.II is an open-source, object-oriented C++ library constructed with this issue in mind. It is equipped with templated classes, custom functions and data types that are typically used in finite element analysis problems, and takes advantage of the modular nature of C++ to give the user the ability to use the library for a variety of physical scenarios. Its mission is \say{to provide well-documented tools to build finite element codes for a broad variety of PDEs, from laptops to supercomputers.} [cite deal.ii ] Because deal.II is open source, users can use the library to further develop for their own applications. In this fashion, deal.II addresses the issues of adaptability and implementation across different problem areas. In addition to providing the library, a comprehensive tutorial suite is included. These tutorials have example problems, complete with supporting mathematical theory, error analysis, sample C++ code, visualizations, practical applications and extensions. The code used in this work was written by extending concepts covered in the deal.II tutorial suite.
- step-3 extensions
	- Framework for FEM in C++, in the context of the deal.II library. 
- step-6 extensions
	- adaptive mesh refinement
- step-8 extensions
- step-20 extensions
	- block linear solvers
- step-29 extensions
- step-49 extensions
	- Outlines the steps to implement a custom mesh from an alternative software such as gmsh, rather than utilizing the built-in meshing functions within deal.II. This allows for calculations to be performed on a wide variety of shape domains, such as the lid driven cavity. 
- step-57 extensions

## FEM and its use in CFD, wrt deal.II

Define the weak form of the pde
1. Mesh Generation over the domain, discretize (`make_grid():`), called the preprocessing
2. Create the matrix system (`steup_system():`) -- This is where the DoFHandler object is initialized and the setup_system function will correctly size the various objects that pertain to the linear algebra 
	1. called separately from mesh generation function because it is called repeatedly over any mesh refinements that occur
3. Assembling the system of equations (`assemble_system():`) 
	1. computation of the RHS of the matrix equation
4. Solving the system (`solve():`) -- the function that computes the solution $\mathbf U$ of the linear system $\mathbf {AU}=\mathbf{F}$ 
5. print the results (`output_results():`) -- print the results, create a visualization, etc.

## UMFPACK sparse direct solver

# Convergence Rates Test
Tables and discussion.

# gmsh implementation

# Lid Driven Cavity
A common benchmarking problem in CFD is the lid driven cavity. It is a physical experiment where a fluid, initially at rest is placed in a cubic or rectangular box and a shearing force acts on the top surface of the fluid. It could be caused by a moving lid, or even by the motion of another fluid itself. There is no body force acting on or within the fluid and boundary conditions for velocity, $u = 0$ on the bottom and sides of the container. At the lid, the boundary 


A parenthetical example of our experiment is as follows: A cube is generated in the software GMesh on the domain $[-1,1]$, with a volume of 8 cubic units. We generate a 2D and 3D unstructured quadrilateral mesh by which we will pass to the code for refinement and calculation. The parameter file holds the following values: $\mu = 1, \gamma = 1, \mathbb{E}[\nu]=0.001, \epsilon = 0.001$ and $n$ timesteps. 
After 

---
$$\begin{align}\end{align}$$