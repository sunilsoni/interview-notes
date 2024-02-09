---
layout: default
title: Spring Data JPA
parent: Spring
resource: true
desc: "Spring Data JPA interview questions and answers."
categories: [ Spring Data JPA]
---

# Spring Data JPA
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

When you implement a new application, you should focus on the business logic instead of technical complexity and boilerplate code. That’s why the Java Persistence API (JPA) specification and Spring Data JPA are extremely popular. JPA handles most of the complexity of JDBC-based database access and object-relational mappings. On top of that, Spring Data JPA reduces the amount of boilerplate code required by JPA. That makes the implementation of your persistence layer easier and faster.

## What is JPA?

JPA or Java Persistence API is the Java specification for accessing, managing and persisting data between Java classes or objects and relational database. The specification was introduced as part of EJB 3.0.

JPA is not an implementation or product, it is just a specification. It contains set of interfaces which need to be implemented. It is a framework that provides an extra layer of abstraction on the JPA implementation. The repository layer will contain three layers as mentioned below.

**Spring Data JPA**: – This provides spring data repository interfaces which are implemented to create JPA repositories.

**Spring Data Commons**: – It provides the infrastructure that is shared between data store specific spring data projects.

**The JPA provider** which implements the JPA persistence API. Hibernate, Eclipselink, Toplink, Spring Data JPA, etc.


Spring data JPA allows us not to write any boilerplate code by adding an additional repository layer.

##  JPA Vs Hibernate


| Category | JPA | Hibernate | 
|--------|------|-----------|
|  Type      | JPA is a specification and defines the way to manage relational database data using java objects.     | Hibernate is an implementation of JPA. It is an ORM tool to persist java objects into the relational databases.         | 
| Package   | JPA uses javax.persistence package.	  | Hibernate uses org.hibernate package.| 
| Factory   | JPA uses EntityManagerFactory interface to get the entity manager to persist objects.  | Hibernate uses SessionFactory interface to create session object which is then used to persist objects.          | 
|  CRUD Operations  |JPA uses EntityManager interface to create/read/delete operation and maintains the persistence context.   |Hibernate uses Session interface to create/read/delete operation and maintains the persistence context.           | 
| Language   | JPA uses JPQL (Java Persistence Query Language) as Object Oriented Query language for database operations.  |  Hibernate uses HQL (Hibernate Query Language) as Object Oriented Query language for database operations.         | 


##  Features

### No-code Repositories

The repository pattern is one of the most popular persistence-related patterns. It hides the data store specific implementation details and enables you to implement your business code on a higher abstraction level.

Implementing that pattern isn’t too complicated but writing the standard CRUD operations for each entity creates a lot of repetitive code. Spring Data JPA provides you a set of repository interfaces which you only need to extend to define a specific repository for one of your entities.

###  Reduced boilerplate code
To make it even easier, Spring Data JPA provides a default implementation for each method defined by one of its repository interfaces. That means that you no longer need to implement basic read or write operations. And even so all of these operations don’t require a lot of code, not having to implement them makes life a little bit easier and it reduces the risk of stupid bugs.

###  Generated queries

Another comfortable feature of Spring Data JPA is the generation of database queries based on method names. As long as your query isn’t too complex, you just need to define a method on your repository interface with a name that starts with find…By. Spring then parses the method name and creates a query for it.

Here is a simple example of a query that loads a Book entity with a given title. Internally, Spring generates a JPQL query based on the method name, sets the provided method parameters as bind parameter values, executes the query and returns the result.

```java
public interface BookRepository extends CrudRepository<Book, Long> {
    Book findByTitle(String title);
}
```

## Repositories in Spring Data JPA

Spring Data Commons project provides repository abstraction which is extended by the datastore-specific subprojects.

We have to be familiar with the Spring Data repository interfaces as it will help us with the implementation of the interfaces. Let’s have a look at the interfaces.

###  Spring Data Commons

Following interfaces are provided as part of this project:

**Repository<T, ID extends Serializable>**  : 
This interface is a marker interface.
- It captures the type of the managed entity and the type of the entity’s id.
- It helps the Spring container to discover the “concrete” repository interfaces when classpath is scanned.

**CrudRepository<T, ID extends Serializable>** : 
- It provides CRUD operations for the managed entity.
- CrudRepository interface defines a repository that offers standard create, read, update and delete operations.

**PagingAndSortingRepository<T, ID extends Serializable>** : 
- This interface declares the methods that are used to sort and paginate entities that are retrieved from the database.
- The PagingAndSortingRepository extends the CrudRepository and adds findAll methods that enable you to sort the result and to retrieve it in a paginated way. Both interface are also supported by other Spring Data projects, so that you can apply the same concepts to different datastores.

**QueryDslPredicateExecutor<T>:** 
- It is not a `repository interface`. 
- It declares the methods that are used to retrieve entities from the database by using QueryDsl Predicate objects.


###  Spring Data JPA
This project provides the following interfaces:

**JpaRepository<T, ID extends Serializable>**  : 
- This interface is a JPA specific repository interface that combines the methods declared by the common repository interfaces behind a single interface.
- The JpaRepository adds JPA-specific methods, like flush() to trigger a flush on the persistence context or `findAll(Example<S> example)` to find entities by example, to the PagingAndSortingRepository.

**JpaSpecificationExecutor<T>** : 
- This is again not a repository interface. 
- It declares the methods that are used to retrieve entities from the database by using `Specification<T>` objects that use the JPA criteria API.

