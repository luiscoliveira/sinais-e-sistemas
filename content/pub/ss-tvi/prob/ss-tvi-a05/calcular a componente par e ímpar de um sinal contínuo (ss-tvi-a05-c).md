---
title: "calcular a componente par e ímpar de um sinal contínuo (ss-tvi-a05)"
---

# Problema

Determinar a componente par e ímpar do sinal real definido pelo seguinte gráfico:

![compon](pub/ss-tvi/prob/ss-tvi-a05/attachments/compon.svg)

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
                  (-t-1, (t>-2) & (t<-1)),
                  (t+1, (t>-1) & (t<1)),
                  (-t+3, (t>1) & (t<2)),
                  (0, t>2))

```

(a) $x_e(t) = (x(t) + x^*(-t))/2$

```run-python
tmin = -3
tmax = 3

p0 = sp.plot(xt, (t, tmin, tmax), xlabel='', ylabel='', show=False)
p0.save('attachments/ss-tvi-a05-xa.svg')

p1 = sp.plot(xt.subs(t, -t), (t, tmin, tmax), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-tvi-a05-xa-.svg')

p2 = sp.plot((xt + xt.subs(t, -t))/2, (t, tmin, tmax), 
xlabel='', ylabel='', show=False)
p2.save('attachments/ss-tvi-a05-xe.svg')

plt.show()

```

$x(t)$
![ss-tvi-a05-xa](pub/ss-tvi/prob/ss-tvi-a05/attachments/ss-tvi-a05-xa.svg)
$x(-t)$
![ss-tvi-a05-xa-](pub/ss-tvi/prob/ss-tvi-a05/attachments/ss-tvi-a05-xa-.svg)
$x_e(t) = (x(t) + x^*(-t))/2$
![ss-tvi-a05-xe](pub/ss-tvi/prob/ss-tvi-a05/attachments/ss-tvi-a05-xe.svg)


(b) $x_o(t) = (x(t) - x^*(-t))/2$

```run-python
tmin = -3
tmax = 3

p0 = sp.plot(xt, (t, tmin, tmax), xlabel='', ylabel='', show=False)
p0.save('attachments/ss-tvi-a05-xb.svg')

  
p1 = sp.plot(xt.subs(t, -t), (t, tmin, tmax), xlabel='', ylabel='', show=False)
p1.save('attachments/ss-tvi-a05-xb-.svg')


p2 = sp.plot((xt - xt.subs(t, -t))/2, (t, tmin, tmax), xlabel='', ylabel='', show=False)
p2.save('attachments/ss-tvi-a05-xo.svg')

plt.show()

```

$x(t)$
![ss-tvi-a05-xb](pub/ss-tvi/prob/ss-tvi-a05/attachments/ss-tvi-a05-xb.svg)
$x(-t)$
![ss-tvi-a05-xb-](pub/ss-tvi/prob/ss-tvi-a05/attachments/ss-tvi-a05-xb-.svg)
$x_o(t) = (x(t) - x^*(-t))/2$
![ss-tvi-a05-xo](pub/ss-tvi/prob/ss-tvi-a05/attachments/ss-tvi-a05-xo.svg)