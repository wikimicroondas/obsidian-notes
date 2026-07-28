# E-R Diagram
Modifying databases after the implementation phase result in large costs. E-R Diagrams is the fastest way to spot design flaws.

## Crow's foot notation
### One-to-One (1-1)
![[one-to-one.svg]]
### One-to-Many (1-M)
![[one-to-many.svg]]
### Many-to-Many (M-M)
![[many-to-many.svg]]
### Optional (O)
![[one-mandatory-to-many-optional-non-identifying.svg]]
> An empty collection can exist
### Mandatory (|)
![[one-mandatory-to-many-mandatory-non-identifying.svg.svg]]
> An empty collection cannot exist

## Identifying and non-identifying relationships
The importance of a FK to an entity
### Identifying
* `Solid line`
The `FK` is used as a part of the `PK` because it cannot exist by itself.
### Non-identifying
* `Dashed line`
The `FK` is used to inform that an entity is part of a collection but can exist by itself.

# E-R Model
## N-M Problem
It is not possible to create a table with multiple values. Since we need a list we use intermediate objects as a value-storage system for instance data.
![[many-to-many-problem-and-solution.svg]]
### Compound PK problem
Using compound primary keys will lead into framework boiler plate code, over complication of child entities from the instance object and slow SQL queries. Use auto incremental  `serial subrogate keys` for this purpose.

