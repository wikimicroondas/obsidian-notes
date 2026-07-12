# Comparable interface
> java.lang.Comparable

> [!info] Comparator vs Comparable
> - The object has **only one obvious, inherent way** to be sorted
> - You own the source code and can modify the class directly

`Comparable` provides the `compareTo()` method which allows comparing an object with other objects of the same type. It's also important to comply with the conditions: all objects can be compared to other objects of the same type in the most widely used way, which means `compareTo()` should be consistent with the `equals` method. A sequence of data has the natural ordering, if for each 2 elements `a` and `b`, where `a` is located to the left of `b`, the condition is true: `a.compareTo(b) <= 0`.

Meaning of its returns:
- `1` - Greater than
- `0` - Equal
- `-1` - Less than

It is important to override `equals` to match `compareTo` implementation.

e.g

```java
class Coin implements Comparable<Coin> {
    private final int nominalValue;    // nominal value
    private final int mintYear;        // the year the coin was minted
	
    Coin(int nominalValue, int mintYear) {
        this.nominalValue = nominalValue;
        this.mintYear = mintYear;
    }
	
	@Override
    public int compareTo(Coin other) {
        if (nominalValue == other.nominalValue) {
            return 0;
        } else if (nominalValue < other.nominalValue) {
            return -1;
        } else {
            return 1;
        }
    }
	
    // We consider two coins equal if they have the same nominal value
    @Override
    public boolean equals(Object that) {
        if (this == that) return true;
        if (that == null || getClass() != that.getClass()) return false;
        Coin coin = (Coin) that;
        return nominalValue == coin.nominalValue;
    }
	
    // getters, setters, hashCode and toString
}
```

Now we can use sort methods:

```java
List<Coin> coins = new ArrayList<>();

coins.add(big);
coins.add(medium1);
coins.add(medium2);
coins.add(small);

Collections.sort(coins);
coins.forEach(System.out::println);
```

Some clases already have implemented the `Comparable` interfaces, such as `Integer` and `String` with their respective natural order.