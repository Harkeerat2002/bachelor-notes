Harkeerat Singh Sawhney & Mak Fazlic

## Problem 1. (Matrix Norms)

### a) Compute Analytically $||A||_1, ||A||_\infin$﻿and $||A||_F$﻿.

Lets assume that $||A||_1 = \space _{1\le j \le n}^{max} \sum_{i=1}^{n} |a_{ij}|$﻿ while having $A = \begin{pmatrix}$﻿, hence adding $|A|$﻿ with 1 is as follows:

$|A| + 1 = \begin{pmatrix}$

Furthermore, lets assume that $||A||_\infin = \space _{1\le i \le n}^{max} \sum_{j=1}^{n} |a_{ij}|$﻿ while having $A = \begin{pmatrix}$﻿, hence adding $|A|$﻿ with 2 is as follows:

$|A| + 2 = \begin{pmatrix}$

Finally, letting $||A||_2 = \space \sigma_{max}(A) \le \left( \space \sum_{i=1}^{n} \sum_{j=1}^{n} |a_{ij}|^2 \right)^{\frac{1}{2}} =: ||A||_F$﻿ , therefore:

$\begin{align*}$

### b) Compute Analytically $||B||_1, ||B||_\infin$﻿and $||B||_F$﻿

Lets assume that $||B||_1 = \space _{1\le j \le n}^{max} \sum_{i=1}^{n} |b_{ij}|$﻿ while having $B = \begin{pmatrix}$﻿, hence adding $|B|$﻿ with 1 is as follows:

$|B| + 1 = \begin{pmatrix}$

Furthermore, lets assume that $||B||_\infin = \space _{1\le i \le n}^{max} \sum_{j=1}^{n} |b_{ij}|$﻿ while having $A = \begin{pmatrix}$﻿, hence adding $|A|$﻿ with 2 is as follows:

$\begin{align*}$

Finally, letting $||B||_2 = \space \sigma_{max}(B) \le \left( \space \sum_{i=1}^{n} \sum_{j=1}^{n} |b_{ij}|^2 \right)^{\frac{1}{2}} =: ||B||_F$﻿ , therefore:

$\begin{align*}$

### c) Compute Analytically $||A||_2$﻿.

To get $||A||_2$﻿ the largest singular value of A must be known:

$||A||_2 = \sqrt{\lambda_{max} (A^{T} A)}$

Therefore, first defining C:

$C =$

Hence, now calculated $|C - \lambda I| = 0$﻿, in which $I$﻿ is the identity matrix:

$\begin{align*}$

Therefore $||A||_2 = \sqrt{15 + \sqrt{221}} \approx \bold{5.4649}$﻿

  

## Problem 3. (Bonus Exercise: Norm Equivalence)

In order to specify the constants, it is important to consider the Sandwich theorem. This theorem states that the sequence of the vectors which are converging to the limit will also be converging to its same limit. Since it is know that all the $1-p$﻿ norms are equal then the following can be stated:

$c_p x_p \le x_2 \le C_px_p \space where \space c_p = 1 \space and \space C_p = \sqrt{d}$

Hence which this, the following can be stated:

$\begin{align*}$

Hence with this,

$\sqrt{\space _{1\le j \le d}^{max}(x_1, x_2, ...., x_{d-1}, x_d)^2}$

Furthermore,

$\begin{align*}$

Hence with this,

$\newline$

Therefore, the constraints are:

$\bold{x_\infin \le x_2 \le \sqrt{d}x_\infin}$