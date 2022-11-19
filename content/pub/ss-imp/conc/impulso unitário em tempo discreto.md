# [impulso unitário em tempo discreto](pub/ss-imp/conc/impulso%20unitário%20em%20tempo%20discreto.md)

$$\delta(n) =
\begin{cases}
0, & n \neq 0.\\
1, & n = 0.
\end{cases}
$$

![300](pub/ss-imp/conc/attachments/impulso.svg)


Nota: Qualquer sinal em tempo discreto pode ser expresso como uma soma de impulsos unitários escalados e deslocados no tempo:
$$ x(n) = \sum_{k = -\infty}^{+\infty} x(k) \delta(n-k) $$