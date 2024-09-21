# Question 1- Instruction Level Parallelism: Pipelining

**Assume that we are using a 7-stage pipeline and that the pipeline is initially empty. Each stage of the pipeline takes 1 nanosecond. You can also assume that there are no "hazards", i.e., there are no conflicting instructions that access the same data.**

1. **How long does it take to execute a single instruction?**
    
    It takes **7 nanoseconds** to execute a single instruction.
    
    $7\space nanoseconds \times 1 \space instruction = 7\space nanoseconds$﻿
    
2. **What is the Instruction Issue Rate?**
    
    - _Rate_ means how many/unit of times(s)
    - Rate metrics always have something time-related in there denominators
        
        $\frac{How \space many \space (Instruction)}{Unit \space of \space times\space (Seconds)}$
        
    - How long does it take for an instruction be issued out? 1 ns, as the pipeline stages
    - What’s the rate?
    
    $\frac{1}{10^{-9}} = 10^{+9} (IPS) = 1000 (MIPS)$
    
3. **How long does it take to finish a program consisting of 20 instructions?**
    
    ![[../../../Attachments/Untitled 57.png|Untitled 57.png]]
    
4. **Draw the pipeline after instruction 6 was fetched (i.e., it "appears" in the first stage), after instruction 10 was fetched, and after instruction 6 was issued/executed (i.e., it "left" the last stage).**
    
    |   |   |   |   |
    |---|---|---|---|
    ||**T4**|**T5**|**T6**|
    |**Stage 1 (FETCH)**|I4|I5|==I6==|
    |**Stage 2**|I3|I4|I5|
    |**Stage 3**|I2|I3|I4|
    |**Stage 4**|I1|I2|I3|
    |**Stage 5**||I1|I2|
    |**Stage 6**|||I1|
    |**Stage 7**||||
    |**Is OUT**||||
    
    |   |   |   |   |
    |---|---|---|---|
    ||**T8**|**T9**|**T10**|
    |**Stage 1 (FETCH)**|I8|I9|==I10==|
    |**Stage 2**|I7|I8|I9|
    |**Stage 3**|I6|I7|I8|
    |**Stage 4**|I5|I6|I7|
    |**Stage 5**|I4|I5|I6|
    |**Stage 6**|I3|I4|I5|
    |**Stage 7**|I2|I3|I4|
    |**Is OUT**|I1|I2|I3|
    
    |   |   |   |   |
    |---|---|---|---|
    ||**T11**|**T12**|**T13**|
    |**Stage 1 (FETCH)**|I11|I12|I13|
    |**Stage 2**|I10|I11|I12|
    |**Stage 3**|I9|I10|I11|
    |**Stage 4**|I8|I9|I10|
    |**Stage 5**|I7|I8|I9|
    |**Stage 6**|I6|I7|I8|
    |**Stage 7**|I5|I6|I7|
    |**Is OUT**|I4|I5|==I6==|
    
5. **Assume that we do not use Instruction Level Parallelism, but have only a single unpartitioned datapath. How fast would we need to clock this datapath so that our 20-instructions program runs just as fast as the pipelined version?**
    
    ![[../../../Attachments/Untitled 1 29.png|Untitled 1 29.png]]
    
      
    
    # Question 2 - Signed Binary Numbers
    
    1. **Write the decimal number 20752 as a signed 16-bit binary in all representations (signed magnitude, one’s complement, two’s complement, excess 2m-1).**
        
        ![[../../../Attachments/Untitled 2 24.png|Untitled 2 24.png]]
        
    
    # Question 3 - Signed Binary Numbers
    
    1. **Write the decimal number 14356 as a signed 16-bit binary in all representations (signed magnitude, one’s complement, two’s complement, excess 2m-1).**
        
        ![[../../../Attachments/Untitled 3 22.png|Untitled 3 22.png]]
        
    2. **What is the largest positive number that can be represented with 6 bits in all representations (signed magnitude, one’s complement, two’s complement, excess 2m-1)? Give both the decimal and the binary representation for each answer.**
        
        ![[../../../Attachments/Untitled 4 19.png|Untitled 4 19.png]]
        
    3. **What is the largest negative number that can be represented with 6 bits in all representations (signed magnitude, one’s complement, two’s complement, excess 2m-1)? Give both the decimal and the binary representation for each answer.**
        
        ![[../../../Attachments/Untitled 5 19.png|Untitled 5 19.png]]
        
    4. **What does it mean when a representation is asymmetric? Which of the representations (signed magnitude, one’s complement, two’s complement, excess 2m-1) are symmetric, and which are asymmetric? What are the pros and cons of asymmetry?**
        
        A representation is “symmetric”, when in a given number of bit-width with a specific range of positive and negative numbers, for each positive number “x”, its negative form is also included in the mentioned range, Otherwise, the representation is “asymmetric”
        
        **Symmetric:**
        
        - Signed Magnitude
        - One’s Complement
        
        **Asymmetric:**
        
        - Two’s Complement
        - Excess 2m-1