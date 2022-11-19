---
title: "amostragem de um tom puro (ss-sin-a03)"
---
# Problema
Dada a expressão para o sinal de um tom puro de 440 Hz em tempo contínuo:
$$\forall t \in \mathbb{R}, x_c(t) = \sin(2 \pi \times 440 t)$$
obter o sinal em tempo discreto resultante da sua amostragem à frequência de 
$$F_s = 132 \text{KHz}$$

_Solução:_

Sendo 
$$ x_c(t) = \sin(2 \pi \times 440 t)$$
e a frequência de amostragem $F_s = 132 \text{KHz}$:
$$T = 1/F_s = 1/132000 $$


$$
\begin{eqnarray}
x(n) & = &  x_c(nT) \\
& = & x_c(n/F_s) \\
& = & \sin(\frac{2 \pi \times 440}{132000} n) \\
& = & \sin(\frac{2 \pi}{300} n) \\
\end{eqnarray}
$$

A amostragem resulta num sinal periódico de período $N = 300$.
