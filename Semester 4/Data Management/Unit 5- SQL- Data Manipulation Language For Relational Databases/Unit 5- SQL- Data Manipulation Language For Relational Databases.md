## Multi-sets

![[../../../Attachments/Untitled 54.png|Untitled 54.png]]

- The above two table are equal, because:
    - They contain the same rows with the same multiplicity
    - The order of rows does not matter
    - The order of columns does not matter, as they are labeled

![[../../../Attachments/Untitled 1 26.png|Untitled 1 26.png]]

- The above two tables are not equal, because:
    - There is a row that appears with different multiplicities in the two tables
    - Row (2, 20) appears twice in R but only once in S
    - But if they were sets then they would be equal

## Nulls

## Typical Queries

## Division

## Joins

## Aggregates

- It is sometimes important to specify whether duplicates should or should not be removed before the appropriate aggregate operator is applied
- The standard aggregate operations are:
    - **SUM**; coputes the sum; NULLs are ignored
    - **AVG**; computes the average; NULLs are ignored
    - **MAX**; computes the maximum; NULLs are ignored
    - **MIN**; computes the minimum; NULLs are ignored
    - **COUNT**; computes the count (the number of); NULLs are ignored, but exception
- Modifier to aggregate operators:
    - **ALL** (default, do not remove duplicates)
    - **DISTINCT** (remove duplicates)
    - **COUNT** can also have ***** specified, to count the number of tuples, without removing duplicates, here NULLs are not ignored.
- Conditions
    - **WHERE**
    - **GROUP BY**
    - **HAVING AVG**

## Duplicates

## Aggregate Operators

## Sub-queries

- It is refereed to as a “inner loop”

## Insertion

## Deletion

## Update