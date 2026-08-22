## Components
Classes managed by the Spring IoC.
### usage
* A component is treated as a bean by the IoC, the main difference with a configuration bean is that it indicates that the class was made in the project while `@Bean` supplies objects from external libraries, making them configurable.
```java
import org.springframework.stereotype.Component;
import java.util.Random;

@Component
public class PasswordGenerator {
	// educational hardcoding
    private static final String CHARACTERS = "abcdefghijklmnopqrstuvwxyz";
    private static final Random random = new Random();
	
    public String generate(int length) {
        StringBuilder result = new StringBuilder();
		
        for (int i = 0; i < length; i++) {
            int index = random.nextInt(CHARACTERS.length());
            result.append(CHARACTERS.charAt(index));
        }
        
        return result.toString();
    }
}
```
service
```java
@Service
public class UserService {
    private final PasswordGenerator generator;
    
    public UserService(PasswordGenerator generator) { // <--
        this.generator = generator;
    }
	
    public void userRegister(String email) {
	    
        String newPassword = generator.generate(12);
        
        System.out.println("User " +
				email + " registered with: " + newPassword);
    }
}
```

### extended usage
`CommandLineRunner` is an interface component whose `run` method is equivalent to the `main` method of console applications.
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.stereotype.Component;

@Component
public class Runner implements CommandLineRunner {
    private final PasswordGenerator generator;
	
    @Autowired
    public Runner(PasswordGenerator generator) {
        this.generator = generator;
    }
	
    @Override
    public void run(String... args) {
        System.out.println("A short password: " + generator.generate(5));
        System.out.println("A long password: " + generator.generate(10));
    }
}
```

# Annotations
## @Component
Indicates that a class is managed by Spring IoC. A component can receive specialized annotations indicating the role of the component.
### @Service
The class holds business logic.
### @Repository
Denotes that the class is responsible for data access and may provide exception translation.
### @Controller | @RestController
Marks classes that handle web requests and responses.
