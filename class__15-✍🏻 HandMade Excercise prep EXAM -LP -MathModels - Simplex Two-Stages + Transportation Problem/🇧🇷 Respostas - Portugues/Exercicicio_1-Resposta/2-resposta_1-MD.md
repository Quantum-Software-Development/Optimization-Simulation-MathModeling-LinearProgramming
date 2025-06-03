
```markdown
# Resolução Detalhada do Problema pelo Método Simplex de Duas Fases

## Problema Original

**Minimizar:**

$$
Z = x_1 + x_2 + x_3
$$

**Sujeito a:**

$$
\begin{cases}
2x_1 + x_2 - x_3 \leq 10 \\
x_1 + x_2 + 2x_3 \geq 20 \\
2x_1 + x_2 + 3x_3 = 60 \\
x_1, x_2, x_3 \geq 0
\end{cases}
$$

<br>

## Fase I: Eliminação das Variáveis Artificiais

### Passo 1: Transformar as desigualdades em igualdades

- Para a restrição $\leq$, adiciona-se variável de folga $s_1 \geq 0$:

$$
2x_1 + x_2 - x_3 + s_1 = 10
$$

- Para a restrição $\geq$, subtrai-se variável de excesso $e_1 \geq 0$ e adiciona-se variável artificial $a_1 \geq 0$:

$$
x_1 + x_2 + 2x_3 - e_1 + a_1 = 20
$$

- Para a restrição de igualdade, adiciona-se variável artificial $a_2 \geq 0$:

$$
2x_1 + x_2 + 3x_3 + a_2 = 60
$$

### Passo 2: Função objetivo auxiliar para a Fase I

$$
\min W = a_1 + a_2
$$

<br>

### Passo 3: Tableau inicial da Fase I

$$
\begin{array}{c|ccccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & a_1 & a_2 & \text{RHS} \\
\hline
s_1 & 2 & 1 & -1 & 1 & 0 & 0 & 0 & 10 \\
a_1 & 1 & 1 & 2 & 0 & -1 & 1 & 0 & 20 \\
a_2 & 2 & 1 & 3 & 0 & 0 & 0 & 1 & 60 \\
\hline
W & -3 & -2 & -5 & 0 & 1 & 0 & 0 & 80 \\
\end{array}
$$

*Obs.: A linha $W$ foi obtida substituindo $a_1$ e $a_2$ pelas suas expressões nas restrições.*

<br>

### Passo 4: Iteração 1 — Entrar $x_3$, sair $a_1$

- O pivô é o elemento 2 na linha $a_1$, coluna $x_3$.
- Dividimos a linha $a_1$ por 2 para tornar o pivô 1:

$$
\frac{1}{2} \times [1 \quad 1 \quad 2 \quad 0 \quad -1 \quad 1 \quad 0 \quad 20] = [0.5 \quad 0.5 \quad 1 \quad 0 \quad -0.5 \quad 0.5 \quad 0 \quad 10]
$$

- Atualizamos as outras linhas para zerar a coluna $x_3$:

$$
\begin{cases}
L_{s_1} = L_{s_1} + 1 \times L_{x_3} \\
L_{a_2} = L_{a_2} - 3 \times L_{x_3} \\
L_W = L_W + 5 \times L_{x_3}
\end{cases}
$$

**Tableau após a 1ª iteração:**

$$
\begin{array}{c|ccccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & a_1 & a_2 & \text{RHS} \\
\hline
s_1 & 2.5 & 1.5 & 0 & 1 & -0.5 & 0.5 & 0 & 20 \\
x_3 & 0.5 & 0.5 & 1 & 0 & -0.5 & 0.5 & 0 & 10 \\
a_2 & 0.5 & -0.5 & 0 & 0 & 1.5 & -1.5 & 1 & 30 \\
\hline
W & -0.5 & 0.5 & 0 & 0 & -1.5 & 2.5 & 0 & 130 \\
\end{array}
$$

<br>

### Passo 5: Iteração 2 — Entrar $e_1$, sair $a_2$

- Pivô: 1.5 na linha $a_2$, coluna $e_1$.
- Dividimos a linha $a_2$ por 1.5:

$$
\frac{1}{1.5} \times [0.5 \quad -0.5 \quad 0 \quad 0 \quad 1.5 \quad -1.5 \quad 1 \quad 30] = \left[\frac{1}{3} \quad -\frac{1}{3} \quad 0 \quad 0 \quad 1 \quad -1 \quad \frac{2}{3} \quad 20\right]
$$

- Atualizamos as outras linhas para zerar a coluna $e_1$:

$$
\begin{cases}
L_{s_1} = L_{s_1} + 0.5 \times L_{e_1} \\
L_{x_3} = L_{x_3} + 0.5 \times L_{e_1} \\
L_W = L_W + 1.5 \times L_{e_1}
\end{cases}
$$

**Tableau após a 2ª iteração:**

$$
\begin{array}{c|ccccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & a_1 & a_2 & \text{RHS} \\
\hline
s_1 & \frac{8}{3} & \frac{4}{3} & 0 & 1 & 0 & 0 & \frac{1}{3} & 30 \\
x_3 & \frac{2}{3} & \frac{1}{3} & 1 & 0 & 0 & 0 & \frac{1}{3} & 20 \\
e_1 & \frac{1}{3} & -\frac{1}{3} & 0 & 0 & 1 & -1 & \frac{2}{3} & 20 \\
\hline
W & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 \\
\end{array}
$$

<br>

### ⚠️ **Atenção: Caso a Fase I termine com $W \neq 0$**

Se no final da Fase I a função objetivo auxiliar $W$ **não for zero**, isto é, $W > 0$, isso indica que **não existe solução factível para o problema original**.

Isso ocorre porque as variáveis artificiais não puderam ser eliminadas da base, indicando inconsistência nas restrições originais.

Nesse caso, o método Simplex de Duas Fases **encerra a resolução e informa que o problema é inviável**.

<br>

## Fase II: Otimização da Função Objetivo Original

### Passo 6: Tableau Inicial da Fase II

Removendo as variáveis artificiais $a_1$ e $a_2$, temos:

$$
\begin{array}{c|ccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & \text{RHS} \\
\hline
s_1 & \frac{8}{3} & \frac{4}{3} & 0 & 1 & 0 & 30 \\
x_3 & \frac{2}{3} & \frac{1}{3} & 1 & 0 & 0 & 20 \\
e_1 & \frac{1}{3} & -\frac{1}{3} & 0 & 0 & 1 & 20 \\
\end{array}
$$

### Passo 7: Função objetivo original em termos das variáveis básicas

Sabemos que:

$$
x_3 = 20 - \frac{2}{3}x_1 - \frac{1}{3}x_2
$$

Logo,

$$
Z = x_1 + x_2 + x_3 = x_1 + x_2 + 20 - \frac{2}{3}x_1 - \frac{1}{3}x_2 = 20 + \frac{1}{3}x_1 + \frac{2}{3}x_2
$$

<br>
### Passo 8: Verificação de Otimalidade

Os coeficientes da função objetivo $Z$ para as variáveis não básicas $x_1$ e $x_2$ são positivos $\left(\frac{1}{3}\right.$ e $\left.\frac{2}{3}\right)$, indicando que a solução atual é ótima.

<br>
## Solução Ótima

$$
\boxed{
(x_1, x_2, x_3) = (0, 0, 20) \quad \text{com} \quad Z_{\min} = 20
}
$$

<br>

## Verificação das Restrições

$$
\begin{cases}
2(0) + 0 - 20 = -20 \leq 10 \quad \checkmark \\
0 + 0 + 2(20) = 40 \geq 20 \quad \checkmark \\
2(0) + 0 + 3(20) = 60 = 60 \quad \checkmark
\end{cases}
$$

---<br>
# **Resumo**

- O método Simplex de Duas Fases foi aplicado corretamente.
- A Fase I eliminou as variáveis artificiais com $W = 0$, indicando que o problema é **factível**.
- A Fase II otimizou a função objetivo original, encontrando a solução ótima.
- Caso $W \neq 0$ no final da Fase I, o problema seria **inviável** (sem solução factível).

```

