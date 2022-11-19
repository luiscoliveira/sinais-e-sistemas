# [periodicidade no tempo da exponencial complexa em tempo discreto](pub/ss-exp/conc/periodicidade%20no%20tempo%20da%20exponencial%20complexa%20em%20tempo%20discreto.md)

No caso discreto, a sequência exponencial complexa nem sempre é
periódica.

$$\begin{eqnarray*}
x(n) & = & x(n+N)\\
|A| e^{j (\omega_0 n + \phi)} & = & |A| e^{j (\omega_0 (n+N) + \phi)} \\
& = &  |A| e^{j (\omega_0 n + \phi)} e^{j \omega_0 N}
\end{eqnarray*}$$

Só é periódica se:
$$ \omega_0 N = 2 \pi k \Leftrightarrow  N = 2 \pi k / \omega_0, \;\; k \in \mathbb{Z} $$

em que $N$ tem de ser inteiro. Para isso acontecer $\omega_0$ tem de ser múltiplo ou submúltiplo de $\pi$.
