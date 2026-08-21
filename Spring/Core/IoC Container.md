## Definition
Inversion of Control Container is the core part responsible of dependency injection and beans life cycle. This tool needs to receive two instructions to work, mapped `POJOs` and `metadata`.

## Orchestration
* `legacy` - A XML file is filled with the objects of interest as `beans`.
```xml
<beans>
    <bean id="userRepository" class="com.example.UserRepository"/>
    
    <bean id="userService" class="com.example.UserService">
        <constructor-arg ref="userRepository"/>
    </bean>
</beans>
```

* `annotation-based-configuration` - the container scan for annotations and manages the procedure automatically (bean life cycle).
```java
@Component
public class UserRepository {
    public String findUser(String userId) {
        return "User: " + userId;
    }
}

@Component
public class UserService {
    private final UserRepository userRepository;
    
    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
    
    public String getUserInfo(String userId) {
        return userRepository.findUser(userId);
    }
}
```

## Contexts and Bean Factory
Bean management can be performed by two main components.
### BeanFactory
Provides basic functionality, managing bean installation, wiring and configuration based of provided metadata. It is straightforward and lightweight, suitable for simpler applications that require minimal advanced features.

### ApplicationContext
Extends BeanFactory with additional features such as internationalization, resource loading, and event propagation. This is the most commonly used container in `modern Spring applications`.