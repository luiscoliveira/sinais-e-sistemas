![pra-ss-imp-2 sinal disc 5 tr (O&W-1.22-p59)-enunciado](pub/ss-imp/prob/ss-imp-o22/pra-ss-imp-2%20sinal%20disc%205%20tr%20(O&W-1.22-p59)-enunciado.md)



```python {pre}

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

# for saving the figures
vault = @vault
note = @note
file = vault[12:] + '/' + note[12:-9]

def u(n: np.array) -> np.array:
	return np.piecewise(
		n.astype(float),
		[n<0, n>=0],
		[0, 1])

def delta(n: np.array) -> np.array:
	return np.piecewise(
		n.astype(float),
		[n<0, n==0, n>0],
		[0, 1, 0])

def x(n: np.array) -> np.array:
	return np.piecewise(n.astype(float),
		[n<-4, ((n>=-4) & (n<0)), ((n>=0) & (n<3)), (n==3), (n>=4)],
		[0, lambda n: 0.5*n+1.5, 1, 0.5, 0])


```

```run-python

# x axis
n = np.arange(-7,10)

print('(e) ye(n)=x(n)u(n-3)')
PlotDSignal(n, x(n), 'x(n)')
plt.savefig(file + 'fig x.svg')
plt.show()

PlotDSignal(n, u(3-n), 'x_e=u(3-n)')
plt.savefig(file + 'fig xe.svg')
plt.show()


PlotDSignal(n, x(n)*u(3-n), 'y_e(n)=x(n)u(3-n)')
plt.savefig(file + 'fig ye.svg')
plt.show()
```

```run-python

# x axis
n = np.arange(-7,10)

print('(f) yf(n)=x(n-2)delta(n-2)')
PlotDSignal(n, x(n), 'x(n)')
plt.show()

PlotDSignal(n, x(n-2), 'x_f=x(n-2)')
plt.savefig(file + 'fig xf.svg')
plt.show()


PlotDSignal(n, x(n-2)*delta(n-2), 'y_f(n)=x(n-2)delta(n-2)')
plt.savefig(file + 'fig yf.svg')
plt.show()
```


```run-python

# x axis
n = np.arange(-7,10)

print('(g) yg(n)=x(n) (1 + (-1)^n)/2')
PlotDSignal(n, x(n), 'x(n)')
plt.show()

PlotDSignal(n, (1 +(-1)**n.astype(float))/2, 'x_g=(1 + (-1)^n)/2')
plt.savefig(file + 'fig xg.svg')
plt.show()


PlotDSignal(n, (1 + (-1)**n.astype(float))*x(n)/2 , 'y_g(n)=(1+(-1)^n)x(n)/2')
plt.savefig(file + 'fig yg.svg')
plt.show()
```


```run-python

# x axis
n = np.arange(-2,5)

print('(h) yf(n)=x((n-1)^2)')
PlotDSignal(n, x(n), 'x(n)')
plt.show()

PlotDSignal(n, (n-1)**2, 'x_h=(n-1)^2')
plt.savefig(file + 'fig xh.svg')
plt.show()


PlotDSignal(n, x((n-1)**2), 'y_h(n)=x((n-1)^2)')
plt.savefig(file + 'fig yh.svg')
plt.show()
```
