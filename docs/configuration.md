# Configuration Guide

This document provides the configuration details required to run the **Appointment Service** locally or in a deployment environment.

---

## 📦 Prerequisites

Before you start, ensure you have:

- **Java 17** or later installed
- **Gradle** (optional, if not using the wrapper)
- **PostgreSQL** installed and running
- **Eureka Discovery Server** running (if service registration is required)

---

## ⚙️ Application Configuration

The application uses **Flyway** for database migrations instead of `spring.jpa.hibernate.ddl-auto`.

Update the `application.yml` file as follows:

```yaml
server:
  port: 8082

spring:
  application:
    name: appointment-service
  datasource:
    url: jdbc:postgresql://localhost:5432/appointmentdb
    username: YOUR_DB_USERNAME
    password: YOUR_DB_PASSWORD
  jpa:
    hibernate:
      ddl-auto: none
    show-sql: true
  flyway:
    enabled: true
    locations: classpath:db/migration

eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka/
