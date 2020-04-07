# How to use properties file

[Properties with Spring and Spring Boot](https://www.baeldung.com/properties-with-spring)

##  Note

1. Both the older *PropertyPlaceholderConfigurer* and the new *PropertySourcesPlaceholderConfigurer* added in Spring 3.1 **resolve ${…} placeholders** within bean definition property values and *@Value* annotations.

   ```
   A very important caveat here is that using <property-placeholder> will not expose the properties to the Spring Environment – this means that retrieving the value like this will not work – it will return null:
   ```

   

2. *@PropertySource*?
3. 