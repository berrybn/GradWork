# Background and Research Motivation
- **Open:** Through the study of fluid motion, we have developed travel by air and sea, perfected intravenous medical treatments, and harnessed the power of naturally flowing water itself to generate electricity. There are many physical phenomena that can be described using the equations that govern fluid motion. Undeniably, they can describe fluid flow like blood in a vessel or fluid motion through a pipe. But they also can be used to describe phenomena such as air flow over a foil, the mixing of hot and cold air within developing weather systems, and can even be seen as analogous to the behavior of electromagnetic fields. 
- **NSE:** The Navier-Stokes equations are famously used to describe the conservation of momentum, mass, and energy within a fluid. They are the governing equations that describe the forces of fluid motion and the physical conditions of fluid flow.
## Problem derivation - Intro to Navier-Stokes Eqs
- The flow variables of the Navier-Stokes equations, density $\rho$, velocity $u$, and pressure $p$, etc. are considered as continuous functions of space and time. These functions are fields. 
	-  **Fields:** how to represent a field on the computer in such a fashion that we can perform operations with them
	- $\mathbf{u}(\mathbf{x},t)$ represents the velocity of a particle within the fluid at a specific vector position $\mathbf{x}$, as time progresses, $t$. 
- **Assumptions**: When studying a physical process or investigating phenomena, it is customary to make assumptions about the physical setting or the equation parameters. This is to focus on the governing equations, relationships between state variables, and the properties of the phenomena itself. 
	- The equations that we have developed are for "ideal" scenarios that do not mimic the real world conditions. 
	- Negligible effects of a variable or some physical assumption — incompressibility is an assumption we make for the system -> requires that the divergence of the velocity field is zero everywhere
		- we can make this assumption because compression is negligible
- to use these formulations for accurate analysis we need to add additional terms, factors to account for these
- In addition, these additional factors make the formulations nigh impossible to solve with traditional methods...enter computational analysis

- development of an efficient, accurate, and robust computation for **turbulent fluid flow** is ongoing, and is the focus of this work. 
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
1. **Inertial Term: $(\rho \frac{\partial \mathbf{u}}{\partial t})$**
   - Represents the change in momentum of the fluid with respect to time.
   - Captures the unsteady or transient behavior of the fluid flow.

2. **Convective Term: (\rho (\mathbf{u} \cdot \nabla) \mathbf{u})**
   - Represents the transport of momentum due to the fluid's velocity field.
   - This term is nonlinear and accounts for the advection of fluid particles, which is a key source of complexity in fluid dynamics.

3. **Pressure Gradient Term: (-\nabla p)**
   - Represents the force exerted by pressure differences within the fluid.
   - Drives the fluid flow from regions of high pressure to low pressure.

4. **Viscous Term: (\mu \nabla^2 \mathbf{u})**
   - Represents the diffusion of momentum due to viscosity.
   - Accounts for the internal friction within the fluid, which tends to smooth out velocity gradients.

5. **External Force Term: (\mathbf{f})**
   - Represents any external forces acting on the fluid, such as gravity or electromagnetic forces.
   - These forces can influence the motion and behavior of the fluid.

 

## Numerical Analysis of Incompressible Fluid Flow

### Method of Manufactured Solutions
The Method of Manufactured Solutions (MMS) is a testing method used in verifying that our numerical scheme is performing properly. For our given PDE, a solution of the appropriate order is assumed for the equation. This solution allows for the computation of the spatial and temporal derivatives for the problem. For the spatial study, the temporal finite difference scheme will represent the solution exactly, while the spatial solution is not exactly represented by finite element shape functions. Conversely, during the temporal study, the spatial solution is exactly represented, and the temporal solution is not. In the context of our problem, we assume an exact solution for velocity, and 

 used to validate the numerical implementation of the EEV scheme
- The backward Euler method would then be used to compute the future values of the solution based on the current state, and these computed values can be compared against the manufactured solution to check for accuracy.
- We will use the finite element method within the dealii library to construct the individual elements over which we will approximate the state variables of the fluid. 

### EEV and the uses of ensemble data in numerical schemes

Viscosity is not constant in real world scenarios


From Backward Euler to EEV scheme
$y'(t_{i-1}) = \lambda y(t_{i+1})$

