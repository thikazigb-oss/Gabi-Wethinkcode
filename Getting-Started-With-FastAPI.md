# Getting Started with FastAPI

## Overview

This exercise introduced me to FastAPI, a modern Python framework used to build APIs quickly and efficiently. I used AI to learn the fundamentals, understand FastAPI terminology, create a simple API, and design a small to-do list application.

# Part 1: Understanding FastAPI Fundamentals

## What is FastAPI?

FastAPI is a modern Python web framework designed for building APIs quickly while maintaining high performance.

It is based on:

* Python type hints
* Automatic validation
* Automatic API documentation
* Asynchronous programming support

## FastAPI Compared to Flask and Django

| Feature                 | FastAPI  | Flask               | Django                      |
| ----------------------- | -------- | ------------------- | --------------------------- |
| Performance             | High     | Moderate            | Moderate                    |
| Automatic Documentation | Yes      | No                  | No                          |
| Validation              | Built-in | Requires extensions | Requires forms/serializers  |
| Async Support           | Native   | Limited             | Supported in newer versions |
| Learning Curve          | Moderate | Easy                | Higher                      |

## Key Advantages of FastAPI

* Fast development
* Automatic API documentation
* Built-in validation using Pydantic
* Type-safe development
* Excellent performance

## Essential FastAPI Glossary

| Term            | Meaning                                      |
| --------------- | -------------------------------------------- |
| FastAPI         | Python framework for building APIs           |
| Endpoint        | A URL that performs an action                |
| Route           | Path that maps to a function                 |
| Pydantic        | Data validation library                      |
| Request         | Data sent to the API                         |
| Response        | Data returned from the API                   |
| Query Parameter | Optional data passed in a URL                |
| Path Parameter  | Variable embedded in a URL path              |
| Uvicorn         | ASGI server used to run FastAPI              |
| Async           | Ability to handle multiple tasks efficiently |

---

# Part 2: Creating My First API

## Hello World API

The basic FastAPI application contains:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
async def root():
    return {"message": "Hello World"}
```

## What I Learned

### FastAPI Instance

```python
app = FastAPI()
```

Creates the application.

### Route Decorator

```python
@app.get("/")
```

Tells FastAPI which URL should execute the function.

### Async Function

```python
async def root():
```

Allows FastAPI to handle requests efficiently.

### JSON Response

```python
return {"message": "Hello World"}
```

Automatically returns JSON data.

## Running the Application

Install dependencies:

```bash
pip install fastapi uvicorn
```

Run:

```bash
uvicorn main:app --reload
```

Useful URLs:

```text
http://127.0.0.1:8000
http://127.0.0.1:8000/docs
```

The `/docs` endpoint automatically generates Swagger API documentation.

---

# Part 3: Enhancing the API

## Understanding Pydantic

Pydantic is used for:

* Input validation
* Data modelling
* Automatic documentation

Example:

```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
```

FastAPI automatically validates incoming data.

---

## Error Handling

FastAPI supports custom exceptions.

Example:

```python
raise HTTPException(
    status_code=404,
    detail="Item not found"
)
```

Benefits:

* Better user experience
* Clear API responses
* Easier debugging

---

## Organizing a FastAPI Project

Suggested structure:

```text
app/
├── main.py
├── models/
├── routes/
├── utils/
└── requirements.txt
```

Benefits:

* Easier maintenance
* Better scalability
* Cleaner separation of responsibilities

---

# Part 4: To-Do List API Challenge

## Project Goal

Build a simple To-Do List API using FastAPI.

Required features:

* Create a to-do item
* List all to-do items
* Filter by completed or pending status
* Mark a task as completed
* Delete a task

---

## Pydantic Model

```python
from pydantic import BaseModel
from datetime import date

class TodoItem(BaseModel):
    title: str
    description: str
    due_date: date
    completed: bool = False
```

---

## Planned Endpoints

### Create Task

```text
POST /todos
```

Creates a new task.

---

### List Tasks

```text
GET /todos
```

Returns all tasks.

---

### Filter Tasks

```text
GET /todos?status=pending
GET /todos?status=completed
```

Returns filtered tasks.

---

### Complete Task

```text
PUT /todos/{id}/complete
```

Marks a task as completed.

---

### Delete Task

```text
DELETE /todos/{id}
```

Deletes a task.

---

## Validation Requirements

* Title cannot be empty.
* Due date must be valid.
* Status defaults to pending.
* Invalid IDs return a 404 error.

---

## Error Handling Plan

Examples:

```python
404 Not Found
422 Validation Error
400 Bad Request
```

FastAPI should provide clear error messages for invalid requests.

---

# Key Learnings

## Learning 1

FastAPI uses Python type hints to automatically validate data and generate documentation.

## Learning 2

FastAPI automatically generates API documentation using Swagger UI at:

```text
/ docs
```

which makes testing APIs easier.

## Learning 3

Pydantic models simplify validation and reduce the amount of manual checking developers need to write.

# Reflection

## What did I find most interesting?

The automatic documentation feature was the most interesting because it removes a lot of manual documentation work.

## What was new to me?

The use of Pydantic models and automatic validation was new to me.

## How did AI help?

AI helped explain FastAPI concepts in beginner-friendly language and showed how a larger application can be structured.

## What would I learn next?

I would like to learn:

* Dependency Injection
* Database integration
* Authentication
* Async programming
* Deployment of FastAPI applications

---

# Final Reflection

This exercise helped me understand how FastAPI simplifies API development by combining validation, documentation, and performance into one framework.

The biggest lesson I learned is that FastAPI allows developers to focus more on business logic and less on boilerplate code while still producing professional APIs.
