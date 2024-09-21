_Harkeerat Singh Sawhney & Mak Fazlic_

## Problem 1. (Floating Point Numbers)

The properties we know are as follows:

β = 2, t = 5, L = 7, U = 7

### a) $x = 30$﻿

We want to represent $x = 30$﻿ in $F(2, 5, 7, 7)$﻿ with

$\pm 1.d_1 d_2 d_3 d_4 \times 2^e, \space \space -7 \le e \le 7, d_i \in \{0, 1\}.$

Therefore,

$30 = 2.15 \rightarrow 0 \newline 15 = 2.7 \rightarrow 1 \newline 7 = 2.3 \rightarrow 1 \newline 3 = 2.1 \rightarrow 1 \newline 1 = 2.0 \rightarrow 1 \newline$

Hence, the decimal number 30 in form of floating point would be,

$30_{10} = 11110 \newline \therefore \bold{\space 1.1110 \times 2^4}$

### b) $x = 3.75$﻿

We want to represent $x = 3.75$﻿ in $F(2, 5, 7, 7)$﻿ with

$\pm 1.d_1 d_2 d_3 d_4 \times 2^e, \space \space -7 \le e \le 7, d_i \in \{0, 1\}.$

First re-writing 3.75 as follows:

$3.75 = 3.0_{10} + 0.75_{10}$

Therefore,

$3 = 2.1 \rightarrow 1 \newline 1 = 2.0 \rightarrow 1$

_and_

$0.75 \times 2 = 1.5 \rightarrow 1 \newline 0.5 \times 2 = 1 \rightarrow 1$

Hence, the decimal number 30 in form of floating point would be,

$3.75 = 11.11 = \bold{1.1110 *2^1}$

### c) $x_{min}$﻿

The smallest positive number in this format is as follows:

$x_{min} = 1.0 \times 2^{-7} \newline x_{min} = \bold{0.0078125} $

### d) $x_{max}$﻿

The maximum positive number in this format is as follows:

$x_{max} = 1.1111 \times 2^{7} \newline x_{max} = \left(\frac{1}{2^0} + \frac{1}{2^1} + \frac{1}{2^2} + \frac{1}{2^3} + \frac{1}{2^4} \right) \times 2^7 \newline x_{max} = \frac{31}{16} \times 128 \newline x_{max} = \bold{248}$

### e) $z = 30.1$﻿

We want to represent $x = 3.75$﻿ in $F(2, 5, 7, 7)$﻿ with

$\pm 1.d_1 d_2 d_3 d_4 \times 2^e, \space \space -7 \le e \le 7, d_i \in \{0, 1\}.$

First re-writing 30.1 as follows:

$30.1 = 30.0_{10} + 0.1_{10}$

Therefore,

$30 = 2.15 \rightarrow 0 \newline 15 = 2.7 \rightarrow 1 \newline 7 = 2.3 \rightarrow 1 \newline 3 = 2.1 \rightarrow 1 \newline 1 = 2.0 \rightarrow 1$

and,

$0.1 \times 2 = 0.2 \rightarrow 0 \newline 0.2 \times 2 = 0.4 \rightarrow 0 \newline 0.4 \times 2 = 0.8 \rightarrow 0 \newline 0.8 \times 2 = 1.6 \rightarrow 1 \newline 0.6 \times 2 = 1.2 \rightarrow 1$

Hence, the decimal number 30.1 in form of floating point would be,

$30.1 = 11110.0\overline{0011} = \bold{1.1110 *2^4}$

This representation is not **exact** because it is not able to represent all the numbers. This is because there are not enough digits to represent the number.

## Problem 2. (Transformation between number representations)

$1 = 2^5 \newline 0 = 2^4 \newline 1 = 2^3 \newline 0 = 2^2 \newline 1 = 2^1 \newline 1 = 2^5 \newline 0 = 2^0 \newline$

### a) $101010_2 $﻿ to Decimal Number

$2^1 + 2^3 + 2^5 = 32 + 8 + 2 = \bold{41}$

### b) $A4E2_{16}$﻿ as Octal Number

Since A4E2 in binary is:

$001010 \space 0100 \space 1110 \space 0010_{2}$

Now converting this to Octal:

$001 = 1 \newline 010 = 2 \newline 010 = 2 \newline 011 = 3 \newline 100 = 4 \newline 010 = 2 $

Therefore the Octal version is:

$\bold{122342_8}$

### c) $A4E2_{16}$﻿ as Binnary Number

A4E2 in binary is:

$\bold{1010010011100010_{2}}$

### d) $101.0111_2$﻿ as Hexadecimal

101 in hexadecimal is

$101 = 2^2 + 2^0 = 5$

0111 in hexadecimal is

$0111 = 2^2 + 2^1+ 2^0 = 7 $

Therefore the hexadecimal version is

$\bold{5.7}_{16}$

### e) $101.0111_2$﻿ as Decimal

101 in decimal is

$101 = 2^2 + 2^0 = 5$

0111 in decimal is

$0111 = 0 \times \frac{1}{2^1} + 1 \times \frac{1}{2^2} + 1 \times \frac{1}{2^3} + 1 \times \frac{1}{2^4} = 0.4375$

Therefore the hexadecimal version is

$\bold{5.4375}_{10}$

  

  

$1 $