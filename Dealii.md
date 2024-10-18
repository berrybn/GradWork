[[C++]]

Governing equations for incompressible flows (no gravity)

$\nabla \cdot u = 0$ 
$\dfrac{\partial \mathbf{u}}{\partial t}=-\mathbf{u}\cdot\nabla\mathbf{u}+\alpha\nabla^2\mathbf{u}-\dfrac{\nabla p}{\rho}$
Where 
1. advection is covered by the $-\mathbf{u} \cdot \nabla \mathbf{u}$ term
2. diffusion is covered by the $\alpha \nabla^2 \mathbf{u}=\alpha \nabla \cdot \nabla \mathbf{u}$ term
3. pressure is covered by the $\nabla p/\rho$ term

For incompressible flows, the hydrodynamic pressure projects the velocity field into an incompressible space

Mathematically the system can be interpreted as differential equations with algebraic constraint

The discretized equations can be written as:
$\mathbf{u}^{n+1} = \mathbf{u}^n+\Delta t(-A^n_{i,j}+D^n_{i,j}) +\Delta t \nabla_{h}P_{i,j}$
$\nabla \cdot \mathbf{u}^{n+1}=0$