The repository hierarchy looks as follows:

<img src="images/JpaRepositoryUml.png" width="1000" />


##  Example Using Spring Boot

###  Maven Dependency

We can also use the Spring Boot Starter Data JPA dependency that will automatically configure the DataSource for us.

We need to make sure that the database we want to use is present in the classpath. In our example, we've added the H2 in-memory database:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
    <version>2.6.1</version>
</dependency>
<dependency>
<groupId>com.h2database</groupId>
<artifactId>h2</artifactId>
<version>1.4.200</version>
</dependency>
```

As a result, just by doing these dependencies, our application is up and running and we can use it for other database operations.

The explicit configuration for a standard Spring application is now included as part of Spring Boot auto-configuration.

We can, of course, modify the auto-configuration by adding our customized explicit configuration.

###  Properties file

Spring Boot provides an easy way to do this using properties in the application.properties file:

```properties
spring.datasource.url=jdbc:h2:mem:db;DB_CLOSE_DELAY=-1
spring.datasource.username=sa
spring.datasource.password=sa
```

or for postgres

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/postgres
spring.datasource.username=postgres
spring.datasource.password=password
spring.jpa.generate-ddl=true
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```



In this example, we've changed the connection URL and credentials.

###  Spring Data JPA Repository Configuration

To activate the Spring JPA repository support, we can use the @EnableJpaRepositories annotation and specify the package that contains the DAO interfaces:

```java
@Configuration
@EnableJpaRepositories
@EnableTransactionManagement
class ApplicationConfig {

    @Bean
    public DataSource dataSource() {

        EmbeddedDatabaseBuilder builder = new EmbeddedDatabaseBuilder();
        return builder.setType(EmbeddedDatabaseType.HSQL).build();
    }

    @Bean
    public LocalContainerEntityManagerFactoryBean entityManagerFactory() {

        HibernateJpaVendorAdapter vendorAdapter = new HibernateJpaVendorAdapter();
        vendorAdapter.setGenerateDdl(true);

        LocalContainerEntityManagerFactoryBean factory = new LocalContainerEntityManagerFactoryBean();
        factory.setJpaVendorAdapter(vendorAdapter);
        factory.setPackagesToScan("com.acme.domain");
        factory.setDataSource(dataSource());
        return factory;
    }

    @Bean
    public PlatformTransactionManager transactionManager(EntityManagerFactory entityManagerFactory) {

        JpaTransactionManager txManager = new JpaTransactionManager();
        txManager.setEntityManagerFactory(entityManagerFactory);
        return txManager;
    }
}
```

The preceding configuration class sets up an embedded HSQL database by using the EmbeddedDatabaseBuilder API of spring-jdbc. Spring Data then sets up an EntityManagerFactory and uses Hibernate as the sample persistence provider. The last infrastructure component declared here is the JpaTransactionManager. Finally, the example activates Spring Data JPA repositories by using the @EnableJpaRepositories annotation, which essentially carries the same attributes as the XML namespace. If no base package is configured, it uses the one in which the configuration class resides.

###  Repository Interface  
The repository interface is used for extending the CRUD interface. This interface adds the layer of a repository in the program. Spring Data JPA provides two major ways of creating queries. These queries are then used in the repository interface to fetch the data from the database.

```java
import java.util.List;
 
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.CrudRepository;
import org.springframework.data.repository.query.Param;
import org.springframework.stereotype.Repository;
 
import com.tutorial.model.Employee;
 
@Repository
public interface EmployeeRepository extends CrudRepository<Employee, Long>{
    List findByLastName(String lastName);
     
@Query("SELECT e FROM Employee e WHERE e.age = :age")
    public List findByAge(@Param("age") int age);
}

```

The `CrudRepository` is the interface from SpringData Common project. The two methods mentioned above for query creation is used at the below-mentioned places in the code.

### Controller class

The controller is the most important class of the complete program. This is the class responsible for all the url mapping. We have added the repository methods for data manipulation in this class itself.

```java
import java.util.List;
import java.util.Optional;
 
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;
 
import com.tutorial.model.Employee;
import com.tutorial.repo.EmployeeRepository;
 
@RestController
@RequestMapping("/employee")
public class WebController {
    @Autowired
    EmployeeRepository repository;
     
    @RequestMapping(value="/save",method = RequestMethod.POST)
    public HttpStatus insertEmployee(@RequestBody Employee employee){
        boolean status = repository.save(employee) != null;     
        return status? HttpStatus.CREATED : HttpStatus.BAD_REQUEST;
    }
     
     
    @RequestMapping("/findall")
    public List findAll(){
         
         
        return (List) repository.findAll();
    }
     
    @RequestMapping("/findbyid")
    public Optional findById(@RequestParam("id") long id){
        Optional result = repository.findById(id);
        return result;
    }
     
    @RequestMapping("/findbylastname")
    public List fetchDataByLastName(@RequestParam("lastname") String lastName){
                 
        return repository.findByLastName(lastName);
    }
    @RequestMapping("/findbyage")
    public List fetchDataByAge(@RequestParam("age") int age){
                 
        return repository.findByAge(age);
    }
}


```




---

## More Details: 
1. [What is Spring Data JPA? And why should you use it?](https://thorben-janssen.com/what-is-spring-data-jpa-and-why-should-you-use-it/)
2. [5. Reference Documentation](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#reference)