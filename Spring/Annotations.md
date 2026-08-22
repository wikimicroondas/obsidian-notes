## @SpringBootApplication
Meta-annotation that contains these `3` annotations. These annotations are subjective to adapt depending on the application type, the number does not change:
### @EnableAutoConfiguration
Spring decision engine, automatically starts the conditions that the application must meet.
`web -> Tomcat server | sql -> db connection`
### @ComponentScan
Recursively scans `main`, looking for `@Configuration`, `@Service`, `@Component` to process objects and pass them to the IoC container.
### @SpringBootConfiguration
Indicates that beans can be declared in the main class.

