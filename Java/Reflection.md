# Reflection
> java.lang.reflect
## Concept
A program can inspect and manipulate its own code at `runtime`.

**workflow**: first get a `Class` object and then manipulate it.
```
java.lang.Class (Class) -> java.lang.reflect.*
```

> [!info] frameworks use reflection to read and execute code alongside notations.
## How to reflect a class

```java
// 1. Get a (Class) object
Class student = Class.forName("Student");

// 2. Get interested class attributes
// [] -> only public ones || Declared -> all of them without Object's methods
Class superclass = student.getSuperclass();
Constructor[] declaredConstructors = student.getDeclaredConstructors();
Constructor[] constructors = student.getConstructors();
Field[] declaredFields = student.getDeclaredFields();
Field[] fields = student.getFields();
Method[] declaredMethods = student.getDeclaredMethods();
Method[] methods = student.getMethods();

// 3. e.g retrieve and print names

System.out.println("Superclass " + superclass);
for (Constructor dc : declaredConstructors) {
    System.out.println("Declared Constructor " + dc.getName());
}
// ...
```

## Real example
Increasing an account balance value at runtime
```java
import java.lang.reflect.Field;

final class AccountUtils {

    private AccountUtils() { }
    
    public static void increaseBalance(Account account, long amount) {
        try {
            Field accountBalance = account.getClass().getDeclaredFields()[0];
            accountBalance.setAccessible(true);
            long currentBalance = accountBalance.getLong(account);
            accountBalance.setLong(account, currentBalance + amount);
        }
        catch (Exception e) { // *logging must be fixed in this case
            e.printStackTrace();
        }
    }
}
```