# Introduction
We propose an algorithm to compute the homogeneous Newtonian fluid flow that is governed by the non-linear stochastic PDE,  $$\begin{align}
\mathbf{u_t}+\mathbf{u}\cdot \nabla \mathbf{u}-\nabla \cdot (\nu(\mathbf{x},\omega) \nabla \mathbf{u})& + \nabla p = f(\mathbf{x},t,\omega)\\
\nabla \cdot \mathbf{u} &= 0\\
\end{align}$$
Here, the vector $\mathbf{u}_t$ represents the unknown time derivative of the velocity field $\mathbf{u}$ at some future time, t. The scalar pressure is given by $p$ and the external force, $\mathbf{f}(\mathbf{x},t,\omega)$. Viscosity, $ν(\mathbf{x},ω)$ is a random field that depends on a spatial variable, the position vector $\mathbf{x}(t)$, and a random variable $ω$ that is taken from a random field, Ω.

We define a complex polyhedral physical domain, $\mathcal{D}⊂R^d$ (d = 2,3) with $∂\mathcal{D}$ on the boundary, where the simulation end-time is represented by T > 0. The vector-valued time derivative for velocity, $\mathbf{u}_t$, is on $\mathcal{D}×(0,T]×Ω ∈R^d$, and the scalar-valued pressure function, p is on D×(0,T] ×Ω ∈R. Specifically, we know that ut is square integrable, that is, L2(D) such that Ω ||ut||2dΩ < ∞.
Velocity belongs to the Hilbert space given by $X := H^1_0(\mathcal{D})$, pressure to the pressure space given by $Q = L^2_0(\mathcal{D})$, and Ω within the stochastic space from which we will select our random variable, $W := L^2_P(Ω)$

Let the inner product in L2(D), be denoted by (·,·). In order to arrive at the weak formulation of our equation, we must multiply by test functions, $ϕ = (v,q)$, and perform integration over the domain Ω. We will take v ∈X and q∈Q. The weak formulation can be thought of as finding u ∈X ⊗W and p∈Q⊗W such that:
$$(ut,v) + (u ·∇u,v)+(ν∇u,∇v) + (p,∇·v) = (f,v), $$
$$(∇·u,q) = 0.$$
Let J be the number of realizations – that is, the number of solutions, for
the equations. We can rewrite the strong form as: We want to find (uj,pj) such
that
uj,t + uj ·∇uj −∇·(νj(x)∇uj) + ∇pj= fj(x,t), in D×(0,T], (1.11)
∇·uj = 0, in D×(0,T]. (1.12)
Where uj and pj are the velocity and pressure solutions, respectively. For
each realization j = 1,2,...J , each corresponding to a kinematic viscosity νj,
a forcing function fj. Assuming νj(x) ∈L∞(D) and a bounded supremum
over this domain. Also ν has a minimum, namely νj(x) ≥νj,min > 0 where
νj,min = min
νj(x).
x∈D
When computing Navier Stokes flow ensembles, even in regular scenarios,
a single sample can call for many iterations with J different realizations. We
want to develop an algorithm that will solve this simple case, as well as the case
of multiple samples, with J different realizations. In numerical simulation of
flows with incomplete data, quantification of uncertainty, increased forecasting
skill, quantification of flow sensitivities and other issues lead to the problem of
computing ensembles uj,pj of solutions of the Navier Stokes equations.”[4] We
are primarily concerned with the computational complexity for the calculation,
and we will discretize in such a way that avoids undue computational cost. ”Us-
ing an implicit-explicit time discretization and keeping the resulting coefficient
matrix independent of the ensemble member, leads to the method:
# Notation and Preliminaries
# Theorem and Proof
### Taylor Hood Element
The Taylor-Hood element is a mixed finite element method that uses a higher-order polynomial for the velocity field and a lower-order polynomial for the pressure field. This combination helps satisfy the Ladyzhenskaya-Babuška-Brezzi (LBB) condition, ensuring stability and convergence of the solution.

