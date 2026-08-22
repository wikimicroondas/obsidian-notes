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

# Annotations
## @Bean
Indicates that the IoC container must treat the following method as a bean supplier.
### @Bean(name = "customName")
A bean can mismatch the method's name for a custom one.
### @Qualifier("selectedBean")
We can specify the exact bean we need if two or more beans share type.

## @Configuration
Indicates that the following class contains beans for a determinate service. 
## @Autowired
Indicates that the following argument must be taken from the IoC container.