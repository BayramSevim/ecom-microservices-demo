# E-Commerce Microservices Demo

This repository demonstrates a sample **e-commerce application** built using **microservices architecture**. The main goal of the project is to showcase how independent services communicate with each other, scale independently, and work together using modern backend technologies.

## 🧩 Architecture Overview

The project is designed around a microservices architecture. Each service has a single responsibility and can be developed, deployed, and scaled independently.

Example services:

* **Product Service** – Manages product-related operations
* **Order Service** – Handles order creation and processing
* **User/Auth Service** – User management and authentication
* **API Gateway** – Single entry point for clients
* **Config / Discovery Service** (if applicable)

> Inter-service communication is handled via REST and event-driven messaging.

## 🛠 Technologies Used

* Java / Spring Boot
* Spring Cloud (Gateway, Config, Eureka, etc.)
* **Spring Cloud Stream**
* **Apache Kafka**
* **RabbitMQ**
* **Keycloak (OAuth2 / OpenID Connect)**
* Docker & Docker Compose (Containerization)
* Zipkin
* Redis
* PostgreSQL / MongoDB (depending on the service)
* Maven
* RESTful APIs

## 📂 Project Structure

```
ecom-microservices-demo/
│
├── api-gateway/
├── product-service/
├── order-service/
├── user-service/
├── config-server/
├── docker-compose.yml
└── README.md
```

## 🚀 Getting Started

### Prerequisites

* Java 17+
* Maven
* Docker & Docker Compose

### Running the Project

```bash
# Clone the repository
git clone https://github.com/BayramSevim/ecom-microservices-demo.git
cd ecom-microservices-demo

# Start all services using Docker
docker-compose up -d
```

Alternatively, services can be run individually:

```bash
cd product-service
mvn spring-boot:run
```

## 🔗 Sample Endpoints

| Service | Endpoint         | Description   |
| ------- | ---------------- | ------------- |
| Product | GET /products    | List products |
| Order   | POST /orders     | Create order  |
| Auth    | POST /auth/login | User login    |

## 🧪 Testing

```bash
mvn test
```

## 📌 Project Scope & Purpose

This project is **actively under development** and is intended to:

* Learn and practice microservices architecture
* Experiment with Spring Cloud ecosystem
* Implement event-driven communication using Kafka
* Apply centralized authentication with Keycloak
* Gain hands-on experience with Docker and containerization

> This project is **not production-ready** and is intended for educational and demo purposes.

## 🧠 Current & Planned Enhancements

The project is continuously evolving. The following features are implemented or planned:

* ✅ Microservices architecture
* ✅ API Gateway
* 🔄 Event-driven communication with **Apache Kafka**
* 🔄 Messaging abstraction with **Spring Cloud Stream**
* 🔄 Centralized authentication & authorization using **Keycloak**
* 🔄 Full **containerization with Docker**
* ⏳ Distributed Tracing (Zipkin / OpenTelemetry)
* ⏳ Centralized Logging (ELK Stack)
* ⏳ Circuit Breaker & Resilience (Resilience4j)

## 🏗 Architecture & Communication Flow

### High-Level Architecture

The system follows a microservices-based architecture with both **synchronous (REST)** and **asynchronous (event-driven)** communication models.

* External clients communicate through the **API Gateway**
* Services authenticate via **Keycloak** using OAuth2 / OpenID Connect
* Inter-service async communication is handled via **Kafka topics**
* **Spring Cloud Stream** is used to abstract message broker details

> This hybrid approach improves scalability, decoupling, and fault tolerance.

### Kafka Event Flow (Example)

```
Order Service  ──►  OrderCreatedEvent  ──►  Kafka Topic
                                       │
                                       ├──► Inventory Service
                                       ├──► Payment Service
                                       └──► Notification Service
```

* Events are immutable
* Services react independently
* No tight coupling between producers and consumers

## 🔐 Authentication & Authorization (Keycloak)

Keycloak is used as a centralized Identity and Access Management (IAM) solution.

* OAuth2 / OpenID Connect compliant
* JWT-based authentication
* Role-based access control (RBAC)

Typical flow:

1. Client authenticates with Keycloak
2. Keycloak issues JWT access token
3. API Gateway validates token
4. Token is propagated to downstream services

## 🐳 Containerization

All services are containerized using Docker.

* Each microservice has its own Dockerfile
* Services are orchestrated using **Docker Compose**
* Infrastructure components (Kafka, Zookeeper, Keycloak, Databases) run as containers

This setup ensures:

* Environment consistency
* Easy local development
* Production-like behavior

## 🤝 Contributing

Contributions are welcome! Please open an issue before making major changes.

## 📄 License

This project is licensed under the MIT License.

---

👤 **Author:** Bayram Sevim
