### Exercise a)

Show graphically the evolution of the logistic map for several values of, e.g.:

```
r = 0.9
r = 1.8
r = 2.6
r = 3.2
r = 3.6
r = 3.9
r = 3.99
```
#### Resolution

```python
#! python3
# import third-party libraries
from matplotlib import pyplot as plt
import numpy as np

# initialize an array of 0s and specify starting values and r constant
# x is iterations
# y is X
# p is Xn
# q is Xn+1
# z is deltaX = Xn+1 - Xn
steps = 100
x = np.zeros(steps + 1)
y = np.zeros(steps + 1)
p = np.zeros(steps + 1)
q = np.zeros(steps + 1)
z = np.zeros(steps + 1)
x[0], y[0] = 0, 0.4

r = 3.99

# loop over the steps and replace array values with calculations
for i in range(steps):
	p[i] = y[i]
	y[i+1] = r * y[i] * (1 - y[i])
	q[i] = y[i+1]
	z[i] = y[i+1] - y[i]
	x[i+1] = x[i] + 1

# plot the figure!
fig, (axs1, axs2, axs3) = plt.subplots(1, 3)
axs1.plot(x, y, alpha=0.5)
axs1.set(xlabel='Iterations', ylabel='X')
axs1.set_title("x against iterations to r = " + str(r))

axs2.plot(x, z, alpha=0.5)
axs2.set(xlabel='Iterations', ylabel='deltaX')
axs2.set_title("deltaX against iterations to r = " + str(r))

axs3.plot(q, p, alpha=0.5)
axs3.set(xlabel='Xn+1', ylabel='Xn')
axs3.set_title("Xn+1 against Xn to r = " + str(r))

plt.show()

```
