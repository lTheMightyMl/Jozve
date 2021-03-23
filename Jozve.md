```python
import god
```
Courtesy: Most content are adopted from 15-780 course at CMU.
# Continuous Optimization
In real life, we face a lot of problems with continues variables.
Actually, the _state_ of the environment the way _time_ is handled the _percepts_ and _actions_ of the agent

might be continuous (or discrete) in our problems, and this section provides a introduction to some local search techniques for finding optimal solutions in continuous spaces.

## Examples

### Weber Point

Given a collection of cities (assume on 2D plane) how can we find the location that minimizes the sum of distances to all cities?
`picture`
Let's denote the location of cities as $y_1, y_2, ..., y_n$.
Then we can find answer to our question by solving the optimization problem below:
$$\min_{x} \sum^{n}_{i=1}||x-y_i||_2$$

### Image deblurring and denoising
`image`
Image **Deblurring** (**Noise reduction**) is the processes of removing blurring artifacts (noise) from images [input image say $Y$ which is blurred image which generally happens due to camera shake or some other phenomenon].
Given corrupted image $Y \in \mathbb R^{m\times n}$, we reconstruct the image by solving the optimization problem below:
$$\min_X \sum_{i, j}|Y_{ij}-(K*X)_{ij}| + \lambda \sum_{i, j}\big((X_{ij}-X_{i, j+1})^2+(X_{i+1, j}-X_{ij})^2\big)^\frac{1}{2}$$
where K * denotes convolution with a blurring filter.
### Machine Learning

# 2

## How difficult is real-valued optimization?

If we do not make any assumptions about the function $f:S\rightarrow\mathbb{R}$ where $S\subseteq\mathbb{R}^n$ is an infinite set, then it is impossible to find a global minimizer or maximiser in finite time. This is due to the fact that the value of the function at any one point does not reveal information about the function's behaviour at other points. As a result, we must know the function value for every point in $S$, which takes infinite time because the set $S$ is simply not finite. Even if we try to find a point at which the function's value is at most  $\epsilon$ far from the real minimum or maximum, we still need to find out the value of the function at all points which was shown cannot be done in finite time.

However, if we make some reasonable assumptions about the function being examined, near-optimal solutions can be found in finite time. One such assumption is Lipschitz continuity. The mathematical definition is as follows:

$$\exists L\in\mathbb{R}:\forall x,y\in\mathbb{R}^n|f(x)-f(y)|\le L||x-y||$$

It means that the difference between the value of the function at two points is never more than a constant multiple of the distance of the two points. This assumption restricts the growth of the function when moving from one point to another. As to know how this assumption can help us find a near optimal solution, consider the following case:

Assume $S$ is a bounded subset of $\mathbb{R}$. We know that $\forall x,y\in\mathbb{R}^n|f(x)-f(y)|\le 5||x-y||$ and we want to find a function value which is at most $0.1$ far from the actual minimum or maximum. ow, consider points in $S$ at most $\frac{0.1}{5}=0.02$ far from each other and from the boundaries of $S$ and call the set of these points $P$. Because of the restriction imposed on $f$ we can be sure that the value of the function at points not in $P$ is at most $0.02 \times 5 = 0.1$ far from the two nearest points in $P$. Consequentially, if we take the minimum or maximum value of $f$ among points in $P$, we can be sure that this value is at most $0.1$ far from the real minimum or maximum of $f$ in $S$.

```image```

Lipschitz continuity made it possible to find near-optimal solutions, but it can be proved that any algorithm to find a near-optimal minimum or maximum for a Lipschitz continuous function on $\mathbb{R}^n$ has $\Omega\big(\frac{1}{t^\frac{1}{n}}\big)$ error after $t$ iterations. We can see that assumptions can make a big difference, but we still need faster algorithms.

# 3

## Convex Optimization
As you may know,  convex optimization problem is an optimization problem in which the objective function is a convex function and the feasible set is a convex set.
Now let's examine some useful properties:

 - every local minimum is a  global minimum
 - the optimal set is convex
 - if the objective function is _strictly_ convex, then the problem has at most one optimal point

In fact many of search algorithms find the local optima, and that's why the first property is the key point that enable us to tackle these types of problems to find the global optima solutions.
Now let's go through its proof:

Assume there exists $x_0$ such that $f(x_0)<f(x_∗)$ where $x_*$ is the local optima of the function. 
Then for any $t∈(0,1]t∈(0,1]$ we have:
$$f(Z) = f((1−t)x_∗+tx_0)≤(1−t)f(x_∗)+tf(x_0)$$$$<(1−t)f(x_∗)+tf(x_∗)$$$$=f(x_∗)$$
$$\Longrightarrow $$$$f(Z) < f(x_*) $$
Now note that $Z$  is lying on the line which connects $x_0$ and $x_*$. Therefore, if $Z$ is chosen very close to $x_*$, the $f(Z)it $ must be greater than $f(x_*)$ due to local optimality of $x_*$ which means:
$$f(Z) \ge f(x_*)$$
which contradicts to the previous relation. Hence the hypothesis was wrong and the property is proved.

---
Now once we found out this useful property, a good idea can be model our problems to a convex optimization problem through which we can apply various iterative methods like `gradient descent` to solve the problems.

### gradient descent
The idea is to take repeated steps in the opposite direction of the gradient (or approximate gradient) of the function at the current point, because this is the direction of steepest descent. Conversely, stepping in the direction of the gradient will lead to a local maximum of that function; the procedure is then known as **gradient ascent**.

![](https://miro.medium.com/max/2976/1*70f9PB-RwFaakqD6lfp4iw.png)

The algorithm is really simple (and effective!!!). Isimple which its pseudocode can be in below:
```
x  = initilize_point()
for EPOCHS tims repeat:
	x -=  contant * gradient(f(x))
```

in fact, the value of $f$ is decreasing in each iteration. The proof is straight forward as it is illustrated in below:
By *taylor exapansion* of a function $f$  we have:

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MjA4NjQzMzYsLTE2MDIyODE3OCwtMT
MwMzI0MzAwOCwtMTQ3ODc3ODU2NywxNDU4NDEwNTE3LDg0Njgy
NjE1MSwtOTc3NTIwMzg5LDE4MzI2Nzk1NDQsLTIyNTI3OTc1Mi
wxNTUzODM0MDE0LDE1NzA0MzE0NTksMjg2MDQ2NDQxLC0xNDQ4
ODQzNTc0LDE2MTUwMTUxNDEsNDcyNDA1NzUzLDM0NTI3MDAyMS
wxMzU4NTU0Mjk4LC0zMjYyNTI2MSw1NzMxOTYwMDUsNTczMTk2
MDA1XX0=
-->