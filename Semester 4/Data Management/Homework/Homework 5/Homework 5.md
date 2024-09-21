## A. Data Structures

1. **Heap**
    1. If the the heap does not need to be “compacted” then it would take 1 operation.
    2. If the heap needs to be “compacted” then it will take always take N operation. The first one would be to reach the record and then to move the tail to close the gap.
2. **Sorted Sequence**
    1. For sorted sequence it usually takes between $log\space N$﻿ or $log \space N+N$﻿ operations. However, it would take $log \space N+N$﻿ operations depending on the variant. For instance, if a “null” value can be put instead of the real value, then it would cause the sequence to grow unnecessarily.

## B. Index and File

1. Dense Index and Sparse Index
    1. **Dense Index:**
        
        An index is dense when it has index entries for every search key value in the data base file. This helps to search faster, however it needs more space to store index records.
        
        ![[../../../../Attachments/Untitled 55.png|Untitled 55.png]]
        
        Figure 1: Dense Indexing
        
        The Figure 1 is an example of Dense Indexing. In figure 1, the method record contains search key value and then points to the real record on the disk.
        
    2. **Sparse Index:**
        
        As compare to Dense Index, Sparse index appears for only some of the values in the file. Hence, due to this it is much slower to locate the records. However, as compare to Dense Indexing, it has small size of index, which in return meant the maintaining the index is also easier.
        
        ![[../../../../Attachments/Untitled 1 27.png|Untitled 1 27.png]]
        
        Figure 2: Sparse Indexing
        
        The Figure 2 is the example of Sparse Indexing, in which not all the values of the file are indexed.
        
2. Clustered File and Un-clustered File
    1. **Clustered File:**
        
        A Data file tends to be clustered if whenever some block B contains records with key values $x$﻿ and $y$﻿, such that $x < y$﻿, and key value $z$﻿, such that $x < z< y$﻿ appears anywhere in the data file, then it must be in block B.
        
        ![[../../../../Attachments/Untitled 2 22.png|Untitled 2 22.png]]
        
    2. **Un-clustered File:**
        
        If the file were first not sorted with contiguous, and then the blocks were not dispersed is Unclustered File.
        
        ![[../../../../Attachments/Untitled 3 19.png|Untitled 3 19.png]]
        
3. 4 Different Types of choices for building indexes
    1. **Dense Index Clustered File:**
        
        They are generally unnecessarily since they have a large index which is not necessarily.
        
    2. **Sparse Index Clustered File:**
        
        These are the best since it increases the resource availability.
        
    3. **Dense Index Un-Clustered File:**
        
        They are good, as they can can easily find the records for every key.
        
    4. **Sparse Index Un-Clustered File:**
        
        These are generally bad since they cannot easily find records for some keys.
        

## C. B+ trees

![[../../../../Attachments/Untitled 4 17.png|Untitled 4 17.png]]

![[../../../../Attachments/Untitled 5 17.png|Untitled 5 17.png]]

![[../../../../Attachments/Untitled 6 16.png|Untitled 6 16.png]]