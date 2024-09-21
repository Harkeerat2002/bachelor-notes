Harkeerat Singh Sawhney & Mak Fazlic

## Problem 1. (Partially pivoted LU decomposition)

$A =$

We know that,

$P\times A = \hat{L} \times U$

where,

**$U$**﻿ = Upper Triangle Matrix

**$P$**﻿ = Permutation Matrix

$\hat{L}$﻿ = Lower Triangle Matrix

Therefore,

$$

and,

$\hat{L} = $

Hence, in order to get P, we first see which rows we switched around. We put the last row on the top, we also put the first row at 3rd and put the fourth row in last. Hence P would look as follows:

$P = $

Hence coming back to the formula we have as following:

$P \times A = \hat{L} \times U \newline$

## Problem 3. (Bonus exercise: Schur Complement)

### a)

Let $A \in \R ^ {n\times n}$﻿ be a symmetric and _positive definite_ matrix, i.e. $x^T Ax > 0$﻿ for all $x \in \R ^n$﻿\ {0}. Then, the Schur complement $S$﻿ is well defined for any block partitioning of $A.$﻿ Moreover, $A_{1,1}$﻿ as well as $S$﻿ are symmetric and positive definite.

### b)

We are going to consider the _Theorem 3.21:_

**Theorem 3.21:** If A is symmetric and positive definite, then A exhibits a Cholesky decomposition.

Hence, then we can apply the Cholesky Decomposition, from which the given formula can be computed. This is because we now the following:

$A = [a_{1, 1} = [l_{1, 1} \times l_{1,1}] = L \times L^T \newline$

### c)

Due to the Lemma 3.18, $a_{1, 1} > 0$﻿ and S is symmetric and positive definite. Hence $l_{1,1} = \sqrt{a_{1,1}} > 0$﻿ and S exhibits a Cholesky decomposition by the induction hypothesis.

$S = \tilde{L}\tilde{L}^T$