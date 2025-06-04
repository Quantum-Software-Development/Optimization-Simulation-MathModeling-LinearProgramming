```markdown
# Detailed Solution of the Problem Using the Two-Phase Simplex Method

## Original Problem

**Minimize:**

$$
Z = x_1 + x_2 + x_3
$$

**Subject to:**

$$
\begin{cases}
2x_1 + x_2 - x_3 \leq 10 \\
x_1 + x_2 + 2x_3 \geq 20 \\
2x_1 + x_2 + 3x_3 = 60 \\
x_1, x_2, x_3 \geq 0
\end{cases}
$$

<br>

## Phase I: Elimination of Artificial Variables

### Step 1: Convert inequalities to equalities

- For the $\leq$ constraint, add slack variable $s_1 \geq 0$:

$$
2x_1 + x_2 - x_3 + s_1 = 10
$$
- For the $\geq$ constraint, subtract excess variable $s_2 \geq 0$ and add artificial variable $a_1 \geq 0$:

$$
x_1 + x_2 + 2x_3 - s_2 + a_1 = 20
$$
- For the equality constraint, add artificial variable $a_2 \geq 0$:

$$
2x_1 + x_2 + 3x_3 + a_2 = 60
$$


### Step 2: Auxiliary objective function for Phase I

$$
\min W = a_1 + a_2
$$

<br>

### Initial Tableau

| **Base** | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | $a_1$ | $a_2$ | **RHS** |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| $\mathbf{s_1}$ | 2 | 1 | -1 | 1 | 0 | 0 | 0 | 10 |
| $\mathbf{a_1}$ | 1 | 1 | 2 | 0 | -1 | 1 | 0 | 20 |
| $\mathbf{a_2}$ | 2 | 1 | 3 | 0 | 0 | 0 | 1 | 60 |
| $\mathbf{W}$ | -3 | -2 | -5 | 0 | 1 | 0 | 0 | 80 |

*Note: The $W$ row is obtained by substituting $a_1$ and $a_2$ from the constraints.*

<br>

### Step 3: Iteration 1 — Enter $x_3$, Leave $a_1$

- **Pivot element:** $2$ (row $a_1$, column $x_3$).
- **Row operations:** Divide row $a_1$ by $2$ and update other rows to zero out column $x_3$.

<br>

### Tableau after Iteration 1

| **Base** | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | $a_1$ | $a_2$ | **RHS** |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| $\mathbf{s_1}$ | 2.5 | 1.5 | 0 | 1 | -0.5 | 0.5 | 0 | 20 |
| $\mathbf{x_3}$ | 0.5 | 0.5 | 1 | 0 | -0.5 | 0.5 | 0 | 10 |
| $\mathbf{a_2}$ | 0.5 | -0.5 | 0 | 0 | 1.5 | -1.5 | 1 | 30 |
| $\mathbf{W}$ | -0.5 | 0.5 | 0 | 0 | -1.5 | 2.5 | 0 | 130 |


<br>

### Step 4: Iteration 2 — Enter $s_2$, Leave $a_2$

- **Pivot element:** $1.5$ (row $a_2$, column $s_2$).
- **Row operations:** Divide row $a_2$ by $1.5$ and update other rows to zero out column $s_2$.

<br>

### Tableau after Iteration 2

| **Base** | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | $a_1$ | $a_2$ | **RHS** |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| $\mathbf{s_1}$ | 8/3 | 4/3 | 0 | 1 | 0 | 0 | 1/3 | 30 |
| $\mathbf{x_3}$ | 2/3 | 1/3 | 1 | 0 | 0 | 0 | 1/3 | 20 |
| $\mathbf{s_2}$ | 1/3 | -1/3 | 0 | 0 | 1 | -1 | 2/3 | 20 |
| $\mathbf{W}$ | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 |


<br>

### ⚠️ **Attention: If Phase I ends with $W \neq 0$**

If at the end of Phase I the auxiliary objective function $W$ **is not zero**, i.e., $W > 0$, this indicates that **there is no feasible solution to the original problem**.

This happens because artificial variables could not be removed from the basis, signaling inconsistency in the original constraints.

In this case, the Two-Phase Simplex method **stops and reports the problem as infeasible**.

<br>

## Phase II: Optimization of the Original Objective Function

### Initial Tableau Phase II

| **Base** | $x_1$ | $x_2$ | $x_3$ | $s_1$ | $s_2$ | **RHS** |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| $\mathbf{s_1}$ | 8/3 | 4/3 | 0 | 1 | 0 | 30 |
| $\mathbf{x_3}$ | 2/3 | 1/3 | 1 | 0 | 0 | 20 |
| $\mathbf{s_2}$ | 1/3 | -1/3 | 0 | 0 | 1 | 20 |


<br>

### Step 5: Write the original objective function in terms of the variables

$$
x_3 = 20 - \frac{2}{3}x_1 - \frac{1}{3}x_2
$$

$$
Z = x_1 + x_2 + x_3 = x_1 + x_2 + 20 - \frac{2}{3}x_1 - \frac{1}{3}x_2 = 20 + \frac{1}{3}x_1 + \frac{2}{3}x_2
$$

---

### Step 6: Optimality Check

The coefficients of $Z$ for the non-basic variables $x_1$ and $x_2$ are positive $\left(\frac{1}{3}\right.$ and $\left.\frac{2}{3}\right)$, indicating the current solution is optimal.

---

## Optimal Solution

$$
\boxed{
(x_1, x_2, x_3) = (0, 0, 20) \quad \text{with} \quad Z_{\min} = 20
}
$$

<br>

## Constraint Verification

$$
\begin{cases}
2(0) + 0 - 20 = -20 \leq 10 \quad \checkmark \\
0 + 0 + 2(20) = 40 \geq 20 \quad \checkmark \\
2(0) + 0 + 3(20) = 60 = 60 \quad \checkmark
\end{cases}
$$

<br>

# **Summary**

- The Two-Phase Simplex method was applied correctly.
- Phase I eliminated artificial variables with $W = 0$, indicating the problem is **feasible**.
- Phase II optimized the original objective function, finding the optimal solution.
- If $W \neq 0$ at the end of Phase I, the problem would be **infeasible** (no feasible solution).
````

