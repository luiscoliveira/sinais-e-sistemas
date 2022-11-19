---
title: "escalão e impulso contínuo (ss-imp-o21)"
---
# Problema

Considere o sinal em tempo contínuo $x(t)$ representado na figura seguinte:

![ss-imp-o21](pub/ss-imp/prob/ss-imp-o21/attachments/ss-imp-o21.svg)
Desenhe cuidadosamente cada um dos seguintes sinais:

(e) $[x(t) + x(-t)] u(t)$

(f) $x(t)\left[\delta(t+\frac{3}{2})-\delta(t-\frac{3}{2})\right]$

## Código

Definir o sinal $x(t)$ e traçar o seu gráfico

```python {pre}
# change current directory to note directory
import os
note_file = @vault[12:] + @note[11:]
note_dir = note_file[:note_file.rfind('/')]
os.chdir(note_dir)

# continuous time signal
import sympy as sp
t = sp.Symbol('t', real=True)

# define the signal
xt = sp.Piecewise((0, t<-2),
                  (t+1, (t>-2) & (t<-1)),
                  (1, (t>-1) & (t<0)),
                  (2, (t>0) & (t<1)),
                  (-t+2, (t>1) & (t<2)),
                  (0, t>2))
# sp.print_latex(xt)

p0 = sp.plot(xt, (t, -3, 3), xlabel='', ylabel='', show=False)
p0.save('attachments/ss-imp-o21-xt.svg')
```

(e) $[x(t) + x(-t)] u(t)$

```run-python

# unit step function U(t)
U = sp.Lambda(t, (sp.sign(t)+1)/2)

# compute x1(t) = x(t) + x(-t)
x1t = (xt + xt.subs(t, -t))
p1 = sp.plot(x1t, (t, -3, 3), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-imp-o21-x1t.svg')

# compute xe(t) = x1(t) U(t)
xet = (xt + xt.subs(t, -t)) * U(t)
p2 = sp.plot(xet, (t, -3, 3), xlabel='', ylabel='', show=False)
p2.save('attachments/ss-imp-o21-xet.svg')
```
$x(t)$
![ss-imp-o21-xt](pub/ss-imp/prob/ss-imp-o21/attachments/ss-imp-o21-xt.svg)
$x_1(t) = x(t) + x(-t)$
![ss-imp-o21-x1t](pub/ss-imp/prob/ss-imp-o21/attachments/ss-imp-o21-x1t.svg)
$x_e(t) = x_1(t) u(t) = (x(t) + x(-t)) u(t)$

![ss-imp-o21-xet](pub/ss-imp/prob/ss-imp-o21/attachments/ss-imp-o21-xet.svg)

(f) $x(t)\left[\delta(t+\frac{3}{2})-\delta(t-\frac{3}{2})\right]$

```run-python

# xf(t) = x(-3/2) delta(t+3/2) - x(3/2) delta(t+3/2)
xft = xt.subs(t,-3/2) * sp.DiracDelta(t+3/2) - xt.subs(t,3/2) * sp.DiracDelta(t-3/2)

p3 = sp.plot(xft, (t, -3, 3), xlabel='', ylabel='', show=False)
p3.save('attachments/ss-imp-o21-xft.svg')
```

![ss-imp-o21-xft](pub/ss-imp/prob/ss-imp-o21/attachments/ss-imp-o21-xft.svg)