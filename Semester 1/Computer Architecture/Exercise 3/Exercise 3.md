# Question 1 - Endianness:

1. Y**ou have the following memory contents:**
    
    |   |   |
    |---|---|
    |**Address**|**Data**|
    |0|0101 1100|
    |1|1001 0110|
    |2|0000 0011|
    |3|1100 1111|
    
    **Imagine you load this data as a 4-byte word into a register** **_R_****. What is the value in** **_R_** **on a** **_big endian_** **machine and what is it on a** **_little endian_** **machine if you interpret the bits as a** **signed integer encoded in 2s complement** **(re. negative numbers described in appendix A.4)?**
    
    ![[../../../Attachments/Untitled 58.png|Untitled 58.png]]
    
2. **You have the following message in memory "Welcome Class 2021”. Each character (also including the numbers "2", "0", "2", "1") is encoded in one byte; the first character ("W") is stored at address 0, the second at address 1, and so on. You load this message from memory into 64 bit registers on a** **_little endian_** **machine and store it back into memory on a** **_big endian_** **machine. How does the string look in memory on the** **_big endian_** **machine?**
    
    ![[../../../Attachments/Untitled 1 30.png|Untitled 1 30.png]]
    

  

# **Question 2 - Error Detection**

**Assume a simple error-detecting code using a single parity bit.**

1. **How many valid code words do you have in 18 bits with odd parity?**
    
    Codeword = data bits + check bits
    
    m = number of data bits
    
    r = number of check bits
    
    m = Codeword = m + r
    
      
    
    Single parity bit means that there is 1 check bit.
    
    Therefore, there are:
    
    $18 = m + 1 \newline m = 17$
    
    Hence there are **$2^{17}$**﻿**memory words**.
    
2. **Give two examples of error detection in 16-bit words with even parity.**
    - 1101 0011 1000 1000
        - The amount of 1’s are not event, hence there is a detection.
    - 1001 0110 0001
        - The amount of 1’s are not event, hence there is a detection.
3. **When will the error detection fail? Give a sufficient condition.**
    - The error detection would fail if there is more that one bit flips. This is because if there is more than one bit flips, then the number of even parity’s would stay even hence the bit flips would not be recognized.

# Question 3 - Hamming Codes

1. **The Hamming Code is described as a method for finding errors in data bits. But what happens if one of the parity bits gets changed by some computer accident? Explain briefly and give an example.**
    
    - The way in which the Hamming Code finds the error in data bits, even if the bits are flipped by computer by accident is through check bits. Through check bits which are positioned properly, checks if there is a bit flit or not:
    
    ![[../../../Attachments/Untitled 2 25.png|Untitled 2 25.png]]
    
2. **How many check bits do you need if you want to correct single bit errors for the following sizes of memory words:**
    
    **a) 322 bits**
    
    - Power of 2 = ==1, 2, 4, 8, 16, 32, 64, 128, 256==, 512, 1024, 2047
    
    9 check bits
    
    **b) 2048 bits**
    
    - Power of 2 = ==1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2047==
    
    12 check bits
    
3. **Compute the Hamming code with even parity for the memory word 0011 1101 0101 1000. Mark which are the parity bits.**
    
    ![[../../../Attachments/Untitled 3 23.png|Untitled 3 23.png]]
    
4. **Correct the single bit error in the following code word, assuming a Hamming code with even parity:**
    
    1110 1110 1010 0010 0010 1
    
    ![[../../../Attachments/Untitled 4 20.png|Untitled 4 20.png]]
    
    # Question 4 - Cache Lines and Alignment
    
    **Section 2.2.5 in the book talks about how CPUs typically load entire cache lines from the main memory, not just a single byte. In aligned data access, the boundaries of these cache lines are fixed. For example, in an architecture that uses a word size of 4-byte, a cache line can only start at the first byte (reading bytes 1-4), from the 5th byte (reading bytes 5-8), from the 9th byte (reading bytes 9-12), and so forth. In unaligned data access, cache lines can start anywhere (in the example given above this would allow, e.g., reading bytes 7-10).**
    
    1. **You have a machine that uses 6-byte words. Which addresses does the CPU load data from, if it loads only aligned data? Give a few examples so that it becomes clear (no need to enumerate more than a few addresses).**
    2. **How many address bits do you need to address 8GB of memory, when only aligned memory access is allowed and word size is 32 bit?**