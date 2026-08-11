> Conceptual notes

## 1NF
* One register cannot contain a list
* One table cannot contain duplicates of the same register.

## 2NF
* Read:
	`x -> y` _'x functionally defines y'_
	       _'y is functionally dependent on x'_
* Every non-key attribute in the same table has to be dependent on the PK's table.

## 3NF
* The relations have no `transitive dependencies`.
