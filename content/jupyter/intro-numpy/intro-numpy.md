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

# Introdução à Biblioteca NumPy

_Luis Caldas de Oliveira_

O NumPy é a biblioteca normalmente usada em Python quando se pretende realizar computação numérica de forma eficiente. Nesse caso a estrutura de dados mais comum é a matriz multi-dimensional.


## Matrizes multi-dimensionais

A classe `ndarray`, definida na biblioteca NumPy, permite realizar operações sobre matrizes de forma mais intuitiva e rápida do que se conseguiria com a classe `list` da versão de base do Python.

Em listas a operação `+` faz a concatenação de duas listas e a `*` não tem significado:

```python
a = [1,2,3]
b = [4,5,6]
print("a+b:", a+b)
try:
    print(a*b)
except TypeError:
    print("A multiplicação de listas (a*b) não tem significado em Python")
```

As mesmas operações têm um significado diferente quando operam sobre a classe `ndarray`:

```python
import numpy as np

a = np.array([1,2,3])
b = np.array([4,5,6])
print("a+b:", a+b)
print("a*b:", a*b)
```

A classe `ndarray` tem também as característas esperadas de uma matriz multi-dimensional, nomeadamente os diferentes eixos. No caso de um matriz bi-dimensional, o primeiro eixo corresponde às linhas da matriz e o segundo às colunas

```python
matriz2D = np.array([[1, 2], [3, 4]])
print(matriz2D)
print(" ")
print(matriz2D[0])
print("matriz2D.sum(axis=0)=", matriz2D.sum(axis=0))
print("matriz2D.sum(axis=1)=", matriz2D.sum(axis=1))
```

Para uma matriz com 3 dimensões:

```python
matriz3D = np.array([[[1, 2, 3], [4, 5, 6], [7, 8, 9]],
                     [[1, 2, 3], [4, 5, 6], [7, 8, 9]],
                     [[1, 2, 3], [4, 5, 6], [7, 8, 9]]])
print(matriz3D)
print(" ")
print(matriz3D.sum(axis=0))
print(" ")
print(matriz3D.sum(axis=1))
print(" ")
print(matriz3D.sum(axis=2))
```

As operações matriciais são fáceis de indicar:

```python
m1 = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
m2 = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(m1+m2)
print(m1*m2)
```

## Funções para matrizes multi-dimensionais

Ao definir funções para processar matrizes multi-dimensionais é útil tornar patente que estas recebem e retornam objetos da classe `ndarray`.

```python
def square(x: np.ndarray) -> np.ndarray:
    '''
    Square each element in the input ndarray.
    '''
    return np.power(x, 2)

matriz = np.array([[1, 2], [3, 4]])
print(matriz)
print(square(matriz))
```

## Representação gráfica

A biblioteca `matplotlib` pode ser usada para visualizar o conteúdo de vetores e matrizes.

Para visualizar um vetor que tem amostras de uma função sinusoidal:

```python
import matplotlib.pyplot as plt

x = np.arange(-2*np.pi, 2*np.pi, 0.1)
y = np.sin(x)
plt.plot(x, y)
plt.xlabel("x")
plt.ylabel("y")
plt.title("y = sin(x)");
```

Para ter mais controlo sobre as figuras, o melhor é usada a abordagem dos objetos para criar um objeto figura que contém todo o gráfico.

```python
# O objeto fig vai conter todo o gráfico
fig = plt.figure()
# Divide o espaço da figura numa linha e numa coluna e usa a
# primeira, divisão, ou seja, o gráfico vai ocupar todo o espaço
ax = fig.add_subplot(111)
# junta coisas ao espaço ax
ax.plot(x, y)
ax.set_xlabel("x")
ax.set_ylabel("y")
ax.set_title("y = sin(x)")
```

Existe uma coleção de [tutoriais para o matplotlib](https://matplotlib.org/stable/tutorials/index.html)
