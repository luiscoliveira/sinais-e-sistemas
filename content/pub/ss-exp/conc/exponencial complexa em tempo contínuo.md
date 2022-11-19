# [exponencial complexa em tempo contínuo](pub/ss-exp/conc/exponencial%20complexa%20em%20tempo%20contínuo.md)

$$x(t) = C e^{a t}$$
em que $C$ e $a$ podem ser números complexos:
$$\begin{eqnarray*}
C = & A e^{j \phi}, & \;A,\phi \in \mathbb{R} \\
a = &-\alpha +j \omega_0, & \;\alpha,\omega_0 \in \mathbb{R}
\end{eqnarray*}$$

$$ x(t) = A e^{-\alpha t} e^{j (\omega_0 t + \phi)} $$
decompondo em parte real e imaginária:
$$\begin{eqnarray*}
\Re \{x(t)\} &=& A e^{-\alpha t} \cos(\omega_0 t + \phi) \\
\Im \{x(t)\} &=& A e^{-\alpha t} \sin(\omega_0 t + \phi)
\end{eqnarray*}$$