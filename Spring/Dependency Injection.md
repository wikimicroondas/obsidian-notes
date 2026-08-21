## Definition of DI
Dependency injection is the delegation of responsibility for object creation to an external entity, relying on interfaces to decouple the code. This can be done through field injection, setter assignments, or constructor declarations.

## Types of DI and examples
DI is a architectural decision, so looking at examples will teach you more than any source.
### Bad case
This service is:
* Hard dependent on `Email`, a single modification can break it.
* Not designed to receive more than one service.
* Can't be tested with any other case.
```java
interface Email {
	public void sendMessage();
}

class EmailService {           //
	Email gmail = new Email(); // <--
}                              //
```

---
## Possible solutions
All of them solve the principal issues but they provide certain advantages.
### Method injection
* The method receives the dependency and uses it when it needs to.
* Avoids storing dependencies at class level.
```java
class EmailService {
	@Override
	public void sendMessage(Email service) {
	    service.sendMessage();
    }
}
```

### Property injection
* Avoids destroying `EmailService` object when it changes services.
```java
class EmailService {
	private Email service; // Starts being empty
	
	@Override
	public void setService(Email service) {
	    this.service = service;
	}
}
```

### Constructor injection
* Most secure one, conditions the creation of the object.
* Guarantees its availability through the service.
```java
class EmailService {
	private Email email;
	
	public EmailService(Email email) {
	    this.email = email;
	}
}
```