
```markdown
# 🚚 Resolução do Problema de Transporte — Método do Custo Mínimo

## 📋 Enunciado

Considere a rede de transporte dada pela tabela abaixo e determine o custo ótimo de transporte, iniciando a resolução com o Método do Custo Mínimo.

---

## 🧩 Dados do Problema

### Suprimentos (Ofertas)

| Fonte | Suprimento |
|-------|------------|
| F1    |    100     |
| F2    |    800     |
| F3    |    150     |
| F4    |    400     |

### Demandas

| Mercado | Demanda |
|---------|---------|
| M1      |   700   |
| M2      |   250   |
| M3      |   500   |

### Custos de Transporte

|        | M1 | M2 | M3 |
|--------|----|----|----|
| **F1** |  5 |  2 |  8 |
| **F2** |  6 |  3 |  7 |
| **F3** |  4 |  3 |  6 |
| **F4** |  8 |  6 |  4 |

---

## 📝 Passo 1: Verificação de Balanceamento

- Oferta total: \(100 + 800 + 150 + 400 = 1450\)
- Demanda total: \(700 + 250 + 500 = 1450\)

**Como oferta = demanda, o problema já está balanceado.**

---

## 📝 Passo 2: Método do Custo Mínimo

A cada passo, selecionamos a célula de menor custo disponível e alocamos o máximo possível, atualizando as ofertas e demandas.

---

### 🔢 Iteração 1

- **Menor custo:** 2 (F1 → M2)
- Oferta F1: 100 | Demanda M2: 250
- **Alocação:** \(x_{12} = 100\)

Tabela após alocação:

|        | M1 | M2 | M3 | Oferta Restante |
|--------|----|----|----|-----------------|
| **F1** |    | 100|    |      0          |
| **F2** |    |    |    |     800         |
| **F3** |    |    |    |     150         |
| **F4** |    |    |    |     400         |
| **Demanda Restante** | 700 | 150 | 500 |   |

---

### 🔢 Iteração 2

- **Próximo menor custo:** 3 (F2 → M2)
- Oferta F2: 800 | Demanda M2: 150
- **Alocação:** \(x_{22} = 150\)

Tabela após alocação:

|        | M1 | M2 | M3 | Oferta Restante |
|--------|----|----|----|-----------------|
| **F1** |    | 100|    |      0          |
| **F2** |    | 150|    |     650         |
| **F3** |    |    |    |     150         |
| **F4** |    |    |    |     400         |
| **Demanda Restante** | 700 | 0 | 500 |   |

---

### 🔢 Iteração 3

- **Próximo menor custo:** 4 (F3 → M1)
- Oferta F3: 150 | Demanda M1: 700
- **Alocação:** \(x_{31} = 150\)

Tabela após alocação:

|        | M1 | M2 | M3 | Oferta Restante |
|--------|----|----|----|-----------------|
| **F1** |    | 100|    |      0          |
| **F2** |    | 150|    |     650         |
| **F3** | 150|    |    |      0          |
| **F4** |    |    |    |     400         |
| **Demanda Restante** | 550 | 0 | 500 |   |

---

### 🔢 Iteração 4

- **Próximo menor custo:** 4 (F4 → M3)
- Oferta F4: 400 | Demanda M3: 500
- **Alocação:** \(x_{43} = 400\)

Tabela após alocação:

|        | M1 | M2 | M3 | Oferta Restante |
|--------|----|----|----|-----------------|
| **F1** |    | 100|    |      0          |
| **F2** |    | 150|    |     650         |
| **F3** | 150|    |    |      0          |
| **F4** |    |    | 400|      0          |
| **Demanda Restante** | 550 | 0 | 100 |   |

---

### 🔢 Iteração 5

- **Próximo menor custo:** 6 (F2 → M1)
- Oferta F2: 650 | Demanda M1: 550
- **Alocação:** \(x_{21} = 550\)

Tabela após alocação:

|        | M1 | M2 | M3 | Oferta Restante |
|--------|----|----|----|-----------------|
| **F1** |    | 100|    |      0          |
| **F2** | 550| 150|    |     100         |
| **F3** | 150|    |    |      0          |
| **F4** |    |    | 400|      0          |
| **Demanda Restante** | 0 | 0 | 100 |   |

---

### 🔢 Iteração 6

- **Próximo menor custo:** 7 (F2 → M3)
- Oferta F2: 100 | Demanda M3: 100
- **Alocação:** \(x_{23} = 100\)

Tabela final:

|        | M1 | M2 | M3 | Oferta Restante |
|--------|----|----|----|-----------------|
| **F1** |    | 100|    |      0          |
| **F2** | 550| 150| 100|      0          |
| **F3** | 150|    |    |      0          |
| **F4** |    |    | 400|      0          |
| **Demanda Restante** | 0 | 0 | 0 |   |

---

## 📊 Tabela Final de Alocação

|        | M1  | M2  | M3  | Suprimento |
|--------|-----|-----|-----|------------|
| **F1** |  -  | 100 |  -  |    100     |
| **F2** | 550 | 150 | 100 |    800     |
| **F3** | 150 |  -  |  -  |    150     |
| **F4** |  -  |  -  | 400 |    400     |
| **Demanda** | 700 | 250 | 500 |        |

---

## 🧮 Cálculo do Custo Total

\[
\begin{align*}
Z &= (100 \times 2) + (150 \times 3) + (550 \times 6) + (100 \times 7) + (150 \times 4) + (400 \times 4) \\
  &= 200 + 450 + 3300 + 700 + 600 + 1600 \\
  &= \boxed{6850}
\end{align*}
\]

---

## ✅ Resposta Final

O custo mínimo de transporte, utilizando o Método do Custo Mínimo, é:

\[
\boxed{Z = 6850}
\]

---

## 🖋️ Observação

O Método do Custo Mínimo fornece uma solução inicial viável, mas não necessariamente ótima.  
Para garantir a otimalidade, recomenda-se aplicar métodos como:
- **Método de MODI (Método de Distribuição Modificada)**
- **Stepping Stone (Caminho Fechado)**
```

