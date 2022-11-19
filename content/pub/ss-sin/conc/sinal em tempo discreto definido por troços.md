---
title: "sinal em tempo discreto definido por troços"
---
 
 Um sinal em tempo discreto definido por troços pode ser representado por um gráfico:
![sinal-discreto-5-trocos](pub/ss-sin/conc/attachments/sinal-discreto-5-trocos.svg)

por uma equação matemática:

$$
\forall n \in \mathbb{Z}, \; x(n) =
\begin{cases} 0 & \text{para}\: n < -4 \\
(3+n)/2 & \text{para}\: n \ge -4 \wedge n < 0 \\
1 & \text{para}\: n \ge 0 \wedge n < 3 \\
1/2 & \text{para}\: n = 3 \\
0 & \text{para}\: n \ge 4 \end{cases}
$$


ou por um programa de computador:

```run-python
import numpy as np

# define signal x(n) as a function
def x(n: np.array) -> np.array:
	return np.piecewise(n.astype(float),
		[n<-4, ((n>=-4) & (n<0)), ((n>=0) & (n<3)), (n==3), (n>=4)],
		[   0, lambda n: (n+3)/2,                1,    0.5,     0 ])

# time axis
n = np.arange(-7,10)

# plot
import matplotlib.pyplot as plt
plt.stem(n, x(n))
plt.grid()
plt.show()
```


Próximo: [valor de fecho de índice de bolsa](pub/ss-sin/conc/valor%20de%20fecho%20de%20índice%20de%20bolsa.md)