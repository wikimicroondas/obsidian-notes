# Comparator interface
> java.util.Comparator

> [!info] Comparator vs Comparable
> - The object can be sorted in multiple different ways depending on the situation
> - You **cannot modify** the original class source code

`Comparator<T>` is a generic interface that has a single abstract method `compare` and quite a few non-abstract methods.

```java
.compare(T o1, T o2);
```

We are expected to implement this method according to the following rules:
- It should return 0 if both arguments are equal;
- It should return a positive number if the first argument is greater than the second one;
- It should return a negative number if the first argument is less than the second one.

This way we can even override the natural ordering for any type that implements the `Comparable` interface.

e.g
```java
class MessageDateComparator implements Comparator<Message> {
	
    @Override
    public int compare(Message message1, Message message2) {
        return message1.getCreated().compareTo(message2.getCreated());
    }
}

class MessageAuthorComparator implements Comparator<Message> {
	
    @Override
    public int compare(Message message1, Message message2) {
        return message1.getFrom().compareTo(message2.getFrom());
    }
}
```
---
```java
// Ordered by date
messages.sort(new MessageDateComparator());
// Ordered by author
messages.sort(new MessageAuthorComparator());
```

## Functional part
As the interface has a single abstract method it can be considered as a Functional Interface. This makes it easier to implement an anonymous class that overrides said function and saves up creating too many classes.

```java
messages.sort((m1, m2) -> m1.getCreated().compareTo(m2.getCreated()));
```
