# Stream API
> java.util.stream

Creates a pipe where data is passed between `intermediate` and `terminal` operations. It can return a value or an empty stream for methods.

```java
long count = numbers.stream()
        .filter(number -> number > 5)
        .count();
```

Once a terminal operation has been evaluated, it is impossible to reuse the stream again. If you try doing that the program will throw `IllegalStateException`.

## Intermediate operations

- `filter` returns a new stream that includes the elements that match a **predicate**;
- `limit` returns a new stream that consists of the first `n` elements of this stream;
- `skip` returns a new stream without the first `n` elements of this stream;
- `distinct` returns a new stream consisting of only unique elements according to the results of `equals`;
- `sorted` returns a new stream that includes elements sorted according to the natural order or a given **comparator**;
- `peek` returns the same stream of elements but allows observing the current elements of the stream for debugging;
- `map` returns a new stream that consists of the elements that were obtained by applying a function (i.e. transforming each element).

## Terminal operations

- `count` returns the number of elements in the stream as a `long` value;
- `max` / `min` returns an `Optional` maximum/minimum element of the stream according to the given comparator;
- `reduce` combines values from the stream into a single value (an aggregate value);
- `findFirst` / `findAny` returns the first / any element of the stream as an `Optional`;
- `anyMatch` returns `true` if at least one element matches a predicate (see also: `allMatch`, `noneMatch`);
- `forEach` takes a **consumer** and applies it to each element of the stream (for example, printing it);
- `collect` returns a collection of the values in the stream;
- `toArray` returns an array of the values in a stream.

Some terminal operations return an `Optional` because the stream can be empty and you need to specify a default value or an action if it is empty.

## Collectors class
> java.util.stream.Collectors

### Usage
```java
import static java.util.stream.Collectors.[method];
```
We copy the method that we want to use, for example:
- `summingInt`, `summingLong`, `summingDouble`
- `averagingInt`, `averagingLong`, `averagingDouble`
- `maxBy`, `minBy`
- `counting`

### Example
```java
double average = accounts.stream()
        .collect(averagingLong(Account::getBalance));
```

### Complex example
```java
String megaNumber = accountStream.collect(Collectors.reducing("",
        account -> account.getNumber(),
        (numbers, number) -> numbers.concat(number)
));
```

## Partitioning
```java
Map<Boolean, List<Account>> accountsByBalance = accounts.stream()
        .collect(Collectors.partitioningBy(account -> account.getBalance() >= 10000));
```
For a balance above or equal to `10_000`. It always return a `Map`.

## Grouping
```java
enum Status {
    ACTIVE,
    BLOCKED,
    REMOVED
}

public class Account {
    private long balance;
    private String number;
    private Status status;
    
    // constructors
    // getters and setters
}
```
We can group the accounts into a map based on a condition. It returns a `Map`.
```java
Map<Status, List<Account>> accountsByStatus = accounts.stream()
        .collect(Collectors.groupingBy(Account::getStatus));
```

## Downstream collectors
```java
Map<Status, Long> sumByStatuses = accounts.stream()
        .collect(Collectors.groupingBy(
                Account::getStatus,
                LinkedHashMap::new,    // <---
                Collectors.summingLong(Account::getBalance))   // <---
         );
```
We can apply a specific implementation of `Map` and concatenate another operation, such as a sum. A `downstream` is a role applied to any method in the collectors class, the only condition given is that it has to be inside of another collectors stream.

## Teeing collector
```java
long[] countAndSum = accounts
        .stream()
        .filter(account -> account.getStatus() == Status.BLOCKED)
        .collect(Collectors.teeing(
                Collectors.counting(),
                Collectors.summingLong(Account::getBalance),
                (count, sum) -> new long[]{count, sum})
        );
```
An optimized option to iterate a list once and apply multiple operations. It takes two downstream collectors.

## Primitive streams
To represent each primitive type we have three primitive streams. `IntStream`, `LongStream` and `DoubleStream`.
### takeWhile and dropWhile
```java
// imports
public List<String> getHexSegment(List<String> hex) {
	return hex.stream()
			  .dropWhile(h -> !h.equals("#000000"))
			  .skip(1)
			  .takeWhile(h -> !h.equals("#FFFFFF"))
			  .collect(Collectors.toList());
}
```
This method takes a segment of a specified range of hex codes using functions in each mentioned method.

## Infinite streams
Stream API provides supplier affected streams that generate objects.

### generate
A constructor is a supplier in this case
```java
Stream<Double> randomNumbers = Stream.generate(Math::random);
Stream<User> userStream = Stream.generate(User::new);
```

### iterate
Substitutes a `for` loop. `(seed, function)`.
```java
Stream<Integer> oddNumbersStream = Stream.iterate(1, x -> x + 2); // 1, 3, ...
```
Overloaded version:
```java
Stream.iterate(1, x -> x < 10, x -> x + 2)
        .forEach(System.out::println); // 1 3 5 7 9
```
In between it takes a predicate that determines whether the loop must continue.
`(seed, condition, function)`.

> In most cases it is preferred to use `limit`, as it improves readability

