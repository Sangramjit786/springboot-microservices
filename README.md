# Spring Boot Microservices Architecture

A comprehensive microservices-based application demonstrating various Spring Cloud features and best practices.

## Project Overview

This project showcases a microservices architecture using Spring Boot and Spring Cloud, featuring independent, scalable services that communicate with each other to provide a complete organizational management solution.

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
