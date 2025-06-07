1. Initial Commit for Two Microservices: 
Created two independent Spring Boot microservices: department-service and employee-service. These services follow the microservices architecture, each having its own isolated responsibilities and database.

2. Global Exception Handling: 
Implemented centralized exception handling using @ControllerAdvice and @ExceptionHandler in both services. This ensures consistent error responses and cleaner controller logic.

3. Synchronous Communication Using RestTemplate: 
Integrated synchronous inter-service communication between employee-service and department-service using Spring’s RestTemplate. Although functional, it’s considered a legacy approach in modern Spring applications.

4. Migration from RestTemplate to WebClient: 
Replaced RestTemplate with WebClient, which is the non-blocking, reactive alternative recommended in Spring 5+. This improved efficiency and scalability for synchronous communication.

5. Inter-Service Communication with Spring Cloud OpenFeign: 
Further improved inter-service communication by adopting Spring Cloud OpenFeign, which abstracts HTTP calls via declarative REST clients, reducing boilerplate code and improving readability.

6. Service Discovery with Eureka: 
Set up Spring Cloud Netflix Eureka Server for dynamic service discovery. Registered both department-service and employee-service as Eureka clients, enabling runtime discovery of services without hardcoded URLs.

7. Load Balancing with Spring Cloud LoadBalancer: 
Implemented client-side load balancing using Spring Cloud LoadBalancer with OpenFeign. This ensured even distribution of requests across service instances, enhancing fault tolerance.

8. API Gateway Configuration: 
Created an api-gateway microservice using Spring Cloud Gateway. Registered it as an Eureka client and manually configured routes to department-service and employee-service. Used Postman for end-to-end testing.

9. Dynamic Routing in API Gateway: 
Replaced manual route configuration in the API Gateway with dynamic route discovery using Spring Cloud Gateway and Eureka. This allows automatic registration of new services without code changes.

10. Config Server Setup: 
Developed a centralized configuration microservice (config-server) using Spring Cloud Config. Connected it to a GitHub repo to manage externalized configurations and registered it with Eureka.

11. Department-Service Integration with Config Server: 
Refactored department-service to externalize its application.properties file to the GitHub repository used by the config-server, enabling centralized configuration management.

12. Employee-Service Integration with Config Server: 
Applied the same refactoring to employee-service, allowing it to fetch configurations from the centralized Git-based config server, ensuring consistency and ease of property updates.

13. Auto-Refresh Configuration Using Spring Cloud Bus: 
Enabled real-time configuration updates using Spring Cloud Bus with RabbitMQ running in Docker. This removed the need for manual /actuator/refresh calls by broadcasting configuration changes.

14. Distributed Tracing with Micrometer: 
Integrated Micrometer for capturing application metrics and traces. It provided insights into service behavior and performance, essential for debugging and monitoring in distributed systems.

15. Circuit Breaker with Resilience4j: 
Implemented circuit breaker patterns using Resilience4j. This helped in gracefully handling service failures by short-circuiting calls to unresponsive services, thereby improving system resilience.

16. Retry Mechanism with Resilience4j: 
Configured retry patterns using Resilience4j for transient failures in service-to-service communication. This automatically re-attempts failed calls before giving up, enhancing fault tolerance.

17. Organization-Service Creation: 
Introduced a new microservice, organization-service, which complements existing services. It communicates with both employee-service and department-service to represent organizational structure.

18. Communication between Employee and Organization Services: 
Enabled WebClient-based synchronous communication from employee-service to organization-service, promoting modular interaction while adhering to non-blocking IO practices.

19. Externalizing Organization-Service Configurations: 
Externalized organization-service configuration to the GitHub-based config repository. This allows all microservices to share a unified and version-controlled configuration source.

20. React Frontend Integration: 
Developed a React frontend application integrated with the API Gateway. Designed a UI to display consolidated data including user, department, and organization details through unified endpoints.

21. API Documentation with SpringDoc OpenAPI: 
Generated Swagger UI documentation using SpringDoc OpenAPI for all services (employee-service, department-service, organization-service). This simplifies REST API exploration and testing for developers.

