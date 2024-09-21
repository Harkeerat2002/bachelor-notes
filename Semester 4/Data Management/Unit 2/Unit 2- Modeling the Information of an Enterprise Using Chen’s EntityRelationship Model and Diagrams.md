## ER Diagrams

- **Entity/relationship (ER) model** provides a common, informal, and convenient method for communication between application end users (customers) and the database designers to model the information’s structure

## Entity and Entity Set

- **Entity** **set** is denoted by a **rectangle** with its type written inside:

![[../../../Attachments/Untitled 51.png|Untitled 51.png]]

## Attribute

- An entity may have a set of zero or more **attributes,** which are some properties

![[../../../Attachments/Untitled 1 23.png|Untitled 1 23.png]]

## Super-key

- Super-key is a single key or a group of multiple keys that can uniquely identify tuples in a table.
- Super key can contain multiple attributes that might not be able to independently identify tuples in a table, but when grouped with certain keys, they can identify tuples uniquely

## Key

- A key is a way to categorize attributes in an ER diagram.

## Candidate Key

- A candidate key is a minimal super key that uniquely identifies an entity.
- Minimal super-keys have no unnecessary attributes; In other words, super-keys that don’t have subsets that are also super-key.

## Primary Key

- If an entity set has one or more keys, one of them (no formal rule which one) is chosen as the primary key.
- In the ER Diagram, the attributes of the primary key are underlines

![[../../../Attachments/Untitled 2 19.png|Untitled 2 19.png]]

## UNIQUE

- In SQL the other keys (which are not primary key), loosely speaking, are referred to using the keyword UNIQUE

## Relationship

- Several entity sets (one ore more) can participate in a relationship
- Relationships are denoted by diamonds, to which the participating entities are “attached”

## Binary Relationship and its functionality

![[../../../Attachments/Untitled 3 16.png|Untitled 3 16.png]]

## Non-binary Relationship

![[../../../Attachments/Untitled 4 14.png|Untitled 4 14.png]]

## Relationship with Attributes

- Consider relationship Buys among Person, Vendor, and Product
- We want to specify that a person Buys a product from a vendor at a specific price
- Price is not
    - A property of a vendor, because different products may be sold by the same vendor at different prices
    - A property of a product, because different vendors may sell the same product at different prices
    - A property of a person, because different products may be bought by the same person at different prices
- So price is really an attribute of the relationship Buys
- For each tuple (person, product, vendor) there is a value of price

![[../../../Attachments/Untitled 5 14.png|Untitled 5 14.png]]

## Aggregation

- It is sometimes natural to consider relationships as if they were entities.
- This will allow us to let relationships participate in other “higher order” relationships
- Here each “contract” needs to be approved by (at most) one agency
- Relationships is “made into” an entity by putting it into a rectangle; note that the edge between Buys and Approves touches the Buys rectangle but not the Buys diamond, to make sure we are not confused

![[../../../Attachments/Untitled 6 13.png|Untitled 6 13.png]]

## Strong and weak Entities

- **A strong entity (set):** Its elements can be identified by the values of their attributes, that is, it has a (primary) key made of its attributes.
- **A weak entity (set):** Its elements cannot be identified by the values of their attributes: there is no primary key made from its own attributes
    
    ![[../../../Attachments/Untitled 7 11.png|Untitled 7 11.png]]
    

![[../../../Attachments/Untitled 8 9.png|Untitled 8 9.png]]

## Discriminant

- An entity that does not have primary key is a weak entity. The discrimination of a weak entity set is a set of attributes that serves to distinguish among entities in the entity set that depend on one particular strong entity.

## ISA

- The subset relationship between the set and its subset is called ISA, meaning “is a”.
- Elements of the subset, have all the attributes and relationships as the elements of the set: they are in the “original” entity set.
- ISA is indicated by a triangle
- The specific ISA could be:
    - **Disjoint:** no entity could be in more than one subclass
    - **Overlapping:** an entity could be in more than one subclass
    - **Total:** every entity has to be in at least one subclass
    - **Partial:** an entity does not have to be in any subclass
- This could be specified by replacing “ISA” in the diagram by an appropriate letter.

## General Carnality Constraints

- It can be specified how many times each entity from some entity set can participate in some relationship, in every instance of the database.

![[../../../Attachments/Untitled 9 8.png|Untitled 9 8.png]]