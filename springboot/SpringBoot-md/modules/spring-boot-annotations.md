Spring Boot Annotations

## 3. *@EnableAutoConfiguration*

*@EnableAutoConfiguration*, as its name says, enables auto-configuration. It means that **Spring Boot looks for auto-configuration beans** on its classpath and automatically applies them.

Note, that we have to use this annotation with *@Configuration*:

```java
@Configuration
@EnableAutoConfiguration
class VehicleFactoryConfig {}
```

