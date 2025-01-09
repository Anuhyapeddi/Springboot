# Springboot

cheatsheet for spring framework

Before going to Springboot framework. Some things to keep in mind.

Framework - It is a reusable set of tools and elements that provide a base for developing applications.

Spring framework - It is an open-source framework that helps Java developers build enterprise-grade applications.

Servlets - It is a Java class that runs on a Java-enabled server to extend the capabilities of web applications

different layers 
* which accepts the request from the client and sends response to the client  -  Controller
* if the controller wants data, it will not ask from database. It will ask from Service layer
* do the business logic - Service Layer
* connect to the database - Repositories

here everything is a class, if you want to work with service inside the controller, then we need to create object of the service inside the controller.

## IOC - Inversion of Control
gererally we create the object, but in IOC we are giving power to someone else to create the object.
IOC is just the philosify, but we need the actual technique to do that. Here comes the concept called Dependency Injection.
Dependency Injection is the actual implementation of IOC.

IOC - principle
DI - Design Pattern

So, Spring says whenever you need an object, don't create the object just ask me I will provide you the object.

There are three techniques to handle the dependency Injection (DI)

* Construtor Injection - what we do in the controller class is we create the construtor and in the constructor we pass the reference of the service. Now I need the service so inject the object
* Setter Injection -  we can create the setter methods for it and do the setter injection
* field Injection - By using some annotations

Most of the time we don't need all the objects in the class, we only need only few objects. In that case we need to configure in Config file. (that means we need to talk to the framework by configure in the file). 

* Springboot - spring 
* Convention over configuration
* springboot is more like standard one, when you initize springboot, you get all the unused dependency also.
* Whereas in Spring, we only get what you have installed but you need to configure everything everything by your self.

Dependency Injection

Spring has it's own container inside the JVM. We call it as IOC container.
```java
SpringApplication.run(LibraryApplication.class, args);
```
whenever I run this line of code, it create and runs this container inside the JVM.


Spring does not create object of all classes, it only creates the object of those classes which have @Component Annotation.

```java
@Component
```
Autowiring

Primary

Qualifier

Springboot MVC

### Difference between @Controller and @RestController

```java
// @Controller checks for the "Welcome to roses and tulips!!" and it sends the page "Welcome to roses and tulips!!"
// in this case we don't have any page. So, it throws us an error

@Controller
public class HomeController {

    @RequestMapping("/")
    public String greet(){
        return "Welcome to roses and tulips!!";
    }

    @RequestMapping("/about")
    public String about(){
        return "Here we sell traditional jwellery!!";
    }
}
```

```java
// In @RestController it sends the data

@RestController
public class HomeController {

    @RequestMapping("/")
    public String greet(){
        return "Welcome to roses and tulips!!";
    }

    @RequestMapping("/about")
    public String about(){
        return "Here we sell traditional jwellery!!";
    }
}
```

```java
// by default @RequestMapping is a GET call

```
### PathVarible
PathVariable is used to extract values from the URI path and bind them to method parameters in your controller methods. This is particularly useful when building RESTful web services where parts of the URL can be dynamically specified

```java
@RequestMapping("/products/{prodID}")
    public Product getProductById(@PathVariable int prodID){
        return service.getProductById(prodID);
    }
```
Jackson library is responsible for conversion from JSON to object and object to JSON.

@RequestBody
This is responsible for getting data in the request and sending data as a reference

Make sure you always follow DRY principle. 
DRY - Do not Repeat Yourself.

## Spring Data JPA

JPA - Java Persistence API. JPA is a Standard.

ORM - Object Relational Mapping

* class name - table name
* member variables - column names
* object variables(data from client) - rows

if you want to create a table for particular class
then that class should have annotation @Entity

For every entity we should define a primary key. 
That can be defined by @Id

```java
@Component
@Entity   // defining entity by annotation
public class Product {

    @Id
    private int prodId;   //primary key
    private String category;
    private String prodName;
    private int price;
    private boolean available;

    public Product() {
    }
```
@CrossOrigin

"CORS" stands for "Cross-Origin Resource Sharing" - it refers to an error that occurs when a web application tries to access data from a different domain without the necessary permissions, essentially a security feature that prevents unauthorized access to resources across different websites.

it can be solved by adding @CrossOrigin annotation in the backend code.

```java
@Component
@CrossOrigin   // @CrossOrigin annotation is added to avoid CORS error
@Entity
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int prodId;
    private String category;
    private String prodName;
    private String prodDesc;
    private BigDecimal price;
    private boolean available;
    private int quantity;
```
jackson library is used to convert one formate to another formate.

@ResponseEntity is resposible for sending the status code.

There are multiple ways to store the image. 
* we can store images on the cloud and use the link 
* or you can directly store image url in database

whenever we are storing a large object like byte, we have to use @Lob annotation.
Where Lob refer to large object

```java
@Component
@CrossOrigin
@Entity
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int prodId;
    private String category;
    private String prodName;
    private String prodDesc;
    private BigDecimal price;
    private boolean available;
    private int quantity;
    private String imageName;
    private String imageType;
    @Lob        // large object
    private byte[] imageData;
```
Difference between @RequestBody and @RequestPart

* @RequestBody - It sends the entire request
* @RequestPart - It sends just a part of the request

MultipartFile - A representation of an uploaded file received in a multipart request

JPQL (Java Persistence Query Language)

* JPQL is used to write custom query
* Instead of table name we use class name
* Instead of column name we use member variable name






























