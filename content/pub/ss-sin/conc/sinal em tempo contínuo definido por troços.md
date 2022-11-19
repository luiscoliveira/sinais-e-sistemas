---
title: "sinal em tempo contínuo definido por troços"
---

 Certos sinais são caracterizados por troços. Um sinal em tempo contínuo dest tipo pode ser representado por um gráfico:
![sinal-cont-6-trocos](pub/ss-sin/conc/attachments/sinal-cont-6-trocos.svg)

por uma equação matemática:

$$
\forall t \in \mathbb{R}, \; x(t) =
\begin{cases}
0 & \text{para}\: t < -2 \\
t + 1 & \text{para}\: t > -2 \wedge t < -1 \\
1 & \text{para}\: t > -1 \wedge t < 0 \\
2 & \text{para}\: t > 0 \wedge t < 1 \\
2 - t & \text{para}\: t > 1 \wedge t < 2 \\
0 & \text{para}\: t > 2
\end{cases}
$$


ou por um programa de computador:

```python
import sympy as sp
t = sp.Symbol('t', real=True)

# define the signal
xt = sp.Piecewise((0, t < -2),
                  (t+1, (t > -2) & (t < -1)),
                  (1, (t > -1) & (t < 0)),
                  (2, (t > 0) & (t < 1)),
                  (-t+2, (t > 1) & (t < 2)),
                  (0, t > 2))

# plot the signal
sp.plot(xt)
```


Próximo: [tom puro em tempo contínuo](pub/ss-sin/conc/tom%20puro%20em%20tempo%20contínuo.md)