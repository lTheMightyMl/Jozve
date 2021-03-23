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

If we do not make any assumptions about the function $f:S\rightarrow\mathbb{R}$ where $S\sube\mathbb{R}^n$ is a , then it is impossible to find a global minimiser or maximiser in finite time. This is due to the fact that the value of the function at any one point does not reveal information about the function's behaviour at other points. As a result, we must know the function value for every point in $\mathbb{R}$, which simply takes infinite time because the set $\mathbb{R}$ is not finite. Even if we try to find a point at which the function's value is at most  $\epsilon$ far from the real minimum or maximum, we still need to find out the value of the function at all points which was shown cannot be done in finite time.
However, if we make some reasonable assumptions about the function being examined,  

# 3

# 4

# 5

# 6

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNzk1MzAzNTEsLTcxNDI3OTM4MiwtOT
U2MTUxMDUyLC0xMTUwMDAwMTgzLC05MTE4MjE3NjcsMTk3NDA5
NjU5OSwtMTM4NTcwMDQ4OCwxNzg5MzkxMzM1LC02MjUyNTAxNj
QsMTY1OTAxNDY4MywtOTQ4NTQ2NjEsNTU5OTk4NDg0LC0xMTgx
MTY4NDI4LDIwMDc5NTE5MDAsLTE3MzU5NTk1MjksLTE0MjEwOD
YwMjJdfQ==
-->