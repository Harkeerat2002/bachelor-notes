## Problem 1. (Floating Point Numbers)

Harkeerat Singh Sawhney & Mak Fazlic

**A)**

**i) Convert 13 into the Floating Point Format**

Converting 13 to a binary number:

$13 = 2 \times 6 \rightarrow 1 \newline 6 = 2 \times 3 \rightarrow 0 \newline 3 = 2 \times 1 \rightarrow 1 \newline 1 = 2 \times 0 \rightarrow 1 \newline$

Hence, the decimal number 13 in form of a binary number is:

$13_{10} = 1101$

Therefore,

$13 = 1101 = 1.101 \times 2^3$

Hence,

$e = 3_{10} = 0011 \newline \bar{e} = 1000 + 0011 \newline \therefore \space \bold{0 |10100000000| 1011}$

**ii) Convert 42.125 into the Floating Point Format**

Converting 42.125 to a binary number:

$41 = 2 \times 21 \rightarrow 0 \newline 21 = 2 \times 10 \rightarrow 1 \newline 10 = 2 \times 5 \rightarrow 0 \newline 5 = 2 \times 2 \rightarrow 1 \newline 2 = 2 \times 1 \rightarrow 0 \newline 1 = 2 \times 0 \rightarrow 1 \newline$

$and$

$0.125 \times 2 = 0.25 \rightarrow 0 \newline 0.25 \times 2 = 0.50 \rightarrow 0 \newline 0.5 \times 2 = 1.0 \rightarrow 1 \newline$

Hence, the decimal number 42.125 in binary format is:

$42.125_{10} = 101010.001 = 1.01010001 \times 2^5$

Hence,

$e = 5_{10} = 0101 \newline \bar{e} = 1000 + 0011 \newline \therefore \space \bold{0|01010001|1101} $

**iii) Convert 0.8 into the Floating Point Format**

Converting 0.8 to a binary number:

$0.8 \times 2 = 0.6 \rightarrow 1 \newline 0.6 \times 2 = 0.2 \rightarrow 1 \newline 0.2 \times 2 = 0.4 \rightarrow 0 \newline 0.4 \times 2 = 0.8 \rightarrow 0 \newline ...$

Hence, the decimal number 0.8 in binary format is:

$0.8_{10} = 0.\overline{1100} = 1.10011001100 \times 2^{-1}$

Hence,

$e = -1_{10} \newline \bar{e} = -1_{10} + 8_{10} = 7 = 0111 \newline \therefore \bold{0/10011001100|0111}$

**B) Determine the decimal number which belongs to the bit pattern 1|01101011100|1101**

First from the first bit, we know that decimal number is a _negative_ _number._

Hence, then the e could be found out from the last 4 bits, which is:

$\bar{e} = 1101 = 1000 - 1101 = 0101 = 5_{10} $

Therefore,

$1.011010111 \times 2^5 = 101101.0111$

Hence converting the 101101.0111 to decimal would be:

$101101 = 2^0 + 2^2 + 2^3 + 2^5 = 1 + 4 + 8 + 32 = 45 \newline 0.0111 = 2^{-2} + 2^{-3} + 2^{-4} = 0.25 + 0.125 + 0.0635 = 0.4375 \newline \therefore \space 101101.0111 = \bold{45.4375_{10}}$

  

**C)**

**i) Determining the** **$x_{max}$**﻿ **and the corresponding bit patterns**

The first bit of the maximum number would be a positive, as a negative number cant be the maximum of this format.

_e_ would be biggest number in the range, which is _7_ hence the e in bit format would be:

$e = 1110 $

Hence the bit format of the maximum number would be:

$\bold{0|11111111111|1110} = 1.1111111111 \times 2^7 = 11111111.1111 = \bold{255.9735}$

**ii) Determining the** **$x_{max}$**﻿ **and the corresponding bit patterns**

The first bit of the minimum number would be a negative, as a positive number cant be the minimum of this format.

_e_ would be smallest number in the range, which is -_7_ hence the e in bit format would be:

$e = 0001$

Hence the bit format of the maximum number would be:

$\bold{1|00000000000|0001} = 1 \times 2^{-7} = \bold{0.0000001}$