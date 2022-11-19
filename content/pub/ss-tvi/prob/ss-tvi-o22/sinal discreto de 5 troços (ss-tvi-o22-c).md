# Problema

(Retirado de O&W-1.22-p59)

Considere o seguinte sinal em tempo discreto $x(n)$ :

![ss-tvi-o22-xn](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-xn.svg)

Desenhe cuidadosamente cada um dos seguintes sinais.

(a) $x(n-4)$

(b) $x(3-n)$

(c) $x(3n)$

(d) $x(3n+1)$

```python {pre}

# change current directory to note directory
import os
note_file = @vault[12:] + @note[11:]
note_dir = note_file[:note_file.rfind('/')]
os.chdir(note_dir)

import numpy as np
import matplotlib.pyplot as plt

def PlotDSignal(var: np.array, signal: np.array, name: str) -> None:
    plt.figure(figsize=(7, 3))
    plt.stem(var, signal, markerfmt='o',basefmt='black')
    plt.xticks(np.arange(min(n), max(n)+1, 1.0))
    plt.gca().margins(y=0.15)
    plt.grid()
    plt.ylabel('$'+name+'$')
    return

# define signal x(n)
def x(n: np.array) -> np.array:
	return np.piecewise(n.astype(float),
		[n<-4, ((n>=-4) & (n<0)), ((n>=0) & (n<3)), (n==3), (n>=4)],
		[0, lambda n: 0.5*n+1.5, 1, 0.5, 0])
```

(a)  $y_a(n) = x(n-4)$
```run-python

# time axis 
n = np.arange(-7,10)

# x(n)
PlotDSignal(n, x(n), 'x(n)')
plt.savefig('attachments/ss-tvi-o22-xa.svg')

# ya(n)=x(n-4)
PlotDSignal(n, x(n-4), 'y_a(n)=x(n-4)')
plt.savefig('attachments/ss-tvi-o22-ya.svg')

```

$x(n)$
![ss-tvi-o22-xa](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-xa.svg)

$y_a(n) = x(n-4)$ (deslocamento temporal de 4 unidades para a direita)
![ss-tvi-o22-ya](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-ya.svg)
(b) $y_b(n) = x(3-n)$

```run-python
# time axis 
n = np.arange(-7,10)

# x(n)
PlotDSignal(n, x(n), 'x(n)')
plt.savefig('attachments/ss-tvi-o22-xb.svg')

# x1b(n) = x(n+3)
PlotDSignal(n, x(n+3), 'x_1b(n)=x(-n)')
plt.savefig('attachments/ss-tvi-o22-x1b.svg')

# yb(n) = x1b(-n) = x(3-n)
PlotDSignal(n, x(3-n), 'y_b(n)=x_1b(-n)=x(3-n)')
plt.savefig('attachments/ss-tvi-o22-yb.svg')

```

$x(n)$
![ss-tvi-o22-xb](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-xb.svg)

$x_{1b}(n) = x(n+3)$ (deslocamento temporal de 3 unidades para a esquerda)
![ss-tvi-o22-x1b](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-x1b.svg)

$y_b(n) = x_{1b}(-n) = x(3-n)$ (inversão temporal)
![ss-tvi-o22-yb](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-yb.svg)

(c) $y_c(n) = x(3n)$

```run-python
# time axis 
n = np.arange(-7,10)

# x(n)
PlotDSignal(n, x(n), 'x(n)')
plt.savefig('attachments/ss-tvi-o22-xc.svg')

# yc(n) = x(3n)
PlotDSignal(n, x(3*n), 'y_c(n)=x(3n)')
plt.savefig('attachments/ss-tvi-o22-yc.svg')

```

$x(n)$
![ss-tvi-o22-xc](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-xc.svg)

$y_c(n) = x(3n)$ (compressão temporal de 3 vezes)
![ss-tvi-o22-yc](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-yc.svg)

(d) $y_d(n) = x(3n+1)$

```run-python
# time axis 
n = np.arange(-7,10)

# x(n)
PlotDSignal(n, x(n), 'x(n)')
plt.savefig('attachments/ss-tvi-o22-xd.svg')

# x1d(n) = x(n+1)
PlotDSignal(n, x(n+1), 'x_d(n)=x(n+1)')
plt.savefig('attachments/ss-tvi-o22-x1d.svg')

# yd(n) = x1d(3n) = x(3n+1)
PlotDSignal(n, x(3*n+1), 'y_d(n)=x_d(3n)=x(3n+1)')
plt.savefig('attachments/ss-tvi-o22-yd.svg')

```

$x(n)$
![ss-tvi-o22-xd](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-xd.svg)

$x_{1d}(n) = x(n+1)$ (deslocamento temporal de 1 unidade para a esquerda)
![ss-tvi-o22-x1d](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-x1d.svg)

$y_d(n) = x_{1d}(3n) = x(3n+1)$ (compressão temporal de 3 vezes)
![ss-tvi-o22-yd](pub/ss-tvi/prob/ss-tvi-o22/attachments/ss-tvi-o22-yd.svg)



