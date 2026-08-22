## Aspect-oriented programming
Paradigm that complements `OOP` by modularizing cross-cutting concerns (logging, security, transaction management), that typically span across multiple layers of the application.

## Spring container
`RAM` application manager inside the `JVM`. It is represented as an instance of the application context.

## Beans
Object instantiations managed by the IoC Container. Mayor default configuration:
* `Name` - `{value="customName"}`, a bean matches its method's name by default.
* `Scope` - `singleton`, the same instance is recycled in the entire application.
### usage
Config
```java
@Configuration
public class PaymentConfig {
	
    @Bean
    public PaymentProcessor paymentProcessor(BankService bankService) {
		return new PaymentProcessor("EUR", 5000);
    }
    
}
```
Service
```java
@Service
public class InvoiceService {
    
    private final PaymentProcessor paymentProcessor;
	
	// the constructor receives the modified parameter from the
	// IoC container
	@Autowired
    public InvoiceService(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor;
    }
	
    public void receivePayment(double quantity) {
        paymentProcessor.process(quantity);
    }
}
```