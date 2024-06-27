# API Gateway

The API Gateway is a central entry point for all client requests in the application. It handles the routing and forwarding of requests to the appropriate microservices.

## Features
- Provides a unified interface for clients to access the application's functionality
- Handles the routing of requests to the correct microservices
- Supports service discovery using Eureka

## Configuration
The API Gateway requires the following configuration:

```properties
# Eureka configuration
eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka

# Gateway locator
spring.cloud.gateway.discovery.locator.enabled=true
spring.cloud.gateway.discovery.locator.lower-case-service-id=true

# Routing configuration
spring.cloud.gateway.routes[0].id=quiz-service
spring.cloud.gateway.routes[0].uri=lb://quiz-service
spring.cloud.gateway.routes[0].predicates[0]=Path=/quiz/**
```

Make sure to update the Eureka server URL according to your environment.

## Deployment
The API Gateway can be deployed as a standalone Spring Boot application. Ensure that the Eureka server is running and the gateway is properly registered with it.

## Endpoints
The API Gateway does not expose any direct endpoints. It acts as a proxy, forwarding client requests to the appropriate microservices.

## Dependencies
- Spring Boot
- Spring Cloud Gateway
- Eureka (for service discovery)

## Known Issues
- The API Gateway does not have any authentication or authorization mechanisms in place.
- The error handling and logging could be improved.
- The API Gateway didn't run successfully in our tests, indicating potential issues with the implementation or configuration.

## Future Improvements
- Implement authentication and authorization for the API Gateway.
- Improve the error handling and logging mechanisms.
- Investigate and resolve the issues that prevented the API Gateway from running successfully.
- Add more test cases to ensure the reliability of the gateway.