the Taylor-Hood element is used to approximate the velocity and pressure fields in the Navier-Stokes equations. The velocity is typically approximated using a $(Q_{degree+1}^d)$ polynomial, while the pressure is approximated using a $(Q_{degree})$ polynomial.
# Deal.II implementation
There are many libraries, software, and packages that have code implementations for utilizing finite elements to find computational solutions for PDEs. Many of these libraries, however, tend to be for use within a specific problem area or physical phenomena, and have not been constructed for a more general, abstracted use. \say{Most available software tools would either be tuned to performance, but be specialized to one class of applications, while others offered flexibility and generality at a significant waste of memory and computing power.} [cite deal.II] deal.II is an open-source, object-oriented C++ library constructed with this issue in mind. It is equipped with templated classes, custom functions and data types that are typically used in finite element analysis problems, and takes advantage of the modular nature of C++ to give the user the ability to use the library for a variety of physical scenarios. Its mission is \say{to provide well-documented tools to build finite element codes for a broad variety of PDEs, from laptops to supercomputers.} [cite deal.ii ] Because deal.II is open source, users can use the library to further develop for their own applications. In this fashion, deal.II addresses the issues of adaptability and implementation across different problem areas. In addition to providing the library, a comprehensive tutorial suite is included. These tutorials have example problems, complete with supporting mathematical theory, error analysis, sample C++ code, visualizations, practical applications and extensions. The code used in this work was written by extending concepts covered in the deal.II tutorial suite.
- step-3 extensions
	- Framework for FEM in C++, in the context of the deal.II library. 
- step-6 extensions
	- adaptive mesh refinement
- step-8 extensions
	- 
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
# Convergence Rates Test
Tables and discussion.

# gmsh implementation

# Lid Driven Cavity
A common benchmarking problem in CFD is the lid driven cavity. It is a physical experiment where a fluid, initially at rest is placed in a cubic or rectangular box and a shearing force acts on the top surface of the fluid. It could be caused by a moving lid, or even by the motion of another fluid itself. There is no body force acting on or within the fluid and boundary conditions for velocity, $u = 0$ on the bottom and sides of the container. At the lid, the boundary 


A parenthetical example of our experiment is as follows: A cube is generated in the software GMesh on the domain $[-1,1]$, with a volume of 8 cubic units. We generate a 2D and 3D unstructured quadrilateral mesh by which we will pass to the code for refinement and calculation. The parameter file holds the following values: $\mu = 1, \gamma = 1, \mathbb{E}[\nu]=0.001, \epsilon = 0.001$ and $n$ timesteps. 
After 

---
# InfoStream

## Steps 2, 3, and introducing the FEMethod 
https://dealii.org/current/doxygen/deal.II/step_3.html
Consider the Poisson eq $$\begin{align}-\Delta u&=f\\ u &=0
\end{align}$$
Using the partial differential equation notation:
$$\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}=f(x,y)$$
We will solve this equation on the square  $\Omega = [-1,1]^2$. We consider the particular case where $f(\mathbf{x})=1$ and will implement a more general case in step-4.

The steps needed to take to approximate the solution $u$ by a finite dimensional approx. 
After we define the weak formulation, we use the following steps of the **Finite Element Method**:
### Using the weak formulation and discretized space:
  
1. **Discretize** - Generate a mesh over the domain  (`make_grid():`) #preprocessing
2. **Create the matrix system** (`steup_system():`) -- This is where the DoFHandler object is initialized and the setup_system function will correctly size the various objects that pertain to the linear algebra #DoF 
	-  called separately from mesh generation function because it is called repeatedly over any mesh refinements that occur
3. **Assembling the system** of equations (`assemble_system():`) --computations of the cell matrix and RHS 
4. **Solving the system** (`solve():`) -- the function that computes the solution $\mathbf U$ of the linear system $\mathbf {AU}=\mathbf{F}$ 
	1. error calculations, if necessary
5. **print the results** (`output_results():`) -- print the results, create a visualization, etc.

**All called in the `run():` function** 

### Defining the weak form of the pde
We obtain the weak form by multiplying the equation by a **test function** $\varphi$ and integrating over the domain $\Omega$ $$-\int_\Omega \varphi \Delta u =\int_\Omega \varphi f $$ and with integration by parts it becomes: $$\int_\Omega \nabla\varphi\cdot\nabla u - \int_\Omega\varphi \mathbf{n} \cdot \nabla u = \int_\Omega \varphi f$$ Here the test function must satisfy the same kind of boundary conditions --that is, it needs to come from the tangent space of the set in which we seek the solution, and so on the boundary $\varphi=0$ and consequently the weak form becomes: $$(\nabla \varphi,\nabla u)=(\varphi, f)$$ where we have used the notation $(a, b)$ to represent $\int_\Omega a~ b$.  We then only need to find a function, $u$ for which the above statement is true, $\forall \varphi \in H^1$

