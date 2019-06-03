---
title: Notes on Linear Algebra
author: Napoleon
header-includes: |
  \usepackage{amsthm}
  \newtheorem{theorem}{Theorem}
---
# Basics of Vector spaces
Let matrix A be of dimension (m x n). We define the following fundamental subspaces of A:

**Column space $C(A)$ or range $R(A)$**  

The space spanned by the columns of the matrix.
$$ R(A) = \{y = Ax \mid x \in \mathbb{R}^n\} $$
Note that the span of a set of vectors equals the range of the matrix where they are as columns. I.e., let $Q = [q_1, q_2, ..., q_n]$. Then we have an equivalent definition for the range, namely
$$ R(Q) = span({q_1, ..., q_n}) := \{ z \in \mathbb{R}^n \mid \sum_{i = 1}^{n} a_i \cdot q_i \; for \; a_i \in \mathbb{R} \}. $$

**Nullspace $N(A)$**

$$ N(A) = \{x \in \mathbb{R}^n \mid Ax = 0 \} $$

**Row space and left nullspace $R(A^T), N(A^T)$**

With the same definitions as above but for the transposed matrix.

## Important theorems
**About dimensions:**   

  1. dim C(A) = dim $C(A^T) = rank$ (proved)
  2. dim C(A) + dim N(A) = n  (rank-nullity theorem, needs to be proved)

**About geometry:**  

  1. $C(A) \cup N(A^T) = \mathbb{R}^m$
  2. $C(A^T) \cup N(A) = \mathbb{R}^n$
  3. $C(A) \perp N(A^T)$ and $C(A^T) \perp N(A)$ (proved)

In essence, the part of geometry says that the pairs {C(A),  $N(A^T)$} and {$C(A^T)$, N(A)} are orthogonal complements.

**About solutions for Ax = b where A is (m x n):**  

  1. if r = n, solution always exists (r < n only if $b \in R(A)$)
  2. if r = m, solution is unique (r < m infinite amount of solutions)

**Others:**  

  1. The number of vectors in a basis of a vector space is always the same. (proved)

**Corollaries:**  

  1. Every vector can be divided into an element in the row space and one in the nullspace, i.e., $x = x_r + x_n \quad \forall x \in \mathbb{R}^n$. This follows from the fact that the two spaces span $\mathbb{R}^n$ and that they are orthogonal complements.
  2. The part from the row space is mapped to the column space.
  3. Dim N(A) = n - r, where r = rank. This follows straight from the equations.

![The four fundamental subspaces, Gilbert Strang](C:\Users\napol\OneDrive\Desktop\MyRepo\Pictures\fundamentalSubspaces.jpg)

## Definitions

**Linear independence (no extra vectors)**  

The vectors $q_1, q_2, ..., q_k$ are linearly independent if
$$ \sum_{i=1}^k x_i \cdot q_i = 0 \quad \implies \quad x_i = 0, $$
or equivalently for $Q = [q_1, ..., q_k]$ if
$$ Qx = 0 \quad \implies \quad x = 0. $$
Note that the other direction is trivial.  

An systematic way to check for independence is the fact that if r = n the columns are independent. Thus one can put the vectors in the column and do Gaussian elimination and see whether all columns become pivot columns. Example: if
$$ EA = \begin{bmatrix} 1 & 0 & -1 \\ 0 & 1 & -2 \\ 0 & 0 & 0 \end{bmatrix}, $$
Then the rank is two, and the third column vector equals $-1 \cdot c_1 -2 \cdot c_2$

**Spanning a space (enough vectors to produce the rest)**

**Basis for a space (not too many or too few)**

The basis for a vector space is a sequence of vectors that are linearly independent and they span the space.

Change of basis:  
Let $x_e$ be in the standard basis, and the columns of Q another basis for the same space. Then we get the equality
$$ x_e = Qx_q. $$
Furthermore, if W has in the columns another basis, we have that
$$ x_w = W^{-1}x_e = W^{-1}Qx_q. $$  

**Dimension of a space (the number of vectors in a basis)**  

Requires that the number of vectors in a basis is unique.

## Proofs
\begin{theorem}
Orthogonality of the fundamental subspaces
\end{theorem}
\begin{proof}
Let $y \in N(A^T)$ so that $A^Ty = 0$. Let x be a variable such that Ax denotes all the possible combinations of the columns of A. If $C(A) \perp N(A^T)$, then we must have that $Ax \cdot y = 0$. Indeed, we get this, since
$$ Ax \cdot y = y^TAx = (A^Ty)^Tx = 0^Tx = 0. $$
Analoguously, we get that $C(A^T) \perp N(A)$ by letting $x \in N(A)$ and taking all possible combinations of rows with $y^TA$, from which we get that $y^TAx = y^T0 = 0$.
\end{proof}

\begin{theorem}
The dimension of the columns space is equal to the dimension of the row space, i.e, $ Dim \; C(A) = Dim \; C(A^T)$
\end{theorem}

\begin{proof}
Let Dim C(A) = r, and let $b_1, ..., b_r$ form a basis for the column space. Since the columns of B span the whole column space of A, we can write A = BC for some coefficient matrix C (think how $a_{col1} = b_{col1} \cdot c_{11} + ... + b_{col \; r} \cdot c_{r1}$). Thus, if A is a (m x n) matrix, B is (m x r) and C is (r x n).

However, changing the point of view, we get that actually BC is also a combination of the rows of C, where B is the coefficient matrix. In this case, we think that $a_{row1} = b_{row1}C = b_{11} \cdot c_{row1} + ... + b_{1r} \cdot c_{row \; r}$. Thus it becomes evident that $Dim \; C(A^T) \leq r$ because the rows of A are a combination of r rows of C, which implies that $Dim \; C(A) = r \geq Dim \; C(A^T)$.

By symmetry of the argument, we get that $Dim \; C(A^T) \geq Dim \; C(A)$, and therefore we conclude that $Dim \; C(A) = Dim \; C(A^T)$
\end{proof}

\begin{theorem}
The amount of vectors in a basis of a vector space is unique
\end{theorem}
\begin{proof}
Let $v_1, v_2 ..., v_n$ and $w_1, w_2, ..., w_m$ be two bases for the same vector space and denote by V and W the matrices containing the vectors as columns. Suppose for the sake of a contradiction that n > m.

Since V spans its column space because a basis contains only independent vectors, we can write W = VA for some coefficient matrix A, and thus, for example,  $w_1 = a_{m1} \cdot v_1 + ... + a_{mn} \cdot v_n$. Therefore, note that the dimension of A is (m x n), and since n > m by assumption, there is a nontrivial solution for the equation Ax = 0.

Thus we get that $Ax = 0 \implies VAx = 0 \implies Wx = 0$ for some nontrivial x, hence we get a contradiction, because this means that some nontrivial combination of the columns of W gives 0 and thus the columns of W cannot be independent.

The case m > n can be proven symmetrically, and thus we get that m = n.
\end{proof}  

Remark: This allows us to define the dimension of a space as the number of vectors in its basis, and the definition is well-defined.
