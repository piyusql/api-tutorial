# API Handbook
## A Beginner-Friendly Handbook for Python Developers

---


## Welcome, Future API Developer!

Congratulations on starting your API journey! By the end of this handbook, you'll be able to:

- Understand how the internet and APIs work
- Consume any third-party API with confidence
- Build your own REST APIs from scratch
- Secure your APIs properly
- Debug API issues like a pro

**This handbook is designed for you if:**

- You know basic Python (variables, functions, loops, dictionaries)
- You've never worked with APIs before (or want to understand them better)
- You learn best with examples and hands-on practice

---

## How to Use This Handbook

### Learning Path for Beginners

#### Standard Path (8 Weeks) - Relaxed Pace

```
Week 1-2: Modules 1-3 (Fundamentals)
    |
    v
Week 3-4: Module 5 (Consuming APIs) <-- Start coding here!
    |
    v
Week 5-6: Module 6 (Building APIs)
    |
    v
Week 7-8: Module 7 (Security)
    |
    v
Optional: Advanced Topics (HTTP versions, gRPC)
```

#### Accelerated Path (4 Weeks) - Intensive Bootcamp Style

> **For motivated learners:** If you can dedicate 2-3 hours daily, you can complete this handbook in 4 weeks!

```
┌────────────────────────────────────────────────────────────────────────────┐
│                    4-WEEK ACCELERATED LEARNING PLAN                        │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  WEEK 1: FOUNDATIONS (Days 1-7)                                            │
│  ─────────────────────────────────────────────────────────────────────     │
│  Day 1-2: Module 1 & 1B (What are APIs, API styles)                        │
│           → Complete: First API call exercise                              │
│  Day 3-4: Module 2 (HTTP Protocol - methods, status codes, headers)        │
│           → Complete: curl exercises                                       │
│  Day 5-6: Module 3 & 4 (REST architecture, how APIs work)                  │
│           → Complete: Trace a request lifecycle                            │
│  Day 7:   Review + Practice with public APIs                               │
│           → Mini-project: Fetch data from 3 different public APIs          │
│                                                                            │
│  WEEK 2: CONSUMING APIs (Days 8-14)                                        │
│  ─────────────────────────────────────────────────────────────────────     │
│  Day 8-9:  Module 5 - curl and Browser DevTools                            │
│            → Complete: Debug a failing API request                         │
│  Day 10-12: Module 5 - Python requests library (all patterns)              │
│            → Complete: Build a CLI tool that uses an API                   │
│  Day 13:   Module 5 - Error handling, retries, timeouts                    │
│            → Complete: Handle rate limits and retries                      │
│  Day 14:   Review + Build a complete API client                            │
│            → Mini-project: Weather app or GitHub stats fetcher             │
│                                                                            │
│  WEEK 3: BUILDING APIs (Days 15-21)                                        │
│  ─────────────────────────────────────────────────────────────────────     │
│  Day 15-16: Module 6 - FastAPI basics (routes, models, validation)         │
│             → Complete: Hello World API with CRUD                          │
│  Day 17-18: Module 6B & 6C - Design patterns, input validation             │
│             → Complete: Add proper error handling                          │
│  Day 19:    Module 6D - Rate limiting                                      │
│             → Complete: Protect your API from abuse                        │
│  Day 20:    Module 6E - Logging & monitoring                               │
│             → Complete: Add structured logging                             │
│  Day 21:    Module 6F & 6G - Versioning & Documentation                    │
│             → Complete: Version your API, generate OpenAPI docs            │
│                                                                            │
│  WEEK 4: SECURITY & CAPSTONE (Days 22-28)                                  │
│  ─────────────────────────────────────────────────────────────────────     │
│  Day 22-23: Module 7 - HTTPS, security fundamentals                        │
│             → Complete: Enable HTTPS, add security headers                 │
│  Day 24-25: Module 7 - Authentication (API keys, JWT, OAuth basics)        │
│             → Complete: Add JWT authentication to your API                 │
│  Day 26-28: CAPSTONE PROJECT                                               │
│             → Build the Weather Dashboard API (or your own project)        │
│             → Include: Auth, validation, rate limiting, docs, tests        │
│                                                                            │
│  ✅ COMPLETION: You're now ready to build production APIs!                 │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### Daily Schedule Template (2-3 hours/day)

```
┌─────────────────────────────────────────────────────────┐
│              DAILY LEARNING BLOCK                       │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  30 min  │  Read theory (concepts, examples)            │
│  ────────┼───────────────────────────────────────────── │
│  60 min  │  Code along (type every example yourself!)   │
│  ────────┼───────────────────────────────────────────── │
│  30 min  │  Practice exercises (don't skip!)            │
│  ────────┼───────────────────────────────────────────── │
│  30 min  │  Build something small (apply what learned)  │
│                                                         │
│  TIP: The "build something small" is the most important │
│       part. Learning sticks when you create!            │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

#### Speed Tips for Fast Learners

1. **Skip Optional Sections First** - HTTP/2, HTTP/3, TLS deep dive, gRPC can wait
2. **Focus on FastAPI** - Don't learn Flask and Django simultaneously
3. **Use the Cheat Sheet** - Reference it constantly (page 2)
4. **Code Every Example** - Don't just read, TYPE the code yourself
5. **Build Daily** - Even 15 minutes of building beats 2 hours of reading
6. **Ask AI for Help** - Use Claude/ChatGPT to explain confusing concepts

### Icons Used in This Handbook

- **Beginner Tip** - Extra help for newcomers
- **Try It Yourself** - Hands-on exercises (don't skip these!)
- **Common Mistake** - Errors beginners often make
- **Real World** - How this applies in actual projects
- **Remember** - Key points to memorize

---

## Prerequisites

Before starting, make sure you have:

```bash
# Python 3.8 or higher
python --version  # Should show Python 3.8+

# pip (Python package manager)
pip --version

# A code editor (VS Code recommended)
# A terminal/command prompt
```

**Install these packages now** (we'll use them throughout):

```bash
pip install requests fastapi uvicorn pydantic
```

---

## Quick Reference Cheat Sheet

Keep this handy! You'll refer to it often.

### HTTP Methods (What action to take)


| Method | What it does     | Example               |
| ------ | ---------------- | --------------------- |
| GET    | Read/fetch data  | Get user profile      |
| POST   | Create new data  | Create new user       |
| PUT    | Replace all data | Update entire profile |
| PATCH  | Update some data | Change just the email |
| DELETE | Remove data      | Delete a user         |


### HTTP Status Codes (What happened)


| Code | Meaning      | When you see it               |
| ---- | ------------ | ----------------------------- |
| 200  | OK, success! | Everything worked             |
| 201  | Created!     | New resource made             |
| 400  | Bad Request  | You sent wrong data           |
| 401  | Unauthorized | Need to log in                |
| 403  | Forbidden    | Logged in but not allowed     |
| 404  | Not Found    | Resource doesn't exist        |
| 500  | Server Error | Server broke (not your fault) |


### Python requests Quick Reference

```python
import requests

# GET - Fetch data
response = requests.get('https://api.example.com/users')
data = response.json()

# POST - Create data
response = requests.post('https://api.example.com/users', json={'name': 'John'})

# With headers (authentication)
headers = {'Authorization': 'Bearer YOUR_TOKEN'}
response = requests.get('https://api.example.com/users', headers=headers)

# Check if successful
if response.ok:  # True for 200-299
    print("Success!")
else:
    print(f"Error: {response.status_code}")
```

---

## Glossary of Terms

**API** - Application Programming Interface. A way for programs to talk to each other.

**Endpoint** - A specific URL where you can access an API resource (like `/users` or `/products/123`).

**Request** - What you send to an API (asking for something).

**Response** - What the API sends back to you.

**JSON** - JavaScript Object Notation. The most common data format for APIs. Looks like Python dictionaries!

**HTTP** - HyperText Transfer Protocol. The rules for how web communication works.

**HTTPS** - HTTP Secure. HTTP with encryption (the 's' = secure).

**REST** - Representational State Transfer. A popular style for designing APIs.

**Authentication** - Proving who you are (like logging in).

**Authorization** - What you're allowed to do after logging in.

**Token** - A secret string that proves you're authenticated.

**Header** - Extra information sent with a request (like your ID badge).

---

## Table of Contents

### Fundamentals

- [Module 1: API Fundamentals](#module-1-api-fundamentals) - What is an API, types, key concepts
  - [Why Should I Care About APIs?](#why-should-i-care-about-apis)
  - [What is an API?](#what-is-an-api-the-restaurant-analogy)
  - [Your First API Call](#your-first-api-call-try-it-now)
- [Module 1B: History of APIs](#module-1b-a-brief-history-of-apis--architectural-styles) - API evolution & styles
  - [REST - The King](#1-rest-representational-state-transfer---the-king)
  - [SOAP - The Grandfather](#2-soap-simple-object-access-protocol---the-grandfather)
  - [GraphQL - The Flexible Newcomer](#3-graphql---the-flexible-newcomer)
  - [gRPC - The Speed Demon](#4-grpc-google-remote-procedure-call---the-speed-demon)
  - [WebSocket - Real-Time Channel](#5-websocket---the-real-time-channel)
  - [Comparison Table](#comparison-which-api-style-to-use)
- [Module 2: HTTP Protocol](#module-2-http-protocol---the-language-of-the-web) - Methods, status codes, headers
  - [HTTP Methods](#http-methods-the-5-actions-you-can-take)
  - [HTTP Status Codes](#http-status-codes-what-the-server-tells-you)
  - [HTTP Headers](#http-headers-the-extra-information)
- [Module 2B: HTTP Versions](#module-2b-http-versions---evolution-and-differences) - HTTP/1.1, HTTP/2, HTTP/3 (Optional)
- [Module 2C: TLS/HTTPS Deep Dive](#module-2c-tlshttps-deep-dive) - Handshakes, certificates (Optional)
- [Module 3: REST API Architecture](#module-3-rest-api-architecture) - REST principles, URL design

### Under the Hood

- [Module 4: How APIs Work](#module-4-how-apis-work-under-the-hood) - DNS, TCP, TLS, request lifecycle
  - [DNS Resolution](#step-1-dns-resolution)
  - [TCP Connection](#step-2-tcp-connection-the-three-way-handshake)
  - [TLS Handshake](#step-3-tls-handshake-for-https)
  - [HTTP Request Anatomy](#step-4-http-request-anatomy)
  - [Server-Side Processing](#step-5-server-side-processing)

### Consuming APIs (Client-Side)

- [Module 5: Consuming APIs](#module-5-consuming-apis---deep-dive) - curl, requests, DevTools
  - [curl - The Swiss Army Knife](#1-curl---the-swiss-army-knife)
  - [Browser DevTools](#2-browser-devtools---network-tab)
  - [Python requests library](#python-with-requests-library)
  - [Response patterns](#understanding-api-response-patterns)
  - [Debugging API issues](#debugging-api-issues)

### Building APIs (Server-Side)

- [Module 6: Building REST APIs](#module-6-building-rest-apis-with-python) - Python frameworks
  - [FastAPI (Recommended)](#example-1-building-with-fastapi-recommended)
  - [Flask](#example-2-building-with-flask)
  - [Django REST Framework](#example-3-django-rest-framework)
- [Module 6B: API Design Best Practices](#module-6b-api-design-best-practices) - URL design, response formats
  - [URL/Endpoint Design](#urlendpoint-design)
  - [Consistent Response Format](#consistent-response-format)
  - [HTTP Status Code Guidelines](#http-status-code-guidelines)
  - [Naming Conventions](#naming-conventions)
- [Module 6C: Input Validation](#module-6c-input-validation--sanitization) - Preventing attacks
  - [Pydantic Validation](#validation-with-pydantic-fastapi)
  - [Preventing Injection Attacks](#preventing-common-injection-attacks)
- [Module 6D: Rate Limiting](#module-6d-rate-limiting-implementation) - Protecting your API
  - [Rate Limiting Strategies](#rate-limiting-strategies)
  - [slowapi Implementation](#implementation-with-slowapi-fastapi)
  - [Custom Redis Rate Limiter](#custom-rate-limiter-with-redis)
- [Module 6E: Logging & Monitoring](#module-6e-logging--monitoring) - Observability
  - [Structured Logging](#structured-logging-with-python)
  - [Security Event Logging](#security-event-logging)
  - [Performance Monitoring](#performance-monitoring)
- [Module 6F: API Versioning](#module-6f-api-versioning---managing-change-without-breaking-things) - **Essential for production**
  - [Why Versioning is Critical](#why-api-versioning-is-critical)
  - [URL Path Versioning](#1-url-path-versioning-recommended-for-most-apis)
  - [Header Versioning](#2-header-versioning)
  - [Query Parameter Versioning](#3-query-parameter-versioning)
  - [Date-Based Versioning](#4-date-based-versioning-stripe-style)
  - [Deprecation Strategy](#3-deprecation-strategy)
- [Module 6G: API Documentation](#module-6g-api-documentation---your-api-is-only-as-good-as-its-docs) - **Non-negotiable**
  - [Why Documentation is Non-Negotiable](#why-documentation-is-non-negotiable)
  - [OpenAPI Specification](#the-openapi-specification-swagger)
  - [FastAPI Auto-Generated Docs](#fastapi-auto-generated-documentation)
  - [Documentation Best Practices](#documentation-best-practices)
  - [Documentation Checklist](#documentation-checklist)
- [Module 6H: Load Testing with Locust](#module-6h-load-testing-with-locust) - **Test before launch!**
  - [Full Guide (separate file)](./api-load-testing-guide.md)

### Security

- [Module 7: API Security](#module-7-api-security-and-authentication) - Comprehensive security guide
  - [Why API Security Matters](#why-api-security-matters)
  - [HTTPS: Foundation of Security](#https-the-foundation-of-api-security)
  - [How HTTPS Encryption Works](#how-https-encryption-works-for-apis)
  - [Implementing HTTPS in Python](#implementing-https-in-python-apis)
  - [Enforcing HTTPS](#enforcing-https-in-your-api)
  - [Secure API Calls (Client)](#making-secure-api-calls-client-side)
  - [Common HTTPS Mistakes](#common-https-mistakes-to-avoid)
  - [Authentication Methods](#authentication-methods)
    - [API Keys](#1-api-keys)
    - [JWT Tokens](#2-jwt-json-web-tokens)
    - [OAuth 2.0](#3-oauth-20)

### Advanced Topics

- [Module 7B: Advanced Topics](#module-7b-advanced-topics) - Pagination, GraphQL, webhooks
  - [Pagination Patterns](#pagination-patterns)
  - [GraphQL](#graphql-alternative-to-rest)
  - [Webhooks](#webhooks-reverse-apis)
- [Module 8: gRPC](#module-8-grpc---modern-high-performance-apis) - Protocol Buffers, streaming (Advanced)
  - [Protocol Buffers](#protocol-buffers-protobuf)
  - [gRPC Server (Python)](#building-a-grpc-server-python)
  - [gRPC Client (Python)](#building-a-grpc-client-python)
  - [gRPC Error Handling](#grpc-error-handling)
  - [gRPC Authentication](#grpc-authentication-and-security)

### Practice & Projects

- [Hands-On Practice Path](#hands-on-practice-path)
  - [Beginner Track (Weeks 1-4)](#beginner-track-weeks-1-4)
  - [Intermediate Track (Weeks 5-8)](#intermediate-track-weeks-5-8)
- [Common Mistakes Beginners Make](#common-mistakes-beginners-make-and-how-to-avoid-them)
- [Capstone Project: Weather Dashboard API](#capstone-project-build-a-weather-dashboard-api)
- [API Implementation Checklist](#api-implementation-checklist) - **Use this for every new API!**
  - [Planning & Design](#phase-1-planning--design)
  - [Project Setup](#phase-2-project-setup)
  - [Core Implementation](#phase-3-core-implementation)
  - [Security Implementation](#phase-4-security-implementation)
  - [Rate Limiting & Protection](#phase-5-rate-limiting--protection)
  - [Documentation](#phase-6-documentation)
  - [Logging & Monitoring](#phase-7-logging--monitoring)
  - [Testing](#phase-8-testing)
  - [Deployment Preparation](#phase-9-deployment-preparation)
  - [Post-Launch](#phase-10-post-launch)
  - [Minimum Viable API Checklist](#quick-reference-minimum-viable-api-checklist)
- [Recommended Resources](#recommended-resources)
- [You Did It!](#you-did-it)

---

## Module 1: API Fundamentals

### Why Should I Care About APIs?

APIs are everywhere! Every time you:

- Check the weather on your phone
- Log in with Google/Facebook
- See your bank balance in an app
- Order food through DoorDash
- Use any app that shows data from the internet

...you're using APIs! Learning APIs opens doors to:

- **Build powerful apps** that connect to any service
- **Automate tasks** (post to social media, send emails, analyze data)
- **Get hired** - API skills are in high demand
- **Create your own services** that others can use

### What is an API? (The Restaurant Analogy)

**API** = Application Programming Interface

Think of a restaurant:

```
YOU (Customer)          WAITER (API)           KITCHEN (Server/Database)
     |                      |                         |
     |-- "I want pizza" --> |                         |
     |                      |-- Takes order to -->    |
     |                      |                         | (Makes pizza)
     |                      | <-- Brings pizza back --|
     | <-- Here's your pizza|                         |
```

- **You** = Your Python code (the client)
- **Menu** = API documentation (what you can order)
- **Waiter** = The API (takes your request, brings response)
- **Kitchen** = The server (does the actual work)

You don't need to know HOW the kitchen makes pizza. You just need to know:

1. What's on the menu (available endpoints)
2. How to order (how to make requests)
3. What you'll get back (response format)

### Your First API Call (Try It Now!)

Open your terminal and type this:

```bash
curl https://api.github.com/users/octocat
```

You just made an API call! You should see JSON data about GitHub's mascot.

Now let's do it in Python:

```python
# your_first_api.py - Type this in a file and run it!
import requests

# Make a GET request to GitHub's API
response = requests.get('https://api.github.com/users/octocat')

# Print the status code (200 = success!)
print(f"Status Code: {response.status_code}")

# Print the data we got back
data = response.json()  # Convert JSON to Python dictionary
print(f"Username: {data['login']}")
print(f"Name: {data['name']}")
print(f"Followers: {data['followers']}")
```

**Try It Yourself:** Run this code! Change `octocat` to your own GitHub username.

### Key Concepts (with Examples)


| Concept      | What it means               | Real example                 |
| ------------ | --------------------------- | ---------------------------- |
| **Client**   | The program making requests | Your Python script           |
| **Server**   | The computer responding     | GitHub's computers           |
| **Request**  | What you ask for            | "Give me user info"          |
| **Response** | What you get back           | User's name, followers, etc. |
| **Endpoint** | The URL you call            | `/users/octocat`             |


```mermaid
sequenceDiagram
    participant You as Your Python Code
    participant API as GitHub API
    participant DB as GitHub Database

    You->>API: GET /users/octocat
    Note right of You: "Hey GitHub, tell me about octocat"
    API->>DB: Look up user 'octocat'
    DB-->>API: Here's the user data
    API-->>You: 200 OK + JSON data
    Note left of API: "Here's everything about octocat!"
```

### Types of APIs (Focus on Web APIs)


| Type         | What it is                    | Example                     |
| ------------ | ----------------------------- | --------------------------- |
| **Web APIs** | APIs over the internet (HTTP) | GitHub API, Twitter API     |
| Library APIs | Functions in code packages    | `requests.get()` is an API! |
| OS APIs      | Talk to your operating system | File system access          |


**In this handbook, we focus on Web APIs** - they're the most useful and common.

### Common Mistake: Confusing API with Library

```python
# This is using the 'requests' LIBRARY
import requests

# This is calling a WEB API
response = requests.get('https://api.github.com/users/octocat')

# The library (requests) helps you call the web API (GitHub)
```

### Try It Yourself: Explore a Public API

JSONPlaceholder is a free fake API for testing. Try these:

```python
import requests

# Get a list of users
response = requests.get('https://jsonplaceholder.typicode.com/users')
users = response.json()
print(f"Found {len(users)} users!")
for user in users[:3]:  # Print first 3
    print(f"  - {user['name']} ({user['email']})")

# Get a specific post
response = requests.get('https://jsonplaceholder.typicode.com/posts/1')
post = response.json()
print(f"\nPost Title: {post['title']}")
```

### Remember: The 4 Things Every API Call Has

1. **URL** - Where to send the request (`https://api.github.com/users/octocat`)
2. **Method** - What action to take (GET, POST, etc.)
3. **Headers** - Extra info (authentication, content type)
4. **Body** - Data you're sending (for POST/PUT requests)

---

## Module 1B: A Brief History of APIs & Architectural Styles

> **Why learn history?** Understanding where APIs came from helps you understand why things work the way they do today, and helps you choose the right approach for your projects.

### The Evolution of APIs: A Timeline

```
1960s-1990s: The Early Days
    |
    v
2000: SOAP is born (XML-based, complex)
    |
    v
2000: REST is defined by Roy Fielding
    |
    v
2005-2010: REST takes over (simpler, JSON)
    |
    v
2012: GraphQL developed at Facebook
    |
    v
2015: gRPC released by Google
    |
    v
2020s: REST dominates, GraphQL grows, gRPC for microservices
```

### The Major API Styles (What You'll Encounter)

#### 1. REST (Representational State Transfer) - The King

**Born:** 2000 (Roy Fielding's PhD dissertation)
**Status:** Most popular today (90%+ of public APIs)

```
What it looks like:
GET    https://api.example.com/users/123
POST   https://api.example.com/users
DELETE https://api.example.com/users/123
```

**Why it won:**
- Simple to understand
- Uses standard HTTP (GET, POST, PUT, DELETE)
- Works with any programming language
- JSON is human-readable
- Stateless (each request is independent)

**Famous REST APIs:** GitHub, Twitter, Stripe, most APIs you'll use

```python
# REST in action - clean and simple
import requests

# Get a user
user = requests.get('https://api.github.com/users/octocat').json()

# Create something
new_post = requests.post('https://api.example.com/posts', json={
    'title': 'Hello World',
    'body': 'My first post'
}).json()
```

#### 2. SOAP (Simple Object Access Protocol) - The Grandfather

**Born:** 1998-2000 (Microsoft, IBM)
**Status:** Legacy, still used in enterprise/banking

```xml
<!-- What SOAP looks like (XML, verbose) -->
<?xml version="1.0"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <GetUser xmlns="http://example.com/users">
      <UserId>123</UserId>
    </GetUser>
  </soap:Body>
</soap:Envelope>
```

**Why it lost popularity:**
- Very verbose (lots of XML)
- Complex to implement
- Harder to debug
- Overkill for most use cases

**Where you'll still see it:** Banks, insurance companies, government systems, older enterprise software

**Real World:** If you work at a large corporation, you might encounter SOAP APIs for legacy systems. Libraries like `zeep` can help:

```python
# Working with SOAP in Python (if you ever need to)
from zeep import Client

client = Client('https://example.com/service?wsdl')
result = client.service.GetUser(UserId=123)
```

#### 3. GraphQL - The Flexible Newcomer

**Born:** 2012 (Facebook), open-sourced 2015
**Status:** Growing, popular for complex UIs

```graphql
# What GraphQL looks like - you ask for exactly what you need
query {
  user(id: 123) {
    name
    email
    posts(limit: 5) {
      title
      createdAt
    }
  }
}
```

**Why it's popular:**
- Get exactly the data you need (no over-fetching)
- One endpoint for everything
- Great for mobile apps (save bandwidth)
- Self-documenting

**Why REST is still more common:**
- GraphQL is more complex to set up
- Caching is harder
- REST is "good enough" for most cases

**Famous GraphQL APIs:** GitHub (v4), Shopify, Yelp

```python
# GraphQL in Python
import requests

query = """
query {
  user(login: "octocat") {
    name
    repositories(first: 5) {
      nodes {
        name
        stargazerCount
      }
    }
  }
}
"""

response = requests.post(
    'https://api.github.com/graphql',
    json={'query': query},
    headers={'Authorization': 'Bearer YOUR_TOKEN'}
)
print(response.json())
```

#### 4. gRPC (Google Remote Procedure Call) - The Speed Demon

**Born:** 2015 (Google)
**Status:** Popular for microservices, internal APIs

```protobuf
// What gRPC looks like - Protocol Buffers definition
service UserService {
  rpc GetUser(GetUserRequest) returns (User);
}

message GetUserRequest {
  int64 id = 1;
}

message User {
  int64 id = 1;
  string name = 2;
  string email = 3;
}
```

**Why it exists:**
- Much faster than REST (binary format)
- Strongly typed (catches errors early)
- Bi-directional streaming
- Great for service-to-service communication

**Why REST is still more common for public APIs:**
- gRPC doesn't work directly in browsers
- Harder to debug (binary, not human-readable)
- More setup required

**Where you'll see it:** Microservices at Google, Netflix, Uber; internal systems

#### 5. WebSocket - The Real-Time Channel

**Born:** 2011 (standardized)
**Status:** Used for real-time features

```python
# WebSocket - persistent two-way connection
import websocket

ws = websocket.create_connection("wss://stream.example.com")
ws.send("subscribe:prices")

while True:
    result = ws.recv()  # Continuously receive updates
    print(f"Price update: {result}")
```

**Why it exists:**
- Real-time updates (no polling)
- Two-way communication
- Low latency

**Where you'll see it:** Chat apps, live sports scores, stock tickers, multiplayer games

### Comparison: Which API Style to Use?

| Style | Best For | Data Format | Complexity | Performance |
|-------|----------|-------------|------------|-------------|
| **REST** | Most APIs, CRUD operations | JSON | Low | Good |
| **SOAP** | Enterprise, legacy systems | XML | High | Moderate |
| **GraphQL** | Complex UIs, mobile apps | JSON | Medium | Good |
| **gRPC** | Microservices, internal APIs | Binary (Protobuf) | Medium | Excellent |
| **WebSocket** | Real-time features | Any | Medium | Excellent |

### What Should You Learn First?

```
Beginner:     REST (this handbook!) ← You are here
              ↓
Intermediate: GraphQL (when you need flexible queries)
              ↓
Advanced:     gRPC (for high-performance microservices)
              WebSocket (for real-time features)
```

**For 95% of your projects, REST will be the right choice.** That's why this handbook focuses on REST.

### Fun Facts & Trivia

- **REST** was defined in Roy Fielding's PhD dissertation. He was one of the authors of HTTP itself!

- **SOAP** stands for "Simple Object Access Protocol" but is ironically one of the most complex API styles.

- **GraphQL** was created at Facebook to solve the problem of mobile apps needing different data than web apps.

- **gRPC** is used internally at Google for virtually all their services - they handle billions of requests per second.

- **JSON** (JavaScript Object Notation) became the standard format because it's both human-readable AND easy for machines to parse. Before JSON, XML was dominant.

- The term **"API"** was first used in 1968 in a paper about data structures!

### The Rise of REST: Why It Won

In the early 2000s, there was a "war" between SOAP and REST:

```
SOAP Supporters:              REST Supporters:
- Enterprise companies        - Web startups
- "It's more secure!"         - "It's simpler!"
- "It has standards!"         - "It just works!"
- Complex tooling             - Use any HTTP client
```

REST won because:
1. **Simplicity** - Any developer could understand it in minutes
2. **JSON** - Much lighter than XML
3. **HTTP** - Used existing web infrastructure
4. **Flexibility** - No strict rules, adapt to your needs

### APIs in the Wild: What Companies Use

| Company | Public API Style | Internal APIs |
|---------|------------------|---------------|
| GitHub | REST + GraphQL | Unknown |
| Twitter | REST | Unknown |
| Google | REST | gRPC |
| Facebook | GraphQL | Thrift/gRPC |
| Netflix | REST | gRPC |
| Stripe | REST | Unknown |
| Shopify | REST + GraphQL | Unknown |
| Uber | REST | gRPC |

### Remember

- **REST** = Your bread and butter. Learn this well.
- **GraphQL** = When you need flexibility. Learn when needed.
- **gRPC** = When you need speed. Learn for advanced projects.
- **SOAP** = Legacy. Learn only if you have to work with old systems.
- **WebSocket** = Real-time. Learn for chat/live features.

---

## Module 2: HTTP Protocol - The Language of the Web

### What is HTTP? (And Why Should I Care?)

HTTP (HyperText Transfer Protocol) is like the **language** that your code and servers speak. Just like you need to know English to order at a restaurant, you need to understand HTTP to work with APIs.

**Good news:** It's simpler than you think! There are only a few things to learn.

### HTTP Methods: The 5 Actions You Can Take

Think of HTTP methods as **verbs** - they describe what you want to do:


| Method     | What it does             | Real-world analogy           | Example             |
| ---------- | ------------------------ | ---------------------------- | ------------------- |
| **GET**    | Read/fetch data          | Looking at a menu            | Get user profile    |
| **POST**   | Create something new     | Placing an order             | Create new account  |
| **PUT**    | Replace everything       | Rewriting your entire order  | Update full profile |
| **PATCH**  | Update part of something | "Actually, change the drink" | Update just email   |
| **DELETE** | Remove something         | Cancel the order             | Delete account      |


```python
import requests

# GET - "Show me the users"
response = requests.get('https://jsonplaceholder.typicode.com/users/1')

# POST - "Create a new post"
response = requests.post(
    'https://jsonplaceholder.typicode.com/posts',
    json={'title': 'My Post', 'body': 'Hello!', 'userId': 1}
)

# PUT - "Replace this entire post"
response = requests.put(
    'https://jsonplaceholder.typicode.com/posts/1',
    json={'title': 'New Title', 'body': 'New Body', 'userId': 1}
)

# PATCH - "Just update the title"
response = requests.patch(
    'https://jsonplaceholder.typicode.com/posts/1',
    json={'title': 'Updated Title Only'}
)

# DELETE - "Remove this post"
response = requests.delete('https://jsonplaceholder.typicode.com/posts/1')
```

**Remember:** GET = Read, POST = Create, PUT/PATCH = Update, DELETE = Remove

### HTTP Status Codes: What the Server Tells You

Status codes are **3-digit numbers** that tell you what happened. You only need to remember the categories:

```
2xx = SUCCESS! (Everything worked)
4xx = YOUR FAULT (You did something wrong)
5xx = SERVER'S FAULT (Something broke on their end)
```

**The Most Common Codes:**


| Code    | Name              | What it means              | What to do                  |
| ------- | ----------------- | -------------------------- | --------------------------- |
| **200** | OK                | Success!                   | Celebrate                   |
| **201** | Created           | New thing made             | Success for POST            |
| **204** | No Content        | Success, nothing to return | Success for DELETE          |
| **400** | Bad Request       | You sent bad data          | Check your request          |
| **401** | Unauthorized      | Not logged in              | Add authentication          |
| **403** | Forbidden         | Logged in but not allowed  | Check permissions           |
| **404** | Not Found         | Doesn't exist              | Check the URL               |
| **422** | Unprocessable     | Data format wrong          | Check your JSON             |
| **429** | Too Many Requests | Slow down!                 | Wait and retry              |
| **500** | Server Error      | Server broke               | Not your fault, retry later |


```python
import requests

response = requests.get('https://api.github.com/users/octocat')

# Check what happened
if response.status_code == 200:
    print("Success! Here's the data:")
    print(response.json())
elif response.status_code == 404:
    print("User not found!")
elif response.status_code == 401:
    print("You need to log in!")
elif response.status_code >= 500:
    print("Server error - try again later")

# Shortcut: response.ok is True for any 2xx code
if response.ok:
    print("It worked!")
```

### HTTP Headers: The Extra Information

Headers are like **notes attached to your request**. The most important ones:


| Header          | What it does               | Example                  |
| --------------- | -------------------------- | ------------------------ |
| `Authorization` | Proves who you are         | `Bearer your_token_here` |
| `Content-Type`  | What format you're sending | `application/json`       |
| `Accept`        | What format you want back  | `application/json`       |


```python
import requests

# Adding headers to your request
headers = {
    'Authorization': 'Bearer my_secret_token',
    'Content-Type': 'application/json'
}

response = requests.get(
    'https://api.example.com/protected-data',
    headers=headers
)

# Reading headers from the response
print(response.headers['Content-Type'])  # Usually 'application/json'
```

### The Request/Response Cycle (Visual)

Every API call follows this pattern:

```mermaid
flowchart LR
    subgraph request [Your Request]
        A[Method: GET]
        B[URL: /users/1]
        C[Headers: Auth token]
        D[Body: empty for GET]
    end
    subgraph response [Server Response]
        E[Status: 200 OK]
        F[Headers: Content-Type]
        G[Body: JSON data]
    end
    request -->|Send| response
```

### Try It Yourself: Explore HTTP in Action

```python
import requests

# Make a request and explore everything
response = requests.get('https://httpbin.org/get')

print("=== REQUEST INFO ===")
print(f"URL: {response.request.url}")
print(f"Method: {response.request.method}")
print(f"Headers we sent: {dict(response.request.headers)}")

print("\n=== RESPONSE INFO ===")
print(f"Status Code: {response.status_code}")
print(f"Status OK? {response.ok}")
print(f"Headers received: {dict(response.headers)}")
print(f"Body (JSON): {response.json()}")
```

### Common Mistake: Forgetting Content-Type

```python
# WRONG - Server doesn't know you're sending JSON
response = requests.post(
    'https://api.example.com/users',
    data='{"name": "John"}'  # This is a string, not JSON!
)

# RIGHT - Use json= parameter (sets Content-Type automatically)
response = requests.post(
    'https://api.example.com/users',
    json={'name': 'John'}  # requests handles everything
)
```

### Quick Reference Card

```
REQUEST:
┌─────────────────────────────────────┐
│ POST /users HTTP/1.1                │ ← Method + Path
│ Host: api.example.com               │ ← Headers
│ Authorization: Bearer token123      │
│ Content-Type: application/json      │
│                                     │
│ {"name": "John", "email": "..."}    │ ← Body (JSON)
└─────────────────────────────────────┘

RESPONSE:
┌─────────────────────────────────────┐
│ HTTP/1.1 201 Created                │ ← Status Code
│ Content-Type: application/json      │ ← Headers
│                                     │
│ {"id": 123, "name": "John"}         │ ← Body (JSON)
└─────────────────────────────────────┘
```

---

## Module 2B: HTTP Versions - Evolution and Differences

> **Note for Beginners:** This section is **optional** for now. You can skip to Module 3 and come back later. The `requests` library handles HTTP versions automatically - you don't need to understand this to use APIs!

Understanding HTTP versions is useful for API performance optimization (but not required to get started).

### HTTP/1.0 (1996) - The Beginning

```
Client                          Server
  |-------- Request 1 ----------->|
  |<------- Response 1 -----------|
  [Connection Closed]

  |-------- Request 2 ----------->|  (New TCP connection!)
  |<------- Response 2 -----------|
  [Connection Closed]
```

**Problems:**

- New TCP connection for every request (expensive)
- High latency due to repeated handshakes
- No persistent connections

### HTTP/1.1 (1997) - Keep-Alive

```
Client                          Server
  |-------- Request 1 ----------->|
  |<------- Response 1 -----------|
  |-------- Request 2 ----------->|  (Same connection!)
  |<------- Response 2 -----------|
  |-------- Request 3 ----------->|
  |<------- Response 3 -----------|
  [Connection kept open]
```

**Improvements:**

- Persistent connections (Connection: keep-alive)
- Pipelining (send multiple requests without waiting)
- Chunked transfer encoding
- Host header (virtual hosting)

**Remaining Problems:**

- Head-of-line blocking (requests processed in order)
- Text-based protocol (verbose headers)
- No true parallelism

### HTTP/2 (2015) - Multiplexing Revolution

```mermaid
flowchart LR
    subgraph http1 [HTTP/1.1]
        A1[Request 1] --> B1[Response 1]
        B1 --> A2[Request 2]
        A2 --> B2[Response 2]
    end
    subgraph http2 [HTTP/2]
        C1[Request 1] --> D1[Response 1]
        C2[Request 2] --> D2[Response 2]
        C3[Request 3] --> D3[Response 3]
    end
```
**Key Features:**

1. **Binary Protocol** - More efficient than text
2. **Multiplexing** - Multiple streams over single connection
3. **Header Compression** (HPACK) - Reduces overhead
4. **Server Push** - Server can send resources proactively
5. **Stream Prioritization** - Important requests first

```bash
# Test HTTP/2 support
curl -I --http2 https://www.google.com

# Force HTTP/2
curl --http2-prior-knowledge https://api.example.com
```

**Frame Structure:**

```
+-----------------------------------------------+
|                 Length (24)                   |
+---------------+---------------+---------------+
|   Type (8)    |   Flags (8)   |
+-+-------------+---------------+-------------------------------+
|R|                 Stream Identifier (31)                      |
+=+=============================================================+
|                   Frame Payload (0...)                      ...
+---------------------------------------------------------------+
```

### HTTP/3 (2022) - QUIC Protocol

HTTP/3 replaces TCP with QUIC (UDP-based).

```mermaid
flowchart TD
    subgraph tcp [HTTP/2 over TCP]
        A[Application Layer - HTTP/2]
        B[Security Layer - TLS 1.2/1.3]
        C[Transport Layer - TCP]
        D[Network Layer - IP]
        A --> B --> C --> D
    end
    subgraph quic [HTTP/3 over QUIC]
        E[Application Layer - HTTP/3]
        F[QUIC - Transport + Security]
        G[Network Layer - UDP]
        H[Network Layer - IP]
        E --> F --> G --> H
    end
```
**Why QUIC/HTTP/3?**

1. **0-RTT Connection** - Faster initial connection
2. **No Head-of-Line Blocking** - Packet loss doesn't block other streams
3. **Connection Migration** - Survives IP changes (mobile networks)
4. **Built-in Encryption** - TLS 1.3 integrated

```bash
# Check if server supports HTTP/3
curl --http3 https://cloudflare.com

# Using curl with HTTP/3 (requires curl 7.66+)
curl -I --http3 https://www.google.com
```

### Comparison Table


| Feature               | HTTP/1.1 | HTTP/2  | HTTP/3     |
| --------------------- | -------- | ------- | ---------- |
| Transport             | TCP      | TCP     | QUIC (UDP) |
| Multiplexing          | No       | Yes     | Yes        |
| Header Compression    | No       | HPACK   | QPACK      |
| Server Push           | No       | Yes     | Yes        |
| Connection Setup      | 1-3 RTT  | 1-3 RTT | 0-1 RTT    |
| Head-of-Line Blocking | Yes      | Partial | No         |


---

## Module 2C: TLS/HTTPS Deep Dive

> **Note for Beginners:** This section explains HOW encryption works. You don't need to understand the technical details to use HTTPS - just remember: **always use `https://` URLs, never `http://**`. Skip to Module 3 if you want to start coding!

### Why HTTPS Matters

```mermaid
flowchart LR
    subgraph http [HTTP - Insecure]
        A[Client] -->|Plain text| B[Attacker can read]
        B -->|Plain text| C[Server]
    end
    subgraph https [HTTPS - Secure]
        D[Client] -->|Encrypted| E[Attacker sees gibberish]
        E -->|Encrypted| F[Server]
    end
```
**HTTPS provides:**

1. **Confidentiality** - Data is encrypted
2. **Integrity** - Data cannot be modified
3. **Authentication** - Server identity verified

### TLS Versions


| Version | Year | Status                     |
| ------- | ---- | -------------------------- |
| SSL 2.0 | 1995 | Deprecated (insecure)      |
| SSL 3.0 | 1996 | Deprecated (POODLE attack) |
| TLS 1.0 | 1999 | Deprecated                 |
| TLS 1.1 | 2006 | Deprecated                 |
| TLS 1.2 | 2008 | Widely used                |
| TLS 1.3 | 2018 | Recommended                |


### TLS 1.2 Handshake (Detailed)

```mermaid
sequenceDiagram
    participant Client
    participant Server

    Note over Client,Server: TCP Connection Established

    Client->>Server: ClientHello
    Note right of Client: TLS version, cipher suites, random bytes

    Server->>Client: ServerHello
    Note left of Server: Chosen cipher, random bytes

    Server->>Client: Certificate
    Note left of Server: Server's X.509 certificate

    Server->>Client: ServerKeyExchange
    Note left of Server: DH parameters (if needed)

    Server->>Client: ServerHelloDone

    Client->>Client: Verify Certificate
    Note right of Client: Check CA signature, expiry, domain

    Client->>Server: ClientKeyExchange
    Note right of Client: Pre-master secret (encrypted)

    Client->>Server: ChangeCipherSpec
    Note right of Client: Switching to encrypted mode

    Client->>Server: Finished (encrypted)

    Server->>Client: ChangeCipherSpec
    Server->>Client: Finished (encrypted)

    Note over Client,Server: Secure channel established (2 RTT)
```

### TLS 1.3 Handshake (Faster)

```mermaid
sequenceDiagram
    participant Client
    participant Server

    Client->>Server: ClientHello + KeyShare
    Note right of Client: Includes key exchange in first message

    Server->>Client: ServerHello + KeyShare + Certificate + Finished
    Note left of Server: Everything in one response

    Client->>Server: Finished

    Note over Client,Server: Secure channel established (1 RTT)
```
**TLS 1.3 Improvements:**

- Reduced handshake from 2 RTT to 1 RTT
- 0-RTT resumption for repeat connections
- Removed insecure algorithms (RSA key exchange, CBC mode)
- Encrypted more of the handshake

### Certificate Chain of Trust

```mermaid
flowchart TD
    A[Root CA Certificate] -->|Signs| B[Intermediate CA Certificate]
    B -->|Signs| C[Server Certificate]

    D[Browser/OS Trust Store] -->|Contains| A
    E[Server] -->|Presents| C
    E -->|Presents| B
```
**Verification Process:**

1. Server sends its certificate + intermediate certificates
2. Client builds chain to a trusted root CA
3. Client verifies each signature in the chain
4. Client checks certificate validity (expiry, domain, revocation)

### Inspecting TLS Connections

```bash
# View certificate details
openssl s_client -connect api.github.com:443 -showcerts

# Check TLS version and cipher
curl -v https://api.github.com 2>&1 | grep -E "SSL|TLS"

# Test specific TLS version
openssl s_client -connect api.github.com:443 -tls1_3

# View certificate expiry
echo | openssl s_client -connect api.github.com:443 2>/dev/null | \
  openssl x509 -noout -dates
```

### Common TLS Errors and Solutions

**1. Certificate Expired**

```
SSL certificate problem: certificate has expired
```

- Server needs to renew certificate
- Check with: `openssl s_client -connect host:443`

**2. Self-Signed Certificate**

```
SSL certificate problem: self signed certificate
```

- Add CA to trust store, or
- Skip verification (testing only): `curl -k`

**3. Hostname Mismatch**

```
SSL certificate problem: hostname mismatch
```

- Certificate doesn't match the domain
- Check certificate's Subject Alternative Names (SAN)

**4. Certificate Chain Incomplete**

```
SSL certificate problem: unable to get local issuer certificate
```

- Server not sending intermediate certificates
- Fix server configuration

### mTLS (Mutual TLS) - Client Certificates

Regular TLS only authenticates the server. mTLS authenticates both parties.

```mermaid
sequenceDiagram
    participant Client
    participant Server

    Client->>Server: ClientHello
    Server->>Client: ServerHello + Server Certificate
    Server->>Client: CertificateRequest
    Note left of Server: Server requests client cert
    Client->>Server: Client Certificate
    Note right of Client: Client proves identity
    Client->>Server: CertificateVerify
    Note over Client,Server: Both parties authenticated
```
**Use cases:**

- Service-to-service authentication (microservices)
- High-security APIs (banking, healthcare)
- Zero-trust architectures

```bash
# curl with client certificate
curl --cert client.crt --key client.key https://api.example.com
```

---

## Module 3: REST API Architecture

### What is REST?

- **RE**presentational **S**tate **T**ransfer
- An architectural style (not a protocol)
- Uses HTTP methods semantically

### REST Principles

1. **Stateless**: Each request contains all info needed
2. **Client-Server**: Separation of concerns
3. **Uniform Interface**: Consistent URL patterns
4. **Resource-Based**: Everything is a resource with a unique URI
5. **Cacheable**: Responses can be cached

### RESTful URL Design

```

# Resources (nouns, not verbs)
GET    /users              # List all users
GET    /users/123          # Get specific user
POST   /users              # Create new user
PUT    /users/123          # Replace user
PATCH  /users/123          # Update user fields
DELETE /users/123          # Delete user

# Nested Resources
GET    /users/123/orders   # Get orders for user 123
GET    /users/123/orders/5 # Get specific order

# Query Parameters (filtering, pagination, sorting)
GET    /users?role=admin&sort=name&page=2&limit=20
```

### JSON Response Structure

```json
{
  "data": {
    "id": 123,
    "name": "John Doe",
    "email": "john@example.com"
  },
  "meta": {
    "timestamp": "2026-01-29T10:00:00Z"
  }
}
```

---

## Module 4: How APIs Work Under the Hood

This module dives deep into what actually happens when you make an API call.

### The Complete Request Lifecycle

```mermaid
sequenceDiagram
    participant Browser
    participant DNS
    participant Server
    participant LoadBalancer as LB
    participant AppServer as App
    participant Database as DB

    Browser->>DNS: Resolve api.example.com
    DNS-->>Browser: IP: 203.0.113.50
    Browser->>Server: TCP Handshake
    Server-->>Browser: Connection Established
    Browser->>Server: TLS Handshake (HTTPS)
    Server-->>Browser: Encrypted Channel Ready
    Browser->>LoadBalancer: HTTP Request
    LoadBalancer->>AppServer: Forward Request
    AppServer->>Database: Query Data
    Database-->>AppServer: Return Results
    AppServer-->>LoadBalancer: HTTP Response
    LoadBalancer-->>Browser: Forward Response
```

### Step 1: DNS Resolution

When you call `https://api.github.com/users`, your system first needs to find the IP address:

```bash
# See DNS resolution in action
nslookup api.github.com

# Or with more detail
dig api.github.com
```

**What happens:**

1. Browser checks local DNS cache
2. If not found, queries your ISP's DNS server
3. DNS server may query root servers, then TLD servers (.com), then authoritative servers
4. IP address returned and cached (TTL = Time To Live)

### Step 2: TCP Connection (The Three-Way Handshake)

Before any HTTP data is sent, a TCP connection must be established:

```
Client                    Server
   |                         |
   |------- SYN ------------>|  "I want to connect"
   |                         |
   |<----- SYN-ACK ----------|  "OK, I acknowledge"
   |                         |
   |------- ACK ------------>|  "Great, let's talk"
   |                         |
   [Connection Established]
```

### Step 3: TLS Handshake (For HTTPS)

For secure connections, another handshake occurs:

```mermaid
sequenceDiagram
    participant Client
    participant Server

    Client->>Server: ClientHello (supported ciphers, TLS version)
    Server-->>Client: ServerHello (chosen cipher) + Certificate
    Client->>Client: Verify Certificate
    Client->>Server: Key Exchange (encrypted with server public key)
    Server-->>Client: Finished
    Note over Client,Server: All further communication is encrypted
```
**Why this matters:**

- Ensures you're talking to the real server (not an imposter)
- Establishes encryption keys
- All API data is encrypted in transit

### Step 4: HTTP Request Anatomy

A complete HTTP request looks like this on the wire:

```http
POST /api/v1/users HTTP/1.1
Host: api.example.com
User-Agent: Mozilla/5.0
Accept: application/json
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
Content-Length: 52
Connection: keep-alive

{"name": "John Doe", "email": "john@example.com"}
```

**Breaking it down:**

- **Request Line**: `POST /api/v1/users HTTP/1.1` (method, path, protocol)
- **Headers**: Key-value metadata about the request
- **Empty Line**: Separates headers from body
- **Body**: The actual data payload

### Step 5: Server-Side Processing

What happens when the server receives your request:

```mermaid
flowchart TD
    A[Incoming Request] --> B[Load Balancer]
    B --> C[Reverse Proxy/nginx]
    C --> D[Application Server]
    D --> E{Authentication}
    E -->|Invalid| F[401 Unauthorized]
    E -->|Valid| G{Authorization}
    G -->|Forbidden| H[403 Forbidden]
    G -->|Allowed| I[Route Matching]
    I --> J[Controller/Handler]
    J --> K[Business Logic]
    K --> L[Database Query]
    L --> M[Serialize Response]
    M --> N[Send Response]
```

### Step 6: HTTP Response Anatomy

```http
HTTP/1.1 201 Created
Date: Thu, 29 Jan 2026 10:30:00 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 127
X-Request-Id: abc123
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
Cache-Control: no-cache

{
  "data": {
    "id": 456,
    "name": "John Doe",
    "email": "john@example.com",
    "created_at": "2026-01-29T10:30:00Z"
  }
}
```

### Understanding Connection Persistence

**HTTP/1.0**: New TCP connection for each request (slow)
**HTTP/1.1**: Keep-Alive connections (reuse TCP connection)
**HTTP/2**: Multiplexing (multiple requests over single connection)
**HTTP/3**: QUIC protocol (UDP-based, even faster)

```bash
# See HTTP version in curl
curl -v --http2 https://api.github.com/users/octocat
```

---

## Module 5: Consuming APIs - Deep Dive

### Tools for Testing and Debugging APIs

#### 1. curl - The Swiss Army Knife

```bash
# Basic GET request
curl https://api.github.com/users/octocat

# Verbose mode - see everything
curl -v https://api.github.com/users/octocat

# See only headers
curl -I https://api.github.com/users/octocat

# Follow redirects
curl -L https://example.com/api

# POST with JSON
curl -X POST https://api.example.com/users \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{"name": "John", "email": "john@example.com"}'

# POST with form data
curl -X POST https://api.example.com/upload \
  -F "file=@/path/to/file.pdf" \
  -F "description=My document"

# PUT request
curl -X PUT https://api.example.com/users/123 \
  -H "Content-Type: application/json" \
  -d '{"name": "John Updated"}'

# DELETE request
curl -X DELETE https://api.example.com/users/123

# Save response to file
curl -o response.json https://api.example.com/data

# Include timing information
curl -w "\nTime: %{time_total}s\n" https://api.example.com/users

# Send cookies
curl -b "session=abc123" https://api.example.com/profile

# Custom timeout
curl --connect-timeout 5 --max-time 10 https://api.example.com/slow
```

#### 2. Browser DevTools - Network Tab

**How to use:**

1. Open DevTools (F12 or Cmd+Option+I)
2. Go to Network tab
3. Filter by "XHR" or "Fetch" to see API calls
4. Click any request to see:
  - Headers (request and response)
  - Payload (request body)
  - Preview (formatted response)
  - Timing (how long each phase took)
  - Cookies

**Pro tips:**

- Right-click request → "Copy as cURL" to reproduce in terminal
- Check "Preserve log" to keep requests across page navigations
- Use "Throttling" to simulate slow connections

### Making Requests in Code - Comprehensive Examples

#### Python with requests library

```python
import requests
from requests.adapters import HTTPAdapter
from urllib3.util.retry import Retry

# ============================================
# BASIC REQUESTS
# ============================================

# Simple GET
response = requests.get('https://api.github.com/users/octocat')
print(response.status_code)  # 200
print(response.headers['content-type'])  # application/json
data = response.json()  # Parse JSON response

# GET with query parameters
response = requests.get(
    'https://api.github.com/search/repositories',
    params={
        'q': 'python',
        'sort': 'stars',
        'order': 'desc',
        'per_page': 10
    }
)
# Results in: /search/repositories?q=python&sort=stars&order=desc&per_page=10

# POST with JSON body
response = requests.post(
    'https://api.example.com/users',
    json={'name': 'John', 'email': 'john@example.com'},  # auto sets Content-Type
    headers={'Authorization': 'Bearer YOUR_TOKEN'}
)
created_user = response.json()

# PUT (full update)
response = requests.put(
    'https://api.example.com/users/123',
    json={'name': 'John Doe', 'email': 'johndoe@example.com', 'role': 'admin'}
)

# PATCH (partial update)
response = requests.patch(
    'https://api.example.com/users/123',
    json={'email': 'newemail@example.com'}  # Only update email
)

# DELETE
response = requests.delete('https://api.example.com/users/123')

# ============================================
# HANDLING RESPONSES
# ============================================

response = requests.get('https://api.example.com/data')

# Check if request was successful
if response.ok:  # True for status codes 200-299
    data = response.json()
else:
    print(f"Error: {response.status_code}")
    print(response.text)  # Error message from server

# More specific status code handling
if response.status_code == 200:
    data = response.json()
elif response.status_code == 201:
    print("Resource created!")
    data = response.json()
elif response.status_code == 204:
    print("Success, no content returned")
elif response.status_code == 400:
    print("Bad request:", response.json().get('error'))
elif response.status_code == 401:
    print("Unauthorized - check your credentials")
elif response.status_code == 403:
    print("Forbidden - you don't have permission")
elif response.status_code == 404:
    print("Resource not found")
elif response.status_code == 429:
    print("Rate limited - slow down!")
    retry_after = response.headers.get('Retry-After', 60)
    print(f"Retry after {retry_after} seconds")
elif response.status_code >= 500:
    print("Server error - try again later")

# Raise exception for bad status codes
response.raise_for_status()  # Raises HTTPError for 4xx/5xx

# ============================================
# AUTHENTICATION PATTERNS
# ============================================

# API Key in header
response = requests.get(
    'https://api.example.com/data',
    headers={'X-API-Key': 'your-api-key'}
)

# API Key in query parameter
response = requests.get(
    'https://api.example.com/data',
    params={'api_key': 'your-api-key'}
)

# Bearer token (JWT, OAuth)
response = requests.get(
    'https://api.example.com/data',
    headers={'Authorization': 'Bearer eyJhbGciOiJIUzI1NiIs...'}
)

# Basic authentication
response = requests.get(
    'https://api.example.com/data',
    auth=('username', 'password')  # Automatically encodes to Base64
)

# ============================================
# SESSION MANAGEMENT (Connection Reuse)
# ============================================

# Using sessions for multiple requests (more efficient)
session = requests.Session()
session.headers.update({
    'Authorization': 'Bearer YOUR_TOKEN',
    'User-Agent': 'MyApp/1.0'
})

# All requests through session share headers and connection pool
users = session.get('https://api.example.com/users').json()
orders = session.get('https://api.example.com/orders').json()
profile = session.get('https://api.example.com/profile').json()

# ============================================
# RETRY LOGIC AND TIMEOUTS
# ============================================

# Configure retry strategy
retry_strategy = Retry(
    total=3,  # Total retries
    backoff_factor=1,  # Wait 1s, 2s, 4s between retries
    status_forcelist=[429, 500, 502, 503, 504],  # Retry on these status codes
)

adapter = HTTPAdapter(max_retries=retry_strategy)
session = requests.Session()
session.mount("https://", adapter)
session.mount("http://", adapter)

# Set timeouts (connect timeout, read timeout)
response = session.get(
    'https://api.example.com/data',
    timeout=(3.05, 27)  # 3s to connect, 27s to read
)

# ============================================
# FILE UPLOADS
# ============================================

# Upload a file
with open('document.pdf', 'rb') as f:
    response = requests.post(
        'https://api.example.com/upload',
        files={'file': ('document.pdf', f, 'application/pdf')},
        data={'description': 'My document'}  # Additional form fields
    )

# Multiple files
files = [
    ('files', ('file1.pdf', open('file1.pdf', 'rb'), 'application/pdf')),
    ('files', ('file2.pdf', open('file2.pdf', 'rb'), 'application/pdf')),
]
response = requests.post('https://api.example.com/upload', files=files)

# ============================================
# STREAMING LARGE RESPONSES
# ============================================

# Stream large files to avoid loading into memory
response = requests.get('https://api.example.com/large-file', stream=True)
with open('large_file.zip', 'wb') as f:
    for chunk in response.iter_content(chunk_size=8192):
        f.write(chunk)

# ============================================
# REUSABLE API CLIENT CLASS
# ============================================

class APIClient:
    """Reusable API client with authentication and error handling"""

    def __init__(self, base_url: str, token: str):
        self.base_url = base_url.rstrip('/')
        self.session = requests.Session()
        self.session.headers.update({
            'Authorization': f'Bearer {token}',
            'Content-Type': 'application/json'
        })

    def get(self, endpoint: str, params: dict = None) -> dict:
        response = self.session.get(
            f'{self.base_url}{endpoint}',
            params=params,
            timeout=30
        )
        response.raise_for_status()
        return response.json()

    def post(self, endpoint: str, data: dict) -> dict:
        response = self.session.post(
            f'{self.base_url}{endpoint}',
            json=data,
            timeout=30
        )
        response.raise_for_status()
        return response.json()

    def put(self, endpoint: str, data: dict) -> dict:
        response = self.session.put(
            f'{self.base_url}{endpoint}',
            json=data,
            timeout=30
        )
        response.raise_for_status()
        return response.json()

    def delete(self, endpoint: str) -> bool:
        response = self.session.delete(
            f'{self.base_url}{endpoint}',
            timeout=30
        )
        response.raise_for_status()
        return response.status_code == 204

# Usage
api = APIClient('https://api.example.com', 'your-token')
users = api.get('/users', params={'page': 1})
new_user = api.post('/users', {'name': 'John', 'email': 'john@example.com'})
api.put('/users/123', {'name': 'John Updated'})
api.delete('/users/123')
```

### Understanding API Response Patterns

#### Successful Responses

```json
// Single resource
{
  "data": {
    "id": 123,
    "name": "John Doe",
    "email": "john@example.com"
  }
}

// Collection with pagination
{
  "data": [
    { "id": 1, "name": "John" },
    { "id": 2, "name": "Jane" }
  ],
  "pagination": {
    "page": 1,
    "per_page": 20,
    "total": 150,
    "total_pages": 8
  },
  "links": {
    "self": "/users?page=1",
    "next": "/users?page=2",
    "last": "/users?page=8"
  }
}

// With metadata
{
  "data": { ... },
  "meta": {
    "request_id": "abc-123",
    "timestamp": "2026-01-29T10:00:00Z",
    "version": "v1"
  }
}
```

#### Error Responses

```json
// Simple error
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid email format"
  }
}

// Detailed validation errors
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "details": [
      { "field": "email", "message": "Invalid email format" },
      { "field": "password", "message": "Must be at least 8 characters" }
    ]
  }
}

// With request ID for debugging
{
  "error": {
    "code": "INTERNAL_ERROR",
    "message": "Something went wrong",
    "request_id": "abc-123"  // Share this with support
  }
}
```

### Debugging API Issues

#### Common Problems and Solutions

**1. CORS Errors (Browser only)**

```
Access to fetch at 'https://api.example.com' has been blocked by CORS policy
```

- **Cause**: Server doesn't allow requests from your domain
- **Solution**: Server must add `Access-Control-Allow-Origin` header
- **Workaround**: Use a proxy server or backend-to-backend calls

**2. SSL/Certificate Errors**

```bash
# Skip SSL verification (ONLY for testing!)
curl -k https://api.example.com/data
```

**3. Timeout Issues**

- Increase timeout values
- Check if server is overloaded
- Consider pagination for large datasets

**4. Rate Limiting**

```python
import time

def api_call_with_retry(url, max_retries=3):
    for attempt in range(max_retries):
        response = requests.get(url)
        if response.status_code == 429:
            retry_after = int(response.headers.get('Retry-After', 60))
            print(f"Rate limited. Waiting {retry_after}s...")
            time.sleep(retry_after)
        else:
            return response
    raise Exception("Max retries exceeded")
```

**5. Debugging with verbose output**

```bash
# curl verbose mode
curl -v https://api.example.com/data

# See request/response timing
curl -w "@curl-format.txt" -o /dev/null -s https://api.example.com/data
```

---

## Module 6: Building REST APIs with Python

### Python Framework Options


| Framework                 | Best For           | Key Features                   |
| ------------------------- | ------------------ | ------------------------------ |
| **FastAPI**               | Modern APIs, async | Auto docs, type hints, fast    |
| **Django REST Framework** | Full-featured apps | ORM, admin, batteries included |
| **Flask**                 | Simple APIs        | Lightweight, flexible          |


### Example 1: Building with FastAPI (Recommended)

```bash
# Install
pip install fastapi uvicorn pydantic
```

```python
# main.py - Complete FastAPI Example
from fastapi import FastAPI, HTTPException, Depends, Query, Path
from fastapi.middleware.cors import CORSMiddleware
from pydantic import BaseModel, EmailStr, Field
from typing import Optional, List
from datetime import datetime

app = FastAPI(
    title="User API",
    description="A sample REST API built with FastAPI",
    version="1.0.0"
)

# CORS middleware
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

# ============================================
# PYDANTIC MODELS (Request/Response Schemas)
# ============================================

class UserCreate(BaseModel):
    name: str = Field(..., min_length=1, max_length=100)
    email: EmailStr
    role: str = Field(default="user", pattern="^(admin|user|guest)$")

class UserUpdate(BaseModel):
    name: Optional[str] = Field(None, min_length=1, max_length=100)
    email: Optional[EmailStr] = None
    role: Optional[str] = Field(None, pattern="^(admin|user|guest)$")

class User(BaseModel):
    id: int
    name: str
    email: str
    role: str
    created_at: datetime

class UserResponse(BaseModel):
    data: User

class UsersListResponse(BaseModel):
    data: List[User]
    total: int
    page: int
    per_page: int

# ============================================
# IN-MEMORY DATABASE (Use real DB in production)
# ============================================

users_db: dict[int, dict] = {}
next_id = 1

# ============================================
# API ENDPOINTS
# ============================================

@app.get("/users", response_model=UsersListResponse)
def list_users(
    page: int = Query(1, ge=1, description="Page number"),
    per_page: int = Query(10, ge=1, le=100, description="Items per page"),
    role: Optional[str] = Query(None, description="Filter by role")
):
    """List all users with pagination and optional filtering."""
    # Filter users
    filtered = list(users_db.values())
    if role:
        filtered = [u for u in filtered if u["role"] == role]

    # Paginate
    total = len(filtered)
    start = (page - 1) * per_page
    end = start + per_page
    paginated = filtered[start:end]

    return {
        "data": paginated,
        "total": total,
        "page": page,
        "per_page": per_page
    }

@app.get("/users/{user_id}", response_model=UserResponse)
def get_user(user_id: int = Path(..., ge=1, description="User ID")):
    """Get a specific user by ID."""
    if user_id not in users_db:
        raise HTTPException(status_code=404, detail="User not found")
    return {"data": users_db[user_id]}

@app.post("/users", response_model=UserResponse, status_code=201)
def create_user(user: UserCreate):
    """Create a new user."""
    global next_id

    # Check for duplicate email
    for existing in users_db.values():
        if existing["email"] == user.email:
            raise HTTPException(status_code=400, detail="Email already exists")

    new_user = {
        "id": next_id,
        "name": user.name,
        "email": user.email,
        "role": user.role,
        "created_at": datetime.utcnow()
    }
    users_db[next_id] = new_user
    next_id += 1

    return {"data": new_user}

@app.put("/users/{user_id}", response_model=UserResponse)
def replace_user(user_id: int, user: UserCreate):
    """Replace a user entirely (PUT)."""
    if user_id not in users_db:
        raise HTTPException(status_code=404, detail="User not found")

    updated_user = {
        "id": user_id,
        "name": user.name,
        "email": user.email,
        "role": user.role,
        "created_at": users_db[user_id]["created_at"]
    }
    users_db[user_id] = updated_user
    return {"data": updated_user}

@app.patch("/users/{user_id}", response_model=UserResponse)
def update_user(user_id: int, user: UserUpdate):
    """Partially update a user (PATCH)."""
    if user_id not in users_db:
        raise HTTPException(status_code=404, detail="User not found")

    existing = users_db[user_id]
    update_data = user.dict(exclude_unset=True)  # Only include provided fields

    for field, value in update_data.items():
        existing[field] = value

    return {"data": existing}

@app.delete("/users/{user_id}", status_code=204)
def delete_user(user_id: int):
    """Delete a user."""
    if user_id not in users_db:
        raise HTTPException(status_code=404, detail="User not found")
    del users_db[user_id]

# ============================================
# RUN THE SERVER
# ============================================

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)
```

```bash
# Run the server
uvicorn main:app --reload

# Access auto-generated docs
# Swagger UI: http://localhost:8000/docs
# ReDoc: http://localhost:8000/redoc
```

### Example 2: Building with Flask

```bash
# Install
pip install flask flask-restful
```

```python
# app.py - Flask REST API
from flask import Flask, request, jsonify
from functools import wraps

app = Flask(__name__)

users_db = {}
next_id = 1

# ============================================
# ERROR HANDLERS
# ============================================

@app.errorhandler(404)
def not_found(error):
    return jsonify({"error": {"code": "NOT_FOUND", "message": str(error)}}), 404

@app.errorhandler(400)
def bad_request(error):
    return jsonify({"error": {"code": "BAD_REQUEST", "message": str(error)}}), 400

# ============================================
# VALIDATION DECORATOR
# ============================================

def validate_json(*required_fields):
    def decorator(f):
        @wraps(f)
        def wrapper(*args, **kwargs):
            if not request.is_json:
                return jsonify({"error": "Content-Type must be application/json"}), 400

            data = request.get_json()
            missing = [field for field in required_fields if field not in data]
            if missing:
                return jsonify({"error": f"Missing fields: {missing}"}), 400

            return f(*args, **kwargs)
        return wrapper
    return decorator

# ============================================
# ENDPOINTS
# ============================================

@app.route('/users', methods=['GET'])
def list_users():
    page = request.args.get('page', 1, type=int)
    per_page = request.args.get('per_page', 10, type=int)

    users = list(users_db.values())
    start = (page - 1) * per_page
    end = start + per_page

    return jsonify({
        "data": users[start:end],
        "total": len(users),
        "page": page,
        "per_page": per_page
    })

@app.route('/users/<int:user_id>', methods=['GET'])
def get_user(user_id):
    if user_id not in users_db:
        return jsonify({"error": "User not found"}), 404
    return jsonify({"data": users_db[user_id]})

@app.route('/users', methods=['POST'])
@validate_json('name', 'email')
def create_user():
    global next_id
    data = request.get_json()

    user = {
        "id": next_id,
        "name": data["name"],
        "email": data["email"],
        "role": data.get("role", "user")
    }
    users_db[next_id] = user
    next_id += 1

    return jsonify({"data": user}), 201

@app.route('/users/<int:user_id>', methods=['PUT'])
@validate_json('name', 'email')
def update_user(user_id):
    if user_id not in users_db:
        return jsonify({"error": "User not found"}), 404

    data = request.get_json()
    users_db[user_id].update({
        "name": data["name"],
        "email": data["email"],
        "role": data.get("role", users_db[user_id].get("role", "user"))
    })

    return jsonify({"data": users_db[user_id]})

@app.route('/users/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
    if user_id not in users_db:
        return jsonify({"error": "User not found"}), 404
    del users_db[user_id]
    return '', 204

if __name__ == '__main__':
    app.run(debug=True, port=5000)
```

### Example 3: Django REST Framework

```bash
# Install
pip install django djangorestframework
django-admin startproject myapi
cd myapi
python manage.py startapp users
```

```python
# users/models.py
from django.db import models

class User(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField(unique=True)
    role = models.CharField(max_length=20, default='user')
    created_at = models.DateTimeField(auto_now_add=True)

# users/serializers.py
from rest_framework import serializers
from .models import User

class UserSerializer(serializers.ModelSerializer):
    class Meta:
        model = User
        fields = ['id', 'name', 'email', 'role', 'created_at']
        read_only_fields = ['id', 'created_at']

# users/views.py
from rest_framework import viewsets, status
from rest_framework.response import Response
from .models import User
from .serializers import UserSerializer

class UserViewSet(viewsets.ModelViewSet):
    queryset = User.objects.all()
    serializer_class = UserSerializer

    def list(self, request):
        queryset = self.get_queryset()

        # Filter by role
        role = request.query_params.get('role')
        if role:
            queryset = queryset.filter(role=role)

        serializer = self.get_serializer(queryset, many=True)
        return Response({"data": serializer.data})

    def retrieve(self, request, pk=None):
        user = self.get_object()
        serializer = self.get_serializer(user)
        return Response({"data": serializer.data})

    def create(self, request):
        serializer = self.get_serializer(data=request.data)
        serializer.is_valid(raise_exception=True)
        serializer.save()
        return Response({"data": serializer.data}, status=status.HTTP_201_CREATED)

# users/urls.py
from django.urls import path, include
from rest_framework.routers import DefaultRouter
from .views import UserViewSet

router = DefaultRouter()
router.register(r'users', UserViewSet)

urlpatterns = [
    path('api/', include(router.urls)),
]
```

---

## Module 6B: API Design Best Practices

Good API design makes your API intuitive, consistent, and easy to use.

### URL/Endpoint Design

```

# GOOD: Use nouns (resources), not verbs
GET    /users           # List users
GET    /users/123       # Get user 123
POST   /users           # Create user
PUT    /users/123       # Replace user 123
PATCH  /users/123       # Update user 123
DELETE /users/123       # Delete user 123

# BAD: Verbs in URLs (anti-pattern)
GET    /getUsers
POST   /createUser
POST   /deleteUser/123

# GOOD: Nested resources for relationships
GET    /users/123/orders          # Orders for user 123
GET    /users/123/orders/456      # Specific order
POST   /users/123/orders          # Create order for user

# GOOD: Use query parameters for filtering/sorting/pagination
GET    /users?role=admin&sort=-created_at&page=2&limit=20
GET    /orders?status=pending&min_total=100

# GOOD: Use plural nouns consistently
/users, /orders, /products  (not /user, /order, /product)
```

### Consistent Response Format

```python
# Define a standard response structure for your API

# SUCCESS RESPONSES
# Single resource
{
    "data": {
        "id": 123,
        "name": "John Doe",
        "email": "john@example.com"
    }
}

# Collection
{
    "data": [
        {"id": 1, "name": "John"},
        {"id": 2, "name": "Jane"}
    ],
    "pagination": {
        "page": 1,
        "per_page": 20,
        "total": 150,
        "total_pages": 8
    }
}

# ERROR RESPONSES - Be consistent!
{
    "error": {
        "code": "VALIDATION_ERROR",
        "message": "Invalid input data",
        "details": [
            {"field": "email", "message": "Invalid email format"},
            {"field": "age", "message": "Must be a positive integer"}
        ],
        "request_id": "req_abc123"  # For debugging
    }
}
```

### Implementing Consistent Responses in FastAPI

```python
from fastapi import FastAPI, HTTPException, Request
from fastapi.responses import JSONResponse
from pydantic import BaseModel
from typing import Generic, TypeVar, Optional, List
import uuid

T = TypeVar('T')

# ============================================
# STANDARD RESPONSE MODELS
# ============================================

class ErrorDetail(BaseModel):
    field: Optional[str] = None
    message: str

class ErrorResponse(BaseModel):
    code: str
    message: str
    details: Optional[List[ErrorDetail]] = None
    request_id: str

class SuccessResponse(BaseModel, Generic[T]):
    data: T

class PaginatedResponse(BaseModel, Generic[T]):
    data: List[T]
    pagination: dict

# ============================================
# CUSTOM EXCEPTION WITH CONSISTENT FORMAT
# ============================================

class APIError(Exception):
    def __init__(
        self,
        code: str,
        message: str,
        status_code: int = 400,
        details: List[dict] = None
    ):
        self.code = code
        self.message = message
        self.status_code = status_code
        self.details = details

app = FastAPI()

# Add request ID to all requests
@app.middleware("http")
async def add_request_id(request: Request, call_next):
    request_id = str(uuid.uuid4())[:8]
    request.state.request_id = request_id
    response = await call_next(request)
    response.headers["X-Request-ID"] = request_id
    return response

# Global exception handler for consistent error format
@app.exception_handler(APIError)
async def api_error_handler(request: Request, exc: APIError):
    return JSONResponse(
        status_code=exc.status_code,
        content={
            "error": {
                "code": exc.code,
                "message": exc.message,
                "details": exc.details,
                "request_id": request.state.request_id
            }
        }
    )

# Usage
@app.get("/users/{user_id}")
def get_user(user_id: int):
    if user_id <= 0:
        raise APIError(
            code="INVALID_ID",
            message="User ID must be positive",
            status_code=400
        )

    user = users_db.get(user_id)
    if not user:
        raise APIError(
            code="NOT_FOUND",
            message=f"User {user_id} not found",
            status_code=404
        )

    return {"data": user}
```

### HTTP Status Code Guidelines

```python
# Use appropriate status codes consistently

# 2xx SUCCESS
200  # OK - GET, PUT, PATCH succeeded
201  # Created - POST created a resource
204  # No Content - DELETE succeeded (no body)

# 4xx CLIENT ERRORS
400  # Bad Request - Invalid syntax, missing fields
401  # Unauthorized - No/invalid authentication
403  # Forbidden - Authenticated but not authorized
404  # Not Found - Resource doesn't exist
409  # Conflict - Resource already exists
422  # Unprocessable Entity - Valid syntax but semantic errors
429  # Too Many Requests - Rate limited

# 5xx SERVER ERRORS
500  # Internal Server Error - Unexpected server error
502  # Bad Gateway - Upstream service failed
503  # Service Unavailable - Temporarily down
504  # Gateway Timeout - Upstream service timeout
```

### Naming Conventions

```python
# Use consistent naming throughout your API

# JSON field names: snake_case (Python style) or camelCase (JS style)
# Pick ONE and stick with it!

# snake_case (recommended for Python APIs)
{
    "user_id": 123,
    "first_name": "John",
    "created_at": "2026-01-29T10:00:00Z",
    "is_active": true
}

# camelCase (if your clients are primarily JavaScript)
{
    "userId": 123,
    "firstName": "John",
    "createdAt": "2026-01-29T10:00:00Z",
    "isActive": true
}

# Date/Time: Always use ISO 8601 format with timezone
"2026-01-29T10:30:00Z"        # UTC
"2026-01-29T10:30:00+05:30"   # With offset
```

---

## Module 6C: Input Validation & Sanitization

Proper input validation is your first line of defense against attacks.

### Why Input Validation Matters

```mermaid
flowchart TD
    A[Malicious Input] --> B{Validation}
    B -->|No Validation| C[SQL Injection]
    B -->|No Validation| D[XSS Attack]
    B -->|No Validation| E[Command Injection]
    B -->|No Validation| F[Data Corruption]
    B -->|Proper Validation| G[Request Rejected]
    G --> H[Safe API]
```

### Validation with Pydantic (FastAPI)

```python
from fastapi import FastAPI, HTTPException, Query, Path, Body
from pydantic import BaseModel, EmailStr, Field, validator, root_validator
from typing import Optional, List
from datetime import date
import re

app = FastAPI()

# ============================================
# PYDANTIC MODELS WITH VALIDATION
# ============================================

class UserCreate(BaseModel):
    # Required fields with constraints
    name: str = Field(
        ...,  # Required
        min_length=1,
        max_length=100,
        description="User's full name"
    )

    email: EmailStr  # Built-in email validation

    password: str = Field(
        ...,
        min_length=8,
        max_length=128,
        description="Password (min 8 chars)"
    )

    age: int = Field(..., ge=0, le=150, description="Age in years")

    role: str = Field(
        default="user",
        pattern="^(admin|user|guest)$",  # Regex pattern
        description="User role"
    )

    # Optional fields
    phone: Optional[str] = Field(
        None,
        pattern=r"^\+?[1-9]\d{1,14}$",  # E.164 format
        description="Phone number"
    )

    tags: List[str] = Field(
        default=[],
        max_items=10,
        description="User tags"
    )

    # Custom validator for password strength
    @validator('password')
    def password_strength(cls, v):
        if not re.search(r'[A-Z]', v):
            raise ValueError('Password must contain uppercase letter')
        if not re.search(r'[a-z]', v):
            raise ValueError('Password must contain lowercase letter')
        if not re.search(r'\d', v):
            raise ValueError('Password must contain digit')
        if not re.search(r'[!@#$%^&*(),.?":{}|<>]', v):
            raise ValueError('Password must contain special character')
        return v

    # Custom validator for name
    @validator('name')
    def name_must_not_contain_numbers(cls, v):
        if any(char.isdigit() for char in v):
            raise ValueError('Name cannot contain numbers')
        return v.strip()  # Also sanitize by stripping whitespace

    # Validate multiple fields together
    @root_validator
    def check_admin_age(cls, values):
        role = values.get('role')
        age = values.get('age')
        if role == 'admin' and age and age < 18:
            raise ValueError('Admin must be at least 18 years old')
        return values

    class Config:
        # Forbid extra fields (security)
        extra = 'forbid'

        # Example for documentation
        schema_extra = {
            "example": {
                "name": "John Doe",
                "email": "john@example.com",
                "password": "SecureP@ss123",
                "age": 30,
                "role": "user"
            }
        }

# ============================================
# PATH AND QUERY PARAMETER VALIDATION
# ============================================

@app.get("/users/{user_id}")
def get_user(
    user_id: int = Path(
        ...,
        ge=1,  # Greater than or equal to 1
        le=1000000,  # Upper bound
        description="User ID"
    )
):
    return {"user_id": user_id}

@app.get("/users")
def list_users(
    page: int = Query(1, ge=1, le=1000, description="Page number"),
    per_page: int = Query(20, ge=1, le=100, description="Items per page"),
    role: Optional[str] = Query(None, pattern="^(admin|user|guest)$"),
    search: Optional[str] = Query(None, min_length=1, max_length=100)
):
    return {"page": page, "per_page": per_page}

# ============================================
# SANITIZATION HELPERS
# ============================================

import html
import bleach

def sanitize_html(text: str) -> str:
    """Remove all HTML tags."""
    return bleach.clean(text, tags=[], strip=True)

def sanitize_for_display(text: str) -> str:
    """Escape HTML for safe display."""
    return html.escape(text)

def sanitize_filename(filename: str) -> str:
    """Make filename safe for filesystem."""
    # Remove path separators and null bytes
    filename = filename.replace('/', '').replace('\\', '').replace('\x00', '')
    # Only allow safe characters
    return re.sub(r'[^a-zA-Z0-9._-]', '_', filename)

# Use in endpoint
@app.post("/comments")
def create_comment(content: str = Body(..., max_length=1000)):
    # Sanitize user input before storing
    safe_content = sanitize_html(content)
    return {"content": safe_content}
```

### Preventing Common Injection Attacks

```python
# ============================================
# SQL INJECTION PREVENTION
# ============================================

# BAD: String concatenation (VULNERABLE!)
def get_user_bad(user_id: str):
    query = f"SELECT * FROM users WHERE id = {user_id}"
    # If user_id = "1; DROP TABLE users;--" -> SQL injection!

# GOOD: Parameterized queries (SAFE)
from sqlalchemy import text

def get_user_good(db, user_id: int):
    # SQLAlchemy automatically escapes parameters
    result = db.execute(
        text("SELECT * FROM users WHERE id = :user_id"),
        {"user_id": user_id}
    )
    return result.fetchone()

# GOOD: Using ORM (SAFE)
def get_user_orm(db, user_id: int):
    return db.query(User).filter(User.id == user_id).first()

# ============================================
# COMMAND INJECTION PREVENTION
# ============================================

import subprocess
import shlex

# BAD: Shell=True with user input (VULNERABLE!)
def process_file_bad(filename: str):
    subprocess.run(f"cat {filename}", shell=True)
    # If filename = "; rm -rf /" -> Command injection!

# GOOD: Use list arguments without shell (SAFE)
def process_file_good(filename: str):
    # Validate filename first
    if not re.match(r'^[a-zA-Z0-9._-]+$', filename):
        raise ValueError("Invalid filename")

    subprocess.run(["cat", filename], shell=False)

# ============================================
# PATH TRAVERSAL PREVENTION
# ============================================

import os
from pathlib import Path

UPLOAD_DIR = Path("/app/uploads")

# BAD: Direct path concatenation (VULNERABLE!)
def get_file_bad(filename: str):
    return open(f"/app/uploads/{filename}", "rb")
    # If filename = "../../../etc/passwd" -> Path traversal!

# GOOD: Validate and resolve path (SAFE)
def get_file_good(filename: str):
    # Sanitize filename
    safe_filename = sanitize_filename(filename)

    # Resolve full path
    file_path = (UPLOAD_DIR / safe_filename).resolve()

    # Ensure path is within upload directory
    if not str(file_path).startswith(str(UPLOAD_DIR.resolve())):
        raise ValueError("Invalid file path")

    if not file_path.exists():
        raise FileNotFoundError("File not found")

    return open(file_path, "rb")
```

---

## Module 6D: Rate Limiting Implementation

> **When to learn this:** After you've built a basic API and want to make it production-ready. Skip for now if you're just learning!

Rate limiting protects your API from abuse and ensures fair usage.

### Why Rate Limiting?

- **Prevent abuse**: Stop malicious users from overwhelming your API
- **Ensure fairness**: Give all users equal access
- **Protect resources**: Prevent server overload
- **Cost control**: Limit expensive operations

### Rate Limiting Strategies

```mermaid
flowchart TD
    A[Rate Limiting Strategies] --> B[Fixed Window]
    A --> C[Sliding Window]
    A --> D[Token Bucket]
    A --> E[Leaky Bucket]

    B --> F[Simple but bursty at window edges]
    C --> G[Smoother, more accurate]
    D --> H[Allows bursts up to bucket size]
    E --> I[Constant rate, smoothest]
```

### Implementation with slowapi (FastAPI)

```bash
pip install slowapi
```

```python
from fastapi import FastAPI, Request
from slowapi import Limiter, _rate_limit_exceeded_handler
from slowapi.util import get_remote_address
from slowapi.errors import RateLimitExceeded

# Create limiter with key function (identifies clients)
limiter = Limiter(key_func=get_remote_address)

app = FastAPI()
app.state.limiter = limiter
app.add_exception_handler(RateLimitExceeded, _rate_limit_exceeded_handler)

# ============================================
# BASIC RATE LIMITING
# ============================================

@app.get("/api/public")
@limiter.limit("10/minute")  # 10 requests per minute
def public_endpoint(request: Request):
    return {"message": "Public data"}

@app.get("/api/search")
@limiter.limit("30/minute")  # More generous for search
def search(request: Request, q: str):
    return {"results": []}

@app.post("/api/expensive-operation")
@limiter.limit("5/hour")  # Very limited for expensive ops
def expensive_operation(request: Request):
    return {"status": "completed"}

# ============================================
# DIFFERENT LIMITS FOR DIFFERENT USERS
# ============================================

def get_user_tier(request: Request) -> str:
    """Get rate limit based on user tier."""
    # In real app, extract from JWT token or API key
    api_key = request.headers.get("X-API-Key", "")

    # Look up tier from database/cache
    tier_limits = {
        "free": "100/day",
        "basic": "1000/day",
        "premium": "10000/day",
        "enterprise": "100000/day"
    }

    user_tier = get_tier_from_api_key(api_key)  # Your lookup function
    return tier_limits.get(user_tier, "100/day")

@app.get("/api/data")
@limiter.limit(get_user_tier)  # Dynamic limit based on user
def get_data(request: Request):
    return {"data": []}
```

### Custom Rate Limiter with Redis

```python
import redis
import time
from fastapi import FastAPI, Request, HTTPException
from functools import wraps

# Redis connection
redis_client = redis.Redis(host='localhost', port=6379, db=0)

class RateLimiter:
    """Token bucket rate limiter using Redis."""

    def __init__(
        self,
        redis_client: redis.Redis,
        requests_per_minute: int = 60,
        burst_size: int = 10
    ):
        self.redis = redis_client
        self.rate = requests_per_minute / 60  # tokens per second
        self.burst_size = burst_size

    def is_allowed(self, key: str) -> tuple[bool, dict]:
        """Check if request is allowed and return rate limit info."""
        now = time.time()
        pipe = self.redis.pipeline()

        # Get current bucket state
        bucket_key = f"ratelimit:{key}"

        # Lua script for atomic token bucket
        lua_script = """
        local key = KEYS[1]
        local rate = tonumber(ARGV[1])
        local burst = tonumber(ARGV[2])
        local now = tonumber(ARGV[3])

        local bucket = redis.call('HMGET', key, 'tokens', 'last_update')
        local tokens = tonumber(bucket[1]) or burst
        local last_update = tonumber(bucket[2]) or now

        -- Add tokens based on time passed
        local time_passed = now - last_update
        tokens = math.min(burst, tokens + (time_passed * rate))

        local allowed = 0
        if tokens >= 1 then
            tokens = tokens - 1
            allowed = 1
        end

        redis.call('HMSET', key, 'tokens', tokens, 'last_update', now)
        redis.call('EXPIRE', key, 3600)

        return {allowed, tokens, burst}
        """

        result = self.redis.eval(
            lua_script, 1, bucket_key,
            self.rate, self.burst_size, now
        )

        allowed, remaining, limit = result

        return bool(allowed), {
            "X-RateLimit-Limit": str(limit),
            "X-RateLimit-Remaining": str(int(remaining)),
            "X-RateLimit-Reset": str(int(now + (limit - remaining) / self.rate))
        }

# Create rate limiter instance
rate_limiter = RateLimiter(redis_client, requests_per_minute=60, burst_size=10)

# Decorator for rate limiting
def rate_limit(requests_per_minute: int = 60):
    def decorator(func):
        @wraps(func)
        async def wrapper(request: Request, *args, **kwargs):
            # Get client identifier
            client_ip = request.client.host
            api_key = request.headers.get("X-API-Key", "")
            key = api_key or client_ip

            allowed, headers = rate_limiter.is_allowed(key)

            if not allowed:
                raise HTTPException(
                    status_code=429,
                    detail="Rate limit exceeded. Please slow down.",
                    headers=headers
                )

            response = await func(request, *args, **kwargs)

            # Add rate limit headers to response
            # (In practice, use middleware for this)
            return response

        return wrapper
    return decorator

# Usage
app = FastAPI()

@app.get("/api/data")
@rate_limit(requests_per_minute=60)
async def get_data(request: Request):
    return {"data": "Here's your data"}
```

### Rate Limit Response Headers

```python
# Always include these headers in responses
{
    "X-RateLimit-Limit": "100",      # Max requests allowed
    "X-RateLimit-Remaining": "95",   # Requests remaining
    "X-RateLimit-Reset": "1706520000" # Unix timestamp when limit resets
}

# When rate limited (429 response)
{
    "Retry-After": "60"  # Seconds until client can retry
}
```

---

## Module 6E: Logging & Monitoring

> **When to learn this:** After you've built a basic API and want to make it production-ready. Skip for now if you're just learning!

Observability is crucial for debugging, security, and performance optimization.

### What to Log

```mermaid
flowchart TD
    A[API Logging] --> B[Request Logs]
    A --> C[Error Logs]
    A --> D[Security Logs]
    A --> E[Performance Metrics]

    B --> B1[Method, Path, Status]
    B --> B2[Request ID]
    B --> B3[Client IP, User Agent]

    C --> C1[Stack Traces]
    C --> C2[Error Context]

    D --> D1[Auth Failures]
    D --> D2[Rate Limit Hits]
    D --> D3[Suspicious Activity]

    E --> E1[Response Time]
    E --> E2[Database Queries]
    E --> E3[External API Calls]
```

### Structured Logging with Python

```python
import logging
import json
import time
import uuid
from datetime import datetime
from fastapi import FastAPI, Request
from starlette.middleware.base import BaseHTTPMiddleware

# ============================================
# STRUCTURED JSON LOGGER
# ============================================

class JSONFormatter(logging.Formatter):
    """Format logs as JSON for easy parsing."""

    def format(self, record):
        log_data = {
            "timestamp": datetime.utcnow().isoformat() + "Z",
            "level": record.levelname,
            "logger": record.name,
            "message": record.getMessage(),
        }

        # Add extra fields if present
        if hasattr(record, 'request_id'):
            log_data['request_id'] = record.request_id
        if hasattr(record, 'user_id'):
            log_data['user_id'] = record.user_id
        if hasattr(record, 'extra_data'):
            log_data.update(record.extra_data)

        # Add exception info if present
        if record.exc_info:
            log_data['exception'] = self.formatException(record.exc_info)

        return json.dumps(log_data)

# Configure logger
logger = logging.getLogger("api")
logger.setLevel(logging.INFO)

handler = logging.StreamHandler()
handler.setFormatter(JSONFormatter())
logger.addHandler(handler)

# ============================================
# REQUEST LOGGING MIDDLEWARE
# ============================================

class RequestLoggingMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request: Request, call_next):
        # Generate unique request ID
        request_id = str(uuid.uuid4())[:8]
        request.state.request_id = request_id

        # Start timer
        start_time = time.time()

        # Log request
        logger.info(
            f"Request started",
            extra={
                'extra_data': {
                    'request_id': request_id,
                    'method': request.method,
                    'path': request.url.path,
                    'query': str(request.query_params),
                    'client_ip': request.client.host,
                    'user_agent': request.headers.get('user-agent', ''),
                }
            }
        )

        # Process request
        try:
            response = await call_next(request)

            # Calculate duration
            duration_ms = (time.time() - start_time) * 1000

            # Log response
            logger.info(
                f"Request completed",
                extra={
                    'extra_data': {
                        'request_id': request_id,
                        'method': request.method,
                        'path': request.url.path,
                        'status_code': response.status_code,
                        'duration_ms': round(duration_ms, 2),
                    }
                }
            )

            # Add request ID to response headers
            response.headers['X-Request-ID'] = request_id

            return response

        except Exception as e:
            duration_ms = (time.time() - start_time) * 1000

            logger.error(
                f"Request failed: {str(e)}",
                extra={
                    'extra_data': {
                        'request_id': request_id,
                        'method': request.method,
                        'path': request.url.path,
                        'duration_ms': round(duration_ms, 2),
                        'error': str(e),
                    }
                },
                exc_info=True
            )
            raise

app = FastAPI()
app.add_middleware(RequestLoggingMiddleware)

# ============================================
# LOGGING IN ENDPOINTS
# ============================================

@app.post("/users")
async def create_user(request: Request, user_data: dict):
    request_id = request.state.request_id

    logger.info(
        "Creating new user",
        extra={
            'request_id': request_id,
            'extra_data': {
                'email': user_data.get('email'),  # Don't log passwords!
            }
        }
    )

    # ... create user ...

    logger.info(
        "User created successfully",
        extra={
            'request_id': request_id,
            'extra_data': {
                'user_id': new_user_id,
            }
        }
    )

    return {"data": {"id": new_user_id}}
```

### Security Event Logging

```python
# ============================================
# SECURITY EVENTS TO LOG
# ============================================

def log_auth_failure(request: Request, reason: str):
    """Log authentication failures for security monitoring."""
    logger.warning(
        "Authentication failed",
        extra={
            'extra_data': {
                'event_type': 'AUTH_FAILURE',
                'reason': reason,
                'client_ip': request.client.host,
                'user_agent': request.headers.get('user-agent'),
                'path': request.url.path,
            }
        }
    )

def log_rate_limit_exceeded(request: Request, limit: str):
    """Log rate limit violations."""
    logger.warning(
        "Rate limit exceeded",
        extra={
            'extra_data': {
                'event_type': 'RATE_LIMIT_EXCEEDED',
                'limit': limit,
                'client_ip': request.client.host,
                'path': request.url.path,
            }
        }
    )

def log_suspicious_activity(request: Request, activity: str):
    """Log suspicious patterns."""
    logger.warning(
        "Suspicious activity detected",
        extra={
            'extra_data': {
                'event_type': 'SUSPICIOUS_ACTIVITY',
                'activity': activity,
                'client_ip': request.client.host,
                'path': request.url.path,
                'headers': dict(request.headers),
            }
        }
    )

# Usage in auth middleware
@app.middleware("http")
async def auth_middleware(request: Request, call_next):
    token = request.headers.get("Authorization")

    if not token:
        log_auth_failure(request, "Missing token")
        # ... return 401 ...

    if not validate_token(token):
        log_auth_failure(request, "Invalid token")
        # ... return 401 ...

    return await call_next(request)
```

### Performance Monitoring

```python
import time
from contextlib import contextmanager
from dataclasses import dataclass
from typing import Optional

@dataclass
class PerformanceMetrics:
    request_id: str
    total_time_ms: float
    db_time_ms: float = 0
    external_api_time_ms: float = 0

    def to_dict(self):
        return {
            'request_id': self.request_id,
            'total_time_ms': self.total_time_ms,
            'db_time_ms': self.db_time_ms,
            'external_api_time_ms': self.external_api_time_ms,
            'processing_time_ms': self.total_time_ms - self.db_time_ms - self.external_api_time_ms
        }

@contextmanager
def track_time(metrics: PerformanceMetrics, metric_name: str):
    """Context manager to track time for a specific operation."""
    start = time.time()
    try:
        yield
    finally:
        elapsed_ms = (time.time() - start) * 1000
        setattr(metrics, metric_name, getattr(metrics, metric_name, 0) + elapsed_ms)

# Usage
@app.get("/users/{user_id}")
async def get_user(request: Request, user_id: int):
    metrics = PerformanceMetrics(request_id=request.state.request_id, total_time_ms=0)
    start = time.time()

    # Track database time
    with track_time(metrics, 'db_time_ms'):
        user = await db.get_user(user_id)

    # Track external API time
    with track_time(metrics, 'external_api_time_ms'):
        enriched_data = await external_api.get_user_details(user_id)

    metrics.total_time_ms = (time.time() - start) * 1000

    # Log performance metrics
    logger.info(
        "Request performance",
        extra={'extra_data': metrics.to_dict()}
    )

    return {"data": {**user, **enriched_data}}
```

### Log Output Examples

```json
// Request started
{
    "timestamp": "2026-01-29T10:30:00.123Z",
    "level": "INFO",
    "logger": "api",
    "message": "Request started",
    "request_id": "abc12345",
    "method": "POST",
    "path": "/api/users",
    "client_ip": "192.168.1.100",
    "user_agent": "Python/3.11 requests/2.28.0"
}

// Request completed
{
    "timestamp": "2026-01-29T10:30:00.456Z",
    "level": "INFO",
    "logger": "api",
    "message": "Request completed",
    "request_id": "abc12345",
    "method": "POST",
    "path": "/api/users",
    "status_code": 201,
    "duration_ms": 333.5
}

// Security event
{
    "timestamp": "2026-01-29T10:30:01.000Z",
    "level": "WARNING",
    "logger": "api",
    "message": "Authentication failed",
    "event_type": "AUTH_FAILURE",
    "reason": "Invalid token",
    "client_ip": "192.168.1.100",
    "path": "/api/admin/users"
}

// Error with stack trace
{
    "timestamp": "2026-01-29T10:30:02.000Z",
    "level": "ERROR",
    "logger": "api",
    "message": "Request failed: Database connection error",
    "request_id": "def67890",
    "exception": "Traceback (most recent call last):\n  File ..."
}
```

---

## Module 6F: API Versioning - Managing Change Without Breaking Things

> **Why This Matters:** APIs evolve. Features get added, bugs get fixed, and sometimes breaking changes are necessary. Without proper versioning, you'll break every client using your API. Versioning is not optional—it's essential for any production API.

### Why API Versioning is Critical

```
❌ Without Versioning:
   - You change the response format
   - Every mobile app crashes
   - Every integration breaks
   - Angry customers, lost revenue
   - Emergency rollback at 2 AM

✅ With Versioning:
   - You release v2 with new format
   - v1 continues working
   - Clients migrate at their own pace
   - Smooth transition, happy users
```

### The Cost of Not Versioning

Real-world consequences of poor versioning:

| Issue | Impact |
|-------|--------|
| Breaking changes | Client applications crash |
| No deprecation notice | Partners lose trust |
| Forced upgrades | Users abandon your API |
| Inconsistent versions | Debugging nightmare |
| No migration path | Technical debt accumulates |

### Versioning Strategies Compared

#### 1. URL Path Versioning (Recommended for Most APIs)

```python
# The most common and explicit approach
/api/v1/users
/api/v2/users
/api/v3/users
```

**Pros:**
- Immediately visible in URL
- Easy to understand and implement
- Clear separation between versions
- Easy to route in load balancers
- Works with all HTTP clients

**Cons:**
- URL changes between versions
- Can lead to URL proliferation

**Implementation in FastAPI:**

```python
from fastapi import FastAPI, APIRouter

app = FastAPI()

# Version 1 router
v1_router = APIRouter(prefix="/api/v1")

@v1_router.get("/users/{user_id}")
async def get_user_v1(user_id: int):
    """V1: Returns basic user info"""
    return {
        "id": user_id,
        "name": "John Doe",
        "email": "john@example.com"
    }

# Version 2 router with enhanced response
v2_router = APIRouter(prefix="/api/v2")

@v2_router.get("/users/{user_id}")
async def get_user_v2(user_id: int):
    """V2: Returns user with metadata"""
    return {
        "data": {
            "id": user_id,
            "name": "John Doe",
            "email": "john@example.com",
            "created_at": "2026-01-15T10:30:00Z"
        },
        "meta": {
            "version": "2.0",
            "deprecated": False
        }
    }

app.include_router(v1_router)
app.include_router(v2_router)
```

#### 2. Header Versioning

```python
# Version specified in Accept header
Accept: application/vnd.myapi.v2+json

# Or custom header
X-API-Version: 2
API-Version: 2024-01-15
```

**Pros:**
- Clean URLs (no version in path)
- Follows HTTP content negotiation
- Good for date-based versioning

**Cons:**
- Not visible in URL (harder to debug)
- Requires header inspection
- Some clients struggle with custom headers

**Implementation in FastAPI:**

```python
from fastapi import FastAPI, Header, HTTPException
from typing import Optional

app = FastAPI()

@app.get("/users/{user_id}")
async def get_user(
    user_id: int,
    x_api_version: Optional[str] = Header(default="1", alias="X-API-Version")
):
    """Route based on version header"""

    if x_api_version == "1":
        return {"id": user_id, "name": "John Doe"}

    elif x_api_version == "2":
        return {
            "data": {"id": user_id, "name": "John Doe"},
            "meta": {"version": "2"}
        }

    else:
        raise HTTPException(
            status_code=400,
            detail=f"Unsupported API version: {x_api_version}"
        )
```

#### 3. Query Parameter Versioning

```python
# Version as query parameter
/users/123?version=2
/users/123?api-version=2024-01-15
```

**Pros:**
- Easy to implement
- Visible in URL
- Easy to test in browser

**Cons:**
- Clutters query string
- Can conflict with other parameters
- Less RESTful

**Implementation:**

```python
from fastapi import FastAPI, Query

app = FastAPI()

@app.get("/users/{user_id}")
async def get_user(
    user_id: int,
    version: int = Query(default=1, ge=1, le=2)
):
    """Route based on version query parameter"""

    if version == 1:
        return {"id": user_id, "name": "John Doe"}
    else:
        return {
            "data": {"id": user_id, "name": "John Doe"},
            "meta": {"version": version}
        }
```

#### 4. Date-Based Versioning (Stripe Style)

```python
# Stripe's approach - version by date
Stripe-Version: 2024-01-15

# Each date represents a snapshot of the API
```

**Pros:**
- Clear timeline of changes
- Easy to understand deprecation
- Used by major APIs (Stripe, Twilio)

**Cons:**
- Many versions to maintain
- Complex routing logic

### Versioning Best Practices

#### 1. Always Start with v1

```python
# Even for your first release
/api/v1/users  ✅

# Never start without a version
/api/users     ❌  # You'll regret this!
```

#### 2. Maintain Backward Compatibility When Possible

```python
# SAFE changes (no new version needed):
# - Adding new optional fields
# - Adding new endpoints
# - Adding new optional query parameters

# V1 response
{"id": 1, "name": "John"}

# V1 response with new optional field (still v1!)
{"id": 1, "name": "John", "avatar_url": "https://..."}

# BREAKING changes (require new version):
# - Removing fields
# - Changing field types
# - Renaming fields
# - Changing response structure
```

#### 3. Deprecation Strategy

```python
from fastapi import FastAPI, Response
from datetime import datetime, timedelta
import warnings

app = FastAPI()

@app.get("/api/v1/users")
async def get_users_v1(response: Response):
    """
    DEPRECATED: Use /api/v2/users instead.
    This endpoint will be removed on 2026-06-01.
    """
    # Add deprecation headers
    response.headers["Deprecation"] = "true"
    response.headers["Sunset"] = "Sat, 01 Jun 2026 00:00:00 GMT"
    response.headers["Link"] = '</api/v2/users>; rel="successor-version"'

    # Log deprecation usage for monitoring
    # logger.warning(f"Deprecated v1 endpoint called")

    return {"users": [...]}


# Middleware to add deprecation warnings to all v1 endpoints
@app.middleware("http")
async def add_deprecation_warning(request, call_next):
    response = await call_next(request)

    if "/api/v1/" in str(request.url):
        response.headers["X-API-Warn"] = "API v1 is deprecated. Please migrate to v2."

    return response
```

#### 4. Version Lifecycle Management

```
┌─────────────────────────────────────────────────────────────────┐
│                    API Version Lifecycle                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ACTIVE ──────► DEPRECATED ──────► SUNSET ──────► REMOVED      │
│    │                │                  │              │         │
│    │                │                  │              │         │
│  Full support    Works but         Read-only      404 Error    │
│  New features    warns users       No writes      Gone!        │
│                  6+ months         30 days                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Recommended Timeline:**
- **Deprecation Notice**: 6-12 months before removal
- **Sunset Period**: 30-90 days (read-only)
- **Removal**: After sunset period ends

#### 5. Document Version Differences

```python
# In your API documentation, maintain a changelog:

"""
## API Changelog

### v2.0.0 (2026-01-15)
- **BREAKING**: Response now wrapped in `data` object
- **BREAKING**: `user_name` renamed to `name`
- Added: `created_at` field to user response
- Added: Pagination metadata in list responses

### v1.2.0 (2025-10-01)
- Added: `avatar_url` field (optional)
- Added: `/users/search` endpoint

### v1.1.0 (2025-07-15)
- Added: `email_verified` field

### v1.0.0 (2025-01-01)
- Initial release
"""
```

### Complete Versioning Example

```python
"""
Production-ready API versioning with FastAPI
"""
from fastapi import FastAPI, APIRouter, Header, Response, HTTPException
from pydantic import BaseModel
from typing import Optional, List
from datetime import datetime
import logging

# Configure logging
logger = logging.getLogger(__name__)

app = FastAPI(
    title="My Versioned API",
    description="API with proper versioning support",
    version="2.0.0"
)

# ============== Models ==============

# V1 Models
class UserV1(BaseModel):
    id: int
    name: str
    email: str

# V2 Models (enhanced)
class UserV2(BaseModel):
    id: int
    name: str
    email: str
    created_at: datetime
    is_active: bool = True

class ResponseWrapperV2(BaseModel):
    data: UserV2
    meta: dict

# ============== V1 Router ==============

v1_router = APIRouter(
    prefix="/api/v1",
    tags=["v1 - Deprecated"]
)

@v1_router.get(
    "/users/{user_id}",
    response_model=UserV1,
    deprecated=True,  # Shows as deprecated in docs
    summary="Get user (DEPRECATED)"
)
async def get_user_v1(user_id: int, response: Response):
    """
    ⚠️ **DEPRECATED** - Use `/api/v2/users/{user_id}` instead.

    This endpoint will be removed on **June 1, 2026**.
    """
    # Add deprecation headers
    response.headers["Deprecation"] = "true"
    response.headers["Sunset"] = "Sat, 01 Jun 2026 00:00:00 GMT"

    # Log deprecated endpoint usage
    logger.warning(f"Deprecated v1 endpoint called: /users/{user_id}")

    return UserV1(
        id=user_id,
        name="John Doe",
        email="john@example.com"
    )

# ============== V2 Router ==============

v2_router = APIRouter(
    prefix="/api/v2",
    tags=["v2 - Current"]
)

@v2_router.get(
    "/users/{user_id}",
    response_model=ResponseWrapperV2,
    summary="Get user with metadata"
)
async def get_user_v2(user_id: int):
    """
    Get user by ID with full metadata.

    **Changes from v1:**
    - Response wrapped in `data` object
    - Added `created_at` and `is_active` fields
    - Added `meta` object with version info
    """
    user = UserV2(
        id=user_id,
        name="John Doe",
        email="john@example.com",
        created_at=datetime.now(),
        is_active=True
    )

    return ResponseWrapperV2(
        data=user,
        meta={
            "version": "2.0",
            "generated_at": datetime.now().isoformat()
        }
    )

# ============== Version Info Endpoint ==============

@app.get("/api/versions", tags=["API Info"])
async def get_api_versions():
    """Get information about available API versions"""
    return {
        "versions": [
            {
                "version": "v1",
                "status": "deprecated",
                "sunset_date": "2026-06-01",
                "documentation": "/docs#/v1%20-%20Deprecated"
            },
            {
                "version": "v2",
                "status": "current",
                "released": "2026-01-15",
                "documentation": "/docs#/v2%20-%20Current"
            }
        ],
        "current_version": "v2",
        "migration_guide": "https://docs.example.com/migration-v1-to-v2"
    }

# Include routers
app.include_router(v1_router)
app.include_router(v2_router)
```

### Remember: Versioning Rules

```
┌────────────────────────────────────────────────────────────────┐
│                  API Versioning Golden Rules                   │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  1. ALWAYS version from day one (/api/v1/...)                 │
│                                                                │
│  2. NEVER remove fields without a new version                 │
│                                                                │
│  3. ALWAYS provide migration documentation                    │
│                                                                │
│  4. ALWAYS give 6+ months deprecation notice                  │
│                                                                │
│  5. ALWAYS add deprecation headers to old versions            │
│                                                                │
│  6. NEVER force immediate upgrades                            │
│                                                                │
│  7. ALWAYS maintain a changelog                               │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## Module 6G: API Documentation - Your API is Only as Good as Its Docs

> **Critical Truth:** An undocumented API is an unusable API. Even the most brilliantly designed API will fail if developers can't figure out how to use it. Documentation is not optional—it's a core feature of your API.

### Why Documentation is Non-Negotiable

```
┌─────────────────────────────────────────────────────────────────┐
│              The Documentation Reality Check                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ❌ Without Documentation:                                      │
│     • Developers won't use your API                            │
│     • Support tickets flood in                                 │
│     • Integration takes weeks instead of hours                 │
│     • Partners get frustrated and leave                        │
│     • You become the documentation (constant questions)        │
│                                                                 │
│  ✅ With Great Documentation:                                   │
│     • Self-service integration                                 │
│     • Reduced support burden                                   │
│     • Faster adoption                                          │
│     • Happy developers = successful API                        │
│     • You can sleep at night                                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### The OpenAPI Specification (Swagger)

OpenAPI (formerly Swagger) is the **industry standard** for API documentation. It's a machine-readable format that describes your entire API.

#### What OpenAPI Provides

```yaml
# openapi.yaml - The contract for your API
openapi: 3.1.0
info:
  title: My Awesome API
  description: |
    This API provides user management functionality.

    ## Authentication
    All endpoints require Bearer token authentication.

    ## Rate Limits
    - 100 requests per minute for free tier
    - 1000 requests per minute for paid tier
  version: 2.0.0
  contact:
    name: API Support
    email: api-support@example.com
    url: https://support.example.com
  license:
    name: MIT
    url: https://opensource.org/licenses/MIT

servers:
  - url: https://api.example.com/v2
    description: Production server
  - url: https://staging-api.example.com/v2
    description: Staging server
  - url: http://localhost:8000/v2
    description: Local development

paths:
  /users:
    get:
      summary: List all users
      description: |
        Returns a paginated list of users.

        **Permissions required:** `users:read`
      operationId: listUsers
      tags:
        - Users
      parameters:
        - name: page
          in: query
          description: Page number (1-indexed)
          schema:
            type: integer
            minimum: 1
            default: 1
        - name: limit
          in: query
          description: Items per page
          schema:
            type: integer
            minimum: 1
            maximum: 100
            default: 20
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/UserList'
              example:
                data:
                  - id: 1
                    name: John Doe
                    email: john@example.com
                  - id: 2
                    name: Jane Smith
                    email: jane@example.com
                pagination:
                  total: 150
                  page: 1
                  limit: 20
        '401':
          $ref: '#/components/responses/Unauthorized'
        '429':
          $ref: '#/components/responses/RateLimited'

  /users/{userId}:
    get:
      summary: Get user by ID
      description: Returns a single user by their unique identifier.
      operationId: getUserById
      tags:
        - Users
      parameters:
        - name: userId
          in: path
          required: true
          description: Unique user identifier
          schema:
            type: integer
            minimum: 1
          example: 123
      responses:
        '200':
          description: User found
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
        '404':
          $ref: '#/components/responses/NotFound'

components:
  schemas:
    User:
      type: object
      required:
        - id
        - name
        - email
      properties:
        id:
          type: integer
          description: Unique identifier
          example: 123
        name:
          type: string
          description: User's full name
          example: John Doe
        email:
          type: string
          format: email
          description: User's email address
          example: john@example.com
        created_at:
          type: string
          format: date-time
          description: Account creation timestamp
          example: "2026-01-15T10:30:00Z"

    UserList:
      type: object
      properties:
        data:
          type: array
          items:
            $ref: '#/components/schemas/User'
        pagination:
          $ref: '#/components/schemas/Pagination'

    Pagination:
      type: object
      properties:
        total:
          type: integer
          description: Total number of items
        page:
          type: integer
          description: Current page number
        limit:
          type: integer
          description: Items per page

  responses:
    Unauthorized:
      description: Authentication required
      content:
        application/json:
          schema:
            type: object
            properties:
              error:
                type: string
                example: "Invalid or missing authentication token"

    NotFound:
      description: Resource not found
      content:
        application/json:
          schema:
            type: object
            properties:
              error:
                type: string
                example: "User not found"

    RateLimited:
      description: Rate limit exceeded
      headers:
        X-RateLimit-Limit:
          schema:
            type: integer
          description: Request limit per minute
        X-RateLimit-Remaining:
          schema:
            type: integer
          description: Remaining requests
        X-RateLimit-Reset:
          schema:
            type: integer
          description: Unix timestamp when limit resets
      content:
        application/json:
          schema:
            type: object
            properties:
              error:
                type: string
                example: "Rate limit exceeded. Try again in 60 seconds."

  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
      description: JWT token obtained from /auth/login

security:
  - bearerAuth: []

tags:
  - name: Users
    description: User management operations
  - name: Authentication
    description: Login and token management
```

### FastAPI: Auto-Generated Documentation

FastAPI automatically generates OpenAPI documentation from your code. This is one of its killer features!

```python
"""
FastAPI automatically generates beautiful, interactive documentation
"""
from fastapi import FastAPI, Query, Path, HTTPException, Depends
from fastapi.security import HTTPBearer, HTTPAuthorizationCredentials
from pydantic import BaseModel, Field, EmailStr
from typing import List, Optional
from datetime import datetime
from enum import Enum

# ============== App Configuration ==============

app = FastAPI(
    title="User Management API",
    description="""
## Overview

This API provides comprehensive user management functionality.

## Features

* **User CRUD** - Create, read, update, delete users
* **Authentication** - JWT-based authentication
* **Pagination** - Efficient data retrieval

## Authentication

All endpoints (except `/auth/login`) require a Bearer token:

```
Authorization: Bearer <your-jwt-token>
```

## Rate Limits

| Tier | Requests/minute |
|------|-----------------|
| Free | 100 |
| Pro | 1,000 |
| Enterprise | 10,000 |

## Support

- Email: api-support@example.com
- Docs: https://docs.example.com
    """,
    version="2.0.0",
    terms_of_service="https://example.com/terms",
    contact={
        "name": "API Support Team",
        "url": "https://example.com/support",
        "email": "api@example.com"
    },
    license_info={
        "name": "MIT",
        "url": "https://opensource.org/licenses/MIT"
    },
    openapi_tags=[
        {
            "name": "Users",
            "description": "Operations for managing users",
        },
        {
            "name": "Authentication",
            "description": "Login and token operations",
        }
    ]
)

# ============== Models with Documentation ==============

class UserRole(str, Enum):
    """User role enumeration"""
    admin = "admin"
    user = "user"
    guest = "guest"

class UserBase(BaseModel):
    """Base user model with common fields"""
    name: str = Field(
        ...,
        min_length=1,
        max_length=100,
        description="User's full name",
        example="John Doe"
    )
    email: EmailStr = Field(
        ...,
        description="User's email address (must be unique)",
        example="john@example.com"
    )
    role: UserRole = Field(
        default=UserRole.user,
        description="User's role in the system"
    )

class UserCreate(UserBase):
    """Model for creating a new user"""
    password: str = Field(
        ...,
        min_length=8,
        max_length=100,
        description="Password (min 8 characters, must include number and special char)",
        example="SecureP@ss123"
    )

    class Config:
        json_schema_extra = {
            "example": {
                "name": "John Doe",
                "email": "john@example.com",
                "role": "user",
                "password": "SecureP@ss123"
            }
        }

class User(UserBase):
    """Complete user model returned by API"""
    id: int = Field(..., description="Unique user identifier", example=123)
    created_at: datetime = Field(..., description="Account creation timestamp")
    is_active: bool = Field(default=True, description="Whether the account is active")

    class Config:
        json_schema_extra = {
            "example": {
                "id": 123,
                "name": "John Doe",
                "email": "john@example.com",
                "role": "user",
                "created_at": "2026-01-15T10:30:00Z",
                "is_active": True
            }
        }

class PaginationMeta(BaseModel):
    """Pagination metadata"""
    total: int = Field(..., description="Total number of items", example=150)
    page: int = Field(..., description="Current page number", example=1)
    limit: int = Field(..., description="Items per page", example=20)
    pages: int = Field(..., description="Total number of pages", example=8)

class UserListResponse(BaseModel):
    """Paginated list of users"""
    data: List[User]
    pagination: PaginationMeta

class ErrorResponse(BaseModel):
    """Standard error response"""
    error: str = Field(..., description="Error message", example="Resource not found")
    detail: Optional[str] = Field(None, description="Additional error details")
    code: Optional[str] = Field(None, description="Error code for programmatic handling")

# ============== Endpoints with Full Documentation ==============

@app.get(
    "/users",
    response_model=UserListResponse,
    tags=["Users"],
    summary="List all users",
    description="""
Retrieve a paginated list of all users in the system.

## Permissions
- Requires `users:read` permission

## Pagination
Use `page` and `limit` parameters to paginate results.
Maximum 100 items per page.

## Filtering
- Filter by role using the `role` parameter
- Search by name using the `search` parameter
    """,
    responses={
        200: {
            "description": "List of users retrieved successfully",
            "content": {
                "application/json": {
                    "example": {
                        "data": [
                            {
                                "id": 1,
                                "name": "John Doe",
                                "email": "john@example.com",
                                "role": "user",
                                "created_at": "2026-01-15T10:30:00Z",
                                "is_active": True
                            }
                        ],
                        "pagination": {
                            "total": 150,
                            "page": 1,
                            "limit": 20,
                            "pages": 8
                        }
                    }
                }
            }
        },
        401: {"model": ErrorResponse, "description": "Authentication required"},
        429: {"model": ErrorResponse, "description": "Rate limit exceeded"}
    }
)
async def list_users(
    page: int = Query(
        default=1,
        ge=1,
        description="Page number (starts at 1)",
        example=1
    ),
    limit: int = Query(
        default=20,
        ge=1,
        le=100,
        description="Number of items per page (max 100)",
        example=20
    ),
    role: Optional[UserRole] = Query(
        default=None,
        description="Filter by user role"
    ),
    search: Optional[str] = Query(
        default=None,
        min_length=1,
        max_length=100,
        description="Search users by name (case-insensitive)"
    )
):
    """
    List all users with pagination and optional filtering.
    """
    # Implementation here
    pass


@app.get(
    "/users/{user_id}",
    response_model=User,
    tags=["Users"],
    summary="Get user by ID",
    description="Retrieve a single user by their unique identifier.",
    responses={
        200: {"description": "User found"},
        404: {
            "model": ErrorResponse,
            "description": "User not found",
            "content": {
                "application/json": {
                    "example": {
                        "error": "User not found",
                        "detail": "No user exists with ID 999",
                        "code": "USER_NOT_FOUND"
                    }
                }
            }
        }
    }
)
async def get_user(
    user_id: int = Path(
        ...,
        ge=1,
        description="Unique user identifier",
        example=123
    )
):
    """
    Get a specific user by their ID.

    - **user_id**: The unique identifier of the user to retrieve
    """
    pass


@app.post(
    "/users",
    response_model=User,
    status_code=201,
    tags=["Users"],
    summary="Create new user",
    description="""
Create a new user account.

## Validation Rules
- **name**: 1-100 characters
- **email**: Must be valid email format, must be unique
- **password**: Minimum 8 characters, must contain number and special character

## Returns
The created user object (without password).
    """,
    responses={
        201: {"description": "User created successfully"},
        400: {"model": ErrorResponse, "description": "Validation error"},
        409: {
            "model": ErrorResponse,
            "description": "Email already exists",
            "content": {
                "application/json": {
                    "example": {
                        "error": "Email already registered",
                        "code": "EMAIL_EXISTS"
                    }
                }
            }
        }
    }
)
async def create_user(user: UserCreate):
    """
    Create a new user with the provided information.
    """
    pass
```

### Documentation Tools Comparison

| Tool | Type | Best For | Auto-Generate |
|------|------|----------|---------------|
| **Swagger UI** | Interactive | Testing endpoints | Yes (FastAPI) |
| **ReDoc** | Reference | Clean reading | Yes (FastAPI) |
| **Stoplight** | Full platform | Enterprise docs | Import OpenAPI |
| **Postman** | Collection | Team collaboration | Export/Import |
| **ReadMe** | Developer portal | Public APIs | Import OpenAPI |

### Accessing FastAPI Documentation

FastAPI provides two documentation UIs out of the box:

```python
# Your FastAPI app automatically serves:

# Swagger UI (interactive)
# http://localhost:8000/docs

# ReDoc (clean reference)
# http://localhost:8000/redoc

# Raw OpenAPI JSON
# http://localhost:8000/openapi.json
```

### Documentation Best Practices

#### 1. Every Endpoint Needs These

```python
@app.get("/users/{user_id}")
async def get_user(user_id: int):
    """
    ✅ Good documentation includes:

    1. SUMMARY: What does this endpoint do?
    2. DESCRIPTION: Detailed explanation
    3. PARAMETERS: What inputs are needed?
    4. RESPONSES: What outputs to expect?
    5. EXAMPLES: Real request/response examples
    6. ERRORS: What can go wrong?
    7. PERMISSIONS: Who can access this?
    """
    pass
```

#### 2. Include Real Examples

```python
class UserCreate(BaseModel):
    name: str
    email: str

    class Config:
        # Always provide realistic examples
        json_schema_extra = {
            "example": {
                "name": "Jane Smith",
                "email": "jane.smith@company.com"
            },
            # Multiple examples for different scenarios
            "examples": {
                "basic": {
                    "summary": "Basic user",
                    "value": {
                        "name": "John Doe",
                        "email": "john@example.com"
                    }
                },
                "admin": {
                    "summary": "Admin user",
                    "value": {
                        "name": "Admin User",
                        "email": "admin@company.com"
                    }
                }
            }
        }
```

#### 3. Document Error Responses

```python
@app.post("/users", responses={
    201: {
        "description": "User created successfully",
        "model": User
    },
    400: {
        "description": "Validation error",
        "content": {
            "application/json": {
                "examples": {
                    "invalid_email": {
                        "summary": "Invalid email format",
                        "value": {
                            "error": "Validation error",
                            "detail": "Invalid email format"
                        }
                    },
                    "missing_field": {
                        "summary": "Required field missing",
                        "value": {
                            "error": "Validation error",
                            "detail": "Field 'name' is required"
                        }
                    }
                }
            }
        }
    },
    409: {
        "description": "Email already exists",
        "content": {
            "application/json": {
                "example": {
                    "error": "Email already registered",
                    "code": "EMAIL_EXISTS"
                }
            }
        }
    }
})
async def create_user(user: UserCreate):
    pass
```

#### 4. Group Related Endpoints with Tags

```python
app = FastAPI()

# Define tags with descriptions
tags_metadata = [
    {
        "name": "Users",
        "description": "Operations for user management. **Requires authentication.**",
    },
    {
        "name": "Authentication",
        "description": "Login, logout, and token refresh operations.",
    },
    {
        "name": "Admin",
        "description": "Administrative operations. **Requires admin role.**",
        "externalDocs": {
            "description": "Admin guide",
            "url": "https://docs.example.com/admin"
        }
    }
]

app = FastAPI(openapi_tags=tags_metadata)

@app.get("/users", tags=["Users"])
async def list_users():
    pass

@app.post("/auth/login", tags=["Authentication"])
async def login():
    pass
```

#### 5. Add Getting Started Guide

```python
app = FastAPI(
    description="""
# Getting Started

## 1. Authentication

First, obtain an access token:

```bash
curl -X POST https://api.example.com/auth/login \\
  -H "Content-Type: application/json" \\
  -d '{"email": "user@example.com", "password": "yourpassword"}'
```

## 2. Make Authenticated Requests

Include the token in all requests:

```bash
curl https://api.example.com/users \\
  -H "Authorization: Bearer YOUR_TOKEN"
```

## 3. Handle Errors

All errors return JSON with this structure:

```json
{
  "error": "Error message",
  "code": "ERROR_CODE",
  "detail": "Additional details"
}
```

## SDKs

- Python: `pip install example-api-client`
- JavaScript: `npm install @example/api-client`

## Support

- Email: api-support@example.com
- Slack: #api-help
    """
)
```

### Exporting Documentation

```python
# Export OpenAPI spec for external tools
import json
from fastapi import FastAPI

app = FastAPI()

# ... your endpoints ...

# Export to file
if __name__ == "__main__":
    # Generate OpenAPI schema
    openapi_schema = app.openapi()

    # Save as JSON
    with open("openapi.json", "w") as f:
        json.dump(openapi_schema, f, indent=2)

    # Save as YAML (requires PyYAML)
    import yaml
    with open("openapi.yaml", "w") as f:
        yaml.dump(openapi_schema, f, default_flow_style=False)

    print("OpenAPI spec exported!")
```

### Documentation Checklist

```
┌────────────────────────────────────────────────────────────────┐
│              API Documentation Checklist                       │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  □ Getting started guide with authentication                  │
│  □ All endpoints documented with descriptions                 │
│  □ Request/response examples for every endpoint               │
│  □ Error responses documented with codes                      │
│  □ Authentication requirements clearly stated                 │
│  □ Rate limits documented                                     │
│  □ Pagination explained with examples                         │
│  □ Changelog maintained                                       │
│  □ SDKs/client libraries documented                          │
│  □ Support contact information                                │
│  □ Terms of service and usage policies                       │
│  □ Interactive testing available (Swagger UI)                │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### Remember: Documentation is a Feature

```
┌────────────────────────────────────────────────────────────────┐
│                Documentation Golden Rules                      │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  1. Write docs BEFORE or WHILE building, not after            │
│                                                                │
│  2. If it's not documented, it doesn't exist                  │
│                                                                │
│  3. Examples are worth a thousand words                       │
│                                                                │
│  4. Keep docs in sync with code (auto-generate!)              │
│                                                                │
│  5. Test your examples - broken examples = broken trust       │
│                                                                │
│  6. Document the "why", not just the "what"                   │
│                                                                │
│  7. Your first user is yourself in 6 months                   │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## Module 6H: Load Testing with Locust

> **Critical for Production:** Never release an API without load testing. You need to know how your API behaves under stress BEFORE your customers find out the hard way.

### Full Guide

For comprehensive load testing documentation, see the dedicated guide:

**[API Load Testing Guide with Locust](./api-load-testing-guide.md)**

The guide covers:
- Why load testing is essential
- Installing and configuring Locust
- Writing your first load test
- Understanding metrics (p95, p99, RPS)
- Test scenarios (baseline, stress, spike, soak)
- Distributed load testing
- CI/CD integration
- Best practices and checklists

### Quick Start

```bash
# Install Locust
pip install locust
```

Create `locustfile.py`:

```python
from locust import HttpUser, task, between

class APIUser(HttpUser):
    wait_time = between(1, 3)

    @task(10)
    def list_items(self):
        self.client.get("/api/v1/items")

    @task(5)
    def get_item(self):
        self.client.get("/api/v1/items/1")

    @task(1)
    def create_item(self):
        self.client.post("/api/v1/items", json={"name": "Test"})
```

Run the test:

```bash
# With web UI
locust -f locustfile.py --host=http://localhost:8000

# Headless (for CI/CD)
locust -f locustfile.py --host=http://localhost:8000 \
    --users 100 --spawn-rate 10 --run-time 5m --headless
```

### Key Metrics to Track

| Metric | Target | Description |
|--------|--------|-------------|
| p95 Response Time | < 500ms | 95% of requests should be this fast |
| Error Rate | < 1% | Percentage of failed requests |
| RPS | Varies | Requests per second your API handles |

### Pre-Release Checklist

```
□ Baseline test completed (establish normal metrics)
□ Load test completed (expected traffic levels)
□ Stress test completed (find breaking point)
□ Spike test completed (sudden traffic surge)
□ P95 < 500ms under expected load
□ Error rate < 1% under expected load
□ Breaking point documented
□ Load tests added to CI/CD
```

**See [API Load Testing Guide](./api-load-testing-guide.md) for complete documentation.**

---

## Module 7: API Security and Authentication

### Why API Security Matters

APIs are the backbone of modern applications, but they're also prime targets for attackers:

- **Data Breaches**: APIs often expose sensitive user data
- **Financial Loss**: Unauthorized access can lead to fraud
- **Reputation Damage**: Security incidents erode user trust
- **Compliance Violations**: GDPR, HIPAA, PCI-DSS require secure data handling

---

### HTTPS: The Foundation of API Security

**HTTPS is not optional for APIs - it's mandatory.** Here's why:

#### What HTTPS Protects Against

```mermaid
flowchart TD
    subgraph attacks [Without HTTPS - Vulnerable To]
        A[Man-in-the-Middle Attack]
        B[Eavesdropping]
        C[Data Tampering]
        D[Credential Theft]
        E[Session Hijacking]
        F[Replay Attacks]
    end

    subgraph protected [With HTTPS - Protected By]
        G[Encryption]
        H[Integrity Checks]
        I[Server Authentication]
    end

    G -->|Prevents| A
    G -->|Prevents| B
    H -->|Prevents| C
    I -->|Prevents| D
```

#### 1. Man-in-the-Middle (MITM) Attacks

Without HTTPS, attackers can intercept and modify API traffic:

```
HTTP (Insecure):
Client ----[API Key: secret123]----> Attacker ----[Modified Request]----> Server
       <---[Sensitive Data]-------- Attacker <----[Response]-----------

HTTPS (Secure):
Client =====[Encrypted Traffic]====> Server
       <=====[Encrypted Traffic]=====

Attacker sees: 0x7f3a9b2c1d4e... (gibberish)
```

**Real-world example**: On public WiFi, an attacker could capture your API tokens and impersonate you.

#### 2. Eavesdropping (Data Interception)

```python
# What an attacker sees with HTTP (INSECURE!)
POST /api/login HTTP/1.1
Host: api.example.com
Content-Type: application/json

{"username": "john", "password": "secret123", "credit_card": "4111-1111-1111-1111"}

# What an attacker sees with HTTPS
0x89 0x4a 0x2f 0x8c 0x3d 0x91 0xb7 0x2e 0x5f 0xa1 0x3c 0x8d...
(Completely encrypted - unreadable without the session key)
```

#### 3. Data Integrity

HTTPS ensures data hasn't been modified in transit:

```python
# Without HTTPS, an attacker could modify your API response:
# Original response from server:
{"balance": 1000.00, "account": "checking"}

# Attacker-modified response (you'd never know!):
{"balance": 0.00, "account": "checking"}

# With HTTPS: Any modification breaks the cryptographic signature
# Client detects tampering and rejects the response
```

#### 4. Server Authentication (Certificates)

HTTPS proves you're talking to the real server, not an imposter:

```mermaid
sequenceDiagram
    participant Client
    participant FakeServer as Attacker's Fake Server
    participant RealServer as Real api.example.com

    Note over Client,FakeServer: Without Certificate Verification
    Client->>FakeServer: Connects to api.example.com (DNS poisoned)
    FakeServer-->>Client: Fake response with stolen data

    Note over Client,RealServer: With HTTPS Certificate Verification
    Client->>RealServer: Request certificate
    RealServer-->>Client: Certificate signed by trusted CA
    Client->>Client: Verify certificate chain
    Client->>RealServer: Encrypted API request
```
---

### How HTTPS Encryption Works for APIs

#### The Three Pillars of HTTPS Security


| Pillar              | What It Does             | How It Helps APIs                    |
| ------------------- | ------------------------ | ------------------------------------ |
| **Confidentiality** | Encrypts all data        | API keys, tokens, user data hidden   |
| **Integrity**       | Detects tampering        | Requests/responses can't be modified |
| **Authentication**  | Verifies server identity | Prevents connecting to fake servers  |


#### Encryption in Action

```python
import requests

# ============================================
# SECURE API CALL (HTTPS)
# ============================================

# Your API key is encrypted in transit
response = requests.post(
    'https://api.example.com/users',  # HTTPS!
    headers={'Authorization': 'Bearer super_secret_token'},
    json={'ssn': '123-45-6789', 'credit_card': '4111111111111111'}
)

# What travels over the network (encrypted):
# TLS Record: 17 03 03 00 45 [encrypted payload...]
# Attacker cannot read: Authorization header, JSON body, or response

# ============================================
# INSECURE API CALL (HTTP) - NEVER DO THIS!
# ============================================

# DANGER: Everything is visible to attackers!
response = requests.post(
    'http://api.example.com/users',  # HTTP - INSECURE!
    headers={'Authorization': 'Bearer super_secret_token'},
    json={'ssn': '123-45-6789'}
)
# Attacker on the network can see EVERYTHING in plain text
```

---

### Implementing HTTPS in Python APIs

#### FastAPI with HTTPS

```python
# main.py
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/secure-data")
def get_secure_data():
    return {"message": "This is transmitted securely over HTTPS"}

if __name__ == "__main__":
    # Development with self-signed certificate
    uvicorn.run(
        app,
        host="0.0.0.0",
        port=443,
        ssl_keyfile="./key.pem",
        ssl_certfile="./cert.pem"
    )
```

```bash
# Generate self-signed certificate for development
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes

# For production, use Let's Encrypt (free) or commercial certificates
# Never use self-signed certificates in production!
```

#### Flask with HTTPS

```python
from flask import Flask
import ssl

app = Flask(__name__)

@app.route('/secure-data')
def secure_data():
    return {"message": "Secure!"}

if __name__ == '__main__':
    # Create SSL context
    context = ssl.SSLContext(ssl.PROTOCOL_TLS_SERVER)
    context.load_cert_chain('cert.pem', 'key.pem')

    app.run(host='0.0.0.0', port=443, ssl_context=context)
```

#### Production Setup with Nginx (Recommended)

```nginx
# /etc/nginx/sites-available/api
server {
    listen 80;
    server_name api.example.com;

    # Redirect all HTTP to HTTPS
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name api.example.com;

    # SSL Certificate (Let's Encrypt)
    ssl_certificate /etc/letsencrypt/live/api.example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/api.example.com/privkey.pem;

    # Modern SSL configuration
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256;
    ssl_prefer_server_ciphers off;

    # HSTS - Force HTTPS for 1 year
    add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;

    # Proxy to your Python API
    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

---

### Enforcing HTTPS in Your API

#### 1. Redirect HTTP to HTTPS (FastAPI)

```python
from fastapi import FastAPI, Request
from fastapi.middleware.httpsredirect import HTTPSRedirectMiddleware

app = FastAPI()

# Automatically redirect HTTP to HTTPS
app.add_middleware(HTTPSRedirectMiddleware)

@app.get("/")
def root():
    return {"message": "You're on HTTPS!"}
```

#### 2. Verify HTTPS in Middleware

```python
from fastapi import FastAPI, Request, HTTPException
from starlette.middleware.base import BaseHTTPMiddleware

class EnforceHTTPSMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request: Request, call_next):
        # Check X-Forwarded-Proto header (set by reverse proxy)
        forwarded_proto = request.headers.get("X-Forwarded-Proto", "http")

        if forwarded_proto != "https" and not request.url.scheme == "https":
            raise HTTPException(
                status_code=403,
                detail="HTTPS required. Insecure connections are not allowed."
            )

        return await call_next(request)

app = FastAPI()
app.add_middleware(EnforceHTTPSMiddleware)
```

#### 3. HSTS Header (HTTP Strict Transport Security)

```python
from fastapi import FastAPI
from starlette.middleware.base import BaseHTTPMiddleware
from starlette.responses import Response

class HSTSMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request, call_next):
        response = await call_next(request)
        # Tell browsers to ONLY use HTTPS for this domain for 1 year
        response.headers["Strict-Transport-Security"] = "max-age=31536000; includeSubDomains"
        return response

app = FastAPI()
app.add_middleware(HSTSMiddleware)
```

---

### Making Secure API Calls (Client-Side)

#### Always Verify SSL Certificates

```python
import requests

# ============================================
# CORRECT: Verify SSL certificates (default)
# ============================================
response = requests.get('https://api.example.com/data')
# requests automatically verifies the certificate

# ============================================
# DANGEROUS: Disabling SSL verification
# ============================================
# NEVER do this in production!
response = requests.get('https://api.example.com/data', verify=False)
# Warning: Unverified HTTPS request is being made

# ============================================
# Custom CA certificate (for internal APIs)
# ============================================
response = requests.get(
    'https://internal-api.company.com/data',
    verify='/path/to/company-ca-bundle.crt'
)
```

#### Certificate Pinning (Extra Security)

```python
import requests
import hashlib
import ssl

def get_certificate_fingerprint(hostname: str, port: int = 443) -> str:
    """Get SHA256 fingerprint of server's certificate."""
    import socket
    context = ssl.create_default_context()

    with socket.create_connection((hostname, port)) as sock:
        with context.wrap_socket(sock, server_hostname=hostname) as ssock:
            cert_der = ssock.getpeercert(binary_form=True)
            return hashlib.sha256(cert_der).hexdigest()

# Pin the certificate fingerprint
EXPECTED_FINGERPRINT = "a1b2c3d4e5f6..."  # Your API's certificate fingerprint

def secure_api_call(url: str) -> dict:
    """Make API call with certificate pinning."""
    from urllib.parse import urlparse

    hostname = urlparse(url).hostname
    actual_fingerprint = get_certificate_fingerprint(hostname)

    if actual_fingerprint != EXPECTED_FINGERPRINT:
        raise SecurityError(f"Certificate fingerprint mismatch! Possible MITM attack.")

    return requests.get(url).json()
```

---

### Common HTTPS Mistakes to Avoid


| Mistake                         | Risk                              | Solution                           |
| ------------------------------- | --------------------------------- | ---------------------------------- |
| Using HTTP for APIs             | All data exposed                  | Always use HTTPS                   |
| `verify=False` in requests      | MITM attacks possible             | Never disable in production        |
| Self-signed certs in production | Users get warnings, no trust      | Use Let's Encrypt or commercial CA |
| Expired certificates            | API calls fail, security warnings | Set up auto-renewal                |
| Mixed content (HTTP + HTTPS)    | Partial exposure                  | Ensure all resources use HTTPS     |
| Weak TLS versions (1.0, 1.1)    | Known vulnerabilities             | Use TLS 1.2 or 1.3 only            |


---

### Testing Your API's HTTPS Configuration

```bash
# Test SSL/TLS configuration
openssl s_client -connect api.example.com:443 -tls1_3

# Check certificate details
echo | openssl s_client -connect api.example.com:443 2>/dev/null | \
  openssl x509 -noout -text

# Test with SSL Labs (comprehensive)
# Visit: https://www.ssllabs.com/ssltest/

# Python script to verify HTTPS
python -c "
import requests
import ssl
import socket

hostname = 'api.example.com'

# Check TLS version
context = ssl.create_default_context()
with socket.create_connection((hostname, 443)) as sock:
    with context.wrap_socket(sock, server_hostname=hostname) as ssock:
        print(f'TLS Version: {ssock.version()}')
        print(f'Cipher: {ssock.cipher()}')
        cert = ssock.getpeercert()
        print(f'Issuer: {cert[\"issuer\"]}')
        print(f'Expires: {cert[\"notAfter\"]}')
"
```

---

### Authentication Methods

Now that your transport is secure with HTTPS, let's add authentication:

```mermaid
flowchart TD
    A[Authentication Methods] --> B[API Keys]
    A --> C[Basic Auth]
    A --> D[Token-Based]
    A --> E[OAuth 2.0]
    D --> F[JWT]
    D --> G[Session Tokens]
    E --> H[Authorization Code]
    E --> I[Client Credentials]
```

### 1. API Keys

- Simple string passed in header or query param
- Good for: Server-to-server, public APIs with rate limits
- **Always transmit over HTTPS!**

```python
# Secure API key usage
import requests
import os

API_KEY = os.environ.get('API_KEY')  # Never hardcode!

response = requests.get(
    'https://api.example.com/data',  # HTTPS required!
    headers={'X-API-Key': API_KEY}
)
```

```bash
curl -H "X-API-Key: your-api-key" https://api.example.com/data
```

### 2. JWT (JSON Web Tokens)

- Self-contained tokens with encoded claims
- Structure: `header.payload.signature`
- **The signature prevents tampering, but HTTPS prevents interception**

```python
# Creating and using JWT securely
import jwt
from datetime import datetime, timedelta
import os

SECRET_KEY = os.environ.get('JWT_SECRET')  # Never hardcode!

# Creating JWT
token = jwt.encode(
    {
        "user_id": 123,
        "exp": datetime.utcnow() + timedelta(hours=1),
        "iat": datetime.utcnow(),  # Issued at
        "iss": "api.example.com"   # Issuer
    },
    SECRET_KEY,
    algorithm="HS256"
)

# Verifying JWT
try:
    payload = jwt.decode(
        token,
        SECRET_KEY,
        algorithms=["HS256"],
        options={"require": ["exp", "iat", "iss"]}
    )
except jwt.ExpiredSignatureError:
    print("Token has expired")
except jwt.InvalidTokenError:
    print("Invalid token")
```

#### JWT Authentication in FastAPI

```python
from fastapi import FastAPI, Depends, HTTPException, status
from fastapi.security import HTTPBearer, HTTPAuthorizationCredentials
import jwt

app = FastAPI()
security = HTTPBearer()
SECRET_KEY = "your-secret-key"

async def verify_token(credentials: HTTPAuthorizationCredentials = Depends(security)):
    try:
        payload = jwt.decode(credentials.credentials, SECRET_KEY, algorithms=["HS256"])
        return payload
    except jwt.ExpiredSignatureError:
        raise HTTPException(status_code=401, detail="Token expired")
    except jwt.InvalidTokenError:
        raise HTTPException(status_code=401, detail="Invalid token")

@app.get("/protected")
async def protected_route(user: dict = Depends(verify_token)):
    return {"message": f"Hello, user {user['user_id']}!"}
```

### 3. OAuth 2.0

- Industry standard for delegated authorization
- Used for "Login with Google/GitHub/etc."
- Flows: Authorization Code, Client Credentials, Implicit (deprecated)

```python
# OAuth 2.0 Client Credentials Flow (server-to-server)
import requests

# Step 1: Get access token
token_response = requests.post(
    'https://oauth.example.com/token',
    data={
        'grant_type': 'client_credentials',
        'client_id': os.environ.get('CLIENT_ID'),
        'client_secret': os.environ.get('CLIENT_SECRET'),
        'scope': 'read:users write:users'
    }
)
access_token = token_response.json()['access_token']

# Step 2: Use access token for API calls
response = requests.get(
    'https://api.example.com/users',
    headers={'Authorization': f'Bearer {access_token}'}
)
```

### Security Best Practices Summary


| Practice                         | Why It Matters                 |
| -------------------------------- | ------------------------------ |
| **Always use HTTPS**             | Encrypts all API traffic       |
| **Validate all inputs**          | Prevents injection attacks     |
| **Implement rate limiting**      | Prevents abuse and DDoS        |
| **Use parameterized queries**    | Prevents SQL injection         |
| **Don't expose secrets in URLs** | URLs are logged, cached        |
| **Set proper CORS headers**      | Controls cross-origin access   |
| **Log and monitor access**       | Detect suspicious activity     |
| **Rotate secrets regularly**     | Limits exposure if compromised |
| **Use short-lived tokens**       | Reduces window of attack       |
| **Implement HSTS**               | Forces HTTPS at browser level  |


---

## Module 7B: Advanced Topics

> **Note:** For comprehensive coverage of **API Versioning**, see [Module 6F](#module-6f-api-versioning---managing-change-without-breaking-things). For **API Documentation**, see [Module 6G](#module-6g-api-documentation---your-api-is-only-as-good-as-its-docs). For **Rate Limiting**, see [Module 6D](#module-6d-rate-limiting-implementation).

### Pagination Patterns

Pagination is essential for APIs that return large datasets. Without it, you'll overwhelm clients and servers.

#### Offset-Based Pagination (Simple)

```python
# Request
GET /users?page=2&limit=20

# Response
{
  "data": [
    {"id": 21, "name": "User 21"},
    {"id": 22, "name": "User 22"},
    // ... 18 more users
  ],
  "pagination": {
    "total": 1000,
    "page": 2,
    "limit": 20,
    "total_pages": 50
  }
}
```

**Pros:** Simple to implement, easy to jump to any page
**Cons:** Inconsistent results if data changes between requests

#### Cursor-Based Pagination (Recommended for Large Datasets)

```python
# First request
GET /users?limit=20

# Response includes cursor for next page
{
  "data": [...],
  "pagination": {
    "next_cursor": "eyJpZCI6MjB9",  # Base64 encoded position
    "has_more": true
  }
}

# Next request uses cursor
GET /users?cursor=eyJpZCI6MjB9&limit=20
```

**Pros:** Consistent results, efficient for large datasets
**Cons:** Can't jump to arbitrary pages

#### FastAPI Pagination Implementation

```python
from fastapi import FastAPI, Query
from pydantic import BaseModel
from typing import List, Optional
import base64
import json

app = FastAPI()

class PaginatedResponse(BaseModel):
    data: List[dict]
    pagination: dict

@app.get("/users", response_model=PaginatedResponse)
async def list_users(
    cursor: Optional[str] = Query(None, description="Pagination cursor"),
    limit: int = Query(20, ge=1, le=100, description="Items per page")
):
    # Decode cursor if provided
    start_id = 0
    if cursor:
        decoded = json.loads(base64.b64decode(cursor))
        start_id = decoded.get("last_id", 0)

    # Fetch users (replace with actual DB query)
    users = get_users_after_id(start_id, limit + 1)  # Fetch one extra

    # Check if there are more results
    has_more = len(users) > limit
    if has_more:
        users = users[:limit]  # Remove the extra item

    # Create next cursor
    next_cursor = None
    if has_more and users:
        next_cursor = base64.b64encode(
            json.dumps({"last_id": users[-1]["id"]}).encode()
        ).decode()

    return PaginatedResponse(
        data=users,
        pagination={
            "limit": limit,
            "has_more": has_more,
            "next_cursor": next_cursor
        }
    )
```

### GraphQL (Alternative to REST)

- Query language for APIs
- Client specifies exactly what data it needs
- Single endpoint, flexible queries

```graphql
# GraphQL Query
query {
  user(id: 123) {
    name
    email
    orders {
      id
      total
    }
  }
}
```

### Webhooks (Reverse APIs)

- Server pushes data to client when events occur
- Client provides a callback URL

```mermaid
sequenceDiagram
    participant Client
    participant Server
    Client->>Server: Register webhook URL
    Note over Server: Event occurs
    Server->>Client: POST to webhook URL
    Client-->>Server: 200 OK
```
---

## Module 8: gRPC - Modern High-Performance APIs

> **Advanced Topic:** gRPC is used in large-scale systems and microservices. If you're just starting out, **skip this section** and focus on REST APIs first. Come back when you're comfortable with everything else!

### What is gRPC?

gRPC (gRPC Remote Procedure Calls) is a high-performance, open-source RPC framework developed by Google.

```mermaid
flowchart LR
    subgraph rest [REST API]
        A[Client] -->|HTTP/JSON| B[Server]
    end
    subgraph grpc [gRPC]
        C[Client] -->|HTTP/2 + Protobuf| D[Server]
    end
```

### REST vs gRPC Comparison


| Aspect          | REST                       | gRPC                      |
| --------------- | -------------------------- | ------------------------- |
| Protocol        | HTTP/1.1 or HTTP/2         | HTTP/2 only               |
| Data Format     | JSON (text)                | Protocol Buffers (binary) |
| API Contract    | OpenAPI/Swagger (optional) | .proto files (required)   |
| Code Generation | Optional                   | Built-in                  |
| Streaming       | Limited                    | Bidirectional             |
| Browser Support | Native                     | Requires gRPC-Web         |
| Performance     | Good                       | Excellent                 |
| Human Readable  | Yes                        | No (binary)               |


### When to Use gRPC

**Use gRPC for:**

- Microservices communication (service-to-service)
- High-performance, low-latency requirements
- Streaming data (real-time updates)
- Polyglot environments (multiple languages)
- Strong typing requirements

**Use REST for:**

- Public APIs (browser-friendly)
- Simple CRUD operations
- When human readability matters
- Broad client compatibility

### Protocol Buffers (Protobuf)

Protobuf is the interface definition language (IDL) and serialization format for gRPC.

#### Defining a Service (.proto file)

```protobuf
// user.proto
syntax = "proto3";

package user;

// Service definition
service UserService {
  // Unary RPC - single request, single response
  rpc GetUser(GetUserRequest) returns (User);
  rpc CreateUser(CreateUserRequest) returns (User);
  rpc UpdateUser(UpdateUserRequest) returns (User);
  rpc DeleteUser(DeleteUserRequest) returns (DeleteUserResponse);

  // Server streaming - single request, stream of responses
  rpc ListUsers(ListUsersRequest) returns (stream User);

  // Client streaming - stream of requests, single response
  rpc BatchCreateUsers(stream CreateUserRequest) returns (BatchCreateResponse);

  // Bidirectional streaming - stream both ways
  rpc Chat(stream ChatMessage) returns (stream ChatMessage);
}

// Message definitions
message User {
  int64 id = 1;
  string name = 2;
  string email = 3;
  UserRole role = 4;
  repeated string tags = 5;  // Array/list
  map<string, string> metadata = 6;  // Key-value pairs
  google.protobuf.Timestamp created_at = 7;
}

enum UserRole {
  USER_ROLE_UNSPECIFIED = 0;
  USER_ROLE_ADMIN = 1;
  USER_ROLE_USER = 2;
  USER_ROLE_GUEST = 3;
}

message GetUserRequest {
  int64 id = 1;
}

message CreateUserRequest {
  string name = 1;
  string email = 2;
  UserRole role = 3;
}

message UpdateUserRequest {
  int64 id = 1;
  optional string name = 2;  // Optional field
  optional string email = 3;
}

message DeleteUserRequest {
  int64 id = 1;
}

message DeleteUserResponse {
  bool success = 1;
}

message ListUsersRequest {
  int32 page_size = 1;
  string page_token = 2;
  string filter = 3;  // e.g., "role=admin"
}

message BatchCreateResponse {
  int32 created_count = 1;
  repeated User users = 2;
}

message ChatMessage {
  string user_id = 1;
  string content = 2;
  google.protobuf.Timestamp timestamp = 3;
}
```

### gRPC Communication Patterns

```mermaid
flowchart TD
    subgraph unary [Unary RPC]
        A1[Client] -->|Single Request| B1[Server]
        B1 -->|Single Response| A1
    end

    subgraph server_stream [Server Streaming]
        A2[Client] -->|Single Request| B2[Server]
        B2 -->|Response 1| A2
        B2 -->|Response 2| A2
        B2 -->|Response N| A2
    end

    subgraph client_stream [Client Streaming]
        A3[Client] -->|Request 1| B3[Server]
        A3 -->|Request 2| B3
        A3 -->|Request N| B3
        B3 -->|Single Response| A3
    end

    subgraph bidi [Bidirectional Streaming]
        A4[Client] <-->|Stream| B4[Server]
    end
```

### Building a gRPC Server (Python)

```bash
# Install dependencies
pip install grpcio grpcio-tools

# Generate Python code from .proto
python -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. user.proto
```

```python
# server.py
import grpc
from concurrent import futures
import user_pb2
import user_pb2_grpc

class UserServicer(user_pb2_grpc.UserServiceServicer):
    def __init__(self):
        self.users = {}
        self.next_id = 1

    def GetUser(self, request, context):
        """Unary RPC - Get single user"""
        user_id = request.id
        if user_id not in self.users:
            context.set_code(grpc.StatusCode.NOT_FOUND)
            context.set_details(f'User {user_id} not found')
            return user_pb2.User()
        return self.users[user_id]

    def CreateUser(self, request, context):
        """Unary RPC - Create user"""
        user = user_pb2.User(
            id=self.next_id,
            name=request.name,
            email=request.email,
            role=request.role
        )
        self.users[self.next_id] = user
        self.next_id += 1
        return user

    def ListUsers(self, request, context):
        """Server streaming - Stream all users"""
        for user in self.users.values():
            yield user  # Stream each user

    def BatchCreateUsers(self, request_iterator, context):
        """Client streaming - Receive stream of users"""
        created = []
        for request in request_iterator:
            user = user_pb2.User(
                id=self.next_id,
                name=request.name,
                email=request.email
            )
            self.users[self.next_id] = user
            created.append(user)
            self.next_id += 1

        return user_pb2.BatchCreateResponse(
            created_count=len(created),
            users=created
        )

    def Chat(self, request_iterator, context):
        """Bidirectional streaming - Echo chat"""
        for message in request_iterator:
            # Echo back with modification
            response = user_pb2.ChatMessage(
                user_id="server",
                content=f"Echo: {message.content}"
            )
            yield response

def serve():
    server = grpc.server(futures.ThreadPoolExecutor(max_workers=10))
    user_pb2_grpc.add_UserServiceServicer_to_server(UserServicer(), server)

    # Add insecure port (use SSL in production)
    server.add_insecure_port('[::]:50051')
    server.start()
    print("gRPC server running on port 50051")
    server.wait_for_termination()

if __name__ == '__main__':
    serve()
```

### Building a gRPC Client (Python)

```python
# client.py
import grpc
import user_pb2
import user_pb2_grpc

def run():
    # Create channel (connection)
    with grpc.insecure_channel('localhost:50051') as channel:
        stub = user_pb2_grpc.UserServiceStub(channel)

        # ============================================
        # Unary RPC - Create User
        # ============================================
        print("Creating user...")
        response = stub.CreateUser(user_pb2.CreateUserRequest(
            name="John Doe",
            email="john@example.com",
            role=user_pb2.USER_ROLE_USER
        ))
        print(f"Created user: {response.id} - {response.name}")

        # ============================================
        # Unary RPC - Get User
        # ============================================
        print("\nGetting user...")
        try:
            user = stub.GetUser(user_pb2.GetUserRequest(id=1))
            print(f"Got user: {user.name} ({user.email})")
        except grpc.RpcError as e:
            print(f"Error: {e.code()} - {e.details()}")

        # ============================================
        # Server Streaming - List Users
        # ============================================
        print("\nListing all users (streaming)...")
        for user in stub.ListUsers(user_pb2.ListUsersRequest()):
            print(f"  - {user.id}: {user.name}")

        # ============================================
        # Client Streaming - Batch Create
        # ============================================
        print("\nBatch creating users...")
        def generate_users():
            users = [
                ("Alice", "alice@example.com"),
                ("Bob", "bob@example.com"),
                ("Charlie", "charlie@example.com")
            ]
            for name, email in users:
                yield user_pb2.CreateUserRequest(name=name, email=email)

        response = stub.BatchCreateUsers(generate_users())
        print(f"Created {response.created_count} users")

        # ============================================
        # Bidirectional Streaming - Chat
        # ============================================
        print("\nStarting chat...")
        def chat_messages():
            messages = ["Hello", "How are you?", "Goodbye"]
            for msg in messages:
                yield user_pb2.ChatMessage(user_id="client", content=msg)

        for response in stub.Chat(chat_messages()):
            print(f"  Server: {response.content}")

if __name__ == '__main__':
    run()
```

### gRPC Error Handling

gRPC uses status codes (similar to HTTP but different):


| gRPC Code          | HTTP Equivalent | Meaning             |
| ------------------ | --------------- | ------------------- |
| OK                 | 200             | Success             |
| CANCELLED          | 499             | Client cancelled    |
| UNKNOWN            | 500             | Unknown error       |
| INVALID_ARGUMENT   | 400             | Bad request         |
| NOT_FOUND          | 404             | Resource not found  |
| ALREADY_EXISTS     | 409             | Conflict            |
| PERMISSION_DENIED  | 403             | Forbidden           |
| UNAUTHENTICATED    | 401             | Unauthorized        |
| RESOURCE_EXHAUSTED | 429             | Rate limited        |
| UNAVAILABLE        | 503             | Service unavailable |
| DEADLINE_EXCEEDED  | 504             | Timeout             |


```python
# Server-side error handling
from grpc import StatusCode

def GetUser(self, request, context):
    if request.id <= 0:
        context.set_code(StatusCode.INVALID_ARGUMENT)
        context.set_details('User ID must be positive')
        return user_pb2.User()

    if request.id not in self.users:
        context.set_code(StatusCode.NOT_FOUND)
        context.set_details(f'User {request.id} not found')
        return user_pb2.User()

    return self.users[request.id]

# Client-side error handling
try:
    user = stub.GetUser(user_pb2.GetUserRequest(id=999))
except grpc.RpcError as e:
    if e.code() == grpc.StatusCode.NOT_FOUND:
        print("User not found")
    elif e.code() == grpc.StatusCode.UNAVAILABLE:
        print("Service unavailable, retrying...")
    else:
        print(f"RPC failed: {e.code()} - {e.details()}")
```

### gRPC Authentication and Security

#### TLS/SSL

```python
# Server with TLS
server_credentials = grpc.ssl_server_credentials(
    [(private_key, certificate_chain)]
)
server.add_secure_port('[::]:50051', server_credentials)

# Client with TLS
channel_credentials = grpc.ssl_channel_credentials(
    root_certificates=trusted_certs
)
channel = grpc.secure_channel('localhost:50051', channel_credentials)
```

#### Token-based Authentication (Interceptors)

```python
# Client interceptor - add auth token to all requests
class AuthInterceptor(grpc.UnaryUnaryClientInterceptor):
    def __init__(self, token):
        self.token = token

    def intercept_unary_unary(self, continuation, client_call_details, request):
        metadata = list(client_call_details.metadata or [])
        metadata.append(('authorization', f'Bearer {self.token}'))

        new_details = client_call_details._replace(metadata=metadata)
        return continuation(new_details, request)

# Use interceptor
channel = grpc.insecure_channel('localhost:50051')
intercept_channel = grpc.intercept_channel(channel, AuthInterceptor('your-token'))
stub = user_pb2_grpc.UserServiceStub(intercept_channel)
```

### gRPC Tools

```bash
# grpcurl - curl for gRPC
# Install: brew install grpcurl (macOS)

# List services (requires reflection enabled)
grpcurl -plaintext localhost:50051 list

# Describe service
grpcurl -plaintext localhost:50051 describe user.UserService

# Call method
grpcurl -plaintext -d '{"id": 1}' localhost:50051 user.UserService/GetUser

# grpc_cli - official gRPC CLI
grpc_cli call localhost:50051 user.UserService.GetUser "id: 1"
```

### gRPC-Web for Browsers

Browsers can't make native gRPC calls. gRPC-Web requires a proxy (like Envoy) to translate between gRPC-Web and gRPC.

```mermaid
flowchart LR
    A[Browser] -->|gRPC-Web| B[Envoy Proxy]
    B -->|gRPC| C[gRPC Server]
```
For Python backends serving browser clients, consider using REST/JSON APIs instead, or implement a REST gateway that calls your gRPC services internally.

### gRPC Best Practices

1. **Design APIs carefully** - Proto files are your contract
2. **Use deadlines** - Always set timeouts on client calls
3. **Handle streaming properly** - Close streams when done
4. **Version your APIs** - Use package versioning in proto files
5. **Enable reflection** - Makes debugging easier
6. **Use interceptors** - For logging, auth, metrics
7. **Consider load balancing** - gRPC has built-in support

```python
# Always use deadlines
stub.GetUser(request, timeout=5.0)  # 5 second timeout

# Or with deadline
import datetime
deadline = datetime.datetime.now() + datetime.timedelta(seconds=5)
stub.GetUser(request, deadline=deadline)
```

---

## Hands-On Practice Path

### Beginner Track (Weeks 1-4)

**Week 1: Explore & Consume**
- [ ] Make 10 different API calls using `requests`
- [ ] Try GET, POST, PUT, DELETE methods
- [ ] Practice with JSONPlaceholder and GitHub API
- [ ] Handle errors gracefully (check status codes)

```python
# Week 1 Challenge: Build a GitHub profile viewer
import requests

def get_github_profile(username):
    """Fetch and display a GitHub user's profile."""
    response = requests.get(f'https://api.github.com/users/{username}')

    if response.status_code == 404:
        print(f"User '{username}' not found!")
        return None

    if not response.ok:
        print(f"Error: {response.status_code}")
        return None

    user = response.json()
    print(f"Name: {user['name']}")
    print(f"Bio: {user['bio']}")
    print(f"Public repos: {user['public_repos']}")
    print(f"Followers: {user['followers']}")
    return user

# Try it!
get_github_profile('octocat')
get_github_profile('your-username-here')
```

**Week 2: Build Your First API**
- [ ] Install FastAPI: `pip install fastapi uvicorn`
- [ ] Create a simple "Hello World" API
- [ ] Add GET and POST endpoints
- [ ] Test with curl or your browser

```python
# Week 2 Challenge: Build a Todo API
# Save as main.py and run with: uvicorn main:app --reload

from fastapi import FastAPI

app = FastAPI()
todos = []

@app.get("/")
def read_root():
    return {"message": "Welcome to my Todo API!"}

@app.get("/todos")
def get_todos():
    return {"todos": todos}

@app.post("/todos")
def create_todo(title: str):
    todo = {"id": len(todos) + 1, "title": title, "done": False}
    todos.append(todo)
    return {"message": "Todo created!", "todo": todo}

# Test it:
# curl http://localhost:8000/
# curl http://localhost:8000/todos
# curl -X POST "http://localhost:8000/todos?title=Learn%20APIs"
```

**Week 3: Add Data Validation**
- [ ] Use Pydantic models for request validation
- [ ] Return proper error messages
- [ ] Add more endpoints (update, delete)

**Week 4: Add Authentication**
- [ ] Implement API key authentication
- [ ] Protect certain endpoints
- [ ] Learn about JWT tokens

### Intermediate Track (Weeks 5-8)

**Week 5-6: Production Features**
- [ ] Add rate limiting
- [ ] Implement logging
- [ ] Connect to a database (SQLite is fine to start)

**Week 7-8: Security & Deployment**
- [ ] Ensure HTTPS everywhere
- [ ] Add input sanitization
- [ ] Deploy to a free service (Railway, Render, or Heroku)

---

## Common Mistakes Beginners Make (And How to Avoid Them)

Learn from others' mistakes! Here are the most common issues:

### Mistake 1: Using HTTP instead of HTTPS

```python
# WRONG - Insecure!
requests.get('http://api.example.com/users')

# RIGHT - Always use HTTPS
requests.get('https://api.example.com/users')
```

### Mistake 2: Not Checking Status Codes

```python
# WRONG - Assumes success
response = requests.get('https://api.example.com/users/999')
data = response.json()  # Might crash if user doesn't exist!

# RIGHT - Check first
response = requests.get('https://api.example.com/users/999')
if response.ok:
    data = response.json()
else:
    print(f"Error: {response.status_code}")
```

### Mistake 3: Hardcoding API Keys

```python
# WRONG - Never put secrets in code!
api_key = "sk_live_abc123secret"

# RIGHT - Use environment variables
import os
api_key = os.environ.get('API_KEY')
```

### Mistake 4: Not Handling Timeouts

```python
# WRONG - Can hang forever
response = requests.get('https://slow-api.example.com/data')

# RIGHT - Set a timeout
response = requests.get('https://slow-api.example.com/data', timeout=10)
```

### Mistake 5: Ignoring Rate Limits

```python
# WRONG - Hammering the API
for i in range(1000):
    requests.get('https://api.example.com/data')

# RIGHT - Respect rate limits
import time
for i in range(1000):
    response = requests.get('https://api.example.com/data')
    if response.status_code == 429:  # Too Many Requests
        time.sleep(60)  # Wait before retrying
```

### Mistake 6: Using data= instead of json=

```python
# WRONG - Sends as form data, not JSON
requests.post('https://api.example.com/users', data={'name': 'John'})

# RIGHT - Sends as JSON (what most APIs expect)
requests.post('https://api.example.com/users', json={'name': 'John'})
```

### Mistake 7: Not Reading the API Documentation

Before using any API:
1. Read the authentication section
2. Check rate limits
3. Look at example requests
4. Understand the response format

---

## Capstone Project: Build a Weather Dashboard API

Put everything together! Build an API that:

1. **Fetches weather data** from a public API (OpenWeatherMap)
2. **Stores user preferences** (favorite cities)
3. **Requires authentication** (API keys)
4. **Has rate limiting** (10 requests/minute)
5. **Returns consistent responses**

```python
# Capstone Project Skeleton
from fastapi import FastAPI, HTTPException, Depends, Header
from pydantic import BaseModel
from typing import Optional
import requests

app = FastAPI(title="Weather Dashboard API")

# Your implementation here!
#
# Endpoints to build:
# GET  /weather/{city}     - Get current weather
# POST /favorites          - Add a favorite city
# GET  /favorites          - List favorite cities
# DELETE /favorites/{city} - Remove a favorite
#
# Features to add:
# - API key authentication
# - Rate limiting
# - Error handling
# - Logging

# Hint: Get a free API key from https://openweathermap.org/api
```

---

## Recommended Resources

### Free APIs to Practice With

| API | What it does | Auth needed? |
|-----|--------------|--------------|
| [JSONPlaceholder](https://jsonplaceholder.typicode.com/) | Fake data for testing | No |
| [httpbin.org](https://httpbin.org/) | Echo service for debugging | No |
| [GitHub API](https://api.github.com/) | GitHub data | Optional |
| [OpenWeatherMap](https://openweathermap.org/api) | Weather data | Free API key |
| [PokeAPI](https://pokeapi.co/) | Pokemon data | No |

### Tools

- **Postman** - GUI for testing APIs (great for beginners)
- **curl** - Built into most systems
- **Python requests** - Simple and powerful HTTP library

### Documentation

- [FastAPI Tutorial](https://fastapi.tiangolo.com/tutorial/) - Official, excellent
- [requests Library Docs](https://requests.readthedocs.io/) - Simple and clear
- [HTTP Status Codes](https://httpstatuses.com/) - Quick reference

### Books (When You're Ready)

- "RESTful Web APIs" by Leonard Richardson
- "API Design Patterns" by JJ Geewax

---

## API Implementation Checklist

> **Use this checklist when building a new API.** Print it out, check off items as you go, and don't ship until everything is complete!

### Phase 1: Planning & Design

```
┌────────────────────────────────────────────────────────────────────────────┐
│                         PLANNING CHECKLIST                                 │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  □ Define the API's purpose and target users                               │
│  □ List all resources (nouns) the API will manage                          │
│  □ Define endpoints for each resource (CRUD operations)                    │
│  □ Design URL structure following REST conventions                         │
│  □ Define request/response formats (JSON schema)                           │
│  □ Plan authentication method (API key, JWT, OAuth)                        │
│  □ Identify rate limiting requirements                                     │
│  □ Plan versioning strategy (start with /api/v1/)                          │
│  □ Create OpenAPI spec draft (even before coding)                          │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 2: Project Setup

```
┌────────────────────────────────────────────────────────────────────────────┐
│                         PROJECT SETUP CHECKLIST                            │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  □ Initialize project with proper structure                                │
│      /app                                                                  │
│        /api                                                                │
│          /v1                                                               │
│            /endpoints                                                      │
│            /models                                                         │
│            /schemas                                                        │
│        /core (config, security, dependencies)                              │
│        /services (business logic)                                          │
│        /tests                                                              │
│        main.py                                                             │
│                                                                            │
│  □ Set up virtual environment                                              │
│  □ Create requirements.txt with pinned versions                            │
│  □ Configure environment variables (.env file)                             │
│  □ Set up .gitignore (exclude .env, __pycache__, etc.)                     │
│  □ Initialize git repository                                               │
│  □ Set up pre-commit hooks (black, ruff, mypy)                             │
│  □ Configure logging from the start                                        │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 3: Core Implementation

```
┌────────────────────────────────────────────────────────────────────────────┐
│                      IMPLEMENTATION CHECKLIST                              │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  MODELS & SCHEMAS                                                          │
│  □ Define Pydantic models for all request bodies                           │
│  □ Define Pydantic models for all responses                                │
│  □ Add field validation (min/max length, regex, etc.)                      │
│  □ Add examples to all models (for documentation)                          │
│  □ Create separate Create/Update/Response models                           │
│                                                                            │
│  ENDPOINTS                                                                 │
│  □ Implement all CRUD endpoints                                            │
│  □ Use proper HTTP methods (GET, POST, PUT, PATCH, DELETE)                 │
│  □ Return correct status codes (200, 201, 204, 400, 401, 404, etc.)        │
│  □ Add path parameters with validation                                     │
│  □ Add query parameters for filtering/pagination                           │
│  □ Implement pagination for list endpoints                                 │
│                                                                            │
│  ERROR HANDLING                                                            │
│  □ Create consistent error response format                                 │
│  □ Handle validation errors gracefully                                     │
│  □ Handle not found errors (404)                                           │
│  □ Handle authentication errors (401)                                      │
│  □ Handle authorization errors (403)                                       │
│  □ Handle server errors (500) with safe messages                           │
│  □ Never expose stack traces in production                                 │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 4: Security Implementation

```
┌────────────────────────────────────────────────────────────────────────────┐
│                        SECURITY CHECKLIST                                  │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  HTTPS & TRANSPORT                                                         │
│  □ Enable HTTPS (TLS 1.2+ only)                                            │
│  □ Redirect HTTP to HTTPS                                                  │
│  □ Add HSTS header                                                         │
│  □ Configure secure cookies (if using sessions)                            │
│                                                                            │
│  AUTHENTICATION                                                            │
│  □ Implement chosen auth method (JWT recommended)                          │
│  □ Use secure password hashing (bcrypt/argon2)                             │
│  □ Set appropriate token expiration times                                  │
│  □ Implement token refresh mechanism                                       │
│  □ Add logout/token revocation                                             │
│                                                                            │
│  INPUT VALIDATION                                                          │
│  □ Validate ALL user input (never trust client)                            │
│  □ Sanitize inputs to prevent injection attacks                            │
│  □ Limit request body size                                                 │
│  □ Validate content-type headers                                           │
│                                                                            │
│  HEADERS & CORS                                                            │
│  □ Configure CORS properly (not *)                                         │
│  □ Add security headers:                                                   │
│      □ X-Content-Type-Options: nosniff                                     │
│      □ X-Frame-Options: DENY                                               │
│      □ Content-Security-Policy                                             │
│  □ Remove server version headers                                           │
│                                                                            │
│  SECRETS MANAGEMENT                                                        │
│  □ Store secrets in environment variables                                  │
│  □ Never commit secrets to git                                             │
│  □ Use different secrets for dev/staging/prod                              │
│  □ Rotate secrets periodically                                             │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 5: Rate Limiting & Protection

```
┌────────────────────────────────────────────────────────────────────────────┐
│                      RATE LIMITING CHECKLIST                               │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  □ Implement rate limiting (requests per minute/hour)                      │
│  □ Add rate limit headers to responses:                                    │
│      □ X-RateLimit-Limit                                                   │
│      □ X-RateLimit-Remaining                                               │
│      □ X-RateLimit-Reset                                                   │
│  □ Return 429 Too Many Requests when exceeded                              │
│  □ Consider different limits for:                                          │
│      □ Anonymous users                                                     │
│      □ Authenticated users                                                 │
│      □ Different API tiers                                                 │
│  □ Implement request size limits                                           │
│  □ Add timeout handling                                                    │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 6: Documentation

```
┌────────────────────────────────────────────────────────────────────────────┐
│                      DOCUMENTATION CHECKLIST                               │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  OPENAPI/SWAGGER                                                           │
│  □ All endpoints have summary and description                              │
│  □ All parameters documented with examples                                 │
│  □ All response codes documented                                           │
│  □ All error responses documented with examples                            │
│  □ Authentication requirements documented                                  │
│  □ Tags used to group related endpoints                                    │
│                                                                            │
│  GETTING STARTED                                                           │
│  □ Quick start guide (first API call in < 5 min)                           │
│  □ Authentication guide with examples                                      │
│  □ Common use cases with code samples                                      │
│  □ Error handling guide                                                    │
│                                                                            │
│  REFERENCE                                                                 │
│  □ Rate limit documentation                                                │
│  □ Pagination documentation                                                │
│  □ Changelog/version history                                               │
│  □ Migration guides between versions                                       │
│  □ SDKs/client libraries (if applicable)                                   │
│                                                                            │
│  SUPPORT                                                                   │
│  □ Contact information                                                     │
│  □ Status page link                                                        │
│  □ Terms of service                                                        │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 7: Logging & Monitoring

```
┌────────────────────────────────────────────────────────────────────────────┐
│                    LOGGING & MONITORING CHECKLIST                          │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  LOGGING                                                                   │
│  □ Structured JSON logging configured                                      │
│  □ Request ID tracking (correlation ID)                                    │
│  □ Log all requests (method, path, status, duration)                       │
│  □ Log authentication events (login, logout, failures)                     │
│  □ Log errors with stack traces (not exposed to client)                    │
│  □ Sensitive data redacted from logs (passwords, tokens)                   │
│  □ Different log levels for dev/prod                                       │
│                                                                            │
│  MONITORING                                                                │
│  □ Health check endpoint (/health or /api/health)                          │
│  □ Readiness endpoint (for Kubernetes)                                     │
│  □ Response time tracking                                                  │
│  □ Error rate monitoring                                                   │
│  □ Alerting for high error rates                                           │
│  □ Alerting for slow responses                                             │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 8: Testing

```
┌────────────────────────────────────────────────────────────────────────────┐
│                         TESTING CHECKLIST                                  │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  UNIT TESTS                                                                │
│  □ Test all Pydantic model validations                                     │
│  □ Test business logic functions                                           │
│  □ Test utility functions                                                  │
│                                                                            │
│  INTEGRATION TESTS                                                         │
│  □ Test all endpoints (happy path)                                         │
│  □ Test authentication flows                                               │
│  □ Test authorization (access control)                                     │
│  □ Test error scenarios (400, 401, 403, 404, 500)                          │
│  □ Test pagination                                                         │
│  □ Test rate limiting                                                      │
│                                                                            │
│  SECURITY TESTS                                                            │
│  □ Test SQL injection prevention                                           │
│  □ Test XSS prevention                                                     │
│  □ Test authentication bypass attempts                                     │
│  □ Test with invalid/expired tokens                                        │
│                                                                            │
│  LOAD TESTING WITH LOCUST (See Module 6H)                                  │
│  □ Install Locust: pip install locust                                      │
│  □ Create locustfile.py with realistic user scenarios                      │
│  □ Model actual user behavior (wait times, task weights)                   │
│  □ Baseline test: Establish normal performance metrics                     │
│  □ Load test: Test with expected concurrent users                          │
│  □ Stress test: Find the breaking point                                    │
│  □ Spike test: Simulate sudden traffic surges                              │
│  □ Verify p95 response time < 500ms under expected load                    │
│  □ Verify error rate < 1% under expected load                              │
│  □ Document breaking point and capacity limits                             │
│  □ Add load tests to CI/CD pipeline                                        │
│                                                                            │
│  COVERAGE                                                                  │
│  □ Aim for 80%+ code coverage                                              │
│  □ 100% coverage on critical paths (auth, payments)                        │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 9: Deployment Preparation

```
┌────────────────────────────────────────────────────────────────────────────┐
│                       DEPLOYMENT CHECKLIST                                 │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  CONFIGURATION                                                             │
│  □ Environment-specific configs (dev, staging, prod)                       │
│  □ All secrets in environment variables                                    │
│  □ Database connection pooling configured                                  │
│  □ Proper timeouts configured                                              │
│                                                                            │
│  CONTAINERIZATION (if using Docker)                                        │
│  □ Dockerfile optimized (multi-stage build)                                │
│  □ Non-root user in container                                              │
│  □ Health check in Dockerfile                                              │
│  □ .dockerignore configured                                                │
│                                                                            │
│  CI/CD                                                                     │
│  □ Automated tests run on every PR                                         │
│  □ Linting/formatting checks                                               │
│  □ Security scanning (dependencies)                                        │
│  □ Automated deployment pipeline                                           │
│                                                                            │
│  PRODUCTION READINESS                                                      │
│  □ Debug mode disabled                                                     │
│  □ Proper CORS configuration (not *)                                       │
│  □ Rate limiting enabled                                                   │
│  □ Logging configured for production                                       │
│  □ Error tracking (Sentry or similar)                                      │
│  □ Backup strategy for database                                            │
│  □ Rollback plan documented                                                │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Phase 10: Post-Launch

```
┌────────────────────────────────────────────────────────────────────────────┐
│                       POST-LAUNCH CHECKLIST                                │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  MONITORING                                                                │
│  □ Monitor error rates (should be < 1%)                                    │
│  □ Monitor response times (p95 < 500ms)                                    │
│  □ Monitor rate limit hits                                                 │
│  □ Set up alerts for anomalies                                             │
│                                                                            │
│  MAINTENANCE                                                               │
│  □ Regular dependency updates                                              │
│  □ Security patch process                                                  │
│  □ Log rotation configured                                                 │
│  □ Database maintenance scheduled                                          │
│                                                                            │
│  DOCUMENTATION                                                             │
│  □ Changelog updated with each release                                     │
│  □ Breaking changes communicated to users                                  │
│  □ Deprecation notices sent in advance                                     │
│                                                                            │
│  FEEDBACK                                                                  │
│  □ Monitor API usage patterns                                              │
│  □ Collect developer feedback                                              │
│  □ Track common support issues                                             │
│  □ Plan improvements based on feedback                                     │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Quick Reference: Minimum Viable API Checklist

> **For MVPs and prototypes:** If you're in a hurry, at minimum complete these items:

```
┌────────────────────────────────────────────────────────────────────────────┐
│                    MINIMUM VIABLE API (MVP) CHECKLIST                      │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  MUST HAVE (Non-negotiable)                                                │
│  ──────────────────────────                                                │
│  □ HTTPS enabled                                                           │
│  □ Input validation on ALL endpoints                                       │
│  □ Authentication implemented                                              │
│  □ Proper error responses (no stack traces)                                │
│  □ Basic rate limiting                                                     │
│  □ API versioning (/api/v1/)                                               │
│  □ Auto-generated documentation (Swagger UI)                               │
│  □ Health check endpoint                                                   │
│  □ Basic logging                                                           │
│  □ Tests for critical paths                                                │
│                                                                            │
│  SHOULD HAVE (Add soon after launch)                                       │
│  ────────────────────────────────────                                      │
│  □ Structured JSON logging                                                 │
│  □ Request ID tracking                                                     │
│  □ Comprehensive test coverage                                             │
│  □ Performance monitoring                                                  │
│  □ Detailed documentation with examples                                    │
│                                                                            │
│  NICE TO HAVE (Plan for future)                                            │
│  ──────────────────────────────                                            │
│  □ SDK/client libraries                                                    │
│  □ Webhooks                                                                │
│  □ GraphQL alternative                                                     │
│  □ API analytics                                                           │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## You Did It!

Congratulations on completing this handbook! You now know:

- What APIs are and how they work
- How to consume any REST API with Python
- How to build your own APIs with FastAPI
- How to secure your APIs properly
- How to version and document your APIs
- How to debug API issues
- What it takes to ship a production-ready API

**Next Steps:**
1. Build the capstone project
2. Use the Implementation Checklist for your first real API
3. Contribute to an open-source project that uses APIs
4. Build something YOU want to build!

Remember: The best way to learn is by building. Pick a project, use the checklist, and start coding!

---

*Happy coding!*
