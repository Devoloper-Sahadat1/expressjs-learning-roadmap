# Backend Development Learning Plan

## Mentor Goal

The goal is not simply to follow tutorials. The objective is to develop the ability to independently:

- Understand backend requirements
- Design API architecture
- Build production-quality APIs
- Debug backend applications
- Test APIs
- Deploy backend systems
- Make sound engineering decisions

The learning approach is based on progressive implementation, code review, debugging, quizzes, and project-based learning.

---

# Complete Backend Learning Plan

## Phase 0 — Foundation (Express Core)

### Goal

Understand what Express is, why it exists, and what problem it solves.

### Topics

- HTTP Revision
- Client vs Server
- Request Lifecycle
- Express Architecture
- Express Installation
- First Server
- Development workflow
- nodemon
- TypeScript integration
- tsconfig
- Environment variables
- npm scripts

### Mini Exercise

Build a simple HTTP server independently.

---

# Phase 1 — Express Fundamentals

### Topics

- Express App
- Routing
- Request
- Response
- Status Codes
- JSON API
- Query Params
- Route Params
- Request Body
- Middleware
- Error Handling

### Mini Project

**Simple Todo API (Memory Based)**

There will be no database initially.

### Goal

Understand Express mechanics before introducing database complexity.

---

# Phase 2 — REST API Design

### Topics

- REST principles
- Resource naming
- HTTP Methods
- Idempotency
- Status codes
- Validation
- API Versioning
- Pagination
- Filtering
- Sorting

### Project

**Todo API v2**

The API will be redesigned using production-style REST principles.

---

# Phase 3 — Project Architecture

### Topics

- Folder structure
- MVC
- Service Layer
- Controller
- Router
- Utils
- Config
- Environment management
- Logger
- Custom Error Classes

### Goal

Learn professional code organization and separation of concerns.

---

# Phase 4 — MongoDB

### Topics

- Documents
- Collections
- BSON
- CRUD
- Indexes
- Aggregation basics

### Exercises

Practice MongoDB queries independently using MongoDB Shell or an equivalent environment.

---

# Phase 5 — Mongoose

### Topics

- Schema
- Model
- Validation
- Hooks
- Virtuals
- Populate
- Middleware

### Project

**Todo API with Database**

The Todo API will now use MongoDB and Mongoose.

---

# Phase 6 — Data Modeling

### Topics

- One-to-One relationships
- One-to-Many relationships
- Many-to-Many relationships
- Embedding
- Referencing

### Exercises

Design database schemas independently from requirements.

---

# Phase 7 — Authentication

### Topics

- Password hashing
- JWT
- Access tokens
- Refresh tokens
- Cookies
- Sessions
- Email verification
- Password reset

### Project

**Authentication API**

---

# Phase 8 — Authorization

### Topics

- RBAC
- Permissions
- Policies
- Resource ownership

### Project

**Blog API**

---

# Phase 9 — File Handling

### Topics

- Multer
- Local storage
- Cloudinary / S3
- Image optimization

### Project

**Photo Backend**

---

# Phase 10 — Video Handling

### Topics

- Video upload
- Streaming
- Chunked uploads
- Video processing

### Project

**Video Backend**

---

# Phase 11 — Redis

### Topics

- Caching
- Session storage
- Rate limiting
- Queue introduction

---

# Phase 12 — Testing

### Topics

- Unit testing
- Integration testing
- Supertest
- Jest / Vitest

---

# Phase 13 — API Documentation

### Topics

- Swagger
- OpenAPI
- API documentation practices

---

# Phase 14 — Docker

### Topics

- Dockerfile
- Docker Compose
- MongoDB container
- Environment configuration

---

# Phase 15 — Deployment

### Topics

- VPS
- Nginx
- PM2
- CI/CD basics
- Environment variables
- Production secrets

---

# Phase 16 — Production Engineering

### Topics

- Structured logging
- Monitoring
- Security
- Rate limiting
- Helmet
- CORS
- Compression

---

# Phase 17 — Basic System Design

### Topics

- Scalability
- Load balancing
- CDN
- Caching
- Database scaling

---

# Long-Term Projects

The projects will increase in complexity progressively:

1. Todo API
2. Blog API
3. Authentication Service
4. Social Media Backend
5. Photo/Video Backend
6. E-commerce Backend

