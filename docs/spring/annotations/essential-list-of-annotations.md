# The Essential List of Spring Boot Annotations and Their Use Cases

The Spring framework is a robust server-side framework for modern Java-based enterprise applications. Since its introduction in 2003, its advantages have made it one of the most dominant server-side frameworks among many organizations. According to a research study by Snyk in 2020 on the usage of the server-side web frameworks, 50% of the respondents have said they use Spring Boot, and 31% of the respondents use Spring MVC. 

Java applications use annotations to provide additional information about the code but do not impact a compiled code. They usually start with ‘@’ and are metadata associated with code components such as variables, methods, classes, etc. Based on the defined annotations, the compiler can change how it treats the program.
What is Java Spring Boot?

Java Spring Boot is an open-source framework that allows the creation of standalone and production-grade enterprise applications that execute on Java Virtual Machine (JVM).

Spring Boot has three core capabilities that enable the development of web applications and microservices faster and easier. 

    Autoconfiguration
                                                                                                                                An opinionated approach to configuration
                                                                                                                                The ability to create standalone applications

You can configure and set up Spring Boot applications with minimal changes from these core capabilities. Any production application needs to be monitored for its uptime. You can use Spring Boot Actuator as a dependency to simplify monitoring your application’s status. 

Spring Boot Features
Why use Annotations? 

Annotations are not just comments in a program. There are many uses of annotations. Annotations help to provide helpful information such as method dependencies, variable meanings, class references, package declaration, type declaration, and many more. Also, they help developers understand the code easily. The compiler can catch errors and suppress specific warnings using annotations. It allows static type checking at compile time. Developers can use these annotations for further processing, such as creating XML files and codes, and with annotations, developers do not have to do cumbersome configurations.
Spring Boot Annotations and their use cases

Spring Boot Annotations are the metadata that provides the additional formation about a Spring Boot program. Several spring boot annotations provide different automatic configurations.

Below are all the essential spring boot annotations you should know about.
1. @Bean

The “@Bean” is a method-level annotation that is analogous to XML <bean> tag. When you declare this annotation, Java creates a bean with the method name and registers it with the BeanFactory. The following shows how the usage of @Bean in a method statement:

@Bean
public ExampleBean exampleBean() {
return new ExampleBean();
}


2. @Springbootapplication

The “@SpringBootApplication” annotation triggers auto-configuration and component scanning. It combines three annotations: @Configuration, @ComponentScan, and @EnabeAutoConfiguration. 

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MyClass {
public static void main(String[] args) {
SpringApplication.run(MyClass.class, args);
}
}


3. @Configuration

The “@Configuration” is a class-based annotation that indicates the definition of one or more Bean methods in the class. Once the Sprint container encounters this annotation, it can process these spring beans to generate bean definitions and service requests at runtime.

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class ConfigClass {
@Bean
public MyBean mybean() {   
return new MyBean();
}
}


4. @ComponentScan

You can use the “@ComponentScan” annotation with the “@Configuration” annotation to define the components you need the program to scan. There are a few arguments in this annotation. The framework scans the current package with sub-packages if you do not specify any argument. You can use the ‘basePackages’ argument to define the specific packages to scan.

package TestPackage;

import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan(basePackages = "TestPackage")

public class TestClass {

}


5. @EnableAutoconfiguration

This annotation allows you to auto-configure the program based on your requirements. The framework decides this auto-configuration based on the jars included in the program and the classpath. For example, suppose you added the “tomcat-embedded.jar” file, then it automatically configures the TomcatServletWebServerFactory if there is no explicit declaration for its related factory bean. Using the “exclude” and “excludeClassName” arguments.

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.EnableAutoConfiguration;

@EnableAutoConfiguration
public class TestClass {
public static void main(String[] args) {
SpringApplication.run(TestClass.class, args);
}
}


6. @RequestMapping 

The “@RequestMapping” Annotation is used to map HTTP requests to REST and MVC controller methods in Spring Boot applications. You can apply this to either class-level or method-level in a controller. Furthermore, you can declare multiple request mappings using a list of values in the annotation.

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class ControllerClass {

    @ResponseBody
    @RequestMapping("/cart")
    public String getCart() {
        return "this is the cart!";
    }
     
    @ResponseBody
    @RequestMapping("/catalogue")
    public String getCatalogue() {
        return "this is the catalogue";
    }
}


