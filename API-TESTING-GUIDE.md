# API Testing Guide

## Introduction
API testing is a critical part of software development that ensures APIs work as intended. This guide covers API testing using Postman and REST Assured.

## What is API Testing?
API testing involves testing application programming interfaces (APIs) directly to ensure they meet expectations in terms of functionality, reliability, performance, and security.

## Tools for API Testing
1. **Postman**
   - A popular API client to test web services.
   - Provides an interface for sending requests and viewing responses.

2. **REST Assured**
   - A Java library for testing RESTful APIs.
   - Provides a domain-specific language (DSL) for writing tests.

## Getting Started with Postman
### Installation
- Download and install Postman from [Postman Download](https://www.postman.com/downloads/).

### Creating Your First API Request
1. Open Postman.
2. Click on `+` to create a new tab.
3. Select the request type (GET, POST, PUT, DELETE) from the dropdown.
4. Enter the request URL.
5. Click on `Send` to execute the request.
6. View the response in the lower section of the interface.

### Writing Tests in Postman
- Use the built-in test scripting feature to validate responses.
- Example:
  ```javascript
  pm.test("Status code is 200", function () {
      pm.response.to.have.status(200);
  });
  ```

## Getting Started with REST Assured
### Setup
- Add the REST Assured dependency in your `pom.xml` file if you are using Maven:
  ```xml
  <dependency>
      <groupId>io.rest-assured</groupId>
      <artifactId>rest-assured</artifactId>
      <version>4.3.0</version>
      <scope>test</scope>
  </dependency>
  ```

### Writing Your First Test
```java
import io.restassured.RestAssured;
import org.junit.Test;
import static io.restassured.RestAssured.*;
import static org.hamcrest.Matchers.*;

public class ApiTest {
    @Test
    public void testGetEndpoint() {
        given()
            .baseUri("https://api.example.com")
            .when()
            .get("/endpoint")
            .then()
            .statusCode(200)
            .body("key", equalTo("value"));
    }
}
```

## Conclusion
API testing is essential for ensuring that web services function correctly. By using tools like Postman and REST Assured, you can efficiently test and validate your APIs. 

---