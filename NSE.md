As an introduction, we studied how dealii is utilized in the finite element method to approximate solutions to various partial differential equations. Most notably, we explored [[step-3]], [[step-6]], and [[step-20]]. 

For our problem, we began with the Navier-Stokes equation with a constant viscosity $\nu = 0.01$. First we begin with the strong form:

$$\begin{align}
\vec{u_t}-\nabla \cdot (\nu \nabla \vec{u})+\vec{u}\cdot \nabla \vec{u}& + \nabla p = \vec{f}\\
\nabla \cdot \vec{u} &= 0\\
\end{align}$$
where 
To find the weak formulation we multiply by a test function and integrate:
After integration by parts, letting $(u,v)$ represent $\int u v$ 
EQ 1: 
$$\begin{align}
(u_t,v)+(\nabla u, \nabla v)+(u \cdot \nabla u, v)&+(p, \nabla v)=(f,v)\\
(\nabla u, q)&=0
\end{align}$$
With Bckwd Euler:
$$\begin{align}
\frac{1}{\Delta t}(u^{n+1},v)+\nu(\nabla u^{n+1}, v)&+(p, \nabla v)=(f,v)\\
(\nabla u, q)&=0
\end{align}$$
 
Within the `EquationData` namespace

# InnerPreconditioner Class
# Data_Storage Class
# BoundaryValues class
Class within `EquationData` namespace. Holds boundary values variables and calculations
1. BoundaryValues class :Function class. :pass features of Function class to BoundaryValues class to solve the problem. Function takes a value, evaluates the function, and returns a vector of values with one or more components
	1. value() - input into the Boundary value Function, default component to evaluate is first one, 0 
	2. vector_value() - Return all components of a vector-valued function at a given point.
2. BoundaryValues::value(...) passes value to BoundaryValues
	1. 
# RightHandSide class
Class within EquationData namespace. Holds RHS values, variables, and calculations
1. RightHandSide class ::Functions
	1. value()
	2. vector_value()

# ExactSolution class
Class within EquationData namespace. Holds Exact Solution values, variables, and calculations
1. ExactSolution class ::Functions
	1. vector_gradient()
	2. vector_value()
# NavierStokesProblem class
Class within the EquationData namespace. Holds all the variables for the approximation calculations over the cells. 
# InverseMatrix class
# SchurComplement class

# NavierStokesProblem::NavierStokesProblem(const unsigned int degree)
# NavierStokesProblem::setup_dofs()
# NavierStokesProblem::assemble_system()
### :: access assemble_system() function through NavierStokesProblem class and thereby all the declarations and calculations that need to be run during this step

`assemble_system()`: declares the following
1. initializes `system_matrix = 0` variable 
2. initializes `system_rhs=0` variable
3. calls `QGauss<dim>` class with quadrature_formula obj that takes the following flags:
	1. `fe` obj
	2. `quadrature_formula(degree+2)` obj
	3. `update_JxW_values` obj
	4. `update_gradients` obj
4. defines expression `const unsigned int dofs_per_cell` = .pass `dofs_per_cell()` result to `fe` obj
5. defines expression `const unsigned int n_q_points` = .pass `size()` function results to `quadrature_formula` obj
6. 
# NavierStokesProblem::solve()
::access solve function within NavierStokesProblemClass
   SparseDirectUMFPACK solver;
     solver.initialize (system_matrix);
     solver.vmult(solution,system_rhs);
     constraints.distribute (solution);
# NavierStokesProblem::output_results()
::access output_results(define `const unsigned int refinement_cycle` variable) function within NavierStokesProblem class

`std::vector<std::string> solution_names(dim,"velocity")`sets solution name for each velocity in the vector and creates a string
# NavierStokesProblem::Pressure_Error() and Error()
### ::access Pressure_Error() function through `NavierStokesProblem` class and thereby all the declarations and calculations that need to be run during this step

