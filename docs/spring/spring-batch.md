---
layout: default
title: Spring Batch
parent: Spring
resource: true
desc: "Spring Batch interview questions and answers."
categories: [Spring Batch]
---

# Spring Batch
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

##  Introduction to Spring Batch

Spring Batch provides reusable functions that are essential in processing large volumes of records, including logging/tracing, transaction management, job processing statistics, job restart, skip, and resource management. It also provides more advanced technical services and features that will enable extremely high-volume and high performance batch jobs through optimization and partitioning techniques. Simple as well as complex, high-volume batch jobs can leverage the framework in a highly scalable manner to process significant volumes of information.

###  Features
- Transaction management
- Chunk based processing
- Declarative I/O
- Start/Stop/Restart
- Retry/Skip
- Web based administration interface (Spring Cloud Data Flow)


###  spring batch components

Spring Batch is a framework for batch processing in the Spring framework. It provides reusable functions for processing large volumes of data in batch jobs. The main components of Spring Batch include:

1. Job: A job is a batch process that is made up of one or more steps.

2. Step: A step is a single unit of work that is executed as part of a job. It can be as simple as reading data from a file and writing it to a database, or as complex as performing multiple tasks in parallel.

3. ItemReader: An ItemReader reads data from a source and provides it to the ItemProcessor.

4. ItemProcessor: An ItemProcessor processes the data read by the ItemReader and returns the processed data.

5. ItemWriter: An ItemWriter writes the processed data to a destination.

6. JobRepository: A JobRepository is responsible for maintaining the state of a job and its steps.

7. JobLauncher: A JobLauncher is used to launch a job.

8. JobExplorer: A JobExplorer allows you to access information about past execution of a job.

9. JobRegistry: A JobRegistry is used to register jobs with the batch infrastructure.

10. JobParameters: JobParameters are used to pass data to a job at runtime.

These are the main components of Spring Batch, there are many other components that can be used to customize and extend the functionality of the framework.

It provides reusable functions that are essential in processing large volumes of records, including logging/tracing, transaction management, job processing statistics, job restart, skip, and resource management.

The architecture of Spring Batch consists of three main components:

**Job:** A job represents a batch process that is executed. It is composed of one or more steps, and each step contains a reader, a processor, and a writer.

**Step:** A step is a domain object that represents an independent, sequential phase of a job and contains a reader, a processor, and a writer.

**Item:** An item represents a single record that is read, processed, and written. Spring Batch provides support for reading and writing items in various formats, including XML, CSV, and database.

In addition to these components, Spring Batch also provides a JobRepository, which is responsible for maintaining the state of the job and its execution status, and a JobLauncher, which is responsible for starting and stopping the job.

Spring Batch also provides a number of built-in components, such as readers, processors, and writers for handling common data formats and tasks, as well as an extensible API for building custom components.


###  Example of how to use Spring Batch

Here's an example of how to use Spring Batch with Spring Boot to read data from a CSV file, process it, and then write it to a database:

1.  First, create a Spring Boot application with the Spring Batch and Spring Data dependencies.

2. Create a batch configuration class that sets up the batch job and the necessary steps.  



```java

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.core.io.ClassPathResource;

@Configuration
public class BatchConfig {
    @Autowired
    private JobBuilderFactory jobBuilderFactory;

    @Autowired
    private StepBuilderFactory stepBuilderFactory;

    @Bean
    public Job readCSVFileJob() {
        return jobBuilderFactory
                .get("readCSVFileJob")
                .start(step1())
                .build();
    }

    @Bean
    public Step step1() {
        return stepBuilderFactory
                .get("step1")
                .<Person, Person>chunk(5)
                .reader(reader())
                .processor(processor())
                .writer(writer())
                .build();
    }



    @Bean
    public PersonItemProcessor processor() {
        return new PersonItemProcessor();
    }

    @Bean
    public JdbcBatchItemWriter<Person> writer() {
        JdbcBatchItemWriter<Person> writer = new JdbcBatchItemWriter<>();
        writer.setDataSource(dataSource);
        writer.setSql("INSERT INTO people (first_name, last_name) VALUES (:firstName, :lastName)");
        writer.setItemSqlParameterSourceProvider(new BeanPropertyItemSqlParameterSourceProvider<>());
        return writer;
    }



}   
```

3. Create a class that represents the data you're reading from the CSV file and a class that handles the processing of the data.

```java
public class Person {
    private String firstName;
    private String lastName;
    // getters and setters
}

public class PersonItemProcessor implements ItemProcessor<Person, Person> {
    @Override
    public Person process(final Person person) throws Exception {
        final String firstName = person.getFirstName().toUpperCase();
        final String lastName = person.getLastName().toUpperCase();
 
        final Person transformedPerson = new Person(firstName, lastName);
        return transformedPerson;
    }
}


```

4. Finally, run the job by creating a `CommandLineRunner` that calls the `jobLauncher.run()` method and passing in the job name as a parameter.


```java

@SpringBootApplication
public class Application implements CommandLineRunner {
    @Autowired
    JobLauncher jobLauncher;
    @Autowired
    Job job;
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
    @Override
    public void run(String... args) throws Exception {
        JobExecution execution = jobLauncher.run(job, new JobParameters());
        System.out.println("Job Exit Status : "+ execution.getStatus());
    }
}


```

This is a basic example of how Spring Batch and Spring Boot can be used to perform batch processing. I








