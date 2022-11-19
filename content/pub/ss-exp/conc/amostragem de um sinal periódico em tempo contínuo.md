# [amostragem de um sinal periódico em tempo contínuo](pub/ss-exp/conc/amostragem%20de%20um%20sinal%20periódico%20em%20tempo%20contínuo.md)

A amostragem de um sinal periódico em tempo contínuo nem sempre resulta num sinal periódico em tempo discreto.

$$x_c(t) = x_c(t+T) , \;\; T \in \mathbb{R} \land \forall t \in \mathbb{R}$$
Sabendo que $x_d(n) = x_c(nT_s)$, para o sinal amostrado ser periódico é necessário que:
$$
\begin{eqnarray*}
x_d(n) &=& x_d(n+N)\\
&=& x_c(nT_s + NT_s)\\
\end{eqnarray*}
$$
Se $NT_s=kT$ com $k \in \mathbb{Z}$ então 
$$
\begin{eqnarray*}
x_d(n) &=& x_c(nTs+kT)\\
&=& x_c(nT_s)\\
\end{eqnarray*}
$$
Para $x_d(n)$ ser periódico é necessário que:
$$
\exists \{k,N\} \in \mathbb{Z_+}: N = k \frac{T}{T_s} 
$$
Ou seja, é necessário que a frequência de amostragem $F_s=1/T_s$ tem de ser um múltiplo da frequência do sinal $F=1/T$.

O período de $x_d(n)$ é o menor valor de $N$ que verifica a equação anterior.

