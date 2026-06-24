# Smart Task Management System

Smart Task Management System is a full-stack project built using **Spring Boot Microservices** for the backend and **Angular** for the frontend. The application is designed to manage users, projects, tasks, notifications, dashboards, and authentication in a scalable microservice-based architecture.

## Project Structure

```text
smart_Task/
│
├── taskmanagement-backend/
│   ├── api-gateway/
│   ├── service-registry/
│   ├── auth-service/
│   ├── user-service/
│   ├── project-service/
│   ├── task-service/
│   ├── notification-service/
│   ├── dashboard-service/
│   └── common-library/
│
├── smart-task-frontend/
│   ├── src/
│   ├── package.json
│   ├── package-lock.json
│   └── angular.json
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
└── README.md
```

## Features

* User registration and login
* JWT-based authentication
* Role-based access control
* Project creation and management
* Task creation, assignment, and tracking
* Task priority and status management
* Dashboard for task and project summary
* Notification service for task updates
* API Gateway for routing requests
* Service Registry for microservice discovery
* Angular frontend integration
* CI pipeline using GitHub Actions

## Tech Stack

### Backend

* Java
* Spring Boot
* Spring Cloud Gateway
* Spring Security
* JWT Authentication
* Spring Data JPA
* Maven
* MySQL / PostgreSQL
* Eureka Service Registry

### Frontend

* Angular
* TypeScript
* HTML
* CSS
* Node.js
* npm

### DevOps

* Git
* GitHub
* GitHub Actions
* Maven CI
* Node.js CI

## Backend Microservices

### 1. API Gateway

The API Gateway acts as the single entry point for all client requests. It routes incoming requests to the correct backend microservice.

### 2. Service Registry

The Service Registry helps all microservices register and discover each other dynamically.

### 3. Auth Service

The Auth Service handles user login, registration, JWT token generation, and authentication validation.

### 4. User Service

The User Service manages user profile details and user-related operations.

### 5. Project Service

The Project Service manages project creation, project members, and project-related operations.

### 6. Task Service

The Task Service handles task creation, task assignment, task status updates, task priority, and task tracking.

### 7. Notification Service

The Notification Service manages task notifications and alerts.

### 8. Dashboard Service

The Dashboard Service provides summary data such as total tasks, completed tasks, pending tasks, and project progress.

### 9. Common Library

The Common Library contains shared DTOs, utility classes, constants, and common exception handling logic used across services.

## How to Run the Backend

Go to the backend folder:

```bash
cd taskmanagement-backend
```

Build the backend using Maven:

```bash
mvn clean install
```

Run each Spring Boot microservice individually:

```bash
cd service-registry
mvn spring-boot:run
```

```bash
cd api-gateway
mvn spring-boot:run
```

```bash
cd auth-service
mvn spring-boot:run
```

```bash
cd user-service
mvn spring-boot:run
```

```bash
cd project-service
mvn spring-boot:run
```

```bash
cd task-service
mvn spring-boot:run
```

```bash
cd notification-service
mvn spring-boot:run
```

```bash
cd dashboard-service
mvn spring-boot:run
```

Recommended startup order:

```text
1. service-registry
2. api-gateway
3. auth-service
4. user-service
5. project-service
6. task-service
7. notification-service
8. dashboard-service
```

## How to Run the Frontend

Go to the frontend folder:

```bash
cd smart-task-frontend
```

Install dependencies:

```bash
npm install
```

Start the Angular application:

```bash
npm start
```

Or:

```bash
ng serve
```

The frontend will usually run on:

```text
http://localhost:4200
```

## API Gateway URL

All frontend requests should go through the API Gateway.

Example:

```text
http://localhost:8080
```

Sample API routes:

```text
/api/auth/**
/api/users/**
/api/projects/**
/api/tasks/**
/api/notifications/**
/api/dashboard/**
```

## GitHub Actions CI Pipeline

This project uses GitHub Actions to build both frontend and backend.

The pipeline performs:

* Checkout repository
* Set up Node.js
* Install frontend dependencies
* Build Angular frontend
* Set up Java
* Build Spring Boot Maven backend
* Upload backend JAR artifact

Example workflow file location:

```text
.github/workflows/ci.yml
```

## Sample CI Workflow

```yaml
name: Fullstack CI - Angular + Spring Boot

on:
  push:
    branches: [ "main" ]
    paths:
      - "smart-task-frontend/**"
      - "taskmanagement-backend/**"
      - ".github/workflows/**"

  pull_request:
    branches: [ "main" ]
    paths:
      - "smart-task-frontend/**"
      - "taskmanagement-backend/**"
      - ".github/workflows/**"

  workflow_dispatch:

permissions:
  contents: read

jobs:
  frontend-build:
    name: Frontend Build - Node
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v7

      - name: Set up Node.js
        uses: actions/setup-node@v6
        with:
          node-version: '22'
          cache: npm
          cache-dependency-path: smart-task-frontend/package-lock.json

      - name: Install frontend dependencies
        run: npm ci
        working-directory: smart-task-frontend

      - name: Build frontend
        run: npm run build
        working-directory: smart-task-frontend

  backend-build:
    name: Backend Build - Spring Boot Maven
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v7

      - name: Set up Java
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'
          cache: maven
          cache-dependency-path: taskmanagement-backend/pom.xml

      - name: Build backend with Maven
        run: mvn -B -f taskmanagement-backend/pom.xml clean verify

      - name: Upload backend JAR
        uses: actions/upload-artifact@v4
        with:
          name: backend-jar
          path: taskmanagement-backend/target/*.jar
```

## Git Commands

Clone the repository:

```bash
git clone https://github.com/your-username/smart_Task.git
```

Go inside the project:

```bash
cd smart_Task
```

Add changes:

```bash
git add .
```

Commit changes:

```bash
git commit -m "Update project"
```

Push changes:

```bash
git push origin main
```

## Future Enhancements

* Docker support for all microservices
* Docker Compose setup
* Kubernetes deployment
* AWS deployment
* Email notification integration
* Real-time task updates using WebSocket
* Admin dashboard
* Team collaboration features
* File attachment support for tasks
* Advanced search and filtering
* Unit and integration test coverage

## Author

**Aaron Sam**

Software Engineer
Java Full Stack Developer
Spring Boot | Microservices | Angular | React | AWS

## Project Status

This project is currently under development.