```markdown
# Resolução Detalhada do Problema pelo Método Simplex de Duas Fases

## Problema Original

**Minimizar:**  
$$
Z = x_1 + x_2 + x_3
$$

**Sujeito a:**  
$$
\begin{cases}
2x_1 + x_2 - x_3 \leq 10 \\
x_1 + x_2 + 2x_3 \geq 20 \\
2x_1 + x_2 + 3x_3 = 60 \\
x_1, x_2, x_3 \geq 0
\end{cases}
$$

<br>

## Fase I: Eliminação das Variáveis Artificiais

### Passo 1: Transformar as desigualdades em igualdades

- Para a restrição $\leq$, adiciona-se variável de folga $s_1 \geq 0$:
$$
2x_1 + x_2 - x_3 + s_1 = 10
$$

- Para a restrição $\geq$, subtrai-se variável de excesso $e_1 \geq 0$ e adiciona-se variável artificial $a_1 \geq 0$:
$$
x_1 + x_2 + 2x_3 - e_1 + a_1 = 20
$$

- Para a restrição de igualdade, adiciona-se variável artificial $a_2 \geq 0$:
$$
2x_1 + x_2 + 3x_3 + a_2 = 60
$$

### Passo 2: Função objetivo auxiliar para a Fase I

$$
\min W = a_1 + a_2
$$

<br>

### Passo 3: Tableau inicial da Fase I

$$
\begin{array}{c|ccccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & a_1 & a_2 & \text{RHS} \\
\hline
s_1 & 2 & 1 & -1 & 1 & 0 & 0 & 0 & 10 \\
a_1 & 1 & 1 & 2 & 0 & -1 & 1 & 0 & 20 \\
a_2 & 2 & 1 & 3 & 0 & 0 & 0 & 1 & 60 \\
\hline
W & -3 & -2 & -5 & 0 & 1 & 0 & 0 & 80 \\
\end{array}
$$

*Obs.: A linha $W$ foi obtida substituindo $a_1$ e $a_2$ pelas suas expressões nas restrições.*

<br>

### Passo 4: Iteração 1 — Entrar $x_3$, sair $a_1$

- O pivô é o elemento 2 na linha $a_1$, coluna $x_3$.

- Dividimos a linha $a_1$ por 2 para tornar o pivô 1:

$$
\frac{1}{2} \times [1 \quad 1 \quad 2 \quad 0 \quad -1 \quad 1 \quad 0 \quad 20] = [0.5 \quad 0.5 \quad 1 \quad 0 \quad -0.5 \quad 0.5 \quad 0 \quad 10]
$$

- Atualizamos as outras linhas para zerar a coluna $x_3$:

$$
\begin{cases}
L_{s_1} = L_{s_1} + 1 \times L_{x_3} \\
L_{a_2} = L_{a_2} - 3 \times L_{x_3} \\
L_W = L_W + 5 \times L_{x_3}
\end{cases}
$$

**Tableau após a 1ª iteração:**

$$
\begin{array}{c|ccccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & a_1 & a_2 & \text{RHS} \\
\hline
s_1 & 2.5 & 1.5 & 0 & 1 & -0.5 & 0.5 & 0 & 20 \\
x_3 & 0.5 & 0.5 & 1 & 0 & -0.5 & 0.5 & 0 & 10 \\
a_2 & 0.5 & -0.5 & 0 & 0 & 1.5 & -1.5 & 1 & 30 \\
\hline
W & -0.5 & 0.5 & 0 & 0 & -1.5 & 2.5 & 0 & 130 \\
\end{array}
$$

<br>

### Passo 5: Iteração 2 — Entrar $e_1$, sair $a_2$

- Pivô: 1.5 na linha $a_2$, coluna $e_1$.

- Dividimos a linha $a_2$ por 1.5:

$$
\frac{1}{1.5} \times [0.5 \quad -0.5 \quad 0 \quad 0 \quad 1.5 \quad -1.5 \quad 1 \quad 30] = \left[\frac{1}{3} \quad -\frac{1}{3} \quad 0 \quad 0 \quad 1 \quad -1 \quad \frac{2}{3} \quad 20\right]
$$

- Atualizamos as outras linhas para zerar a coluna $e_1$:

$$
\begin{cases}
L_{s_1} = L_{s_1} + 0.5 \times L_{e_1} \\
L_{x_3} = L_{x_3} + 0.5 \times L_{e_1} \\
L_W = L_W + 1.5 \times L_{e_1}
\end{cases}
$$

**Tableau após a 2ª iteração:**

$$
\begin{array}{c|ccccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & a_1 & a_2 & \text{RHS} \\
\hline
s_1 & \frac{8}{3} & \frac{4}{3} & 0 & 1 & 0 & 0 & \frac{1}{3} & 30 \\
x_3 & \frac{2}{3} & \frac{1}{3} & 1 & 0 & 0 & 0 & \frac{1}{3} & 20 \\
e_1 & \frac{1}{3} & -\frac{1}{3} & 0 & 0 & 1 & -1 & \frac{2}{3} & 20 \\
\hline
W & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 \\
\end{array}

<br>

### ⚠️ **Atenção: Caso a Fase I termine com $ W \neq 0 $**

Se no final da Fase I a função objetivo auxiliar $ W $ **não for zero**, isto é, $ W > 0 $, isso indica que **não existe solução factível para o problema original**.  

Isso ocorre porque as variáveis artificiais não puderam ser eliminadas da base, indicando inconsistência nas restrições originais.

Nesse caso, o método Simplex de Duas Fases **encerra a resolução e informa que o problema é inviável**.

<br>

## Fase II: Otimização da Função Objetivo Original

### Passo 6: Tableau Inicial da Fase II

Removendo as variáveis artificiais $a_1$ e $a_2$, temos:

$$
\begin{array}{c|ccccc|c}
\text{Base} & x_1 & x_2 & x_3 & s_1 & e_1 & \text{RHS} \\
\hline
s_1 & \frac{8}{3} & \frac{4}{3} & 0 & 1 & 0 & 30 \\
x_3 & \frac{2}{3} & \frac{1}{3} & 1 & 0 & 0 & 20 \\
e_1 & \frac{1}{3} & -\frac{1}{3} & 0 & 0 & 1 & 20 \\
\end{array}
$$

### Passo 7: Função objetivo original em termos das variáveis básicas

Sabemos que:

$$
x_3 = 20 - \frac{2}{3}x_1 - \frac{1}{3}x_2
$$

Logo,

$$
Z = x_1 + x_2 + x_3 = x_1 + x_2 + 20 - \frac{2}{3}x_1 - \frac{1}{3}x_2 = 20 + \frac{1}{3}x_1 + \frac{2}{3}x_2
$$

<br>

### Passo 8: Verificação de Otimalidade

Os coeficientes da função objetivo $Z$ para as variáveis não básicas $x_1$ e $x_2$ são positivos $\left(\frac{1}{3}\right.$ e $\left.\frac{2}{3}\right)$, indicando que a solução atual é ótima.

<br>

## Solução Ótima

$$
\boxed{
(x_1, x_2, x_3) = (0, 0, 20) \quad \text{com} \quad Z_{\min} = 20
}
$$

<br>

## Verificação das Restrições

$$
\begin{cases}
2(0) + 0 - 20 = -20 \leq 10 \quad \checkmark \\
0 + 0 + 2(20) = 40 \geq 20 \quad \checkmark \\
2(0) + 0 + 3(20) = 60 = 60 \quad \checkmark
\end{cases}
$$

<br>

# **Resumo**

- O método Simplex de Duas Fases foi aplicado corretamente.
- A Fase I eliminou as variáveis artificiais com $ W = 0 $, indicando que o problema é **factível**.
- A Fase II otimizou a função objetivo original, encontrando a solução ótima.
- Caso $ W \neq 0 $ no final da Fase I, o problema seria **inviável** (sem solução factível).
```