7. @GetMapping 

The “@GetMapping” is a shortcut for the  “@RequestMapping(method = RequestMethod.GET)” annotation, which handles the HTTP GET requests corresponding to the specified URL. The following class uses the “@RestController” annotation to indicate it can handle web requests. The “@GetMapping” maps /hello to the hello() method

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class TestController {

@GetMapping("/hello")
public String hello() {
return "Hello Spring Boot!";
}
}


8. @RequestParam

The “@RequestParam” annotation enables extracting input query parameters, form data, etc. For example, suppose you have an endpoint /API/book which takes a query string parameter called id. Then you can specify that parameter in the following manner using the @RequestParam annotation. 

@GetMapping("/api/book")
@ResponseBody
public String getBook(@RequestParam String id) {
return "Book ID: " + id;
}


9. @Service 

The @Service is a class-level annotation used to indicate that the class is a service class that defines the business logic. For instance, the below @Service annotation indicates that BankService is a service class that offers bank services. 

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class BankService {

    private final BankInfo bankInfo;
 
    @Autowired
    public BankService(BankInfo bankInfo) {
        this.bankInfo = bankInfo;
    }
}


10. @Component 

This component allows the framework to automatically detect the component classes without any need to write any explicit code. Spring framework scans classes with @component, initialize them, and injects the required dependencies.

import org.springframework.stereotype.Component;

@Component
public class TestComponentAnnotation {

public int multiply(int x, int y) {
return x * y;
}
}

11. @Repository

The “@Repository” is a specialized version of the “ @Component” annotation. It indicates that the class is a repository that contains data storage and other operations such as updating, deleting, searching, and retrieving data on objects. 

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;
import com.howtodoinjava.demo.model.BookEntity;

@Repository
public interface BookRepository extends JpaRepository<BookEntity, Long>
{
}


12. @Controller

This class-based annotation is also a specialization of the “@Component” annotation, marking the class as a controller. It usually combines with handler methods annotated with the @RequestMapping annotation and is used with Spring MVC applications. Spring scans these classes with this annotation and catches @RequestMapping annotations. Below is an example of its usage.

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class TestController {

    @RequestMapping("/hello")
    public String hello()
    {
        return "Hello Spring!";
    }
}


13. @Autowired

The “@Autowired” annotation can auto wire bean on a constructor,  setter method, property, or methods with multiple parameters. When you use @Autowired annotation on setter methods, you can eliminate the <property> tag in the XML configuration file. 

import org.springframework.beans.factory.annotation.Autowired;

public class Product {
private Product product;

@Autowired
public void setProduct( Product product ){
this.product = product;
}
public Product getProduct( ) {
return product;
}
}

14. @SpringBootTest

As the name suggests, @SpringBootTest annotation can be used on a test class that executes Spring Boot-based tests. You can use it easily for integration testing as it loads the full application context. 

import org.springframework.boot.test.context.SpringBootTest;

@SpringBootTest(webEnvironment=WebEnvironment.RANDOM_PORT)
public class DemoTest
{   
@Autowired
private DemoController demoController;

@Test
public void contextLoads() throws Exception {
assertThat(demoController).isNotNull();
}
}


15. @MockBean

Using this annotation, you can specify mocks in ApplicationContext and mocks the services or REST API endpoints from your programs. Spring loads the mock version of the application context when you run the application. You can specify this annotation at the class and field levels, and it is possible to specify them in configuration classes. Below is an example of using the “@MockBean” annotation.

import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.mock.mockito.MockBean;

@RunWith(SpringRunner.class)
@SpringBootTest
public class ProductServiceTest {

@Autowired
private ProductService productService;

@MockBean(name="Product")
private Product product;

@Test
public void test(){
when(product.findAll()).thenReturn(Collections.emptyList());
assertTrue(productService.findAll().isEmpty());
}
}

Summary 

Spring Boot has a collection of annotations that enable you to develop web applications faster and more efficiently. While developing with Spring Boot,  speed and productivity are absolute priorities for all developers. Lightrun is a key observability platform that helps developers build applications faster by enabling them to add logs, traces, and metrics to their code on-demand and in real-time while the app runs.

## Links
- [The Essential List of Spring Boot Annotations and Their Use Cases - lightrun.com](https://lightrun.com/spring-boot-annotations/)