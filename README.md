# Spring Boot Microservices Architecture

A comprehensive microservices-based application demonstrating various Spring Cloud features and best practices.
This repository ([springboot-microservices](https://github.com/Sangramjit786/springboot-microservices.git)) demonstrates the development of a **microservices-based architecture** using **Spring Boot** and the **Spring Cloud ecosystem**.  
It covers essential patterns such as service discovery, API gateway, centralized configuration, inter-service communication, resilience patterns, distributed tracing, and frontend integration.  

---
## Project Architecture:
<img width="1620" height="725" alt="image" src="https://github.com/user-attachments/assets/6ec8170e-d108-4173-932f-5f4386133c2f" />

## Project Overview

This project showcases a microservices architecture using Spring Boot and Spring Cloud, featuring independent, scalable services that communicate with each other to provide a complete organizational management solution.
The system consists of multiple microservices:

- **department-service** – Manages department-related operations.
- **employee-service** – Manages employee-related operations and communicates with department-service and organization-service.
- **organization-service** – Represents the organizational structure by integrating employee and department data.
- **api-gateway** – A unified entry point for all services.
- **config-server** – Centralized configuration management using GitHub.
- **react-frontend** – A frontend UI to interact with the API Gateway.

---

## Key Features and Implementations

### 1. Initial Commit for Two Microservices
- Created **department-service** and **employee-service** as independent Spring Boot microservices.  
- Each service has **its own database** and isolated responsibilities following **microservices architecture principles**.

### 2. Global Exception Handling
- Implemented **centralized exception handling** with `@ControllerAdvice` and `@ExceptionHandler`.  
- Ensures **consistent error responses** across services and cleaner controller code.

### Different Synchronous ways of inter-service communication:
<img width="992" height="457" alt="image" src="https://github.com/user-attachments/assets/838723ce-4f7e-4788-92e4-f3b9168921b0" />

### 3. Synchronous Communication Using RestTemplate
- Integrated **inter-service communication** between employee-service and department-service using `RestTemplate`.  
- This provided a starting point, though it is considered a **legacy approach** in Spring.

### 4. Migration from RestTemplate to WebClient
- Replaced `RestTemplate` with **WebClient** (reactive, non-blocking, Spring 5+).  
- Improved **scalability** and **efficiency** in synchronous communications.

### 5. Inter-Service Communication with Spring Cloud OpenFeign
- Adopted **OpenFeign**, a declarative REST client.  
- Reduced boilerplate code for HTTP calls and improved **readability** and **maintainability**.

### Service Discovery Architecture:
<img width="907" height="463" alt="image" src="https://github.com/user-attachments/assets/b7c6fcd1-c8cc-41ea-9fb7-81ca6893b709" />

### 6. Service Discovery with Eureka
- Set up a **Eureka Server** for dynamic service discovery.  
- Registered employee-service and department-service as **Eureka clients**, removing the need for hardcoded URLs.

### 7. Load Balancing with Spring Cloud LoadBalancer
- Implemented **client-side load balancing** with OpenFeign and Spring Cloud LoadBalancer.  
- Requests are evenly distributed across multiple service instances, ensuring **high availability**.

### API Gateway Architecture:
<img width="1914" height="966" alt="Screenshot 2025-08-19 070908" src="https://github.com/user-attachments/assets/3abe1bc9-8931-4de1-a532-386cc7d9d4b7" />

### 8. API Gateway Configuration
- Built an **API Gateway** microservice using Spring Cloud Gateway.  
- Registered it with Eureka and configured manual routes for department-service and employee-service.  
- Verified end-to-end flow using **Postman**.

### 9. Dynamic Routing in API Gateway
- Configured **dynamic routing** in the API Gateway via Eureka.  
- New services are automatically registered without updating gateway routes manually.

### Config Server Flow:
<img width="996" height="503" alt="Screenshot 2025-08-19 071026" src="https://github.com/user-attachments/assets/7731fe76-e201-456f-88f0-510162d4beca" />

### 10. Config Server Setup
- Created a **config-server** using Spring Cloud Config.  
- Linked it to a **GitHub repository** to manage externalized configurations.  
- Registered config-server with Eureka.

### 11. Department-Service Integration with Config Server
- Externalized `application.properties` of department-service to the config repository.  
- Achieved **centralized configuration management**.

### 12. Employee-Service Integration with Config Server
- Applied the same externalization for employee-service.  
- Ensured consistency and **easy updates** via GitHub-managed configuration.

### 13. Auto-Refresh Configuration Using Spring Cloud Bus
- Enabled **real-time config updates** with Spring Cloud Bus and **RabbitMQ in Docker**.  
- Eliminated the need for manual `/actuator/refresh` calls.

### Distributed Tracing Flow:
<img width="922" height="410" alt="image" src="https://github.com/user-attachments/assets/4ea89187-3889-44e4-b8fa-f93acc911931" />

### Distributed Tracing Implementation:
<img width="938" height="493" alt="image" src="https://github.com/user-attachments/assets/9c5bb33e-c1c3-4c86-bfd6-127d801211fe" />

### 14. Distributed Tracing with Micrometer
- Integrated **Micrometer** to collect metrics and traces.  
- Enabled better **monitoring**, **debugging**, and **performance analysis** in a distributed environment.

### Circuit Breaker Pattern Implementation:
<img width="912" height="427" alt="image" src="https://github.com/user-attachments/assets/0e44c545-2569-4b4f-a535-04edd6eed22a" />

### 15. Circuit Breaker with Resilience4j
- Implemented **circuit breaker** patterns using Resilience4j.  
- Prevented cascading failures by **short-circuiting calls** to unresponsive services.

### 16. Retry Mechanism with Resilience4j
- Configured **retry logic** for transient failures.  
- Automatically retries failed calls before giving up, improving **fault tolerance**.

### 17. Organization-Service Creation
- Introduced **organization-service** to aggregate employee and department data.  
- Strengthened the domain model with an **organizational perspective**.

### 18. Communication between Employee and Organization Services
- Established **WebClient-based communication** from employee-service to organization-service.  
- Followed **non-blocking I/O practices**.

### 19. Externalizing Organization-Service Configurations
- Externalized organization-service configurations into the config repository.  
- Ensured a **unified and version-controlled configuration** across all services.

### 20. React Frontend Integration
- Developed a **React frontend** integrated with the API Gateway.  
- Displayed **consolidated data** (user, department, organization) via unified endpoints.

### 21. API Documentation with SpringDoc OpenAPI
- Integrated **SpringDoc OpenAPI** in all services.  
- Provided **Swagger UI** for API documentation, simplifying **API exploration** and **testing**.

---

## Tech Stack

- **Backend**: Spring Boot, Spring Cloud (Eureka, Config, Gateway, LoadBalancer, OpenFeign, WebClient)  
- **Resilience**: Resilience4j (Circuit Breaker, Retry)  
- **Message Broker**: RabbitMQ (via Docker)  
- **Tracing & Metrics**: Micrometer  
- **Frontend**: React  
- **Config Management**: GitHub-based Config Server  
- **API Documentation**: SpringDoc OpenAPI (Swagger UI)  

---

## Key Features

### 1. Core Microservices
- **Department Service**: Manages department-related operations
- **Employee Service**: Handles employee data and operations
- **Organization Service**: Provides organizational structure and relationships

### 2. Architecture Components
- **Service Discovery**: Spring Cloud Netflix Eureka for dynamic service registration and discovery
- **API Gateway**: Spring Cloud Gateway for routing and API composition
- **Configuration Server**: Centralized configuration management with Spring Cloud Config
- **Distributed Tracing**: Integrated with Micrometer for observability
- **Circuit Breaker**: Resilience4j for fault tolerance

### 3. Communication Patterns
- **Synchronous**: REST APIs with OpenFeign and WebClient
- **Asynchronous**: Event-driven communication
- **Load Balanced**: Client-side load balancing with Spring Cloud LoadBalancer

### 4. Development & Operations
- **API Documentation**: SpringDoc OpenAPI (Swagger) integration
- **Configuration Management**: Git-based configuration with auto-refresh
- **Frontend**: React-based UI integrated with the API Gateway

## Getting Started

### Prerequisites
- Java 21+
- Maven 3.6+
- Docker (for RabbitMQ, Zipkin)
- Node.js & npm (for React frontend)

### Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone [https://github.com/Sangramjit786/springboot-microservices.git](https://github.com/Sangramjit786/springboot-microservices.git)
   cd springboot-microservices
     ```


2. **Start the services**:
```bash
# Start Eureka Server
mvn spring-boot:run -pl service-registry

# Start Config Server
mvn spring-boot:run -pl config-server

# Start other services
mvn spring-boot:run -pl department-service
mvn spring-boot:run -pl employee-service
mvn spring-boot:run -pl organization-service
mvn spring-boot:run -pl api-gateway
```

3. **Access the applications**:
- Eureka Dashboard: http://localhost:8761
- API Gateway: http://localhost:9191
- Swagger UI: http://localhost:8080/swagger-ui.html (for each service)
  
### Technical Implementation Details
1. **Service Discovery with Eureka**
- Dynamic registration and discovery of microservices
- Heartbeat mechanism for service health monitoring

2. **API Gateway**
- Dynamic routing configuration
- Request/Response transformation
- Cross-cutting concerns (Authentication, Logging)

3. **Centralized Configuration**
- Git-based configuration management
- Profile-specific properties
- Auto-refresh with Spring Cloud Bus and RabbitMQ

4. **Resilience Patterns**
- Circuit breaking with Resilience4j
- Retry mechanisms for transient failures
- Bulkhead pattern for resource isolation

5. **Observability**
- Distributed tracing with Micrometer and Zipkin
- Health check endpoints
- Metrics collection and monitoring

### Project Structure
```
springboot-microservices/
├── api-gateway/          # API Gateway service
├── config-server/        # Configuration server
├── department-service/   # Department microservice
├── employee-service/     # Employee microservice
├── organization-service/ # Organization microservice
├── service-registry/     # Eureka server
└── react-frontend/       # React-based UI
```

### API Documentation
Each service exposes its API documentation through Swagger UI:
- Department Service: http://localhost:8080/swagger-ui.html
- Employee Service: http://localhost:8082/swagger-ui.html
- Organization Service: http://localhost:8083/swagger-ui.html

