# Custom Annotations
> java.lang.annotation.*

Custom annotations have to be defined in `@interface` files
```java
public @interface Description {}
```

## Retention policies
Specifies at which level the annotation will be applied (source, class or runtime).
```java
@Retention(RetentionPolicy.RUNTIME)
public @interface Description {}
```

## Target types
Restricts the types it can be applied to.
```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Description {}
```

## Parameters
The default value can't be null.
The parameters can be primitives, String, Class, Enum, annotation and arrays of these types.
```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Description {
    String author();
    String description();
    int version() default 0;
}
```

## Meta-annotations
Mark as `@Repeatable` when it can be use multiple times at the same place. You need to provide them a container class.
```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Descriptions {
    Description[] value();
}

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
@Repeatable(Descriptions.class) 
public @interface Description {...}
```
Now it accepts collaborations
```java
@Description(author = "John Doe", description = "first description")
@Description(author = "Richard Roe", description = "second description")
public void testMethod() {
```
And the processor to print the annotation's data would look like this:
```java
public class DescriptionProcessor {
	
    public void printDescription(Object o) {
        Class<?> processingClass = o.getClass();
        for (Method m : processingClass.getDeclaredMethods()) {
	        
            if (m.isAnnotationPresent(Descriptions.class)) {
                Descriptions descriptions = m.getAnnotation(Descriptions.class);
                StringBuilder sb = new StringBuilder();
				
                for (Description d : descriptions.value()) {
                    sb.append("Description: ")
                            .append(d.description())
                            .append(" Author : " )
                            .append(d.author())
                            .append(" Version : ")
                            .append(d.version())
                            .append("\n");
                }
                System.out.println(m.getName() + " Descriptions: ");
                System.out.println(sb.toString());
            }
        }
    }
}
```