Of course, we can't find such a function, $u$ on a computer in a general case, so we seek an approximation for $u_h(\mathbf{x})=\sum_j U_j \varphi_j(\mathbf{x})$, where the $U_j$ is a vector expansion of coefficients. Because we will compute $U_j$ as the solution of a linear or nonlinear system, they are called "unknowns" or the **degrees of freedom** (number of variables at each mesh node) and $\varphi_j(\mathbf{x})$ are the **finite element shape functions** we will use. 

A mathematical description of finite element problems is often to say that we are looking for a finite dimensional function $𝑢_ℎ∈𝑉_ℎ$ that satisfies some set of equations $𝑎(𝑢_ℎ,𝜑_ℎ)=(𝑓,𝜑_ℎ)$ for all test functions $𝜑_ℎ∈𝑉_ℎ$. In other words, all we say here is that the solution needs to lie in some space $𝑉_ℎ$. 

However, to actually solve this problem on a computer we need to choose a basis of this space; **this is the set of shape functions $𝜑_𝑗(𝐱)$ we have used above in the expansion of $𝑢_ℎ(𝐱)$ with coefficients** $𝑈_𝑗$. There are of course many bases of the space $𝑉_ℎ$, but we will specifically choose the one that is described by the finite element functions that are traditionally defined locally on the cells of the mesh. -- we will use the Lagrange basis. 

- THE SHAPE FUNCTION IS THE INTERPOLANT

Each of these shape functions and degrees of freedom is associated with a vertex of the mesh. Later examples will demonstrate higher order elements where degrees of freedom are not necessarily associated with vertices any more, but can be associated with edges, faces, or cells.

Once we have defined the set of test functions, $\varphi_i$, we can define the weak form of the discrete problem as: Find a function $𝑢_ℎ$, i.e., find the expansion coefficients $𝑈_𝑗$ mentioned above, so that $$(∇𝜑_𝑖,∇𝑢_ℎ)=(𝜑_𝑖,𝑓),~𝑖=0…𝑁−1.$$
Substituting our representation of $u_h$ in gives: 
$$\begin{align}
(∇𝜑_𝑖,∇𝑢_ℎ)&=(∇𝜑_𝑖,∇\big[\sum_𝑗𝑈_𝑗𝜑_𝑗\big])\\
&=\sum_𝑗(∇𝜑_𝑖,∇[𝑈_𝑗𝜑_𝑗])\\
&=\sum_𝑗(∇𝜑_𝑖,∇𝜑_𝑗)𝑈_𝑗
\end{align}$$

With this substitution, the problem reads: Find a vector $𝑈$ so that $$𝐴𝑈=𝐹,$$where the matrix $𝐴$ and the right hand side $𝐹$ are defined as: 

$$\begin{align}
𝐴_{𝑖𝑗}&=(∇𝜑_𝑖,∇𝜑_𝑗),\\𝐹_𝑖&=(𝜑_𝑖,𝑓)\end{align}$$

**Assembling the matrix and right hand side vector**
Now we know what we need -- objects that hold the matrix and vectors, as well as ways to compute $𝐴_{𝑖𝑗},~𝐹_𝑖$, and we can look at what it takes to make that happen:

