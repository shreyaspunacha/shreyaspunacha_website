# Solving Two Dimensional Heat Equation Using Finite Difference Method

## Introduction

Suppose we have a square shaped iron plate and we know how the heat is distributed across the plate at a certain point in time. What we are curious in is the following question:

How will the heat distribution change over time?

We know that the heat tends to flow from the warmer region to the colder region. Therefore, what we are trying to find is an equation that describes this process. The phenomenon of heat flow can be modelled by a partial differential equation called heat equation. The application of this equation is quite diverse. It is used by both engineers and physicists to describe processes like heat flow, molecular diffusion, Brownian motion etc.  

Mathematically, the phenomenon of heat flow can be modelled using the following equation.

$$
\frac{\partial{u}}{\partial{t}} = D  \Bigg(\frac{\partial^2{u}}{\partial{x^{2}}} + \frac{\partial^2{u}}{\partial{y^{2}}}\Bigg)
$$

where D is a constant called diffusion coefficient, characteristic of the material through which the heat is flowing and $u(x,y,t)$ is the unknown temperature function to be solved for.

To obtain the unique solution of the heat equation or to apply any numerical method, we need to know the initial and the boundary conditions. The diffusion equation needs one initial condition at $t=0$; i.e $u(x,y,0) = I(x,y)$, where $I(x,y)$ is a given function. Apart from the initial condition, boundary conditions are required on each point on the boundary.


## Finite Difference Explicit Method


In this post, we are going to solve the heat equaiton numerically using the finite difference explicit method. Explicit means the solution at a given time step depends only on the previous time step which is in contrast to the implicit method where the solution also depends on the subsequent time step. Finite difference method provides an approximate numerical solution to the problem by descritising the domain into grids. The temperature $u(x,y,t)$ is sought on each node of the grid.

Suppose we seek the solution of $u(x,y,t)$ for a time interval $0 < t < T$ in a 2D domain having dimensions $[0,Lx]×[0,Ly]$, where $L_{x}$ and $L_{y}$ are the length of the domain along $x$ and $y$ directions. As a first step, we generate a mesh grid with discretization steps $dx$ and $dy$ in two spatial directions and $dt$ in time as follows; 

$0 = x_{0} < x_{1} ··· < x_{n_{x}} = L_{x}$ <br>
$0 = y_{0} < y_{1} ··· < y_{n_{y}} = L_{y}$.

The temporal domain $[0, T ]$ is discretized as, 

$0 = t_{0} < t_{1} ··· < t_{n_{t}} = T$.

The solution $u(x,y,t)$ is known only on the grid points $(x_{i},y_{j})$ with $i = 0,...,n_{x},$
and $j = 0,...,n_{y}$. We approximate the contineous function $u(x,y,t)$ by a discrete function $u^{n}_{i,j}$ on the grid. On the mesh, the discritised heat equation can be written as,

$$ 
\frac{\partial{}}{\partial{t}} u(x_{i},y_{j},t_{n}) = D  \Bigg(\frac{\partial^2{}}{\partial{x^{2}}} + \frac{\partial^2{}}{\partial{y^{2}}}\Bigg) u(x_{i},y_{j},t_{n})
$$

The next step is to replace the derivatives by their finite difference approximations. It is done using forward difference method in time and central difference method in space:

$$
\frac{ u^{n+1}_{i,j} - u^{n}_{i,j} }{dt} = D 
\Bigg( \frac{u^{n}_{i+1,j}-2 u^{n}_{i,j}+u^{n}_{i-1,j}}{dx^{2}} + \frac{u^{n}_{i,j+1}-2 u^{n}_{i,j}+u^{n}_{i,j-1}}{dy^{2}}  \Bigg)
$$

Now we have converted the partial differential equations into algebraic equations, which makes them easy to solve. Solving with respect to the unknown $u^{n+1}_{i,j}$:

$$
u^{n+1}_{i,j} = u^{n}_{i,j} + \frac{D dt}{dx^{2}}  \bigl( u^{n}_{i+1,j}-2 u^{n}_{i,j}+u^{n}_{i-1,j} \bigl)  + \frac{D dt}{dy^{2}} \bigl( u^{n}_{i,j+1}-2 u^{n}_{i,j}+u^{n}_{i,j-1} \bigl)
$$

## Stability

The finite difference explicit method is conditionally stable. We can show with [**Von Neumann Stablity Analysis**](https://ocw.mit.edu/courses/18-336-numerical-methods-for-partial-differential-equations-spring-2009/c7c12accea163007923288875bb42604_MIT18_336S09_lec14.pdf) that we need the discritised time step $dt$ to satisfy the folliwing condition.

$$dt < \frac{1}{2 D} \frac{(dx  dy)^2}{(dx)^2 +(dy)^2}$$

# Conclusions

The heat equation is of fundamental importance across scientific fields. The more general version of the heat equation called diffusion equation is used extensively in physical and biological sciences. In physics and statistics, the heat equation is related with the study of Brownian motion via Fokker-Planck equaiton. In this post we saw how the heat equation can be discritised into set of algebraic equaitons on a mesh grid. In the next post we solve these algebraic equations using Python programming language. 


```python

```
