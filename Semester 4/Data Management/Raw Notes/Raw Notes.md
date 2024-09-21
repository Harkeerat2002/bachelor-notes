# Table of Contents

---

Table of Contents

Unit 2: Modeling the Information of an Enterprise Using Chen’s Entity/Relationship Model and Diagrams

Basic Concepts

Entity and Entity Set

Attribute

Sets, Subsets, and Super-sets

Keys

Primary Keys

Relationship

Ternary Relationship

Relationship With Non-distinct Entity Sets

Strong And Weak Entities

The ISA Relationship

Unit 3 The Relational Model And From ER Diagram to Relational Database

Sets

Relation

Keys (and Super-keys)

Relational Implementation for the Example

Crow’s Feet: Improved Arrow Notation

End of Lines in Crow’s Feet Notation

Unit 4 Relational Algebra (Using SQL Syntax): Data Manipulation Language For Relations

Sets and Operations on Them

Many Empty Relations

Projection: Choice Of Columns

Selection: Choice of Rows

Cartesian Product

A Typical use of Cartesian Product

Union

Union Compatibility

Difference

Intersection

Relationship Algebra Using Standard Relational Algebra Mathematical Notation

Unit 5 SQL: Data Manipulation Language For Relational Databases

Key Differences between Relational Algebra And SQL

Multi-sets

Set Operations (UNION)

Set Operations (MINUS)

Set Operations (INTERSECT)

---

  

# Unit 2: Modeling the Information of an Enterprise Using Chen’s Entity/Relationship Model and Diagrams

- **Entity/relationship (ER) model** provides a common, informal, and convenient method for communication between application end users (customers) and the database designers to model the information’s structure

## Basic Concepts

**Entity:**

- This is an “object”. Example:
    - Bob
    - Boston

**Relationship**

- Entities Participate in relationships with each other. Examples:
    - Alice and Boston are in relationship likes (Alice _likes_ Boston)

**Attribute**

- Example:
    - Age is a property of Persons
    - Size is a property of cities

## Entity and Entity Set

- **Entity** **set** is denoted by a **rectangle** with its type written inside:

![[../../../Attachments/Untitled 51.png|Untitled 51.png]]

## Attribute

- An entity may have a set of zero or more **attributes,** which are some properties

![[../../../Attachments/Untitled 1 23.png|Untitled 1 23.png]]

- Attributes can be
    
    - **Base;** or **derived** denoted by dashed ellipses (such as Age, derived from DOB and the current date)
    - **Simple** (such as DOB); or **composite** having their component attributes attached to them (sch as Address, when we think of it explicitly as consisting of street and number and restricting ourselves to one city only)
    - **Single-valued** (such as DOB); or **multi-valued** with unspecified in advance number of valued denoted by thick-lined ellipses (such as Child; a person may have any number of children; we do not consider children as persons in this example, this means that they are not elements of the entity set Person, just attributes of elements of this set)
    
    ![[../../../Attachments/Untitled 16 6.png|Untitled 16 6.png]]
    

## Sets, Subsets, and Super-sets

![[../../../Attachments/Untitled 17 5.png|Untitled 17 5.png]]

## Keys

- Most of the times, some subset (proper or not) of the attributes of an entity has the property that **two different entities in an entity set must differ on the values of these attributes**
- This must hold for all conceivable entities in our database.
- Such a set of attributes is called a **super-key** (”weak” super-set of a key: either proper super-set or equal)
- Informal Definition:
    - Super-key values can identify an individual entity but there may be unnecessary attributes
    - Key value can identify an individual entity but there are no unnecessary attributes
- Example:
    - Social Security Number + Last Name form a super-key, which is not a key as Social Security Number is enough to identify a person.
- _Every key is a super-key_

## Primary Keys

![[../../../Attachments/Untitled 18 4.png|Untitled 18 4.png]]

## Relationship

![[../../../Attachments/Untitled 19 4.png|Untitled 19 4.png]]

![[../../../Attachments/Untitled 20 4.png|Untitled 20 4.png]]

- Formally we say that R is a **relationship** among (not necessarily distinct) entity set E1 E2, .... En if and only if R is a subset of E1 * E2 * .... * En (Cartesian Product)

## Ternary Relationship

![[../../../Attachments/Untitled 21 4.png|Untitled 21 4.png]]

## Relationship With Non-distinct Entity Sets

![[../../../Attachments/Untitled 22 3.png|Untitled 22 3.png]]

![[../../../Attachments/Untitled 23 3.png|Untitled 23 3.png]]

![[../../../Attachments/Untitled 24 3.png|Untitled 24 3.png]]

## Strong And Weak Entities

- A **strong entity** (set): Its elements can be identified by the values of their attributes, that is, it has a (primary) key made of its attributes
    
    Tacitly, we assumed only such entities so far
    
- **A weak entity** (set): Its elements cannot be identified by the values of their attributes: there is no primary key made from its own attributes
    
    Such entities can be identified by a combination of their attributes and the relationship they have with another entity set
    
    **Discriminant** is when that attribute is necessary to recognize the entity.
    

![[../../../Attachments/Untitled 25 3.png|Untitled 25 3.png]]

![[../../../Attachments/Untitled 26 3.png|Untitled 26 3.png]]