The object for 𝐴 is of type `SparseMatrix` while those for $𝑈$ and $𝐹$ are of type `Vector`. We will see in the program what classes are used to solve linear systems.
**C++ classes for `dealii` that we need:**
- We need a way to form the integrals. In the finite element method, this is most commonly done using **quadrature**, i.e. the integrals are replaced by a weighted sum over a set of quadrature points on each cell. That is, we first split the integral over Ω into integrals over all cells, $$\begin{align}𝐴_{𝑖𝑗}=(∇𝜑_𝑖,∇𝜑_𝑗)&=\sum_{𝐾∈𝕋}∫_𝐾∇𝜑_𝑖⋅∇𝜑_𝑗,\\ F_i=(𝜑_𝑖,𝑓)&=\sum_{𝐾∈𝕋}∫_𝐾𝜑_𝑖𝑓
	\end{align}$$
    
    and then approximate each cell's contribution by quadrature:$$\begin{align}𝐴^𝐾_{𝑖𝑗}=∫_𝐾∇𝜑_𝑖⋅∇𝜑_𝑗&≈\sum_𝑞∇𝜑_𝑖(𝐱^𝐾_𝑞)⋅∇𝜑_𝑗(𝐱^𝐾_𝑞)𝑤^𝐾_𝑞,\\ 𝐹^𝐾_𝑖=∫_𝐾𝜑_𝑖𝑓&≈\sum_𝑞𝜑_𝑖(𝐱^𝐾_𝑞)𝑓(𝐱^𝐾_𝑞)𝑤^𝐾_𝑞\end{align}$$where $𝕋≈Ω$ is a `Triangulation` approximating the domain, $𝐱^𝐾_𝑞$ is the 𝑞th quadrature point on cell 𝐾, and $𝑤^𝐾_𝑞$ the 𝑞th quadrature weight ([[Legendre Polynomials]]) . There are different parts to what is needed in doing this, and we will discuss them in turn next.
	- First, we need a way to describe the location $𝐱^𝐾_𝑞$ of quadrature points and their weights $𝑤^𝐾_𝑞$. They are usually mapped from the reference cell in the same way as shape functions, i.e., implicitly using the `MappingQ1` class or, if you explicitly say so, through one of the other classes derived from `Mapping` (Abstract base class for mapping classes.). 
	- The locations and weights on the reference cell are described by objects derived from the `Quadrature` base class. Typically, one chooses a quadrature formula (i.e. a set of points and weights) so that the quadrature exactly equals the integral in the matrix; this can be achieved because all factors in the integral are polynomial, and is done by Gaussian quadrature formulas, implemented in the `QGauss` class.
	- We then need something that can help us evaluate $𝜑_𝑖(𝐱^𝐾_𝑞)$ on cell 𝐾. This is what the `FEValues` class does: it takes a finite element objects to describe 𝜑 on the reference cell, a quadrature object to describe the quadrature points and weights, and a mapping object (or implicitly takes the `MappingQ1` and provides values and derivatives of the shape functions on the real cell 𝐾 as well as all sorts of other information needed for integration, at the quadrature points located on 𝐾.

**Solving the linear system**
The linear system we end up with here is relatively small -- matrix has a size of $1089 \times 1089$, owing to the fact that the mesh we use is $32 \times 32$ and so there are $32^2=1089$ vertices on the mesh. In later programs, *we regularly solve problems with more than a hundred million equations.* We need to develop a method to solve these linear systems. The first method one typically learns for solving linear systems is **Gaussian elimination**. The problem with this method is that it requires a number of operations that is proportional to $𝑁^3$, where $𝑁$ is the number of equations or unknowns in the linear system – more specifically, the number of operations is $\frac{2}{3}𝑁^3,$ give or take a few. 

With $𝑁=1089$, this means that we would have to do around 861 million operations. This is a number that is quite feasible and it would take modern processors less than 0.1 seconds to do this. But it is clear that this isn't going to scale: If we have twenty times as many equations in the linear system (that is, twenty times as many unknowns), then it would already take 1000-10,000 seconds or on the order of an hour. Make the linear system another ten times larger, and it is clear that we can not solve it any more on a single computer.
### Sparsity and the Conjugate Gradient Method
One can rescue the situation somewhat by realizing that only a relatively small number of entries in the matrix are nonzero – that is, the matrix is **sparse**![[sparsity#Definition]]
Variations of Gaussian elimination can exploit this, making the process substantially faster; we will use one such method – implemented in the `SparseDirectUMFPACK` class – in step-29 for the first time, among several others than come after that. These variations of Gaussian elimination might get us to problem sizes on the order of 100,000 or 200,000, *but not all that much beyond that.*

Instead, what we will do here is take up an idea from 1952: the [Conjugate Gradient method](https://en.wikipedia.org/wiki/Conjugate_gradient_method), or in short "CG". *CG is an "iterative" solver in that it forms a sequence of vectors that converge to the exact solution*; in fact, after 𝑁 such iterations in the absence of roundoff errors it finds the exact solution if the matrix is symmetric and positive definite. The method was originally developed as another way to solve a linear system exactly, like Gaussian elimination, but as such it had few advantages and was largely forgotten for a few decades. But, when computers became powerful enough to solve problems of a size where Gaussian elimination doesn't work well any more (sometime in the 1980s), CG was rediscovered as people realized that it is well suited for large and sparse systems like the ones we get from the finite element method. This is because (i) the vectors it computes converge to the exact solution, and consequently we do not actually have to do all 𝑁 iterations to find the exact solution as long as we're happy with reasonably good approximations; and (ii) it only ever requires matrix-vector products, which is very useful for sparse matrices because a sparse matrix has, by definition, only $\mathcal{O}(𝑁)$ entries and so a matrix-vector product can be done with $\mathcal{O}(𝑁)$ effort whereas it costs $𝑁^2$ operations to do the same for dense matrices. As a consequence, we can hope to solve linear systems with at most $\mathcal{O}(𝑁^2)$ operations, and in many cases substantially fewer.

Finite element codes therefore almost always use iterative solvers such as CG for the solution of the linear systems, and we will do so in this code as well. (We note that the CG method is only usable for matrices that are symmetric and positive definite; for other equations, the matrix may not have these properties and we will have to use other variations of iterative solvers such as [BiCGStab](https://en.wikipedia.org/wiki/Biconjugate_gradient_stabilized_method) or [GMRES](https://en.wikipedia.org/wiki/Generalized_minimal_residual_method) that are applicable to more general matrices.)
## Vector Valued Problems
symmetric gradient: 𝐃𝑢 = $\frac{1}{2}$(∇𝐮 + (∇𝐮 )$^𝑇$)

Trial function = f
test function = v
Can be viewed as three copies of the scalar space, implemented using FESystem

consider $\mathbf u = (u_1,u_2,u_3)^T$ and $\mathbf v$ accordingly. in coordinates it is: 
$$𝑎(𝑢,𝑣) = \int_\Omega(∇u_1 ⋅ ∇v_1 + ∇u_2 ⋅ ∇v_2 + ∇u_3 ⋅ ∇v_3 ) 𝑑𝑥 = \int_\Omega(f_1v_1 +f_2v_2 +f_3v_3 ) 𝑑𝑥$$

This is just three copies of the bilinear form of the Laplacian, one applied to each component. We can make this weak form a system of differential equations by choosing special test functions: first choose $\mathbf v = (v_1,0,0)^T$ then $\mathbf v = (0,v_2,0)^T$ and finally $\mathbf v = (0,0,v_3)^T$  to obtain the system:
$$\begin{matrix}
(∇u_1, ∇v_1)&&&=(f_1,v_1)\\
&(∇u_2, ∇v_2)&&=(f_2,v_2)\\
&&(∇u_3, ∇v_3)&=(f_3,v_3)
\end{matrix}
$$
The solution to the equation we need is of the form:
$$U = \begin{pmatrix}
\mathbf u\\
p
\end{pmatrix}$$
with three components: the vector $\mathbf u = (u_1, u_2)$ and one scalar component, $p$ 
With test functions $$V = \begin{pmatrix}
\mathbf v\\
q
\end{pmatrix}$$
$\mathbf v$ is the test function for velocity and $q$ is the test function for pressure. 
$$\begin{align}
(u_t,v)+(\nabla u, \nabla v)+(u \cdot \nabla u, v)&+(p, \nabla v)=(f,v)\\
(\nabla u, q)&=0
\end{align}$$
It is this form that we will later use in assembling the discrete weak form 
1. Into a matrix and 
2. A right hand side vector
	1. We will have a matrix type solution U that consist of a number of vector components that we can extract. 
	2. We will have matrix type test functions V that consist of a number of vector components that we can extract. 

FEValuesExtractors obj store which components of the vector-valued finite element constitute a scalar component or a tensor of rank 1(a physical vector always consisting of *dim* components)
```c
const FEValuesExtractors::Vector velocities (0);
    const FEValuesExtractors::Scalar pressure (dim);
```
We declare an object that represents the velocities consisting of dim components starting at component zero, and the extractor for the pressure, which is a scalar component at position dim. 


