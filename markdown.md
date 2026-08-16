# 🧭 Backend Development — Learning Plan

**Learner:** Sahadat · **Track:** Node.js → Express → MongoDB · **Status:** Phase 00 · Lesson 01

> **Mentor goal —** not to follow tutorials, but to build the ability to independently understand backend requirements, design API architecture, build production-quality APIs, debug, test, and deploy — and to make sound engineering decisions along the way.

The approach: progressive implementation, code review, debugging, quizzes, and project-based learning.

---

## 🗺️ Phase Roadmap

| # | Phase | Topics | Project |
|---|-------|--------|---------|
| **00** ▶️ | **Foundation — Express Core** | HTTP revision, client vs server, request lifecycle, Express architecture, install, first server, nodemon, TypeScript integration, tsconfig, env vars, npm scripts | Build a simple HTTP server independently |
| 01 | Express Fundamentals | Routing, request/response, status codes, JSON API, query & route params, request body, middleware, error handling | Todo API (memory-based) |
| 02 | REST API Design | REST principles, resource naming, HTTP methods, idempotency, validation, versioning, pagination, filtering, sorting | Todo API v2 |
| 03 | Project Architecture | Folder structure, MVC, service layer, controller, router, utils, config, logger, custom error classes | — |
| 04 | MongoDB | Documents, collections, BSON, CRUD, indexes, aggregation basics | — |
| 05 | Mongoose | Schema, model, validation, hooks, virtuals, populate, middleware | Todo API with database |
| 06 | Data Modeling | 1:1, 1:N, N:N relationships, embedding vs referencing | — |
| 07 | Authentication | Password hashing, JWT, access & refresh tokens, cookies, sessions, email verification, password reset | Authentication API |
| 08 | Authorization | RBAC, permissions, policies, resource ownership | Blog API |
| 09 | File Handling | Multer, local storage, Cloudinary / S3, image optimization | Photo Backend |
| 10 | Video Handling | Video upload, streaming, chunked uploads, video processing | Video Backend |
| 11 | Redis | Caching, session storage, rate limiting, queue introduction | — |
| 12 | Testing | Unit & integration testing, Supertest, Jest / Vitest | — |
| 13 | API Documentation | Swagger, OpenAPI, documentation practices | — |
| 14 | Docker | Dockerfile, Docker Compose, MongoDB container, environment config | — |
| 15 | Deployment | VPS, Nginx, PM2, CI/CD basics, production secrets | — |
| 16 | Production Engineering | Structured logging, monitoring, security, rate limiting, Helmet, CORS, compression | — |
| 17 | Basic System Design | Scalability, load balancing, CDN, caching, database scaling | — |

**▶️ = current phase**

---

## 🚀 Long-Term Projects

Complexity increases progressively across six major builds:

`Todo API` → `Blog API` → `Authentication Service` → `Social Media Backend` → `Photo/Video Backend` → `E-commerce Backend`

---

## 📋 First Project Plan — Todo API

**Goal:** build a production-style REST API that allows users to manage Todo items, expanding from an in-memory API through validation, MongoDB, and finally authentication.

### Feature Rollout

- **Phase 1** — Create, get all, get by ID, update, delete
- **Phase 2** — Pagination, filtering, sorting
- **Phase 3** — Input validation, error handling
- **Phase 4** — MongoDB integration
- **Phase 5** — Authentication

### Endpoints

| Method | Endpoint | Purpose |
|--------|----------|---------|
| `GET` | `/todos` | Get all Todos |
| `GET` | `/todos/:id` | Get a specific Todo |
| `POST` | `/todos` | Create a Todo |
| `PATCH` | `/todos/:id` | Update a Todo |
| `DELETE` | `/todos/:id` | Delete a Todo |

### Data Model

```
Todo
├── id
├── title
├── description
├── completed
├── createdAt
└── updatedAt
```

### Planned Folder Architecture

*Introduced later, once abstraction solves a real problem — not before.*

```
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

### ✅ Validation Requirements

- [ ] `title` is required
- [ ] `title` has an appropriate length
- [ ] `completed` must be a boolean
- [ ] Invalid IDs are handled correctly
- [ ] Invalid request bodies are rejected

### 🔒 Security Requirements

- [ ] Input validation
- [ ] Helmet
- [ ] CORS configuration
- [ ] Rate limiting
- [ ] Authentication
- [ ] Authorization

---

## 🎓 Teaching Method

Each lesson follows the same eight-step structure:

`1 · Concept` → `2 · Real-world analogy` → `3 · Backend example` → `4 · Mini challenge` → `5 · Student implementation` → `6 · Code review` → `7 · Quiz` → `8 · Summary`

---

## 📖 Lesson 01 — Express.js: What and Why?

### The Problem

Consider a food delivery application. The frontend sends requests like:

```http
GET /restaurants
POST /orders
```

The backend has to decide:

- Who receives the request?
- Which route handles it?
- Which function executes?
- How is the response returned?
- What happens on error?

Node's built-in `http` module *can* handle this manually — but routing, middleware, and error handling become repetitive fast as an app grows.

> **Express.js** is a lightweight framework that organizes these concerns, so development can focus on business logic instead of HTTP plumbing.

### Simple Analogy

| Node.js | Express.js |
|---------|------------|
| An empty piece of land | A structured framework built on that land |

You *can* build everything yourself on raw Node — Express just gives you practical structure and utilities for the common web-server work.

### Request Lifecycle

```
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

Each stage of this pipeline is explored in depth across the Express phase.

### 🧩 Mini Challenge

Answer in your own words before moving to the next lesson.

1. **Node.js vs Express.js** — What is the main difference between the two?
2. **Without Express** — What extra work would a backend dev need to do when building an HTTP API on raw Node.js?
3. **Request Flow** — When a browser sends an HTTP request, what steps happen before the response returns? Describe the flow.
4. **Frameworks** — Why is using a framework generally useful for a production backend?

### 📊 Progress Tracker

**Learned**
- [x] Purpose of Express.js
- [x] Node.js vs Express.js
- [x] High-level HTTP request lifecycle
- [x] Why frameworks are useful

**Not Yet Covered**
- [ ] Creating an Express application
- [ ] `app.listen()`
- [ ] Express routing
- [ ] Request and Response objects
- [ ] Middleware
- [ ] Error handling

> **Next lesson —** Express Setup + First Server, implemented in TypeScript, with every important line explained for both what it does and why it's needed. **Prerequisite:** complete the four Mini Challenge questions above.

---
*Backend Learning Plan · Rev. 01*
