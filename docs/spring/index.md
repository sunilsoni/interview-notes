---
layout: default
title: Spring
has_children: true
nav_order: 2
permalink: docs/spring
resource: true
desc: "Spring interview questions and answers."
categories: [Spring]
---

# Spring
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

The Spring Framework provides a comprehensive programming and configuration model for modern Java-based enterprise applications - on any kind of deployment platform.

A key element of Spring is infrastructural support at the application level: Spring focuses on the "plumbing" of enterprise applications so that teams can focus on application-level business logic, without unnecessary ties to specific deployment environments.

---

## Features

### Core technologies
Dependency injection, events, resources, i18n, validation, data binding, type conversion, SpEL, AOP.

### Testing
mock objects, TestContext framework, Spring MVC Test, WebTestClient.

### Data Access
transactions, DAO support, JDBC, ORM, Marshalling XML.

### Spring MVC and Spring WebFlux web frameworks.

### Integration
remoting, JMS, JCA, JMX, email, tasks, scheduling, cache.

### Languages
Kotlin, Groovy, dynamic languages.

---

## Inversion Of Control (IOC) and Dependency Injection(DI)

These are the design patterns that are used to remove dependency from the programming code. They make the code easier to test and maintain. Let's understand this with the following code:

```java
class Employee{  
    Address address;  
    Employee(){  
        address=new Address();  
    }  
}  
```

In such case, there is dependency between the Employee and Address (tight coupling). In the Inversion of Control scenario, we do this something like this:
```java
class Employee{  
    Address address;  
    Employee(Address address){  
        this.address=address;  
    }  
}  
```

Thus, IOC makes the code loosely coupled. In such case, there is no need to modify the code if our logic is moved to new environment.

In Spring framework, IOC container is responsible to inject the dependency. We provide metadata to the IOC container either by XML file or annotation.



### Inversion of Control

Inversion of Control is a principle in software engineering which transfers the control of objects or portions of a program to a container or framework.

###  Advantages of Inversion of Control

1. decoupling the execution of a task from its implementation
2. making it easier to switch between different implementations
3. greater modularity of a program
4. greater ease in testing a program by isolating a component or mocking its dependencies, and allowing components to communicate through contracts

We can achieve Inversion of Control through various mechanisms such as: Strategy design pattern, Service Locator pattern, Factory pattern, and Dependency Injection (DI).

### Dependency Injection

Dependency injection is a pattern we can use to implement IoC, where the control being inverted is setting an object's dependencies.

Connecting objects with other objects, or “injecting” objects into other objects, is done by an assembler rather than by the objects themselves.


### Advantage of Dependency Injection
- makes the code loosely coupled so easy to maintain
- makes the code easy to test

### Spring IoC Container

In the Spring framework, the interface ApplicationContext represents the IoC container. The Spring container is responsible for instantiating, configuring and assembling objects known as beans, as well as managing their life cycles.

The Spring framework provides several implementations of the ApplicationContext interface: ClassPathXmlApplicationContext and FileSystemXmlApplicationContext for standalone applications, and WebApplicationContext for web applications.

In order to assemble beans, the container uses configuration metadata, which can be in the form of XML configuration or annotations.

Here's one way to manually instantiate a container:

```java
ApplicationContext context
        = new ClassPathXmlApplicationContext("applicationContext.xml");
```

Dependency Injection in Spring can be done through constructors, setters or fields.


### Stackoverflow

The Inversion-of-Control (IoC) pattern, is about providing any kind of callback (which "implements" and/or controls reaction), instead of acting ourselves directly (in other words, inversion and/or redirecting control to the external handler/controller).

> For example, rather than having the application call the implementations provided by a library (also known as toolkit), a framework calls the implementations provided by the application.

The Dependency-Injection (DI) pattern is a more specific version of IoC pattern, where implementations are passed into an object through constructors/setters/service lookups, which the object will 'depend' on in order to behave correctly.

> Every DI implementation can be considered IoC, but one should not call it IoC, because implementing Dependency-Injection is harder than callback (Don't lower your product's worth by using the general term "IoC" instead).

**IoC without using DI**, for example, would be the Template pattern because the implementation can only be changed through sub-classing.

**DI frameworks** are designed to make use of DI and can define interfaces (or Annotations in Java) to make it easy to pass in the implementations.

**IoC containers** are DI frameworks that can work outside of the programming language. In some you can configure which implementations to use in metadata files (e.g. XML) which are less invasive. With some you can do IoC that would normally be impossible like inject an implementation at pointcuts.

