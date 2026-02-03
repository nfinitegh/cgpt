# Deployment Architecture

## High-Level Diagram (Text)
```
[Kiosk/POS] --(HTTPS/WebSocket)--> [API Gateway] --> [Microservices]
[Mobile App] --(HTTPS)---------> [API Gateway] --> [Microservices]
[Admin Web] --(HTTPS)----------> [API Gateway]

[Microservices] -> [PostgreSQL] / [Redis] / [Object Storage]
[Microservices] -> [Message Bus (Kafka/SQS)]
[Hardware Layer] <-> [Device Service] <-> [Edge Agents]
```

## Components
- **API Gateway**: Auth, rate limiting, routing.
- **Microservices**: parking, billing, booking, reporting, device.
- **Data**: PostgreSQL (transactions), Redis (cache), S3/GCS (images).
- **Messaging**: Kafka/SQS for device events and payments.
- **Edge Agents**: Local services for offline mode and hardware control.

## Environments
- **Dev**: Single-node Docker Compose.
- **Staging**: Kubernetes with horizontal scaling.
- **Prod**: Multi-AZ Kubernetes, managed DB, CDN.

## Availability & Scale
- Stateless services with auto-scaling.
- Read replicas for reporting.
- Circuit breakers for payment/hardware providers.
