
## Apply Electrical Lows
1.From incidence matrix (A) we can apply KCL.

$$
A =
\begin{bmatrix}
-1 &  1 &  0 & -1 &  0 &  0 \\
0 & -1 &  1 &  0 &  1 &  0 \\
1 &  0 & -1 &  0 &  0 &  1
\end{bmatrix}
$$

Let the branch-current vector be
$$
\mathbf{j}_B =
\begin{bmatrix} j_a \ j_b \ j_c \ j_d \ j_e \ j_f \end{bmatrix}.
$$


### Kirchhoff’s Current Law (KCL) in matrix form

If rows of (A) correspond to nodes, KCL is written as

$$
A \cdot \mathbf{j}_B = \mathbf{0}
$$

Multiplying gives the node equations (one row per node):

$$
\begin{bmatrix}
-1 &  1 &  0 & -1 &  0 &  0 \\
0 & -1 &  1 &  0 &  1 &  0 \\
1 &  0 & -1 &  0 &  0 &  1
\end{bmatrix}
\begin{bmatrix}
j_a \\
j_b \\
j_c \\
j_d \\
j_e \\
j_f
\end{bmatrix}
=
\begin{bmatrix}
0 \\
0 \\
0
\end{bmatrix}
$$

which expands to the three scalar KCL equations:

1. Node 1: $$-j_a + j_b - j_d = 0$$
2. Node 2: $$-j_b + j_c + j_e = 0$$
3. Node 3: $$j_a - j_c - j_f = 0$$


#### Interpretation

* Each equation is the algebraic sum of currents (with signs per the incidence matrix convention) at that node \(= 0\).
* Example: Node 1 says currents leaving minus currents entering (per your chosen signs) sum to zero \( \rightarrow -j_a + j_b - j_d = 0 \).
* The vector you multiply must be \( [j_a, j_b, j_c, j_d, j_e, j_f]^T \) (not repeated entries).


Nice — I'll clean that up and write it precisely and compactly, matching the style you've been using.

---

### KVL from the Tie-Set (Loop) Matrix (B)

Let (B) be the loop (tie-set) matrix (rows = loops, columns = branches).
For branch-voltage vector (\mathbf{v}_B) (columns ordered as (a,b,c,d,e,f)), **KVL** for every fundamental loop is:

$$
B\,\mathbf{v}_B = \mathbf{0}.
$$

Using the earlier example
$$
B=
\begin{bmatrix}
-1 & 0 & -1 & 1 & 0 & 0 \\
1 & 1 &  0 & 0 & 1 & 0 \\
0 & -1 &  1 & 0 & 0 & 1
\end{bmatrix},
$$
the three KVL scalar equations (one per row) are
$$
\begin{aligned}
\text{Loop 1:}&\quad -v_a - v_c + v_d = 0 \\
\text{Loop 2:}&\quad v_a + v_b + v_e = 0 \\
\text{Loop 3:}&\quad -v_b + v_c + v_f = 0
\end{aligned}
$$

### Write KVL in loop-current form (useful for solving)

Express branch currents in terms of loop currents using

$$
\mathbf{i}_B = B^{T}\mathbf{i}_L
$$

where $\mathbf{i}_L$ is the vector of loop currents $[I_1, I_2, I_3]^T$.


Perfect 👍 Here's your statement rewritten clearly and formatted in proper engineering/matrix notation:

---

### Expressing Branch Currents in Terms of Loop Currents

We can express the **branch currents** in terms of the **loop currents** using the **transpose of the tie-set matrix**:

$$
\boxed{
\mathbf{J}_B = B^{T} \mathbf{I}_L
}
$$

Where:

* $\mathbf{J}_B$ → vector of **branch currents**
* $B^{T}$ → **transpose of the tie-set (loop incidence) matrix**
* $\mathbf{I}_L$ → vector of **loop currents**

## Relation between Network Topology Matrices
$$
C_L = -B_T^t
$$

$$
C_L = (A_T)^{-1} \cdot A_L
$$

$$
C = (A_T)^{-1} \cdot A
$$