Each major project will be developed using production-oriented practices.

---

# First Project Plan — Todo API

## Project Goal

Build a production-style REST API that allows users to manage Todo items.

---

## Features

### Phase 1

- Create Todo
- Get all Todos
- Get Todo by ID
- Update Todo
- Delete Todo

### Phase 2

- Pagination
- Filtering
- Sorting

### Phase 3

- Input validation
- Error handling

### Phase 4

- MongoDB integration

### Phase 5

- Authentication

---

# API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/todos` | Get all Todos |
| GET | `/todos/:id` | Get a specific Todo |
| POST | `/todos` | Create a Todo |
| PATCH | `/todos/:id` | Update a Todo |
| DELETE | `/todos/:id` | Delete a Todo |

---

# Initial Data Model

```text
Todo

id

title

description

completed

createdAt

updatedAt
```

---

# Planned Folder Architecture

When the architecture phase begins, the project will evolve toward:

```text
src/

  app/

    controllers/

    services/

    routes/

    middlewares/

    models/

    interfaces/

    utils/

    config/

  server.ts

  app.ts
```

The initial Express lessons will intentionally avoid introducing this full architecture immediately.

The purpose is to understand Express fundamentals first and add abstractions only when they solve a real problem.

---

# Validation Requirements

The Todo API will eventually validate:

- `title` is required
- `title` has an appropriate length
- `completed` must be a boolean
- Invalid IDs are handled correctly
- Invalid request bodies are rejected

---

# Security Requirements

Security practices will be introduced progressively:

- Input validation
- Helmet
- CORS configuration
- Rate limiting
- Authentication
- Authorization

---

# Teaching Method

Each lesson will generally follow this structure:

1. Concept
2. Real-world analogy
3. Backend example
4. Mini challenge
5. Student implementation
6. Code review
7. Quiz
8. Summary

The learner will be encouraged to implement solutions independently before receiving complete solutions.

---

# Lesson 1 — Express.js: What and Why?

## The Problem

Suppose we are building a food delivery application.

The frontend might send requests such as:

```http
GET /restaurants
```

or:

```http
POST /orders
```

The backend needs to determine:

- Who receives the request?
- How does the server identify which route should handle it?
- Which function should execute?
- How should a response be returned?
- What should happen if an error occurs?

Node.js provides the built-in `http` module, so these tasks can be implemented manually.

However, manually handling routing, middleware, request processing, error handling, and other HTTP concerns becomes repetitive and difficult to maintain as an application grows.

**Express.js** provides a lightweight framework for organizing these concerns so developers can focus more on application and business logic.

---

## Simple Analogy

Think of:

- **Node.js** as an empty piece of land.
- **Express.js** as a structured framework built on that land.

You can build everything yourself using Node.js, but Express gives you a practical structure and utilities for handling common web-server tasks.

---

# Request Lifecycle

At a high level:

```text
Client
   │
   ▼
HTTP Request
   │
   ▼
Express App
   │
   ▼
Middleware
   │
   ▼
Route Handler
   │
   ▼
Business Logic
   │
   ▼
Response
   │
   ▼
Client
```

The individual parts of this pipeline will be explored in depth throughout the Express phase.

---

# Mini Challenge

Answer the following questions in your own words before moving to the next lesson.

## 1. Node.js vs Express.js

What is the main difference between Node.js and Express.js?

## 2. Without Express

If Express did not exist, what kinds of additional work would a backend developer need to perform when building an HTTP API with Node.js?

## 3. Request Flow

When a browser sends an HTTP request to a server, what steps do you think happen before the response returns to the browser?

Describe the flow in your own words.

## 4. Frameworks

Why do you think using a framework is generally useful for a production backend?

---

# Progress Tracker

## Learned

- Purpose of Express.js
- Node.js vs Express.js
- High-level HTTP request lifecycle
- Why frameworks are useful

## Not Yet Covered

- Creating an Express application
- `app.listen()`
- Express routing
- Request and Response objects
- Middleware
- Error handling

## Next Lesson Prerequisites

Complete the four questions in the Mini Challenge.

After reviewing the answers, the next lesson will cover:

**Express Setup + First Server**

The implementation will use TypeScript, and each important line will be explained in terms of both **what it does** and **why it is needed**.
