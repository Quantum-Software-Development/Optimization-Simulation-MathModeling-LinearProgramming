
```markdown
# 🚚 Transportation Problem Solution — Minimum Cost Method

## 📋 Problem Statement

Consider the transportation network given by the table below and determine the optimal transportation cost, starting the resolution using the Minimum Cost Method.

---

## 🧩 Problem Data

### Supplies (Sources)

| Source | Supply |
|--------|--------|
| S1     |  100   |
| S2     |  800   |
| S3     |  150   |
| S4     |  400   |

### Demands (Destinations)

| Market | Demand |
|--------|--------|
| M1     |  700   |
| M2     |  250   |
| M3     |  500   |

### Transportation Costs

|        | M1 | M2 | M3 |
|--------|----|----|----|
| **S1** |  5 |  2 |  8 |
| **S2** |  6 |  3 |  7 |
| **S3** |  4 |  3 |  6 |
| **S4** |  8 |  6 |  4 |

---

## 📝 Step 1: Check for Balance

- Total supply: \(100 + 800 + 150 + 400 = 1450\)
- Total demand: \(700 + 250 + 500 = 1450\)

**Since supply equals demand, the problem is balanced.**

---

## 📝 Step 2: Minimum Cost Method

At each step, select the cell with the lowest available cost and allocate the maximum possible amount, updating supplies and demands accordingly.

---

### 🔢 Iteration 1

- **Lowest cost:** 2 (S1 → M2)
- Supply S1: 100 | Demand M2: 250
- **Allocation:** \(x_{12} = 100\)

Table after allocation:

|        | M1 | M2 | M3 | Remaining Supply |
|--------|----|----|----|------------------|
| **S1** |    |100 |    |        0         |
| **S2** |    |    |    |       800        |
| **S3** |    |    |    |       150        |
| **S4** |    |    |    |       400        |
| **Remaining Demand** | 700 | 150 | 500 |          |

---

### 🔢 Iteration 2

- **Next lowest cost:** 3 (S2 → M2)
- Supply S2: 800 | Demand M2: 150
- **Allocation:** \(x_{22} = 150\)

Table after allocation:

|        | M1 | M2 | M3 | Remaining Supply |
|--------|----|----|----|------------------|
| **S1** |    |100 |    |        0         |
| **S2** |    |150 |    |       650        |
| **S3** |    |    |    |       150        |
| **S4** |    |    |    |       400        |
| **Remaining Demand** | 700 | 0 | 500 |            |

---

### 🔢 Iteration 3

- **Next lowest cost:** 4 (S3 → M1)
- Supply S3: 150 | Demand M1: 700
- **Allocation:** \(x_{31} = 150\)

Table after allocation:

|        | M1 | M2 | M3 | Remaining Supply |
|--------|----|----|----|------------------|
| **S1** |    |100 |    |        0         |
| **S2** |    |150 |    |       650        |
| **S3** |150 |    |    |        0         |
| **S4** |    |    |    |       400        |
| **Remaining Demand** | 550 | 0 | 500 |            |

---

### 🔢 Iteration 4

- **Next lowest cost:** 4 (S4 → M3)
- Supply S4: 400 | Demand M3: 500
- **Allocation:** \(x_{43} = 400\)

Table after allocation:

|        | M1 | M2 | M3 | Remaining Supply |
|--------|----|----|----|------------------|
| **S1** |    |100 |    |        0         |
| **S2** |    |150 |    |       650        |
| **S3** |150 |    |    |        0         |
| **S4** |    |    |400 |        0         |
| **Remaining Demand** | 550 | 0 | 100 |            |

---

### 🔢 Iteration 5

- **Next lowest cost:** 6 (S2 → M1)
- Supply S2: 650 | Demand M1: 550
- **Allocation:** \(x_{21} = 550\)

Table after allocation:

|        | M1 | M2 | M3 | Remaining Supply |
|--------|----|----|----|------------------|
| **S1** |    |100 |    |        0         |
| **S2** |550 |150 |    |       100        |
| **S3** |150 |    |    |        0         |
| **S4** |    |    |400 |        0         |
| **Remaining Demand** | 0 | 0 | 100 |              |

---

### 🔢 Iteration 6

- **Next lowest cost:** 7 (S2 → M3)
- Supply S2: 100 | Demand M3: 100
- **Allocation:** \(x_{23} = 100\)

Final table:

|        | M1  | M2  | M3  | Remaining Supply |
|--------|-----|-----|-----|------------------|
| **S1** |     | 100 |     |        0         |
| **S2** | 550 | 150 | 100 |        0         |
| **S3** | 150 |     |     |        0         |
| **S4** |     |     | 400 |        0         |
| **Remaining Demand** | 0 | 0 | 0 |                |

---

## 📊 Final Allocation Table

|        | M1  | M2  | M3  | Supply |
|--------|-----|-----|-----|--------|
| **S1** |  -  | 100 |  -  |  100   |
| **S2** | 550 | 150 | 100 |  800   |
| **S3** | 150 |  -  |  -  |  150   |
| **S4** |  -  |  -  | 400 |  400   |
| **Demand** | 700 | 250 | 500 |      |

---

## 🧮 Total Cost Calculation

\[
\begin{align*}
Z &= (100 \times 2) + (150 \times 3) + (550 \times 6) + (100 \times 7) + (150 \times 4) + (400 \times 4) \\
  &= 200 + 450 + 3300 + 700 + 600 + 1600 \\
  &= \boxed{6850}
\end{align*}
\]

---

## ✅ Final Answer

The minimum transportation cost, using the Minimum Cost Method, is:

\[
\boxed{Z = 6850}
\]

---

## 🖋️ Note

The Minimum Cost Method provides a feasible initial solution but does not guarantee optimality.  
To verify optimality, it is recommended to apply methods such as:
- **MODI Method (Modified Distribution Method)**
- **Stepping Stone Method**
```