`Pressure_Error()` initializes variables and calls a function to take portions of the solution over which to refine the mesh - based on what component it is (pressure)
1. `double true_pres_mean_value = 0`
2. `double L2_Pressure_Error = 0`
3. `double finite_pres_mean = 0.0`
4. `const ComponentSelectFunction<dim> pressure_mask(dim,dim+1)`
5. define a vector function with double entries that holds the third component of the solution vector, `difference_per_cell_3(triangulation.n_active_cells())`, also receives results from triangulation obj calling n_active_cells function
6.  define `finite_pres_mean_value` = ::access `compute_mean_value` function that takes flags(`dof_handler` obj, `QGauss<2>(4)` class, `solution` obj, `dim` variable) within VectorTools class
7. define `true_pres_mean_value`= ::access  `compute_mean_value` function that takes flags(`dof_handler` obj, `QGauss<2>(4)` class, `solution` obj, `dim` variable) within VectorTools class
8. .pass `add` function with flags `(-finite_pres_mean_value+true_pres_mean_value)` function to `block(1)` function to `solution` obj
9. print true_pressure_mean_value "TPM" and finite_pressure_mean_value "FPM"
10. ::access `integrate_difference` function takes flags(`dof_handler` obj, `solution` obj, `exact_solution` obj, `difference_per_cell_3` vector, `QGauss<dim>(4)` class, ::access `L2_norm` function within VectorTools class, `&pressure_mask` pointer))
11. define `L2_Pressure_Error` as vector function `difference_per_cell_3`, .pass results from `l2_norm()` function to difference_per_cell.
12. return L2_Pressure_Error \*L2_Pressure_Error
### ::access Error() function through `NavierStokesProblemClass` and thereby all the declarations and calculations that need to be run during this step

`Error()`: initializes variables and calls a function to take portions of the solution over which to refine the mesh - based on what component it is (velocity)
1. `double L2error = 0`
2. `double H1error = 0`
3. `const ComponentSelectFunction<dim> velocity_mask(std::make_pair(0,dim),dim+1)`
4. define a vector function with double entries that holds the third component of the solution vector, `difference_per_cell_1(triangulation.n_active_cells())`, also receives results from triangulation obj calling n_active_cells function
5. define a vector function with double entries that holds the third component of the solution vector, `difference_per_cell_2(triangulation.n_active_cells())`, also receives results from triangulation obj calling n_active_cells function
6. ::access `integrate_difference` function takes flags(`dof_handler` obj, `solution` obj, `exact_solution` obj, `difference_per_cell_1` vector, `QGauss<dim>(4)` class, ::access `L2_norm` function within VectorTools class, `&velocity_mask` pointer))
	1. for first velocity component
7. ::access `integrate_difference` function takes flags(`dof_handler` obj, `solution` obj, `exact_solution` obj, `difference_per_cell_2` vector, `QGauss<dim>(4)` class, ::access `H1_seminorm` function within VectorTools class, `&velocity_mask` pointer))
	1. for second velocity component
8. define `L2_Error` as vector function `difference_per_cell_1`, .pass results from `l2_norm()` function to difference_per_cell_1
9. define `H1Error` as vector function `difference_per_cell_2`, .pass results from `l2_norm()` function to difference_per_cell_2
10. return `L2error*L2error+H1Error*H1Error`
# NavierStokesProblem::run()
### ::access `run` function through the`NavierStokesProblem` class and thereby all the declarations and calculations that need to be run during this step

`run()`: Declares the variables for the error calculations (to compare with approx solution) and sets an error loop
1. `double H1_Veclocity_Error` variable
2. `double L2H1_Velocity_Error[10]`, an array of size 10
3. `double L2_Pressure_Error` variable
4. `double L2L2_Pressure_Error[10]`, an array of size 10
5. `double rate[10]`, an array of size 10

Initializing the rate, the velocity, and pressure error variables, to be calculated at each i:
- for each i in rate array, initialize the rate array, the L2H1 array, and the L2L2 Pressure array.
	- `L2H1_Velocity_Error[i] = 0.0`
	- `L2L2_Pressure_Error[i] = 0.0`
		- make sure each i in the array = 0 at first

`subdivisions` variable is declared a vector of integers of dimensions (dim,1) - a row matrix
`subdivisions[0]` -> sets first subdivision row entry = 4

::access `hyper_cube (triangulation, 0, 1)` function in `GridGenerator` class - creates a unit cube and pass to the `GridGenerator` class

.pass `refine_global(1)`-1x refinement function to `triangulation` obj  -> causes the initial refinement

#### Refinement Cycle Loop:
- for (declare `refinement_cycle = 0` variable), each refinement_cycle < the 6th one, then increment to the next refinement_cycle:
1. Initialize `H1_Velocity_Error` variable
2. Initialize `L2_Pressure_Error` variable
3. Initialize `time` variable
4. pass `set_time` function, with `time` variable to `exact_solution` obj
5. Initialize `old_timestep_solution`
6. Check to make sure refinement_cycle >0:
	1. if so, pass `refine_global(1)`->1x refinement function to `triangulation` obj
