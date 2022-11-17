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

# Introdução aos Jupyter notebooks e ao Python

_Luis Caldas de Oliveira_

Este notebook tem como objetivo explicar o que é um Jupyter notebook e fazer uma breve introdução à linguagem de programação Python.


## Jupyter Notebooks

Um Jupyter Notebook é um ficheiro com extensão `.ipynb` que é composto por uma sequência de blocos denominados de células. Existem células de texto e células de código que podem ser editadas clicando nelas com o rato (as células de texto precisam de um duplo clique).

### Células de código

A célula seguinte é um exemplo de uma célula de código:

```python
print ("Célula de código")
```

Uma célula de código pode ser executada, sendo o resultado do da execução do código apresentado logo a seguir à célula. Para executar uma célula de código basta selecionar a célula e carregar em `Run` na barra de ferramentas no topo do notebook. Nessa barra existe também um botão com `+` que cria uma nova célula a seguir à célula atualmente ativa. A nova célula é, por omissão, uma célula de código que se identifica por ter à sua esquerda a sequência `In [ ]`. Depois de executada a célula de código é colocado um número no espaço entre os parênteses retos que indica a ordem em que as células foram executadas. A memória é persistente o que significa que, por exemplo, o valor das variáveis é mantido até à execução de outra célula e é independente da sua posição no notebook.



### Células de Texto

Para mudar uma célula de código para uma célula de texto muda-se o seletor da barra de ferramentas de `Code` para `Markdown` indicando que o texto deve ser formatado de acordo com esta norma.

Este é um exemplo de texto em Markdown:

````
# Título de nível 1
## Título de nível 2
### Título de nível 3

Lista de items:
- **primeiro em negrito**
- *segundo em itálico*
- _terceiro em itálico_

Lista enumerada
1. primeiro
2. segundo
3. terceiro

variável `a` e segmento de código
```
print ("segmento de código")
```
````

Após a execução da célula de texto com o comando `Run` o texto fica formatado assim:

# Título de nível 1
## Título de nível 2
### Título de nível 3

Lista de items:
- **primeiro em negrito**
- *segundo em itálico*
- _terceiro em itálico_

Lista enumerada
1. primeiro
2. segundo
3. terceiro

variável `a` e segmento de código
```
print ("segmento de código")
```

O interpretador de Markdown também aceita fórmula matemáticas em LaTeX. Por exemplo, a sequência:
```
Expressão no meio do texto $\sqrt{2}$ ou equação matemática:
$$ x = \frac{-b \pm \sqrt{b^2 - 4 a c}}{2a} $$
```
Resulta em:

Expressão no meio do texto $\sqrt{2}$ ou equação matemática:
$$ x = \frac{-b \pm \sqrt{b^2 - 4 a c}}{2a} $$



### Truques e atalhos do Jupyter

É possível executar comandos do interpretador de comandos do computador (shell) numa célula de código usando o símbolo `!` antes do comando.
Por exemplo para saber a diretoria atual:

```python
!pwd
```

Pode-se também usar comandos especiais do iPython como o `%timeit`para medir o tempo de execução do código:

```python
%timeit [x**2 for x in range(100)]
```

Pode-se também usar `?` para obter ajuda sobre um comando:

```python
?print
```

Também se pode usar o **Tab** para completar o texto ou **Shift-Tab** para obter uma ajuda rápida.


## Python Básico

### Variáveis e operações básicas

O Python segue as normas habituais para os operadores de atribuição (`=`), soma (`+`), subtração (`-`), multiplicação (`*`) e divisão (`/`). Em Python as variáveis não precisam de ser declaradas, assumindo o tipo adequado à atribuição que for feita.

```python
inteiro = 3
real = 3.2
cadeia = "abcd"
print (inteiro, " ", real, " ", cadeia)
```

Uma atribuição pode mudar o tipo da variável

```python
real = cadeia
print(real)
```

Uma das coisas mais originais do Python é que a identação do código é a forma de expecificar um bloco.
Por exemplo na instrução `if`, o código a executar no caso da condição ser verdadeira deve estar identado:

```python
x, y = 5, 2
if x > 2:
    print (x, ">", y)
else:
    print (x, "<", y)
```

### Tipos de dados

O Pyhthon tem 6 tipos de dados básicos: inteiros, números de vírgula flutuante, cadeias de carateres, listas, tuplos e dicionários.
Os 3 primeiros são semelhantes a outras linguagens de programação mas os restantes necessitam de uma explicação adicional


#### Listas

As listas são semelhantes aos vetores de outras linguagem mas em que cada elemento pode ter um tipo diferente.
O Python permite por exemplo:

```python
lista = [1, 2.1, "abcd"]
print(lista[0])
```

O primeiro elemento de uma lista tem o índice `0`. Pode-se obter o comprimento de uma lista com a função `len()`. Para imprimir o último elemento da lista pode-se fazer:

```python
print(lista[len(lista)-1])
```

