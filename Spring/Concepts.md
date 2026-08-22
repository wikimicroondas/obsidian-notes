## Aspect-oriented programming
Paradigm that complements `OOP` by modularizing cross-cutting concerns (logging, security, transaction management), that typically span across multiple layers of the application.

## Spring container
`RAM` application manager inside the `JVM`. It is represented as an instance of the application context.

## Beans
Objects that are instantiated, assembled, and managed by the Spring IoC container
* These units must be applied over POJOs when you don't need one for each user (e.g a db connection is the same for every user, but each user needs its own data).

Major default configuration:
* `Name` - `{value="customName"}`, a bean matches its method's name by default.
* `Scope` - `singleton`, the same instance is recycled in the entire application.
### usage
the standard is to create a configuration classes for each technical responsibility (AuthConfig, PaymentConfig, ServiceConfig). Beans can be placed everywhere, for clarity we use these classes.
```java
@Configuration
public class PaymentConfig {
	
    @Bean
    public PaymentProcessor paymentProcessor(BankService bankService) {
		return new PaymentProcessor("EUR", 5000);
    }
    
}
```
service
```java
@Service
public class InvoiceService {
    
    private final PaymentProcessor paymentProcessor;
	
	// the constructor receives the modified parameter from the
	// IoC container. Autowired can be skipped and it will work anyway
	@Autowired
    public InvoiceService(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor;
    }
	
    public void receivePayment(double quantity) {
        paymentProcessor.process(quantity);
    }
}
```

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

