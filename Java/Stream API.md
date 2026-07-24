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
`import static java.util.stream.Collectors.[method];
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
