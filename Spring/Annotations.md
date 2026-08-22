## @SpringBootApplication
Meta-annotation that contains these `3` annotations. These annotations are subjective to adapt depending on the application type, the number does not change:
### @EnableAutoConfiguration
Spring decision engine, automatically starts the conditions that the application must meet.
`web -> Tomcat server | sql -> db connection`
### @ComponentScan
Recursively scans `main`, looking for `@Configuration`, `@Service`, `@Component` to process objects and pass them to the IoC container.
### @SpringBootConfiguration
Indicates that beans can be declared in the main class.

## @Bean
Indicates that the IoC container must treat the following method as a bean supplier.
### @Bean(name = "customName")
A bean can mismatch the method's name for a custom one.
### @Qualifier("selectedBean")
We can specify the exact bean we need if two or more beans share type.

## @Component
Indicates that a class is managed by Spring IoC. A component can receive specialized annotations indicating the role of the component.
### @Service
The class holds business logic.
### @Repository
Denotes that the class is responsible for data access and may provide exception translation.
### @Controller | @RestController
Marks classes that handle web requests and responses.

## @Configuration
Indicates that the following class contains beans for a determinate service. 
## @Autowired
Indicates that the following argument must be taken from the IoC container.