7. call `setup_dofs` function
8. access `interpolate` function within `VectorTools` class
	1. `interpolate` function takes (`dof_handler` obj, `exact_solution` obj, and `old_timestep_solution` variable)
9. perform backward euler -> `solution = old_timestep_solution`
10. for each n in `timestep_number` - to increment timesteps:
	1. set `time` variable = time_step $\cdot$ n 
	2. pass `set_time` function with `time` variable to `right_hand_side` obj
	3. pass `set_time` function with the `time` variable to the `BV` obj
	4. pass `set_time` function with the `time` variable to the `exact_solution` obj
	5. call `assemble_system` function
	6. call `solve` function
	7. set `old_timestep_solution = solution` (Bckwd Euler)
	8. set`H1_Velocity_Error = H1_Velocity_Error + Error(refinement_cycle)` - error from each refinement, velocity components
	9. set` L2_Pressure_Error = L2_Pressure_Error + Pressure_Error(refinement_cycle)` - error from each refinement, pressure components
11. `output_results(refinement_cycle)` - for each refinement cycle
12. print L2H1 error and L2L2 error, for each timestep
	1. `L2H1_Velocity_Error[refinement_cycle+1]` an array of size refinement cycle +1, is given by: $\sqrt{\text{timestep}* \text{H1VelocityError}}$
		1. calculates error for each H1_Velocity_Error calculated at each timestep
	2. `L2L2_Pressure_Error[refinement_cycle+1]` array of size refinement cycle +1, is given by: $\sqrt{\text{timestep}* \text{L2PressureError}}$
		1. calculates error for each L2_Pressure_Error calculated at each timestep
#### Rate calculation Loop:
1. print rate calculation for each error, for each i in the rate array:
	1. $$rate[i-1]=\log(\dfrac{\frac{\text{L2H1VelocityError}[i-1]}{\text{L2H1VelocityError}[i]}}{\log(2)})$$
	2. print `L2H1_Velocity_Error` for each i-1 in rate array i-1
2. for each i in rate array, incrementing to next i, initializing the array:
	1. `rate[i]=0` each variable spot in rate array = 0 at first
3. print rate calculation for each error, for each i in the rate array:
	1. $$rate[i-1]=\log(\dfrac{\frac{\text{L2L2PressureError}[i-1]}{\text{L2H2PressureError}[i]}}{\log(2)})$$
	2. print `L2L2_Pressure_Error` for each i-1 in rate array i-1
END `run()`
#### mesh generation
Generates the initial grid and calls other functions in their respective order. Initially, we begin with a mesh (the first rectangle) of $4 \times 1$ in 2D or $4 \times 1 \times 1$ in 3D, placed in $\mathbb{R}^2/\mathbb{R}^3$ as $(-2,2)\times(-1,0)$ or $(-2,2)\times(0,1)\times(-1,0)$, respectively. We then subdivide the rectangle 4x in the first coordinate direction. We contain this in a single code block to limit the scope of the variables associated with mesh generation.

We use a boundary indicator of 1 for all boundaries that have Dirchlet boundary conditions (to faces that are located at 0 in the coordinate direction)

`refinement_cycle`: We apply an initial refinement before the first calculations on the mesh. We will cycle over different refinement levels,==and a small version of the program is performed over each cell:== refine, set up dofs and matrices, assemble solve and create output for each refinement.  
# main()
try:
using namespace dealii
using namespace NSE
pass depth_console funciton to deallog

Set \<dim\> of the NavierStokesProblem class, call flow_problem function of degree 1
pass run function to flow_problem

exceptions and abortion criteria



2nd_order_mhd_ensemble_tem_prm2

I would declare the parameter as a string, use  
Utilities::split_string_list(prm.get("vector")), and then convert the  
entries of the std::vector<std::string> to whatever number format you  
want.
[[📒 Vector-valued Problems]]




expected -viscosity - 0.01
randomness, adding noise, Random variables

100 random variables (-1,1) inside the code use the generator copy paste into code

create an array instead of using the parameter file

use generator noise[i] <- a vector run the code however many times 

viscosity = expected viscosity*noise[]*1/10
# Background Research





# Debug
add a printer to each section to see what is working and what step we are at

add the printer for debugging

put it in the for loop in the assembly

to check that it is pulling the parameters from the file properly, specifically