![[../../../Attachments/Untitled 27 3.png|Untitled 27 3.png]]

## The ISA Relationship

- The subset relationship between the set and its subset is called **ISA,** meaning “is a”
- Elements of the subset, of course, have all the attributes and relationships as the elements of the set: they are in the “original” entity set.
- ISA is indicated by a triangle
- The elements of the subset are weak entities.

![[../../../Attachments/Untitled 28 4.png|Untitled 28 4.png]]

![[../../../Attachments/Untitled 29 2.png|Untitled 29 2.png]]

![[../../../Attachments/Untitled 30 2.png|Untitled 30 2.png]]

![[../../../Attachments/Untitled 31 3.png|Untitled 31 3.png]]

# Unit 3 The Relational Model And From ER Diagram to Relational Database

## Sets

- A **set** is a “bag” of elements, some/all of which could be sets themselves and a binary relationship “is element of” denoted by $\in$﻿ such as 2 $\in$﻿ {2, 5, 3, 7}, {2, 8} $\in$﻿ {2, {2, 8}, 5, 3, 7},

## Relation

![[../../../Attachments/Untitled 32 2.png|Untitled 32 2.png]]

## Keys (and Super-keys)

Keys:

- **Primary** Keys
- **Keys** (beyond primary)
- **Foreign** **keys** and what they reference

![[../../../Attachments/Untitled 33 2.png|Untitled 33 2.png]]

![[../../../Attachments/Untitled 34 2.png|Untitled 34 2.png]]

- A set of columns in a relation is a **super-key** if and only any two tuples that are equal on the elements of these columns are (completely equal)
- **A relation always has at least one super-key**
- A minimal super-key, is a **key**
- A relation always has at least one key (start with any super-key and remove unnecessary columns)
- Exactly one key is chosen as **primary key**
- Sometimes they are called **candidate keys**

## Relational Implementation for the Example

![[../../../Attachments/Untitled 35 2.png|Untitled 35 2.png]]

## Crow’s Feet: Improved Arrow Notation

![[../../../Attachments/Untitled 36 2.png|Untitled 36 2.png]]

![[../../../Attachments/Untitled 37 2.png|Untitled 37 2.png]]

## End of Lines in Crow’s Feet Notation

![[../../../Attachments/Untitled 38 2.png|Untitled 38 2.png]]

# Unit 4 Relational Algebra (Using SQL Syntax): Data Manipulation Language For Relations

- **SQL is based on relational algebra with many extensions**

## Sets and Operations on Them

![[../../../Attachments/Untitled 53.png|Untitled 53.png]]

## Many Empty Relations

![[../../../Attachments/Untitled 1 25.png|Untitled 1 25.png]]

## Projection: Choice Of Columns

![[../../../Attachments/Untitled 2 21.png|Untitled 2 21.png]]

## Selection: Choice of Rows

![[../../../Attachments/Untitled 3 18.png|Untitled 3 18.png]]

## Cartesian Product

![[../../../Attachments/Untitled 4 16.png|Untitled 4 16.png]]

## A Typical use of Cartesian Product

![[../../../Attachments/Untitled 5 16.png|Untitled 5 16.png]]

## Union

![[../../../Attachments/Untitled 6 15.png|Untitled 6 15.png]]

## Union Compatibility

- We require same-arity (number of columns), otherwise the result is not a relation

## Difference

![[../../../Attachments/Untitled 7 13.png|Untitled 7 13.png]]

## Intersection

![[../../../Attachments/Untitled 8 10.png|Untitled 8 10.png]]

## Relationship Algebra Using Standard Relational Algebra Mathematical Notation

![[../../../Attachments/Untitled 9 9.png|Untitled 9 9.png]]

![[../../../Attachments/Untitled 10 8.png|Untitled 10 8.png]]

![[../../../Attachments/Untitled 11 8.png|Untitled 11 8.png]]

![[../../../Attachments/Untitled 12 7.png|Untitled 12 7.png]]

![[../../../Attachments/Untitled 13 6.png|Untitled 13 6.png]]

![[../../../Attachments/Untitled 14 6.png|Untitled 14 6.png]]

![[../../../Attachments/Untitled 15 6.png|Untitled 15 6.png]]

# Unit 5 SQL: Data Manipulation Language For Relational Databases

## Key Differences between Relational Algebra And SQL

- SQL data model is a multi-set not a set; still rows in tables (we sometimes continue calling relations)
- SQL contains all the power of relational algebra and more
- SQL provides statistical operators, such as AVG (average)

## Multi-sets

![[../../../Attachments/Untitled 39 2.png|Untitled 39 2.png]]

![[../../../Attachments/Untitled 40 2.png|Untitled 40 2.png]]

## Set Operations (UNION)

![[../../../Attachments/Untitled 41 2.png|Untitled 41 2.png]]

![[../../../Attachments/Untitled 42 2.png|Untitled 42 2.png]]

## Set Operations (MINUS)

![[../../../Attachments/Untitled 43 2.png|Untitled 43 2.png]]

![[../../../Attachments/Untitled 44 2.png|Untitled 44 2.png]]

## Set Operations (INTERSECT)

![[../../../Attachments/Untitled 45 2.png|Untitled 45 2.png]]

![[../../../Attachments/Untitled 46 2.png|Untitled 46 2.png]]