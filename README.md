# Project-4
Project4-gilhari-simplifying-exchanging-of-json-data-with-an-rdbms-on-gcp


*Gilhari Simple Example*

Welcome to the Simple Example for the Gilhari product by Software Tree! This example demonstrates the basic usage of Gilhari for integrating REST APIs with relational databases.

Table of Contents

    Introduction
    Prerequisites
    Setup
    Running the Example
    Understanding the Code
    Troubleshooting
    Additional Resources

Introduction

Gilhari is a lightweight middleware solution that facilitates the integration of REST APIs with relational databases. It allows developers to map RESTful operations to database actions seamlessly. This simple example will guide you through the basic setup and demonstrate how to perform CRUD operations using Gilhari.
Prerequisites

Before you start, make sure you have the following installed:

    Java Development Kit (JDK) 8 or higher
    Apache Maven
    A relational database (e.g., MySQL, PostgreSQL)

Setup

    Clone the Repository: Clone the Gilhari repository to your local machine.

    sh

git clone https://github.com/SoftwareTree/gilhari.git

Navigate to the Simple Example Folder:

sh

cd gilhari/examples/simple-example

Configure the Database: Update the application.properties file with your database connection details.

properties

spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase
spring.datasource.username=root
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update

Build the Project:

sh

    mvn clean install

Running the Example

    Start the Application:

    sh

    mvn spring-boot:run

    Access the Application: The application will start on http://localhost:8080. You can use tools like curl or Postman to interact with the REST API.

Understanding the Code

This example includes the following components:

    Entity Classes: Represent the database tables.
    Repository Interfaces: Provide CRUD operations.
    Controller Classes: Handle HTTP requests and map them to database operations.
    Application Class: The main class that bootstraps the Spring Boot application.

Entity Class Example

java

@Entity
public class ExampleEntity {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private String description;

    // Getters and Setters
}

Repository Interface Example

java

public interface ExampleRepository extends JpaRepository<ExampleEntity, Long> {
}

Controller Class Example

java

@RestController
@RequestMapping("/api/examples")
public class ExampleController {

    @Autowired
    private ExampleRepository exampleRepository;

    @GetMapping
    public List<ExampleEntity> getAllExamples() {
        return exampleRepository.findAll();
    }

    @PostMapping
    public ExampleEntity createExample(@RequestBody ExampleEntity exampleEntity) {
        return exampleRepository.save(exampleEntity);
    }

    // Additional CRUD methods...
}

Troubleshooting

If you encounter issues, ensure that:

    Your database server is running and accessible.
    The application.properties file contains correct database configurations.
    You have installed all necessary dependencies using Maven.

Additional Resources

    Gilhari Documentation
    Spring Boot Documentation
    JPA Documentation
