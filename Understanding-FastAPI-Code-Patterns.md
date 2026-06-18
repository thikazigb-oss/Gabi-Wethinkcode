# Understanding FastAPI Code Patterns

## Overview

This exercise focused on understanding advanced FastAPI code patterns, especially dependency injection, middleware, repository patterns, authentication, and role-based access control.

The goal was not only to read the code, but to understand why the code is structured this way and how new features can be added using the same patterns.

# Part 1: Analyzing Complex Code

## Patterns Identified

The FastAPI code uses several important patterns:

* Repository Pattern
* Dependency Injection
* Service Layer
* Middleware
* JWT Authentication
* Role-Based Access Control
* Lifespan Event Handling
* Pydantic Response Models

## Repository Pattern

The `Repository` class is used to separate database access from route logic.

Instead of writing database queries directly inside every endpoint, the repository handles database operations.

Example:

```python
class Repository(Generic[T]):
    def __init__(self, model: Type[T]):
        self.model = model
```

## Why This Is Useful

The repository pattern makes the code easier to maintain because database logic is kept in one place.

If database queries need to change, they can be updated in the repository instead of changing many API endpoints.

## Generic[T]

`Generic[T]` allows the repository to work with different database models.

For example:

```python
Repository[User]
```

means the repository is being used for the `User` model.

This makes the repository reusable instead of creating a completely separate repository structure for every model.

## Dependency Injection

FastAPI dependency injection is used through:

```python
Depends()
```

Example:

```python
db: AsyncSession = Depends(get_db)
```

This means FastAPI will provide a database session when the route runs.

Dependency injection is useful because it:

* Reduces repeated code
* Makes testing easier
* Keeps routes cleaner
* Allows shared logic such as authentication to be reused

## Service Layer

The `UserService` class handles business logic such as:

* Authenticating users
* Verifying passwords
* Creating access tokens

This keeps business rules separate from API routes.

## Middleware

The `TimingMiddleware` measures how long each request takes.

It adds the result to the response header:

```python
response.headers["X-Process-Time"] = str(process_time)
```

This is useful for monitoring performance.

## Role-Based Access Control

The `requires_role("admin")` decorator protects routes that should only be accessed by admin users.

If the user is not a superuser, the code raises:

```python
HTTPException(status_code=403)
```

This prevents unauthorized users from accessing admin-only endpoints.

---

# Part 2: Tracing Execution Flow

## Endpoint Traced

```text
GET /admin/users/
```

## Step-by-Step Request Flow

```text
Client sends request
↓
TimingMiddleware starts timer
↓
FastAPI matches request to /admin/users/
↓
OAuth2 extracts bearer token
↓
get_current_user dependency runs
↓
JWT token is decoded
↓
Username is extracted from token
↓
Database session is created using get_db
↓
UserRepository looks up user
↓
requires_role("admin") checks permissions
↓
If user is admin, list_users runs
↓
UserRepository lists users from database
↓
Response is returned
↓
TimingMiddleware adds X-Process-Time header
```

## Authentication Flow

1. The user sends a token in the Authorization header.
2. FastAPI extracts the token using OAuth2.
3. The token is decoded.
4. The username is retrieved from the token.
5. The user is loaded from the database.
6. If the user is valid, the request continues.

## Authorization Flow

Authentication checks who the user is.

Authorization checks what the user is allowed to do.

For `/admin/users/`, the user must be an admin.

---

# Part 3: Simplifying Complex Concepts

## asynccontextmanager and Lifespan

The lifespan function controls what happens when the application starts and shuts down.

Simple explanation:

* Before `yield`: startup logic
* After `yield`: shutdown logic

This is useful for tasks such as opening and closing resources.

## TimingMiddleware

Middleware runs before and after a request.

In this code, the middleware:

1. Records the start time.
2. Lets the request continue.
3. Measures how long it took.
4. Adds the processing time to the response header.

## JWT Authentication

JWT authentication works like a digital pass.

Simple flow:

1. User logs in.
2. Server creates a token.
3. User sends the token with future requests.
4. Server checks if the token is valid.
5. If valid, the user can access protected routes.

## Dependency Injection in Simple Words

Dependency injection means a function asks FastAPI for what it needs instead of creating it itself.

Example:

```python
current_user: User = Depends(get_current_user)
```

This means:

“Before running this route, please find the current user.”

---

# Part 4: Building Understanding Through Implementation

## New Feature

The challenge was to implement a simple logging system that records user actions such as logins and admin actions.

## How I Would Add This Feature

I would follow the same existing patterns:

1. Create an `ActionLog` model.
2. Create an `ActionLogRepository`.
3. Create an `ActionLogService`.
4. Add logging inside important actions.
5. Use dependency injection where needed.

## Proposed Components

| Component           | Responsibility                          |
| ------------------- | --------------------------------------- |
| ActionLog           | Represents a user action record         |
| ActionLogRepository | Saves and retrieves logs                |
| ActionLogService    | Handles logging business logic          |
| log_user_action()   | Reusable function for recording actions |

## Example Design

```python
class ActionLog(Base):
    __tablename__ = "action_logs"
    id: int
    username: str
    action: str
    timestamp: datetime
```

## Example Service

```python
class ActionLogService:
    def __init__(self, repository):
        self.repository = repository

    async def log_action(self, db, username: str, action: str):
        log = {
            "username": username,
            "action": action,
            "timestamp": datetime.utcnow()
        }
        await self.repository.create(db, log)
```

## Where Logging Would Be Added

| Action           | Where to Add Logging                                     |
| ---------------- | -------------------------------------------------------- |
| User login       | Inside `/token` endpoint after successful authentication |
| Admin list users | Inside `/admin/users/` endpoint                          |
| Failed login     | Inside `/token` endpoint when authentication fails       |

---

# Reflection Questions

## How does implementing this feature help me understand the architecture?

It helped me understand that new features should follow the existing structure instead of being added randomly. The code already separates repositories, services, dependencies, and routes, so logging should follow that same pattern.

## Which design patterns did I find most useful?

The most useful patterns were:

* Repository Pattern
* Dependency Injection
* Service Layer

These patterns make the application easier to extend.

## How would I explain the repository pattern to a colleague?

I would explain that the repository pattern keeps database logic in one place so routes do not need to know the details of database queries.

## How would I explain dependency injection?

Dependency injection means FastAPI provides required objects or values to a route automatically, such as the current user or database session.

## How did tracing the execution flow help?

Tracing the request helped me see where authentication, authorization, database access, and middleware fit into the request lifecycle. This made it clearer where a new logging feature should be added.

---

# Final Reflection

This exercise helped me understand that advanced FastAPI applications are built in layers.

Routes handle requests, dependencies provide shared logic, repositories handle database access, services handle business rules, and middleware handles cross-cutting concerns such as timing.

The biggest lesson I learned is that understanding the request flow makes it easier to safely add new features without breaking the application.
