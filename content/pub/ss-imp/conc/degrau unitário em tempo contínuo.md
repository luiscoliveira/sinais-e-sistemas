# [degrau unitário em tempo contínuo](pub/ss-imp/conc/degrau%20unitário%20em%20tempo%20contínuo.md)

$$ u(t) =
\begin{cases}
0, & t < 0.\\
1, & t > 0.
\end{cases}
$$

![escalaoc](pub/ss-imp/conc/attachments/escalaoc.svg)

Para resolver a ambiguidade em $0$ usa-se por vezes:
$$ u_a(t) =
\begin{cases}
0, & t < 0.\\
a, & t = 0.\\
1, & t > 0.
\end{cases}
$$

A representação do degrau unitário como um integral de impulsos:
$$ u(t) = \int_{0}^{+\infty} \delta(t-\tau) d\tau.$$