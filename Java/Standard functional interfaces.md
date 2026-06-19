# Standard functional interfaces
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
sumFunction.apply(5, 10); // 15
```
Returns a single value.
### Operators
> Operator<T, T>
```java
BinaryOperator<String> appender = (str1, str2) -> str1 + str2;
appender.apply("Hello", "World"); // "Hello World"
```
Returns a value of the same type `T`
### Predicates
> Predicate < T>
```java
Predicate<Character> isDigit = Character::isDigit;
boolean isNumber = isDigit.test('8'); // true
```
Returns a `boolean`
### Suppliers
> Supplier< T>
```java
IntSupplier intSupplier = () -> 33;
int numero = intSupplier.getAsInt(); // 33

// Suppliers generally return Strings, (Supplier<String>):
// stringSupplier.get();
```
Accepts no values and returns a single value
### Consumers
> Consumer < T>
```java
Consumer<String> printer = System.out::println;
printer.accept("!!!"); // "!!!"
```
Accepts a value and returns no value

# Composing functions
Creating a new function using another one as a base. This solution returns a `new` function.
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

## Composing predicates
Predicates have three composing methods `and`, `or`, `negate`.

e.g
```java
IntPredicate isOdd = n -> n % 2 != 0; // true for all odd values
IntPredicate isEven = isOdd.negate(); // true for all even values

IntPredicate isOddOrLessThan11 = isOdd.or(lessThan11);
System.out.println(isOddOrLessThan11.test(10)); // true

IntPredicate isOddAndLessThan11 = isOdd.and(lessThan11);
System.out.println(isOddAndLessThan11.test(8)); // false
```

## Composing consumers
It has `andThen` method to chain the supplied values.

e.g
```java
Consumer<String> consumer = System.out::println;
Consumer<String> doubleConsumer = consumer.andThen(System.out::println);
doubleConsumer.accept("Hi!");
// Hi!
// Hi!
```

In a real situation, you could use it to output a value to different destinations, a database or a logger.

## Composing function example

```java
Function next = x -> x + 1;
Function previous = x -> x - 1;
Function square = x -> x * x;
Function mult3 = x -> x * 3;

next.compose(nex.compose(square)).andThen(previous).andThen(mult3);
// mult3(next(previous(next(square(x)))))
```

This exercise is read from left to right, the point is that there is an internal block that is executed from right to left.

```java
.compose(nex.compose(square)).andThen(previous)
```

When we use `.andThen()`, the compiler understands `A.andThen(B)` as a block, so we are forced to solve `A` and then `B`. When we reach the same level it is read from left to right.