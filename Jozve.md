```python
import god
```
Courtesy: Most content are adopted from 15-780 course at CMU.
# Continuous Optimization
In real life, we face a lot of problems with continues variables.
Actually, 
1. the state of the environment
2. the way time is handled
3. the percepts and actions of the agent

might be continuous (or discrete) in our problems, and this section provides a very brief introduction to some local search techniques for finding optimal solutions in continuous spaces

## Examples

### Weber Point

Given a collection of cities (assume on 2D plane) how can we find the location that minimizes the sum of distances to all cities?
`picture`
Let's denote the location of cities as $y_1, y_2, ..., y_n$.
Then we can find answer to our question by solving the optimization problem below:
$$\min_{x} \sum^{n}_{i=1}||x-y_i||_2$$

### Image deblurring and denoising

### Machine Learning

# 2

## How difficult is real-valued optimisation?

If we do not make any assumptions about the function $f:S\rightarrow\mathbb{R}$ where $S\subseteq\mathbb{R}^n$ is an infinite set, then it is impossible to find a global minimiser or maximiser in finite time. This is due to the fact that the value of the function at any one point does not reveal information about the function's behaviour at other points. As a result, we must know the function value for every point in $S$, which takes infinite time because the set $S$ is simply not finite. Even if we try to find a point at which the function's value is at most  $\epsilon$ far from the real minimum or maximum, we still need to find out the value of the function at all points which was shown cannot be done in finite time.

However, if we make some reasonable assumptions about the function being examined, near-optimal solutions can be found in finite time. One such assumption is Lipschitz continuity. The mathematical definition is as follows:

$$\exists L\in\mathbb{R}:\forall x,y\in\mathbb{R}^n|f(x)-f(y)|\le L||x-y||$$

It means that the difference between the value of the function at two points is never more than a constant multiple of the distance of the two points. This assumption restricts the growth of the function when moving from one point to another. As to know how this assumption can help us find a near optimal solution, consider the following case:

Assume $S$ is a bounded subset of $\mathbb{R}$. We know that $\forall x,y\in\mathbb{R}^n|f(x)-f(y)|\le 5||x-y||$ and we want to find a function value which is at most $0.1$ far from the actual minimum or maximum. ow, consider points in $S$ at most $\frac{0.1}{5}=0.02$ far from each other and from the boundaries of $S$ and call the set of these points $P$. Because of the restriction imposed on $f$ we can be sure that the value of the function at points not in $P$ is at most $0.02 \times 5 = 0.1$ far from the two nearest points in $P$. Consequentially, if we take the minimum or maximum value of $f$ among points in $P$, we can be sure that this value is at most $0.1$ far from the real minimum or maximum of $f$ in $S$.

```image```

Lipschitz continuity made it possible to find near-optimal solutions, but it can be proved that any algorithm to find a near-optimal minimum or maximum for a Lipschitz continuous function has $\Omega(\frac{1}{t})$ error

# 3

## Convex Optimization
As you may know,  convex optimization problem is an optimization problem in which the objective function is a convex function and the feasible set is a convex set.
Now let's examine some useful properties:

 - -   every local minimum is a  global minimum
 - the optimal set is convex
 - if the objective function is _strictly_ convex, then the problem has at most one optimal point

which the first property is the key point that enable us to tackle 

# 4

# 5

# 6
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNDAwNjEzOSwtNDI2ODkxNTMyLDEyOD
k3MzcyNzQsMTM1ODU1NDI5OCwtMzI2MjUyNjEsNTczMTk2MDA1
LDU3MzE5NjAwNSwtMTU2NTA3NDYzMCw2NDkyOTIzOTcsMTczMD
I1MTU0NiwtMTM5NTEyOTcyMCwtMjA5MTEzNzE1MywtNzE0Mjc5
MzgyLC05NTYxNTEwNTIsLTExNTAwMDAxODMsLTkxMTgyMTc2Ny
wxOTc0MDk2NTk5LC0xMzg1NzAwNDg4LDE3ODkzOTEzMzUsLTYy
NTI1MDE2NF19
-->