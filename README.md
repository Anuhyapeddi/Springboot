# Springboot

cheatsheet for spring framework

Before going to Springboot framework. Some things to keep in mind.

Framework - It is a reusable set of tools and elements that provide a base for developing applications.

Spring framework - It is an open-source framework that helps Java developers build enterprise-grade applications.

Servlets - It is a Java class that runs on a Java-enabled server to extend the capabilities of web applications

different layers 
1. accept the client request -  controller 
2. do the business logic - service
3. connect to the database - repositories

here everything is a class, if you want to work with service inside the controller, then we need to create object of the service inside the controller.

IOC - Inversion of Control
gererally we create the object, but in IOC we are giving power to someone else to create the object.
IOC is just the philosify, but we need the actual technique to do that. Here comes the concept called Dependency Injection.
Dependency Injection is the actual implementation of IOC.

IOC - principle
DI - Design Pattern

So, Spring says whenever you need an object, don't create the object just ask me I will provide you the object.

There are three techniques to handle the dependency Injection (DI)

1. Construtor Injection - what we do in the controller class is we create the construtor and in the constructor we pass the reference of the service. Now I need the service so inject the object
2. Setter Injection -  we can create the setter methods for it and do the setter injection
3. field Injection -

Most of the time we don't need all the objects in the class, we only need only few objects. In that case we need to configure in Config file. (that means we need to talk to the framework by configure in the file). 

Springboot - spring 
Convention over configuration
springboot is more like standard one, when you initize springboot, you get all the unused dependency also.
Whereas in Spring, we only get what you have installed but you need to configure everything everything by your self.

Dependency Injection

Spring has it's own container inside the JVM. We call it as IOC container.
SpringApplication.run(LibraryApplication.class, args);
whenever I run this line of code, it create and runs this container inside the JVM.

Spring does not create object of all classes, it only creates the object of those classes which have @Component Annotation.

Autowiring