ou mais facilmente:

```python
print(lista [-1])
```

#### Tuplos

Um tuplo é usado para guardar vários objetos numa única variável. A diferença entre uma lista e um tuplo é o os elementos da primeira podem ser alterados enquanto um tuplo é imutável, ou seja, tem de se mudar todos os seus elementos.

```python
lista = [0.5, 0.7, 0.9]
tuplo = (0.5, 0.7, 0.9)
print(lista, tuplo)
lista[0] = 0.1
try:
    tuplo[0] = 0.1
except TypeError:
    print("Erro: um tuplo é imutável")
print(lista, tuplo)
```

#### Dicionários

Um dicionário é uma lista em que cada elemento é indexado por uma chave.

```python
nomes_alunos = {"João": 5, "Maria": 3}
nomes_alunos["Pedro"] = 2
print(nomes_alunos["Pedro"])
print(nomes_alunos.keys())
print(nomes_alunos.items())
```

### Objetos em Python

Em Python tudo é um objeto, ou seja, uma instância de uma classe que tem associada um conjunto de comportamentos oferecido pela classe.

Estes comportamentos assumem a forma de propriedades (atributos do objeto) e métodos (funções que atuam sobre o objeto).

Por exemplo, podemos criar uma variável `z` que é uma instância da classe dos números complexos e que tem associado as propriedades `real` e `imag` e o método `conjugate()`:

```python
z = 1 + 2j
print(z)
print(type(z))
print("Re(z)=", z.real, " Im(z)=",z.imag)
print(z.conjugate())
```

### Cadeias de carateres e listas

As listas e as cadeias de carateres são dois objetos relacionados e que têm alguns métodos comuns:


```python
lista = [1, 2, 3, 4, 5]
cadeia = "Era uma vez um gato"
print(lista[2:5], cadeia[2:5])
print(lista.count(3), cadeia.count("a"))
print(len(lista), len(cadeia))
print(lista + [6], cadeia + ".")
```

Há no entanto métodos específicos para [cadeias de carateres](https://www.w3schools.com/python/python_ref_string.asp) e para [listas](https://www.w3schools.com/python/python_ref_list.asp).
Alguns exemplos:

```python
palavras = cadeia.split()
print(palavras)
palavras.append("maltês")
print(palavras)
palavras.sort()
print(palavras)
```

### Ciclos em Python

Os ciclos são construídos com a instrução `for a in b` em que `a` é uma variável e `b` é uma lista. Por exemplo:

```python
sinal = [10, 11, 12]
for n in [0, 1, 2]:
    print(sinal[n])
```

É mais elegante iterar sobre a própria lista

```python
sinal = [10, 11, 12]
for amostra in sinal:
    print(amostra)
```

A função `range()` gera um objeto para iterar

```python
sinal = [10, 11, 12]
for n in range(3):
    print(sinal[n])
```

Os ciclos podem também ser usados para gerar uma lista

```python
lista_inteiros = [5, 6, 7, 8]
lista_carateres = [str(i) for i in lista_inteiros]
print(lista_carateres)
```

### Funções

As funções são definidas com a instrução `def nome(argumentos):` seguida de um bloco identado com o código da função terminado com
a instrução `return ...`.

Por exemplo:

```python
def soma_5(lista_entrada):
    lista_saida = [i+5 for i in lista_entrada]
    return lista_saida

print(soma_5([10, 11, 12]))
```

Se a função tiver mais de um argumento, estes separam-se com vírgulas.
Podem também ser atribuídos valores por omissão aos argumentos se estes não forem definidos quando a função é chamada.

É boa prática indicar na definição da função a classe de objetos que aceita à entrada e a que resulta da sua execução.

```python
def soma_val(lista_entrada: list, val: int = 1) -> list:
    lista_saida = [i+val for i in lista_entrada]
    return lista_saida

print(soma_val([10, 11, 12]))
print(soma_val([10, 11, 12],3))
```

### Importação de bibliotecas

As funcionalidades do Python podem ser extendidas através da importação de bibliotecas. Por exemplo, a biblioteca NumPy permite operar com matrizes multidimensionais chamadas de `ndarrays`.
Por exemplo:

```python
import numpy

a = numpy.array([10, 11, 12])
print(type(a))
print(a)
```

Pode-se também definir um nome abreviado para chamar as funções do pacote:

```python
import numpy as np

a = np.array([10, 11, 12])
print(type(a))
print(a)
```

Há bibliotacas que são instalados em conjunto com o Python no computador, mas há outras que necessitam de ser instaladas antes da sua importação num programa. 
Por exemplo, se a biblioteca SymPy não estiver instalada é preciso primeiro fazer:
```
!pip install sympy
```
Se a biblioteca já estiver instalada, não há alteração.

```python
!pip install sympy
```

```python
import sympy as sp
```

A forma de utilizar estas bibliotecas será feita em notebooks separados.

```python

```
