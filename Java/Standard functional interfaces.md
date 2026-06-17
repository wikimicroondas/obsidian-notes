> java.lang.function

Functional programming is a concept made for avoid repetitive code and process streams and large amounts of data using functions.

## Functional programming basics in Java
### Functions
In Java, there is no practical difference between methods and functions. We will see them using a different syntax, that's why it is mentioned.

```java
Function<Integer, Integer> example; // Takes and gives an Integer value

example.apply(n); // almost every function has the apply method, that's how we                        use it
```
### Lambda expressions
Logical definition of a function, it's syntax requires an arrow `(n) -> (m)`.

- If we have more than one parameter we must use parenthesis.
- If our logical part has more than one line we use an expression with the reserved word `return`.

```java
BiFunction<Integer, Integer, Integer> sumTwo = (x, y) -> {
	return x + y;
};

sumTwo.apply(6, 7); // 13
```

### Method references
If our functions parameters of input and output matches a method of a class or an instance of a class we can write it in one line.

```java
Function<String, Integer> converter = Integer::parseInt;

converter.apply("1000"); // 1000 (Integer)
```

Note that there are more ways to apply this solution but this is a brief introduction.
See:
- Generics and Generic programming in Java
- How to write a functional interface
- `java.lang` package, as it has really useful methods

## Standard Functional Interfaces
In order to optimize syntax we need to know the base interfaces that can match our current goal.
### Functions
> Function<T, R>
```java
BiFunction<Integer, Integer, Integer> sumFunction = (a, b) -> a + b;
```
Returns a single value.
### Operators
> Operator<T, T>
```java
BinaryOperator<String> appender = (str1, str2) -> str1 + str2;
```
Returns a value of the same type `T`
### Predicates
> Predicate < T>
```java
Predicate<Character> isDigit = Character::isDigit;
```
Returns a `boolean`
### Suppliers
> Supplier< T>
```java
IntSupplier intSupplier = () -> 33;
```
Accepts no values and returns a single value
### Consumers
> Consumer < T>
```java
Consumer<String> printer = System.out::println;

printer.accept("!!!"); // "!!!"
```
Accepts a value and returns no value

## Composing functions
The functional interface `Function<T, R>` has two default methods `compose` and `andThen` for composing new functions. The main difference between these methods lies in the execution order.

- `f.compose(g).apply(x)`  -->   `f(g(x))`
- `f.andThen(g).apply(x)`  -->   `g(f(x))`

e.g
```java
Function<Integer, Integer> adder = x -> x + 10;
Function<Integer, Integer> multiplier = x -> x * 5;

// compose: adder(multiplier(5))
System.out.println("result: " + adder.compose(multiplier).apply(5)); // 35

// andThen: multiplier(adder(5))
System.out.println("result: " + adder.andThen(multiplier).apply(5)); // 75
```
