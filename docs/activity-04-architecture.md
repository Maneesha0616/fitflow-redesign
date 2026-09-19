# Activity 4 – High-Level Architecture

## 4.1 Architecture Overview

The proposed FitFlow architecture uses a scalable and modular structure consisting of a Flutter frontend, NestJS backend, Python FastAPI AI microservice, PostgreSQL database, Redis cache, real-time communication, and secure authentication.

The Flutter application provides a single cross-platform frontend for Android, iOS, and Web. User requests are securely transmitted through HTTPS to the backend API. The NestJS backend manages authentication, workout and fitness functions, nutrition, social sharing, notifications, and communication with other services.

A separate FastAPI-based AI microservice is used for personalized workout recommendations and nutrition analysis. PostgreSQL is used for structured application and health-related data, while Redis provides caching and improves response performance. AWS S3 can be used for storing user-uploaded files and media.

## 4.2 Main Components

| Component               | Responsibility                                               |
| ----------------------- | ------------------------------------------------------------ |
| Flutter Client          | Provides the user interface for Android, iOS, and Web        |
| API Gateway             | Handles secure API communication between clients and backend |
| NestJS Backend          | Provides the main business logic and REST APIs               |
| FastAPI AI Microservice | Provides AI/ML-based workout and nutrition functions         |
| PostgreSQL              | Stores structured user, workout, nutrition, and social data  |
| Redis                   | Provides caching and improves application performance        |
| Supabase Auth           | Handles user authentication and identity management          |
| WebSocket / Socket.IO   | Supports real-time communication and updates                 |
| AWS S3                  | Stores images, files, and other user-generated media         |

## 4.3 Data Flow

### Personalized Workout Plans

The user submits fitness information through the Flutter application. The request is sent securely to the NestJS backend. The backend communicates with the FastAPI AI microservice, which analyses the relevant information and generates a personalized workout recommendation. The result is returned through the backend and displayed in the Flutter application.

### Social Sharing

Users can create and share fitness-related content through the Flutter application. The request is processed by the NestJS backend and relevant information is stored in PostgreSQL. Images or other media can be stored using AWS S3.

### Nutrition Analysis

Nutrition information entered by the user is sent from the Flutter application to the NestJS backend. The backend can communicate with the FastAPI AI service to perform nutrition analysis. The processed results are returned to the application.

## 4.4 Security and Scalability

The architecture uses HTTPS/TLS to protect communication between the client and backend. Authentication is handled through Supabase Auth, while JWT-based authorization can be used for secure API access.

Role-based access control can restrict access to administrative and user-specific functions. PostgreSQL provides structured and reliable data storage, while Redis can reduce database load through caching.

The backend and AI service can be containerized using Docker and deployed in a cloud environment. The modular architecture allows individual services to be scaled independently as the number of FitFlow users increases.

## 4.5 Architecture Decision

The proposed architecture was selected because it supports cross-platform development while maintaining a dedicated backend and AI service. Separating AI functionality into a FastAPI microservice allows Python-based machine-learning technologies to be used without making the main backend dependent on Python.

The combination of Flutter, NestJS, FastAPI, PostgreSQL, Redis, Supabase Auth, and WebSocket communication provides a modular architecture suitable for FitFlow's fitness, nutrition, social, real-time, and AI-related requirements.