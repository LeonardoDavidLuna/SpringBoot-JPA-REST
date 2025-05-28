# SpringBoot-REST-JPA

## Overview

This repository contains a demo Spring Boot application that exposes a RESTful API to manage `Person` entities using:

- **Spring Boot**
- **Spring Data JPA**
- **Spring Data REST**
- **H2 in-memory database**

It demonstrates how to auto-generate full CRUD REST endpoints with minimal boilerplate code using Spring Data REST's convention-over-configuration approach.

---

## 📌 Features

- Auto-generated RESTful endpoints (no controller needed)
- In-memory H2 database (no setup required)
- JPA-based repository layer
- Maven-based build system
- Java 17 compatibility

---

## 🧱 Architecture

The application is organized into three logical layers:

- **Presentation Layer**: Auto-generated REST endpoints via Spring Data REST
- **Business Layer**: Spring Data JPA repositories
- **Persistence Layer**: H2 in-memory database

---

## 🚀 Technology Stack

| Technology             | Version  | Purpose                                 |
|------------------------|----------|-----------------------------------------|
| Spring Boot            | 3.5.0    | Application framework and auto-config   |
| Spring Data JPA        | Included | Database abstraction and repositories   |
| Spring Data REST       | Included | Automatic REST endpoint generation      |
| H2 Database            | Runtime  | In-memory database                      |
| Java                   | 17       | Runtime platform                        |
| Maven                  | 3.9.9    | Build and dependency management         |

---

## 📂 Application Structure

### Main Classes

| Class                          | Location                            | Description                                 |
|-------------------------------|-------------------------------------|---------------------------------------------|
| `AccessingDataRestApplication`| `com.example.jpa_rest`              | Main entry point (`@SpringBootApplication`) |
| `PersonRepository`            | `com.example.jpa_rest.repository`   | JPA repository (`@RepositoryRestResource`)  |
| `Person`                      | `com.example.jpa_rest.model`        | Entity definition (`@Entity`)               |

### Auto-generated REST Endpoints

| Method | Endpoint        | Description                       |
|--------|------------------|-----------------------------------|
| GET    | `/people`        | Retrieve all Person entities      |
| POST   | `/people`        | Create a new Person entity        |
| GET    | `/people/{id}`   | Retrieve Person by ID             |
| PUT    | `/people/{id}`   | Update an existing Person         |
| DELETE | `/people/{id}`   | Delete Person by ID               |
| GET    | `/people/search` | Discover search methods           |

---

# 📡 SpringBoot-REST-JPA: API Endpoints

## 📖 Overview

This Spring Boot application uses **Spring Data REST** to automatically generate a full-featured REST API for managing `Person` entities. With minimal configuration and no manual controller implementation, the system supports complete CRUD operations and query methods based on repository interfaces.

> All responses and requests use JSON format.

---

## 🔧 Auto-Generated REST Endpoints

The REST API is generated based on the `PersonRepository` interface, annotated with `@RepositoryRestResource`.

**Source**: [`PersonRepository.java`](src/main/java/com/example/jpa_rest/PersonRepository.java)

### Standard CRUD Endpoints

| HTTP Method | Endpoint           | Description                       |
|-------------|--------------------|-----------------------------------|
| GET         | `/people`          | Retrieve all persons              |
| GET         | `/people/{id}`     | Retrieve person by ID             |
| POST        | `/people`          | Create a new person               |
| PUT         | `/people/{id}`     | Replace an existing person        |
| PATCH       | `/people/{id}`     | Partially update a person         |
| DELETE      | `/people/{id}`     | Delete person by ID               |

---

## 🔍 Search Endpoints

Spring Data REST exposes custom query methods as search endpoints:

| HTTP Method | Endpoint                                 | Description                        |
|-------------|------------------------------------------|------------------------------------|
| GET         | `/people/search`                         | List available query methods       |
| GET         | `/people/search/findByLastName?name=XXX` | Find people by last name           |

The query method `findByLastName(String name)` is defined in the repository interface and automatically translated into a SQL query by Spring Data JPA.

---

## 📦 Request & Response Format

All API requests and responses follow a consistent JSON schema, based on the `Person` entity.

### Person JSON Schema

```json
{
  "firstName": "string",
  "lastName": "string"
}



## ⚙️ Build & Configuration

### Maven Details

- **Group ID**: `com.example`
- **Artifact ID**: `jpa-rest`
- **Version**: `0.0.1-SNAPSHOT`
- **Packaging**: Executable JAR
- **Java Target**: 17

### Build Commands

```bash
# Package the application
./mvnw clean package

# Run the application
./mvnw spring-boot:run
