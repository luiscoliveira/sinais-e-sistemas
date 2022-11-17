---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.13.5
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

# Problemas Cap. 1

_Luis Caldas de Oliveira_




## Problema 1.21

[[Sec-1.2 Transformação da variável independente (tvi)]]

Considere o sinal em tempo contínuo $x(t)$ definida por ramos (_picewise_):

$$
x(t) = 
\begin{cases} 0 & \text{para}\: t < -2 \\t + 1 & \text{para}\: t > -2 \wedge t < -1 \\1 & \text{para}\: t > -1 \wedge t < 0 \\2 & \text{para}\: t > 0 \wedge t < 1 \\2 - t & \text{para}\: t > 1 \wedge t < 2 \\0 & \text{para}\: t > 2 \end{cases}
$$

Desenhe cuidadosamente cada um dos seguintes sinais.

(a) $x(t-1)$

(b) $x(2-t)$

(c) $x(2t+1)$

(d) $x(4-\frac{t}{2})$

(e) $[x(t) + x(-t)] u(t)$

(f) $x(t)\left[\delta(t+\frac{3}{2})-\delta(t-\frac{3}{2})\right]$



```python
import sympy as sp
t = sp.Symbol('t', real=True)
xt = sp.Piecewise((0, t<-2),
                  (t+1, (t>-2) & (t<-1)),
                  (1, (t>-1) & (t<0)),
                  (2, (t>0) & (t<1)),
                  (-t+2, (t>1) & (t<2)),
                  (0, t>2))
# sp.print_latex(xt)

print('x(t)')
p0 = sp.plot(xt, (t, -3, 5), xlabel='', ylabel='', show=False)
p0.save('fig-p-1-21.svg')
p0.show()
```

```python
print('(a) x(t-1)')
xta = xt.subs(t, t-1)
p1 = sp.plot(xta, (t, -3, 5), xlabel='', ylabel='', show=False)

print('x(t)')
p0.show()
print('x(t-1)')
p1.save('fig-p-1-21-a.svg')
p1.show()
```

```python
print('(b) x(2-t)')
x1t = xt.subs(t, -t)
p1 = sp.plot(x1t, (t, -3, 5), xlabel='', ylabel='', show=False)
x2t = xt.subs(t, 2-t)
p2 = sp.plot(x2t, (t, -3, 5), xlabel='', ylabel='', show=False)

print('x(t)')
p0.show()
print('x1(t) = x(-t)')
p1.save('fig-p-1-21-b-x1.svg')
p1.show()
print('x2(t) = x1(t-2) = x(2-t)')
p2.save('fig-p-1-21-b.svg')
p2.show()
```

```python
print('(c) x(2t+1)')
x1t = xt.subs(t, 2*t)
p1 = sp.plot(x1t, (t, -3, 5), xlabel='', ylabel='', show=False)
x2t = xt.subs(t, 2*t+1)
p2 = sp.plot(x2t, (t, -3, 5), xlabel='', ylabel='', show=False)

print('x(t)')
p0.show()
print('x1(t) = x(2t)')
p1.save('fig-p-1-21-c-x1.svg')
p1.show()
print('x2(t) = x1(t+1/2) = x(2t+1)')
p2.save('fig-p-1-21-c.svg')
p2.show()
```

```python
print('(d) x(4-t/2)')
p0 = sp.plot(xt, (t, -4, 13), xlim=(-4, 13), xlabel='', ylabel='', show=False)
x1t = xt.subs(t, -t/2)
p1 = sp.plot(x1t, (t, -4, 13), xlim=(-4, 13), xlabel='', ylabel='', show=False)
x2t = xt.subs(t, 4-t/2)
p2 = sp.plot(x2t, (t, -4, 13), xlim=(-4, 13), xlabel='', ylabel='', show=False)

print('x(t)')
p0.show()
print('x1(t) = x(-t/2)')
p1.save('fig-p-1-21-d-x1.svg')
p1.show()
print('x2(t) = x1(t-8) = x(4-t/2)')
p2.save('fig-p-1-21-d.svg')
p2.show()
```

```python
print('(e) (x(t) + x(-t)) u(t)')
U = sp.Lambda(t, (sp.sign(t)+1)/2)

p0 = sp.plot(xt, (t, -3, 5), xlabel='', ylabel='', show=False)
x1t = (xt + xt.subs(t, -t))
p1 = sp.plot(x1t, (t, -3, 5), xlabel='', ylabel='', show=False)
x2t = (xt + xt.subs(t, -t)) * U(t)
p2 = sp.plot(x2t, (t, -3, 5), xlabel='', ylabel='', show=False)

print('x(t)')
p0.show()
print('x1(t) = x(t) + x(-t)')
p1.save('fig-p-1-21-e-x1.svg')
p1.show()
print('x2(t) = x1(t) u(t) = (x(t) + x(-t)) u(t)')
p2.save('fig-p-1-21-e.svg')
p2.show()
```

```python
print('(f) x(t) (\delta(t+3/2)) - \delta(t-3/2))')

x1t = xt.subs(t,-3/2) * sp.DiracDelta(t+3/2) - xt.subs(t,3/2) * sp.DiracDelta(t-3/2)

sp.init_printing()
display(x1t)
```

## Problema 1.22

[[Sec-1.2 Transformação da variável independente (tvi)]]

Página 59 do livro guia

Considere o seguinte sinal em tempo discreto $x(n)$ :

Desenhe cuidadosamente cada um dos seguintes sinais.

(a) $x(n-4)$

(b) $x(3-tn)$

(c) $x(3n)$

(d) $x(3n+1)$

(e) $x(n) u(3-n)$

(f) $x(n-2)\delta(n-2)$

(g) $\frac{1}{2} x(n) + \frac{1}{2} (-1)^n x(n)$

(h) $x((n-1)^2)$


```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

n = np.arange(-5,5)
x = np.array([0, -1, -1/2, 1/2, 1, 1, 1, 1, 1/2, 0])

plt.figure(figsize=(6, 3))
plt.stem(n, x)
plt.xlabel('$n$')
plt.ylabel('$x(n)$')
plt.gca().margins(y=0.1)
```

```python
import numpy as np
import matplotlib
import matplotlib.pyplot as plt

def PlotDSignal(var: np.array, signal: np.array, name: str) -> None:
    plt.figure(figsize=(7, 3))
    plt.stem(var, signal, markerfmt='o',basefmt='black')
    plt.xticks(np.arange(min(n), max(n)+1, 1.0))
    plt.gca().margins(y=0.15)
    plt.grid()
    plt.ylabel('$'+name+'$')
    return

def x(n: np.array) -> np.array:
	return np.piecewise(n.astype(float), [n<-4, ((n>=-4) & (n<0)), ((n>=0) & (n<3)), (n==3), (n>=4)], [0, lambda n: 0.5*n+1.5, 1, 0.5, 0])

n = np.arange(-7,10)

print('(a)  ya(n)=x(n-4)')
stc = PlotDSignal(n, x(n), 'x(n)')
print(type(st))
plt.savefig('teste' + '.svg')
plt.show()

PlotDSignal(n, x(n-4), 'y_a(n)=x(n-4)')
plt.show()

```

```python

```
