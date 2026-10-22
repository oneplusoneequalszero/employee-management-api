# Employee Management REST API

A Spring Boot REST API for managing employees, built with a layered architecture
(Controller → Service → Repository → Entity, with DTOs and a global exception handler).

## Tech Stack
Java 21, Spring Boot 4.1.1, Spring Data JPA (Hibernate), Bean Validation, MySQL, Maven, WAR packaging, JUnit 5 + Mockito.

## Architecture
- `controller` – HTTP endpoints only
- `service` – business logic and DTO/entity mapping
- `repository` – database access (Spring Data JPA)
- `entity` – JPA entities mapped to tables
- `dto` – request/response objects (entities are never exposed directly)
- `exception` – custom exceptions + `@RestControllerAdvice` global handler

## Setup
1. Install Java 21, MySQL, Maven (or use the IDE's embedded Maven).
2. Create the database: `CREATE DATABASE employee_db;`
3. Edit `src/main/resources/application.properties` with your MySQL username and password.
4. Run: `mvn spring-boot:run` or run the main class from Eclipse.
5. The API runs on `http://localhost:8080`. Tables are created automatically.

## Database Configuration
```
spring.datasource.url=jdbc:mysql://localhost:3306/employee_db
spring.datasource.username=root
spring.datasource.password=<your password>
spring.jpa.hibernate.ddl-auto=update
```

## Endpoints
| Method | URL | Description |
|---|---|---|
| POST | /api/employees | Create employee (201) |
| GET | /api/employees | List employees. Optional: `keyword`, `status`, `page`, `size` |
| GET | /api/employees/{id} | Get one employee |
| PUT | /api/employees/{id} | Update employee |
| DELETE | /api/employees/{id} | Delete employee (204) |

## Validation Rules
firstName, lastName, department: required; email: required and valid format, unique; salary: required and positive.

## Error Responses
400 (validation / bad input), 404 (not found), 409 (duplicate email), 500 (unexpected).

## Sample Request / Response
(See the examples in `postman/` or below.)

## API Docs
A Postman collection is in `/postman`.
