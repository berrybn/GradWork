# Vocabulary
==Linear combination as it relates to scaling a vector and scaling relates to parametrization of a line==
==span==
==orthogonal==

# Methods
## System of Equations
A **system of equations** is a set of equations in a particular collection of variables. Its **solution** is a sequence of numbers (given as a list) $(x_0,x_1,...x_n)$

$$\begin{align}
c_0x_0+c_1x_1+c_2x_2+...+c_nx_n&=b_0\\
c_0x_0+c_1x_1+c_2x_2+...+c_nx_n&=b_1\\
\vdots \\
c_0x_0+c_1x_1+c_2x_2+...+c_nx_n&=b_n\\
\end{align}$$
- **Unique Solution:** It takes at least $n$ linear equations to uniquely determine $n$ unknowns
- **Dependent System**: A linear system with more unknowns than equations is called "under-determined" and will have infinitely many solutions ($0=0$), and one variable can be expressed in terms of the others, called the "free-variable"
	 - Initially, one of the equations that was given was a linear combination of the others
	 - [[degrees of freedom]] will indicate how many more variables there are than equations.
	 - When we express the free variable in terms of the other variables:![[parametric equation]]
 - **Inconsistent System:** A linear system with more equations than unknowns, system has no solutions

## Using Matrices to solve systems of equations w/ Gaussian Elimination
If we translate the system to its augmented matrix form, in order to solve it, we end up using a method called [[Gaussian Elimination]] and we solve the matrix equation: $$\mathbf{A}\vec x=\vec b$$where A is the matrix of coefficients of the system, x is the vector of unknowns and b is the column vector formed from the constants. 
NOTE: This method works for all above scenarios

We end up taking advantage of this structure to do calculations with systems of equations.

## Basis
[[monomial basis]]


# Applications
## Polynomial Interpolation and the Monomial Basis
One such application is polynomial interpolation and in general [[approximation]]. We create a matrix of coefficients based on test points that are given, which then dictate the size of the matrix. There are many different bases we can use to translate the system. The monomial basis goes as follows:
![[monomial basis#$ phi_j$ Form]]


Consider the points $(2,3), (1,4)$ and $(-2, 2)$. We can utilize the form above to create a system of equations to approximate the $f(x)$ that passes through these points. Since we will have 3 data points, we need 3 equations in 3 variables. 

$$\begin{align}
p(2)&=c_0\phi_0(2)+c_1\phi_1(2)+c_2\phi_2(2)=3\\
p(1)&=c_0\phi_0(1)+c_1\phi_1(1)+c_2\phi_2(1)=4\\
p(-2)&=c_0\phi_0(-2)+c_1\phi_1(-2)+c_2\phi_2(-2)=2\\
\end{align}$$
Which creates the matrix equation:
$$\begin{bmatrix}
1&2&4\\
1&1&1\\
1&-2&4\\
\end{bmatrix} \begin{bmatrix}
c_0\\
c_1\\
c_2\\
\end{bmatrix}=\begin{bmatrix}
3\\
4\\
2\\
\end{bmatrix}$$
For which we can create a polynomial that will give us function that passes through the sample points. 
$$p_2(x)=\dfrac{-5 x^2}{12} + \dfrac{x}{4} + \dfrac{25}{6}$$
## Integration and Differential Equations



[[jacobian matrix]]