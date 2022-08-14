---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Solving Two Dimensional Heat Equation Using Finite Difference Method"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2022-08-12T20:01:31+05:30
lastmod: 2022-08-12T20:01:31+05:30
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
## Introduction

Suppose we have a square-shaped iron plate and know how the heat is distributed across the plate at a certain point in time. What we are curious about is the following question:

How will the heat distribution change over time?

We know that the heat tends to flow from the warmer region to the colder region. Therefore, we are trying to find an equation that describes this process. The phenomenon of heat flow can be modelled by a partial differential equation called the heat equation. The application of this equation is quite diverse. Both engineers and physicists use it to describe processes like heat flow, molecular diffusion, Brownian motion Etc.  

Mathematically, the phenomenon of heat flow can be modelled using the following equation.

$$
\frac{\partial{u}}{\partial{t}} = D  \Bigg(\frac{\partial^2{u}}{\partial{x^{2}}} + \frac{\partial^2{u}}{\partial{y^{2}}}\Bigg)
$$

Where D is a constant called diffusion coefficient, characteristic of the material through which the heat flows and $u(x,y,t)$, is the unknown temperature function to be solved.

We need to know the initial and boundary conditions to obtain the unique solution of the heat equation or to apply any numerical method. The diffusion equation needs one initial condition at $t=0$; i.e $u(x,y,0) = I(x,y)$, where $I(x,y)$ is a given function. Besides the initial condition, boundary conditions are required at each point on the boundary.


## Finite Difference Explicit Method


In this post, we will solve the heat equation numerically using the finite difference explicit method. Explicit means the solution at a given time step depends only on the previous time step, which is in contrast to the implicit method, where the solution also depends on the subsequent time step. The finite difference method provides an approximate numerical solution to the problem by discretizing the domain into grids. The temperature $u(x,y,t)$ is sought on each node of the grid.

Suppose we seek the solution of $u(x,y,t)$ for a time interval $0 < t < T$ in a 2D domain having dimensions $[0,Lx]×[0,Ly]$, where $L_{x}$ and $L_{y}$ are the length of the domain along $x$ and $y$ directions. As a first step, we generate a mesh grid with discretization steps $dx$ and $dy$ in two spatial directions and $dt$ in time as follows;

$0 = x_{0} < x_{1} ··· < x_{n_{x}} = L_{x}$ <br>
$0 = y_{0} < y_{1} ··· < y_{n_{y}} = L_{y}$.

The temporal domain $[0, T ]$ is discretized as,

$0 = t_{0} < t_{1} ··· < t_{n_{t}} = T$.

The solution $u(x,y,t)$ is known only on the grid points $(x_{i},y_{j})$ with $i = 0,...,n_{x},$
and $j = 0,...,n_{y}$. We approximate the continuous function $u(x,y,t)$ by a discrete function $u^{n}_{i,j}$ on the grid. On the mesh, the discretized heat equation can be written as,

$$
\frac{\partial{}}{\partial{t}} u(x_{i},y_{j},t_{n}) = D  \Bigg(\frac{\partial^2{}}{\partial{x^{2}}} + \frac{\partial^2{}}{\partial{y^{2}}}\Bigg) u(x_{i},y_{j},t_{n})
$$

The next step is to replace the derivatives with their finite difference approximations. It is done using the forward difference method in time and the central difference method in space:

$$
\frac{ u_{i,j}^{n+1} - u_{i,j}^{n} }{dt} = D
\Bigg( \frac{u_{i+1,j}^{n} -2 u_{i,j}^{n} + u_{i-1,j}^{n}}{dx^{2}} + \frac{u_{i,j+1}^{n} - 2 u_{i,j}^{n} + u^{n}_{i,j-1}}{dy^{2}}  \Bigg)
$$

Now we have converted the partial differential equations into algebraic equations, which makes them easy to solve. Solving for the unknown $u^{n+1}_{i, j}$:

$$
u_{i,j}^{n+1} = u_{i,j}^{n} + \frac{D dt}{dx^{2}}  \bigl( u_{i+1,j}^{n} - 2 u_{i,j}^{n} + u_{i-1,j}^{n} \bigl)  + \frac{D dt}{dy^{2}} \bigl( u_{i,j+1}^{n} - 2 u_{i,j}^{n} + u^{n}_{i,j-1} \bigl)
$$

## Stability

The finite difference explicit method is conditionally stable. We can show with [**Von Neumann Stability Analysis**](https://ocw.mit.edu/courses/18-336-numerical-methods-for-partial-differential-equations-spring-2009/c7c12accea163007923288875bb42604_MIT18_336S09_lec14.pdf) that we need the discretized time step $dt$ to satisfy the following condition.

$$dt < \frac{1}{2 D} \frac{(dx  dy)^2}{(dx)^2 +(dy)^2}$$

# Conclusions

The heat equation is of fundamental importance across scientific fields. The more general version of the heat equation, the diffusion equation, is used extensively in physical and biological sciences. In physics and statistics, the heat equation is related to the study of Brownian motion via the Fokker-Planck equation. In this post, we saw how the heat equation could be discretized into a set of algebraic equations on a mesh grid. In the next post, we solve these algebraic equations using the Python programming language.
