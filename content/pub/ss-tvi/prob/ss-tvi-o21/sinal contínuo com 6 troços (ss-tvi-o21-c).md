---
title: "sinal contínuo com 6 troços (ss-tvi-o21-c)"
---

# Problema

(retirado de O&W-1.21-p59)

Considere o sinal em tempo contínuo $x(t)$ representado na figura seguinte:

![ss-tvi-o21](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21.svg)
Desenhe cuidadosamente cada um dos seguintes sinais:

(a) $x(t-1)$

(b) $x(2-t)$

(c) $x(2t+1)$

(d) $x(4-\frac{t}{2})$

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


```

(a) $y_a(t) = x(t-1)$

```run-python
tmin = -3
tmax = 5

p0 = sp.plot(xt, (t, tmin, tmax), xlabel='', ylabel='', show=False)
p0.save('attachments/ss-tvi-o21-xa.svg')

p1 = sp.plot(xt.subs(t, t-1), (t, tmin, tmax), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-tvi-o21-ya.svg')

plt.show()

```

$x(t)$
![ss-tvi-o21-xa](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-xa.svg)
$y_a(t) = x(t-1)$ (deslocamento temporal de uma unidade para a direita)
![ss-tvi-o21-ya](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-ya.svg)

(b) $y_b(t) = x(2-t)$

```run-python
tmin = -5
tmax = 5

p0 = sp.plot(xt, (t, tmin, tmax), xlabel='', ylabel='', show=False)
p0.save('attachments/ss-tvi-o21-xb.svg')

# x1b(t) = x(t+2)
p1 = sp.plot(xt.subs(t, t+2), (t, tmin, tmax), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-tvi-o21-x1b.svg')

# yb(t) = x1b(-t) = x(2-t)
p1 = sp.plot(xt.subs(t, 2-t), (t, tmin, tmax), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-tvi-o21-yb.svg')

plt.show()

```

$x(t)$
![ss-tvi-o21-xb](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-xb.svg)

$x_{1b}(t) = x(t+2)$ (deslocamento temporal de 2 unidades para a esquerda)
![ss-tvi-o21-x1b](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-x1b.svg)
$y_b(t) = x_{1b}(-t) = x(2-t)$ (inversão temporal)
![ss-tvi-o21-yb](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-yb.svg)

(c) $y_c(t) = x(2t+1)$

```run-python
tmin = -4
tmax = 4

p0 = sp.plot(xt, (t, tmin, tmax), xlabel='', ylabel='', show=False)
p0.save('attachments/ss-tvi-o21-xc.svg')

# x1c(t) = x(t+1)
p1 = sp.plot(xt.subs(t, t+1), (t, tmin, tmax), xlabel='', ylabel='', show=False) 
p1.save('attachments/ss-tvi-o21-x1c.svg')

# yc(t) = x1c(2t) = x(2t+1)
p1 = sp.plot(xt.subs(t, 2*t+1), (t, tmin, tmax), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-tvi-o21-yc.svg')

plt.show()

```

$x(t)$

![ss-tvi-o21-xc](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-xc.svg)
$x_{1c}(t) = x(t+1)$ (deslocamento temporal de 1 unidade para a esquerda)
![ss-tvi-o21-x1c](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-x1c.svg)
$y_c(t) = x_{1c}(2t) = x(2t+1)$ (compressão temporal)
![ss-tvi-o21-yc](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-yc.svg)

(d) $y_d(t) = x(4-\frac{t}{2})$

```run-python
tmin = -7
tmax = 13

p0 = sp.plot(xt, (t, tmin, tmax), xlabel='', ylabel='', show=False)
p0.save('attachments/ss-tvi-o21-xd.svg')

# x1d(t) = x(t+4)
p1 = sp.plot(xt.subs(t, t+4), (t, tmin, tmax), xlabel='', ylabel='', show=False) 
p1.save('attachments/ss-tvi-o21-x1d.svg')

# yd(t) = x1d(-t/2) = x(4-t/2)
p1 = sp.plot(xt.subs(t, 4-t/2), (t, tmin, tmax), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-tvi-o21-yd.svg')

plt.show()

```

$x(t)$
![ss-tvi-o21-xd](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-xd.svg)
$x_{1d}(t) = x(t+4)$ (deslocamento temporal de 4 unidades para a esquerda)
![ss-tvi-o21-x1d](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-x1d.svg)

$y_d(t) = x_{1d}(-t/2) = x(4-t/2)$ (inversão temporal e expansão)
![ss-tvi-o21-yd](pub/ss-tvi/prob/ss-tvi-o21/attachments/ss-tvi-o21-yd.svg)



