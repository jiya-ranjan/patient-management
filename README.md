# 🏥 Patient Management System

> A production-style **Microservices-based Patient Management System** built with **Spring Boot**, demonstrating modern backend architecture using **REST APIs, gRPC, Apache Kafka, JWT Authentication, API Gateway, Docker, PostgreSQL, and Integration Testing**.

This project simulates a real-world healthcare backend where independent microservices communicate through both synchronous and asynchronous mechanisms while remaining secure, scalable, and loosely coupled.

---

## 🚀 Architecture

```text
                           Client
                              │
                              ▼
                   ┌────────────────────┐
                   │    API Gateway     │
                   │ JWT Authentication │
                   └─────────┬──────────┘
                             │
        ┌────────────────────┼─────────────────────┐
        │                    │                     │
        ▼                    ▼                     ▼
 ┌───────────────┐    ┌──────────────┐    ┌────────────────┐
 │ Auth Service  │    │Patient Service│    │ Billing Service│
 └───────────────┘    └──────┬───────┘    └────────────────┘
                             │
                    gRPC Communication
                             │
                             ▼
                    Billing Account Creation

                             │
                      Publish Event
                             ▼
                     Apache Kafka Topic
                             │
               ┌─────────────┴──────────────┐
               ▼                            ▼
      Analytics Service            (Future Services)
```

---

# ✨ Features

- Microservices Architecture
- Spring Cloud API Gateway
- JWT Authentication & Authorization
- RESTful APIs
- gRPC Service-to-Service Communication
- Apache Kafka Event Streaming
- PostgreSQL Database
- Dockerized Services
- OpenAPI / Swagger Documentation
- Integration Testing
- Spring Data JPA
- Layered Architecture
- DTO Pattern
- Environment-based Configuration

---

# 🛠️ Tech Stack

### Backend

- Java 21
- Spring Boot
- Spring Cloud Gateway
- Spring Security
- Spring Data JPA
- Hibernate

### Database

- PostgreSQL

### Communication

- REST APIs
- gRPC
- Protocol Buffers

### Event Streaming

- Apache Kafka

### Authentication

- JWT (JSON Web Tokens)

### Documentation

- OpenAPI / Swagger

### Testing

- JUnit 5
- Spring Boot Integration Testing

### DevOps

- Docker
- Docker Compose

---

# 📂 Project Structure

```
patient-management
│
├── api-gateway
├── auth-service
├── patient-service
├── billing-service
├── analytics-service
├── integration-test
└── README.md
```

---

# 🔧 Microservices

## 🔐 Authentication Service

Responsible for

- User Authentication
- Password Verification
- JWT Token Generation
- JWT Validation

### Endpoints

```
POST /login
GET /validate
```

---

## 🌐 API Gateway

Acts as the single entry point into the system.

Responsibilities

- Request Routing
- JWT Validation
- Authentication Filter
- Route Management

---

## 🩺 Patient Service

Responsible for

- Register Patient
- Retrieve Patient Details
- Update Patient Information
- Delete Patient Records

Whenever a patient is created, the service

- Creates a billing account using **gRPC**
- Publishes a Patient Created event to **Kafka**

---

## 💳 Billing Service

Receives gRPC requests from the Patient Service and automatically creates a billing account for newly registered patients.

---

## 📊 Analytics Service

Consumes Patient Created events from Kafka and processes them asynchronously for analytics purposes.

---

# 🔄 Communication Flow

## REST Communication

```
Client
   │
   ▼
API Gateway
   │
   ▼
Patient Service
```

---

## gRPC Communication

```
Patient Service
        │
        ▼
Billing Service
```

---

## Kafka Communication

```
Patient Service
        │
        ▼
   Kafka Topic
        │
        ▼
Analytics Service
```

---

# 🔐 Authentication Flow

```
Client
   │
POST /login
   │
   ▼
Auth Service
   │
Returns JWT
   │
   ▼
Client sends Authorization Header
   │
   ▼
API Gateway
   │
Validates Token
   │
   ▼
Requested Microservice
```

---

# 📖 API Documentation

Swagger UI is available for each service.

Example

```
http://localhost:4000/swagger-ui/index.html
```

---

# 🐳 Running the Project

Clone the repository

```bash
git clone https://github.com/jiya-ranjan/patient-management.git
```

Navigate into the project

```bash
cd patient-management
```

Build all services

```bash
docker compose build
```

Run the project

```bash
docker compose up
```

---

# 🧪 Integration Testing

A dedicated **integration-test** module validates communication between microservices and verifies the overall system workflow.

Run the tests

```bash
mvn test
```

---

# 📌 Current Capabilities

✅ REST APIs

✅ JWT Authentication

✅ API Gateway

✅ PostgreSQL Persistence

✅ Dockerized Microservices

✅ Apache Kafka Integration

✅ gRPC Communication

✅ OpenAPI Documentation

✅ Integration Testing

---

# 🎯 Learning Outcomes

This project demonstrates practical experience with

- Designing distributed systems using Microservices
- Implementing synchronous and asynchronous communication
- Building secure APIs using JWT Authentication
- Containerizing applications with Docker
- Working with Apache Kafka and gRPC
- Building scalable backend services with Spring Boot
- Writing Integration Tests for distributed applications

---

# 👨‍💻 Author

**Jiya Ranjan**

GitHub: https://github.com/jiya-ranjan

LinkedIn: https://www.linkedin.com/in/jiya-ranjan
