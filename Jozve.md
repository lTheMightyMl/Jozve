```python
import god
```
Courtesy: Most content are adopted from 15-780 course at CMU.
# Continuous Optimization
bluh bluh bluh

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

However, if we make some reasonable assumptions about the function being examined, near optimal solutions can be found in finite time. One such assumption is Lipschitz continuity. The mathematical definition is as follows:
$$\exists L\in\mathbb{R}:\forall x,y\in\mathbb{R}^n|f(x)-f(y)|\le L||x-y||$$
It means that the difference between the value of the function at two points is never more than a constant multiple of the distance of the two points. This assumption restricts the growth of the function when moving from one point to another. As to know how this assumption can help us find a near optimal solution, consider the following example:


# 3

# 4

# 5

# 6
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkxMzEyMjc5MSwtMjA5MTEzNzE1MywtNz
E0Mjc5MzgyLC05NTYxNTEwNTIsLTExNTAwMDAxODMsLTkxMTgy
MTc2NywxOTc0MDk2NTk5LC0xMzg1NzAwNDg4LDE3ODkzOTEzMz
UsLTYyNTI1MDE2NCwxNjU5MDE0NjgzLC05NDg1NDY2MSw1NTk5
OTg0ODQsLTExODExNjg0MjgsMjAwNzk1MTkwMCwtMTczNTk1OT
UyOSwtMTQyMTA4NjAyMl19
-->