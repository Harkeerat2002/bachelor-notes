Harkeerat Singh Sawhney

## Question 1

$AB \rightarrow C \newline$

### a)

1. **Closure of AB**
    
    $AB \rightarrow C \newline$
    
2. **Closure of AEG**
    
    $AE \rightarrow H \newline$
    
3. **Closure of EG**
    
    $G \rightarrow DG \newline$
    
4. **Closure of ABCD**
    
    $AB \rightarrow C \newline$
    
5. **Closure of AE**
    
    $AE \rightarrow H \newline$
    

### b)

**ABD, ABG**

## Question 2

$\bold{Us} \space (Users) \newline$

### a)

$\bold{Us} \rightarrow \bold{AlTi} \newline$

### b)

$\bold{Us} \rightarrow \bold{AlTiPr} \newline$

### c)

1. **Table from the Minimal Cover:**
    
    $\bold{UsAlTiPr} \newline$
    
2. No, you can not because there is no table which is redundant mean there is table which is a subset of another table.
3. Looking at the current tables and seeing if it contains the key $\bold{UsAlTiLeRePrYeDa}$﻿.
    
    $\bold{UsAlTiPr^+} = \bold{AlTiPrLeReDaYe}$
    
    As it can be seen above, the first table does contain the global key. Hence we do not need to add a new table to store the global key.
    

## Question 3

$CF \rightarrow E \newline$

### a)

- The attributed can be classified into 4 classes:
    - Appearing on both sides of FDs:
        - **E**
        - **C**
        - **F**
    - Appearing on left sides only:
        - **A**
        - **B**
    - Appearing on right sides only:
        - **D**
    - Not appearing in FDs
        - **None**
- What we know as facts:
    - Attributes of class 2 and 4 must appear in every key
    - Attributes of class 3 do not appear in any key
    - Attributes of class 1 may or may not appear in keys
- Every key must contain **AB**
- To see, which attributes, if any have to be added, we compute which attributes, if any have to be added, we compute which attributes are determined by **AB**
- We obtain:
    - $AB^+ = ABFD$﻿
- Hence, we are missing CE, therefore we need C in the key as well.
- **The key is** **$ABC^+$**﻿

### b)

- CF → E = Key Dependency
- AE → C = Partial Dependency
- F → D = Transitive Dependency
- E → F = Partial Dependency
- B → F = Partial dependency

### c)

- Minimal Cover is a simplified and reduced version of the given set of FD. This is a Minimal Cover already because there is no Redundant to remove, and no Extraneous Attribute to remove as well.

## Question 4

$ABFH \rightarrow DE \newline$

### a) Explaining why the relation is not in BCNF

The relation is not in **BCNF** because **N** is not in the relation scheme R.

### b) Finding the Minimal Cover for the FDs

$AB \rightarrow E \newline$

### c)

1. **Table from the minimal cover:**
    
    $ABE \newline$
    
2. No, you can not because there is no table which is redundant mean there is table which is a subset of another table.
3. Looking at the current tables and seeing if it contains the key **ABCDEFGH**.
    
    $ABE^+ = ABEDGHF \newline$
    
    As it can be seen with the first table, the only relation missing is **C,** however that is not in the FDs, hence then the global key would be $ABEC^+$﻿. A new table needs to be added to add the Global key, since no existing table could represent the Global key.
    

## Question 5

### a)

The relation is not in 2NF because as we know F can only dependent on the primary key, however A → F is a partial dependency.

### b)

Due to FD being a partial dependency it is in the 2NF, however the reason it is not in the 3NF because it is also Transitive Dependency.