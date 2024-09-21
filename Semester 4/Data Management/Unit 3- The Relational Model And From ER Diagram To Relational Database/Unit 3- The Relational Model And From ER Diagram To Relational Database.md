  

## Sets

- Two sets A and B are equal iff (if and only if) they have the same elements
- A = B
- Therefore, as sets: {2, 5, 3, 7} = {2, 7, 5, 3, 5, 3, 3}

## Relations and Tables

- Another word for row is **tuple**
- Example of a table S of two columns A and B

![[../../../Attachments/Untitled 52.png|Untitled 52.png]]

- A **relation** is such a table
- Since relations are sets of tuples, the following two relations are equal.

![[../../../Attachments/Untitled 1 24.png|Untitled 1 24.png]]

- Each relations could be defined by following keys:
    - **Primary Keys**
    - **Keys (beyond primary)**
    - **Foreign Keys** and what they reference

## Relational Schema

- A relational scheme defines a set of relations.
- A relational scheme defines a finite set of finite relations.
- We want to define a structure for some table:
    - We give it a name (we have S)
    - We chose the number of columns (we had 2) and give them distinct names (we had A and B)
    - We decide on constraints, if any, on the permitted values (for example, we can assume as it was true for our example that any two rows that are equal on A must be equal on B)

![[../../../Attachments/Untitled 2 20.png|Untitled 2 20.png]]

## Primary Keys

![[../../../Attachments/Untitled 3 17.png|Untitled 3 17.png]]

- Considering the above example, it is told that any two tuples that are equal on both FN and LN are (completely) equal
- This is a property of every possible instance of Person in this application.
- Then (FN, LN) is a **super-key** of Person, and in fact a **key**, because neither FN or LN by themselves are sufficient.

![[../../../Attachments/Untitled 4 15.png|Untitled 4 15.png]]

- Considering another example, it is told that for any instance of Pay, any two tuples that equal on Grade are (completely) equal
- Then Grade is a key
- Salary is not a key because its not told as.

  

- A set of columns in a relation is a **super-key** if and only any two tuples that are equal on the elements of these columns are (completely equal)
- A relation **always** as at least one super-key.
- A minimal super-key, is a **key.**
- Exactly one key is chosen as **primary key.**
- Other keys are just key, sometimes they are called as **candidate keys.**

## Implementing an ER diagram as a relational schema (relational database)

## General Implementation of strong entities

## Handling attributes of different types

## General Implementation of relationships

## Possible special implementation of binary many-to-one relationships

## Implementation of ISA

## Implementation of weak Entities

## Foreign Keys

- Foreign key reference to the primary key of another table (relation)

## Primary Key / Foreign Key constraints inducing many-to-one relationships between tables

![[../../../Attachments/Untitled 5 15.png|Untitled 5 15.png]]

## Concept of Referential Integrity

## Crow’s feet notation: Ends of Lines

![[../../../Attachments/Untitled 6 14.png|Untitled 6 14.png]]

## Crows’ feet notation: pattern of lines

![[../../../Attachments/Untitled 7 12.png|Untitled 7 12.png]]