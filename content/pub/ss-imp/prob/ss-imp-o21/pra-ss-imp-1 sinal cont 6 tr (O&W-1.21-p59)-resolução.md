
![pra-ss-imp-1 sinal cont 6 tr (O&W-1.21-p59)-enunciado](pra-ss-imp-1%20sinal%20cont%206%20tr%20(O&W-1.21-p59)-enunciado)

(e) $[x(t) + x(-t)] u(t)$

O sinal original
$x(t)$
![fig-p-1-21.svg](fig-p-1-21.svg)
O temo $x(t) + x(-t)$ é o dobro da parte par do sinal $x(t)$
$x_1(t) = x(t) + x(-t)$
![fig-p-1-21-e-x1.svg](fig-p-1-21-e-x1.svg)
Resta agora multiplicar pelo escalão unitário $u(t)$, ou seja, tomar só a parte em que $t>0$.
$x_2(t) = \left[ x(t) + x(-t) \right] u(t)$
![fig-p-1-21-e.svg](fig-p-1-21-e.svg)

(f) $x(t)\left[\delta(t+\frac{3}{2})-\delta(t-\frac{3}{2})\right]$

Retomando o sinal original
$x(t)$
![fig-p-1-21.svg](fig-p-1-21.svg)

Conhecida a propriedade da função $\delta(t)$:
$$
x(t) \delta(t-t_0) = x(t_0) \delta(t-t_0)
$$
Aplicado ao nosso sinal $x(t)$:

$$
x(t)\left[\delta(t+1.5)-\delta(t-1.5)\right] = 
x(-1.5) \delta(t+1.5) - x(1.5) \delta(t-1.5)
$$
ou seja
$$
x(t)\left[\delta(t+1.5)-\delta(t-1.5)\right] = 
-0.5 \delta(t+1.5) - 0.5 \delta(t-1.5)
$$

