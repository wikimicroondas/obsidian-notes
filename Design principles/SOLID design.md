Design principles are rules that guide you to better decision for the design of your program.

Some of them are simple:
* **DRY** - don't repeat yourself
* **YAGNI** - you ain't gonna need it
* **KISS** - keep it simple, stupid

In other cases, a design can define a whole ecosystem that needs a better understanding.

# SOLID
Each letter of **SOLID** stands for a design principle by itself.
## Single responsibility principle (SRP)
- One design flaw must only affect that functionality.
- An object can only know and do what it is supposed to.
- An object dependencies is defined by cohesive behaivor.

> [!info] Controllers help to distribute methods and functions among objects

## Open/closed principle (OCP)
* A component must be open for extention but close for modification.
* Don't break backward compatibility.
* Use the existing code, don't create methods that will need mantainance.
* The bases shouldn't be modified.

> [!info] Interfaces serve as contracts that restricts objects in one way. Adapters use existing code and need no mantainance.

## Liskov substitution principle (LSP)
- Any subclass `S` of the base class `C` can substitute `C` without changing the correctness of the program.

> [!info] Superclasses can correctly identify degenrated subclasses of other inherited classes


## Interface segregation principle (ISP)
- Interfaces must be integral to its purpose.
- A class should not have degenerate method implementations (empty, error)

> [!info] Following verbal syntax for interfaces (`[v]-able`, `with-[condition]`) can help write and produce clean and clear code.

## Dependency inversion principle (DIP)