See also this [Martin Fowler's article](https://martinfowler.com/articles/injection.html#InversionOfControl).


---

## Advantages of Spring Framework


There are many advantages of Spring Framework. They are as follows:

| Name        | Details          | 
|:-------------|:------------------|
| Predefined Templates           | Spring framework provides templates for JDBC, Hibernate, JPA etc. technologies. So there is no need to write too much code. It hides the basic steps of these technologies. Let's take the example of JdbcTemplate, you don't need to write the code for exception handling, creating connection, creating statement, committing transaction, closing connection etc. You need to write the code of executing query only. Thus, it save a lot of JDBC code.| 
| Loose Coupling | The Spring applications are loosely coupled because of dependency injection.   | 
| Easy to test           | The Dependency Injection makes easier to test the application. The EJB or Struts application require server to run the application but Spring framework doesn't require server.      |
| Lightweight           | Spring framework is lightweight because of its POJO implementation. The Spring Framework doesn't force the programmer to inherit any class or implement any interface. That is why it is said non-invasive. | 
| Fast Development           | The Dependency Injection feature of Spring Framework and it support to various frameworks makes the easy development of JavaEE application. | 
| Powerful abstraction           | It provides powerful abstraction to JavaEE specifications such as JMS, JDBC, JPA and JTA. | 
|  Declarative support           | It provides declarative support for caching, validation, transactions and formatting. | 



---

## Dependency Injection

Dependency Injection is the most important feature of Spring framework. Dependency Injection is a design pattern where the dependencies of a class are injected from outside, like from an xml file. It ensures loose-coupling between classes.

In a Spring MVC application, the controller class has dependency of service layer classes and the service layer classes have dependencies of DAO layer classes.

Suppose class A is dependent on class B. In normal coding, you will create an object of class B using ‘new’ keyword and call the required method of class B. However, what if you can tell someone to pass the object of class B in class A? Dependency injection does this. You can tell Spring, that class A needs class B object and Spring will create the instance of class B and provide it in class A.

In this example, we can see that we are passing the control of objects to Spring framework, this is called Inversion of Control (IOC) and Dependency injection is one of the principles that enforce IOC.


---

## Types of Dependency Injection

Spring framework provides 2 ways to inject dependencies:
- By Constructor
- By Setter method

### Constructor-based DI

when the required dependencies are provided as arguments to the constructor, then it is known as constructor-based dependency injection, see the examples below:

_Using XML based configuration:_
Injecting a dependency is done through the bean-configuration file, for this <constructor-arg> xml tag is used:

```xml
 <bean id="classB" class="com.demo.B" />

<bean id="classA" class="com.demo.A">
         <constructor-arg ref="classB" /> 
</bean>
```

In case of more than 1 dependency, the order sequence of constructor arguments should be followed to inject the dependencies.
Java Class A:
```java
package com.demo;
public Class A{
    B b;
    A(B b){
        this.b=b;
        }
}
```
Java Class B:

```java
package com.demo;
public Class B{
   
}
```

**Using Java Based Configuration:**

When using Java based configuration, the constructor needs to be annotated with `@Autowired` annotation to inject the dependencies,

Classes A and B will be annotated with `@Component` (or any other stereotype annotation), so that they will be managed by Spring.

```java
package com.demo;
package org.springframework.beans.factory.annotation.Autowired;
package  org.springframework.stereotype.Component;

@Component
public Class A{
    B b;
    @Autowired
    A(B b){
            this.b=b;
    }
}
```
Java class B:

```java
package com.demo;
package org.springframework.stereotype.Component;

@Component
public Class B{

}
```

Before Spring version 4.3, `@Autowired` annotation was needed for constructor dependency injection, however, in newer Spring versions, @Autowired is optional, if the class has only one constructor.
But, if the class has multiple constructors, we need to explicitly

But, if the class has multiple constructors, we need to explicitly add ``@Autowired`` to one of the constructors so that Spring knows which constructor to use for injecting the dependencies.


### Setter-method injection

in this, the required dependencies are provided as the field parameters to the class and the values are set using setter methods of those properties. See the examples below.

**Using XML based configuration:**
Injecting a dependency is done through the bean configuration file and <property> xml tag is used where ‘name’ attribute defines the name of the field of java class.


```xml
 <bean id="classB" class="com.demo.B" />

<bean id="classA" class="com.demo.A">
<property name="b">
         <constructor-arg ref="classB" />
</property>
</bean>
```



Java Class A:
```java
package com.demo;
public Class A{
    B b;
    public void setB(B b){
        this.b=b;
        }
}
```
Java Class B:

```java
package com.demo;
public Class B{

        }
```
**Using Java based configuration:**

The setter method needs to be annotated with `@Autowired` annotation.

```java
package com.demo;
package org.springframework.beans.factory.annotation.Autowired;
package  org.springframework.stereotype.Component;

@Component
public Class A{
    B b;
    @Autowired
    public void setB(B b){
            this.b=b;
    }
}
```
Java class B:

```java
package com.demo;
package org.springframework.stereotype.Component;

@Component
public Class B{

}
```

There is also a Field injection, where Spring injects the required dependencies directly into the fields when those fields are annotated with `@Autowired` annotation.

### Constructor Vs Setter injection

The differences are:
- Partial dependency is not possible with Constructor based injection, but it is possible with Setter based injection. Suppose there are 4 properties in a class and the class has setter methods and a constructor with 4 parameters. In this case, if you want to inject only one/two property, then it is only possible with setter methods (unless you can define a new parametrized constructor with the needed properties)
- Cyclic dependency is also not possible with Constructor based injection. Suppose class A has dependency on class B and class B has dependency on class A and we are using constructor based injection, then when Spring tries to create object of class A, it sees that it needs class B object, then it tries to resolve that dependency first. But when it tries to create object of class B, it finds that it needs class A object, which is still under construction. Here Spring recognizes that a circular reference may have occurred and you will get an error in this case. This problem can easily be solved by using Setter based injection because dependencies are not injected at the object creation time
- While using Constructor injection, you will have to remember the order of parameters in a constructor when the number of constructor parameters increases. This is not the case with Setter injection
- Constructor injection helps in creating immutable objects, because a bean object is created using constructor and once the object is created, its dependencies cannot be altered anymore. Whereas with Setter injection, it’s possible to inject dependency after object creation which leads to mutable objects.

Use constructor-based injection, when you want your class to not even be instantiated if the class dependencies are not resolved because Spring container will ensure that all the required dependencies are passed to the constructor.

---

## BeanFactory and ApplicationContext

The differences are:

- BeanFactory is the most basic version of IOC containers which should be preferred when memory consumption is critical whereas ApplicationContext extends BeanFactory, so you get all the benefits of BeanFactory plus some advanced features for enterprise applications
- BeanFactory instantiates beans on-demand i.e. when the method getBean(beanName) is called, it is also called Lazy initializer whereas ApplicationContext instantiates beans at the time of creating the container where bean scope is Singleton, so it is an Eager initializer
- BeanFactory only supports 2 bean scopes, singleton and prototype whereas ApplicationContext supports all bean scopes
- ApplicationContext automatically registers BeanFactoryPostProcessor and BeanPostProcessor at startup, whereas BeanFactory does not register these interfaces automatically
- Annotation based dependency injection is not supported by BeanFactory whereas ApplicationContext supports it
- If you are using plain BeanFactory, features like transactions and AOP will not take effect (not without some extra steps), even if nothing is wrong with the configuration whereas in ApplicationContext, it will work
- ApplicationContext provides additional features like MessageSource access (i18n or Internationalization) and Event Publication

Use an ApplicationContext unless you have a really good reason for not doing so.

---

## Spring Bean life-cycle

Spring beans are java classes that are managed by Spring container and the bean life-cycle is also managed by Spring container.

The bean life-cycle has below steps:
- Bean instantiated by container
- Required dependencies of this bean are injected by container
- Custom Post initialization code to be executed (if required)
- Bean methods are used
- Custom Pre destruction code to be executed (if required)

When you want to execute some custom code that should be executed before the bean is in usable state, you can specify an init() method and if some custom code needs to be executed before the bean is destroyed, then a destroy() method can be specified.
There are various ways to define these init() and destroy() method for a bean:

By using xml file, bean tag has 2 attributes that can be used to specify its init  and destroy methods, You can give any name to your initialization and destroy methods, and here is our Test class


```java
package com.demo;
public Class Test{
    public void init() throws Exception{
        System.out.prinln("Init Method");
    }
    public void destroy() throws Exception{
        System.out.prinln("Destroy Method");
    }
}
```


By implementing InitializingBean and DisposableBean interfaces

InitializingBean interface has afterPropertiesSet() method which can be used to execute some initialization task for a bean and DisposableBean interface has a destroy() method which can be used to execute some cleanup task.

Here is our Test class,

```java
package com.demo;


```

---

## Spring Bean Scopes

Spring framework supports 5 scopes:
- **singleton** – only one bean instance per Spring IOC container
- **prototype** – it produces a new instance each and every time a bean is requested
- **request** – a single instance will be created and made available during complete life-cycle of an HTTP request
- **session** – a single instance will be created and made available during complete life-cycle of an HTTP session
- **global session** – a single instance will be created during the life-cycle of a ServletContext

`@Scope` annotation or scope attribute of bean tag can be used to define bean scopes in Spring.

Default scope of a bean is `Singleton` that means only one instance per context.

### What happens when we inject a prototype scope bean in a singleton scope bean?

When you define a bean scope to be singleton, that means only one instance will be created and whenever we request for that bean, that same instance will be returned by the Spring container, however, a prototype scoped bean returns a new instance every time it is requested.

Spring framework gets only one chance to inject the dependencies, so if you try to inject a prototyped scoped bean inside a singleton scoped bean, Spring will instantiate the singleton bean and will inject one instance of prototyped scoped bean. This one instance of prototyped scoped bean is the only instance that is ever supplied to the singleton scoped bean.

So here, whenever the singleton bean is requested, `you will get the same instance of prototyped scoped bean`.

### How to inject a prototype scope bean in a singleton scope bean?

We have discussed in the previous question that when a prototyped scoped bean is injected in a singleton scoped bean, then on each request of singleton bean, we will get the same instance of prototype scoped bean, but there are certain ways where we can get a new instance of prototyped scoped bean also.

The solutions are:
- Injecting an ApplicationContext in Singleton bean and then getting the new instance of prototyped scoped bean from this ApplicationContext
- Lookup method injection using @Lookup
- Using scoped proxy

**Injecting ApplicationContext:**

To inject the ApplicationContext in Singleton bean, we can either use @Autowired annotation or we can implement ApplicationContextAware interface,

```java
package com.demo;

import org.springframework.beans.BeansException;
import org.springframework.context.ApplicationContextAware;
import org.springframework.context.ApplicationContext;
import org.springframework.sterotype.Component;

@Component
public class SingletonBean implements ApplicationContextAware{
    
    private ApplicationContext applicationContext;
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException{
        this.applicationContext=applicationContext;
    }

    public PrototypeBeann getProtoTypeBean(){
        return. applicationContext.getBean(PrototypeBean.class);
    }
}

```

Here, whenever the getPrototypeBean() method is called, it will return a new instance of PrototypeBean.
But this approach contradicts with Spring IOC (Inversion of Control), as we are requesting the dependencies directly from the container.



**Lookup Method Injection using @Lookup:**

```java
package com.demo;

import org.springframework.beans.factory.annotations.Lookup;
import org.springframework.sterotype.Component;

@Component
public class SingletonBean {
    @Lookup
    public PrototypeBeann getProtoTypeBean(){
        return null;
    }
}

```

Here, Spring will dynamically overrides getPrototypeBean() method annotated with @Lookup and it will look up the bean which is the return type of this method. Spring uses CGLIB library to do this.

**Using Scoped Proxy**

```java
package com.demo;

import org.springframework.beans.factory.ConfigurableBeanFactory;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Scope;
import org.springframework.context.annotation.ScopedProxyMode;
import org.springframework.sterotype.Component;

import java.beans.BeanProperty;

@Component
public class SingletonBean {

    private ApplicationContext applicationContext;

    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
        this.applicationContext = applicationContext;
    }

    @Bean
    @Scope(value=ConfigurableBeanFactory.ScopedProxyMode,
    proxyMode=ScopedProxyMode.TARGET_CLASS)
    public PrototypeBean getProtoTypeBean() {
        return new PrototypeBean();
    }
}

```

Spring uses CGLIB to create the proxy object and the proxy object delegates method calls to the real object. In the above example, we are using ScopedProxyMode.TARGET_CLASS which causes an AOP proxy to be injected at the target injection point. The default Proxy mode is ScopedProxyMode.NO .

To avoid CGLIB usage, configure the proxy mode with ScopedProxyMode.INTERFACES and it will use JDK dynamic proxy.

---

## Stereotype Annotations


`@Component`, `@Controller`, `@Service` and `@Repository` annotations are called stereotype annotations and they are present in org.springframework.stereotype package.

@Component: it is a general purpose stereotype annotation which indicates that the class annotated with it, is a spring managed component.

@Controller, @Service and @Repository are special types of @Component, these 3 themselves are annotated with @Component,

```java
package org.springframework.stereotype;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Indexed
public @interface Component {
    String value() default "";
} 
```

```java

package org.springframework.stereotype;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;
import org.springframework.core.annotation.AliasFor;

@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Component
public @interface Controller {
    @AliasFor(
            annotation = Component.class
    )
    String value() default "";
}
```




```java
package org.springframework.stereotype;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;
import org.springframework.core.annotation.AliasFor;

@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Component
public @interface Service {
    @AliasFor(
        annotation = Component.class
    )
    String value() default "";
}
```

```java

package org.springframework.stereotype;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;
import org.springframework.core.annotation.AliasFor;

@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Component
public @interface Repository {
    @AliasFor(
        annotation = Component.class
    )
    String value() default "";
}
```


So, the classes annotated with these annotations gets picked up in Component scanning and they are managed by Spring.

- **@Controller:** the classes annotated with `@Controller` will act as Spring MVC controllers. DispatcherServlet looks for `@RequestMapping` in classes that are annotated with `@Controller`. That means you cannot replace `@Controller` with `@Component`, if you just replace it with `@Component` then yes it will be managed by Spring but it will not be able to handle the requests.
  (Note: if a class is registered with Spring using `@Component`,  then @RequestMapping annotations within class can be picked up, if the class itself is annotated with @RequestMapping)

- **@Service:** The service layer classes that contain the business logic should be annotated with `@Service`. Apart from the fact that it is used to indicate that the class contains business logic, there is no special meaning to this annotation, however it is possible that Spring may add some additional feature to `@Service` in future, so it is always good idea to follow the convention.

- **@Repository:** The classes annotated with this annotation defines data repositories. It is used in DAO layer classes. @Repository has one special feature that it catches platform specific exceptions and re-throw them as one of the Spring’s unified unchecked exception i.e. `DataAccessException` .


---

## @Controller vs @RestController annotation

The differences are:

- `@Controller` annotation is used to mark a class as Spring MVC controller where the response is a view name which will display the Model object prepared by controller, whereas @RestController annotation is a specialization of @Controller and it is used in RESTful web services where the response is usually JSON/XML.
- `@RestController` is made up of 2 annotations, @Controller and @ResponseBody. @ResponseBody annotation is used to attach the generated output directly into the body of http response.
- `@Controller` can be used with @ResponseBody which will have same effect as @RestController. @ResponseBody annotation can be used at the class level or at the individual methods also. When it is used at the method level, Spring will use HTTP Message Converters to convert the return value to HTTP response body (serialize the object to response body).

---

## @Qualifier annotation

Let’s consider an example to understand @Qualifier annotation better. Suppose we have an interface called Shape and there are 2 classes Rectangle and Circle that are implementing this interface. We are autowiring our Shape interface in our controller class using @Autowired, now here a conflict will happen, because there are 2 beans of the same type.


```java
public interface Shape{

}

@Service 
public class Rectangle implements Shape{


}

@Service 
public class Circle implements Shape{

}


@RestController
public class ShapeCOntroller{


@Autowired
Shape shape;

}
```

When you try to start your application, you will get

```log
Could not autowire. There is more than one bean of 'Shape' type.
Beans:
circle (Circle.java) rectangle  (Rectangle.java) 
```

Now, to resolve this you can give names to your Rectangle and Circle class, like:


```java
public interface Shape{

}

@Service("rectangle")
public class Rectangle implements Shape{


}

@Service("circle") 
public class Circle implements Shape{

}
```

And you will use @Qualifier annotation to specify which bean should be autowired, like:
```java
@RestController
public class ShapeCOntroller{
    @Autowired
    @Qualifier("circle")
    Shape shape;
}
```

Now, Spring will not get confused as to what bean it has to autowire.
NOTE , you can also use @Qualifier annotation to give names to your Rectangle and Circle classes, like
```java
@RestController
public class ShapeCOntroller{
    @Autowired
    @Qualifier("rectangle")
    Shape shape;
}
```


---

## @Transactional annotation


Spring provides Declarative Transaction Management via `@Transactional` annotation. When a method is applied with `@Transactional`, then it will execute inside a database transaction. `@Transactional` annotation can be applied at the class level also, in that case, all methods of that class will be executed inside a database transaction.

**How @Transactional works:**

When `@Transactional` annotation is detected by Spring, then it creates a proxy object around the actual bean object. So, whenever the method annotated with `@Transactional` is called, the request first comes to the proxy object and this proxy object invokes the same method on the target bean. These proxy objects can be supplied with interceptors. Spring creates a TransactionInterceptor and passes it to the generated proxy object. So, when the `@Transactional` annotated method is called, it gets called on the proxy object first, which in turn invokes the TransactionInterceptor that begins a transaction. Then the proxy object calls the actual method of the target bean. When the method finishes, the TransactionInterceptor commits/rollbacks the transaction.

One thing to remember here is that the Spring wraps the bean in the proxy, the bean has no knowledge of it. So, only the external calls go through the proxy. As for the internal calls (`@Transactional` method calling the same bean method), they are called using ‘this’.
Using `@Transactional` annotation, the transaction’s propagation and isolation can be set directly, like:

```java

 @Transactional(propogation = Propogationn.REQUIRES_NEW,
        isolation = Isolation.READ_UNCOMMITTES
        rollbackFor = Exception.class)
 public String process(){
            return "Success";
        }
 
```
Also, you can specify a ‘rollbackFor’ attribute and specify which exception types must cause a transaction rollback (a transaction with Runtime exceptions and errors are by default rolled back).
If your process() method is calling another bean method, then you can also annotate that method with `@Transactional` and set the propagation level to decide whether this method should execute in the same transaction or it requires a new transaction.

---

## @ControllerAdvice annotation

`@ControllerAdvice` annotation is used to intercept and handle the exceptions thrown by the controllers across the application, so it is a global exception handler. You can also specify @ControllerAdvice for a specific package,

```java
@ControllerAdvice(basePackage = com.demo.controller")
public class Test{

}
```

Or a specific controller,
```java
@ControllerAdvice(assignableTypes=  = DemoController.class)
public class Test{

}
```

Or even a specific annotation,
```java
@ControllerAdvice(annotations=  = RestController.class)
public class Test{

}
```
`@ExceptionHandler` annotation is used to handle specific exceptions thrown by controllers, like,
```java
@ControllerAdvice
public class Test{
    ExceptioHandler(SQLException.class)
    public String handleSQLException(){
        return null;
    }
    
    ExceptioHandler(UserNotFoundException.class)
    public String handleUserNotFoundException(){
        return null;
    }
}
```

Here, we have defined a global exception handler using `@ControllerAdvice`. If a SQLException gets thrown from a controller, then `handleSQLException()` method will be called. In this method, you can customize the exception and send a particular error page/error code. Also, custom exceptions can be handled.

If you don’t want to create a global exception handler, then you can also define some `@ExceptionHandler` methods in a particular controller itself.

---

## @Bean annotation

`@Bean` annotation is used when you want to explicitly declare and register a bean into application context, so that it will be managed by Spring.

Some points to remember:
- When using `@Bean`, you have the control over the bean creation logic.
- `@Bean` is a method level annotation, the body of the method contains the logic for creating the bean instance and this method returns the instance which will be registered in the spring application context.
- Using `@Bean`, you can register the classes from 3rd party libraries into the application context
- `@Bean` annotation is usually declared in configuration classes.

---

## @Component vs @Bean annotation

The differences are:

- `@Component` auto-detects and configures the beans using classpath scanning, whereas @Bean explicitly declares a single bean rather than letting Spring do it automatically
- `@Component` is a class level annotation, whereas @Bean is a method level annotation
- `@Component` has different specializations called stereotype annotations like `@Controller`, `@Service` and @Repository, whereas @Bean has no specializations
- `@Bean` lets you create and configure beans exactly how you choose it to be, whereas in @Component, Spring has the control
- `@Bean` lets you configure classes from 3rd party libraries where you are not the owner of the source code, but you can’t use @Component in this case

---


## Spring Boot Security using OAuth2 with JWT


OAuth2 is an authorization framework superseding it first version OAuth, created back in 2006. It defines the authorization flows between clients and one or more HTTP services in order to gain access to protected resources.

The main goal of the OAuth2 framework is to provide a simple flow of authorization that can be implemented on the web application, mobile phones, desktop application, and even on the devices used in our living rooms.

OAuth2 defines the  server-side roles:

- **Resource Owner**: The service responsible for controlling resources’ access
- **Resource Server**: The service who actually supplies the resources
- **Authorization Server**: The service handling authorization process acting as a middleman between client and resource owner
- **JSON Web Token, or JWT**, is a specification for the representation of claims to be transferred between two parties. The claims are encoded as a JSON object used as the payload of an encrypted structure, enabling the claims to be digitally signed or encrypted.

### OAuth2 Terminology

- **Resource Owner** The user who authorizes an application to access his account. The access is limited to the `scope`.
- **Resource Server:** A server that handles authenticated requests after the `client` has obtained an `access token`.
- **Client** An application that access protected resources on behalf of the resource owner.
- **Authorization Server** A server which issues access tokens after successfully authenticating a `client` and `resource owner`, and authorizing the request.
- **Access Token** A unique token used to access protected resources
- **Scope** A Permission
- **JWT** JSON Web Token is a method for representing claims securely between two parties.
- **Grant type** A `grant` is a method of acquiring an access token.

### Json Web Token(JWT)


JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.a stateless authentication mechanism as the user state is never saved in server memory.A JWT token consists of 3 parts seperated with a dot(.) i.e. Header.payload.signature

Header has 2 parts type of token and hashing algorithm used.The JSON structure comprising these two keys are Base64Encoded.

```json
{
"alg": "HS256",
"typ": "JWT"
}
```
Payload contains the claims.Primarily, there are three types of claims: reserved, public, and private claims. Reserved claims are predefined claims such as iss (issuer), exp (expiration time), sub (subject), aud (audience).In private claims, we can create some custom claims such as subject, role, and others.

```json
{
"sub": "Alex123",
"scopes": [
{
"authority": "ROLE_ADMIN"
}
],
"iss": "http://devglan.com",
"iat": 1508607322,
"exp": 1508625322
}
```
Signature ensures that the token is not changed on the way.For example if you want to use the HMAC SHA256 algorithm, the signature will be created in the following way:

```log
HMACSHA256(
base64UrlEncode(header) + "." +
base64UrlEncode(payload),
secret)
```

sample JWT token
```log
eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJBbGV4MTIzIiwic2N.v9A80eU1VDo2Mm9UqN2FyEpyT79IUmhg
```

### Spring Boot Rest Authentication with JWT Token Flow

- Customers sign in by submitting their credentials to the provider.
- Upon successful authentication, it generates JWT containing user details and privileges for accessing the services and sets the JWT expiry date in payload.
- The server signs and encrypts the JWT if necessary and sends it to the client as a response with credentials to the initial request.
- Based on the expiration set by the server, the customer/client stores the JWT for a restricted or infinite amount of time.
- The client sends this JWT token in the header for all subsequent requests.
- The client authenticates the user with this token. So we don't need the client to send the user name and password to the server during each authentication process, but only once the server sends the client a JWT.

---

## Web server and  application server

| Web Server       | Application Server                         |
|-----------------|-----------------------------------|
| Supports HTTP protocol. When the Web server receives an HTTP request, it responds with an HTTP response, such as sending back an HTML page (static content) or delegates the dynamic response generation to some other program such as CGI scripts or Servlets or JSPs in the application server.        | Exposes business logic and dynamic content to the client through various protocols such as HTTP, TCP/IP, IIOP, JRMP etc.                            |
| Uses various scalability and fault-tolerance techniques.           | Uses various scalability and fault-tolerance techniques. In addition provides resource pooling, component life cycle management, transaction management, messaging, security etc.Provides services for components like Web container for servlet components and EJB container for EJB components.                    |

---

## Spring Transaction Management

> A transaction is a logical unit of work that either completely succeeds or fails. Think about a banking transaction. Here, the unit of work is money debiting from Account A and money crediting to Account B. If one of them fails, the entire process fails. We call it a rollback of all the steps in the transaction if anything fails in between.


### Global Transactions

There can be applications (very unlikely) where the transaction can happen between different databases. This is called distributed transaction processing. The transaction manager cannot sit within the application to handle it, rather it sits in the application server level. JTA or java transaction API is required with the support of JNDI to lookup different databases, and the transaction manager decides the commit or rollback of the distributed transaction. This is a complex process and requires knowledge at the application server level.

### Local Transactions

Local transactions happen between the application and a singled RDBMS, such as a simple JDBC connection. With local transaction, all the transaction code is within our code.

In both global and local transaction, we have to manage the transaction by ourselves. If I am using JDBC, then the transaction management API is for JDBC. If I am using Hibernate, then the hibernate transaction API and JTA at application server is for global transactions.


Spring framework overcomes all of the these problems by providing an abstraction over the different transaction APIs, providing a consistent programming model. The abstraction is via org.springframework.transaction.PlatformTransactionManager interface. Here is the snippet of the interface:

```java
public interface PlatformTransactionManager {
    TransactionStatus getTransaction(TransactionDefinition definition) throws TransactionException;

    void commit(TransactionStatus status) throws TransactionException;

    void rollback(TransactionStatus status) throws TransactionException;
}
```
There are various spring managed transaction managers that implement PlatformTransactionManager. Some of them are:

- **org.springframework.orm.jpa.JpaTransactionManager** — For JPA transactions
- **org.springframework.jdbc.datasource.DataSourceTransactionManager** — For JDBC transactions
- **org.springframework.orm.hibernate5.HibernateTransactionManager** — For Hibernate transactions and it binds with SessionFactory
- **org.springframework.transaction.jta.JtaTransactionManager** — For JTA transactions.
- **org.springframework.transaction.jta.WebLogicJtaTransactionManager** — For Oracle Weblogic managed transaction
- **org.springframework.transaction.jta.WebSphereUowTransactionManager** — For IBM Websphere Application Server managed transactions.
- **org.springframework.jms.connection.JmsTransactionManager** — For JMS messaging transaction by binding JMS connection factory.

Spring transactions can be managed by 2 approaches: programmatic and declarative.

### Programmatic Approach

Spring provides a programmatic approach in 2 ways :

1. Using the TransactionTemplate
2. Using a `PlatformTransactionManager` implementation directly

The programmatic approach is not widely used, as the transaction management sits with the business logic. In an application where we have transactions for a few CRUD operations, the programmatic approach is preferred as transaction proxies can be a heavy operation.


### Declarative Approach (@Transactional)

The declarative approach is widely used because transaction management stays out of business logic. It uses AOP proxies behind to drive transactions around method invocation with appropriate TransactionManager. It can be done either with annotation or with XML. But nowadays, most of the applications are annotation based, so I am covering how it works with the annotations.


- **1. Use `@EnableTransactionManagement`** at the top of the configuration class, which has `@Configuration` annotation. This is the same as the XML tag:

```xml
 <tx:annotation-driven transaction-manager="txManager"/>
```

```java
@Configuration
@EnableTransactionmanagement
public class SpringConfiguration{
...........
        ...........
} 
```

- **2. Define the datasource and transaction manager**

```java
    @Bean
     public FooRepository fooRepository() {
         // configure and return a class having @Transactional methods
         return new JdbcFooRepository(dataSource());
     }

     @Bean
     public DataSource dataSource() {
         // configure and return the necessary JDBC DataSource
     }

     @Bean
     public PlatformTransactionManager txManager() {
         return new DataSourceTransactionManager(dataSource());
     }
} 
```

- **3. Use the @Transactional annotation** above the methods and concrete classes. If applied at class level, all the methods will be by default transactional.

Let's try to understand how the annotation works with a simple example:

Assume we have a sample service lass

```java
 Class SampleService {
    @Transactional
    public void serviceMethod(){
        //call to dao layer 
    }
}
```

When SampleService is injected in another class, Spring will inject it in the below manner internally:

```java
 class ProxySampleService extends SampleService{
    private SampleService sampleService;
    public ProxySampleService(SampleService s){
        this.sampleService=s;
    }
    @Override
    public void sampleMethod(){
        try{
            //open transaction 
            sampleService.sampleMethod();
            //close transaction
        }
        catch(Exception e){
            //rollback
        }

    }

}
```

This is the proxy design that works behind the scenes.

Now let's see how we can fine tune the @Transactional annotation by changing the setting of the attributes.

Settings of the attributes in @Transactional annotation:

### propagation

Optional setting for propagation. This is a very important attribute in setting the transactional behavior. I will cover a use case of it below.
- **REQUIRED** — support a current transaction, create a new one if none exist
- **REQUIRES_NEW** — create a new transaction and suspend the current transaction if none exist
- **MANDATORY** — support a current transaction, throw an exception if none exists
- **NESTED** — executes within a nested transaction if a current transaction exists
- **SUPPORTS** — supports currents transaction but execute non-transactionally if none exists

### isolation

transaction isolation level. It decides the level to what the transaction should be isolated to other transactions
- **DEFAULT** — default isolation level of the datasource
- **READ_COMMITTED** — indicates dirty reads to be prevented, non-repeatable, and phantom reads can occur.
- **READ_UNCOMMITTED** — indicates that dirty reads, non-repeatable, and phantom reads can occur
- **REPEATABLE_READ** — indicates dirty and non-repeatable reads are prevented but phantom reads can occur
- **SERIALIZABLE** — indicates dirty read phantom read, and non-repeatable reads are prevented


we also have  other settings

- **readOnly** whether the transaction is read-only or read/write
- **timeout** — transaction timeout
- **rollbackFor** — arrays of exception class objects that must cause a rollback of the transaction
- **rollbackForClassName** — arrays of exception class names that must cause a rollback of the transaction
- **noRollbackFor** — arrays of exception class objects that must not cause a rollback of the transaction
- **noRollbackForClassName** — arrays of exception class names that must not cause a rollback of the transaction



---

## Misc Questions

### What happens if we use  service annotation on a repository class  in spring boot ?

If you annotate a repository class with the `@Service` annotation in Spring Boot, it will still be treated as a repository class. However, by convention, it is more common to use the `@Repository` annotation for DAO (Data Access Object) classes in Spring, as this provides a more clear indication of the class's purpose.

Annotating a repository class with @Service could lead to confusion and make it harder for other developers to understand the purpose of the class. Additionally, in a large codebase with many different types of classes, having clear, well-defined annotations can help with organization and maintainability.

That being said, if you annotate a repository class with `@Service`, it will still work as expected, since both `@Service` and `@Repository` are simply specializations of the `@Component` annotation, which tells Spring to include the class in component scanning and create a bean for it.



