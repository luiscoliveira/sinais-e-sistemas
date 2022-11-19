---
title: "transformação linear da variável independente"
---

Para as transformações da variável independente na forma:
$$
\forall n \in \mathbb{Z},\; y(n) = x (an - n_0)
$$
Em que $a$ e $n_0$ são constantes.

**Passo 1**: Começar pelo deslocamento temporal:
$$x_1(n) = x(n - n_0)$$
- $n_0 > 0$ - deslocamento para a direita
- $n_0<0$ - deslocamento para a esquerda

**Passo 2**: No caso de $a<0$ fazemos a inversão temporal:
$$x_2(n) = x_1(-n) = x(-n-n_0)$$
**Passo 3**: Finalmente faz-se o escalamento temporal:
$$y(n) = x_2(|a| n) = x(an - n_0)$$
- $|a|>1$ - compressão temporal
- $|a|<1$ - expansão temporal

