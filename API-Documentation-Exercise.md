# API Documentation Exercise

Name: Gabisile Buhle Thikazi

## Original API Endpoint Code

# Prompt 1: Comprehensive Endpoint Documentation

## Endpoint

POST /api/users/register

### Purpose

Registers a new user account in the system.

### Request Body

| Field    | Type   | Required | Description                        |
| -------- | ------ | -------- | ---------------------------------- |
| username | String | Yes      | Unique username                    |
| email    | String | Yes      | Valid email address                |
| password | String | Yes      | Password with minimum 8 characters |

### Success Response

**201 Created**

```json
{
  "message": "User registered successfully",
  "user": {
    "id": 1,
    "username": "johndoe",
    "email": "john@example.com",
    "role": "user"
  }
}

### Error Responses

**400 Bad Request**

* Missing required field
* Invalid email format
* Weak password

**409 Conflict**

* Username already exists
* Email already registered

**500 Internal Server Error**

* Database or server failure

### Authentication

No authentication required.

### Example Request

```json
{
  "username": "johndoe",
  "email": "john@example.com",
  "password": "SecurePass123"
}

# Prompt 2: OpenAPI / Swagger Format

openapi: 3.0.0

info:
title: User Registration API
version: 1.0.0

paths:
/api/users/register:
post:
summary: Register a new user

  requestBody:
    required: true

  responses:
    '201':
      description: User registered successfully
    '400':
      description: Validation error
    '409':
      description: User already exists
    '500':
      description: Server error

# Prompt 3: Developer Usage Guide

## User Registration Guide

### Step 1

Send a POST request to:

/api/users/register

### Step 2

Provide:

* username
* email
* password

### Step 3

Review the response.

### Common Errors

| Error                  | Cause                       |
| ---------------------- | --------------------------- |
| Missing required field | Required field not supplied |
| Invalid email          | Incorrect email format      |
| Weak password          | Less than 8 characters      |
| Username taken         | Username already exists     |

### Best Practices

* Validate input before sending.
* Use strong passwords.
* Handle all error responses gracefully.
* Store returned user information securely.

# Reflection

## Which parts of the API were most challenging to document?

The validation rules and different error responses required careful review to ensure all possible outcomes were documented correctly.

## How did you adjust your prompts to get better results?

I provided the full endpoint code and explicitly requested request parameters, response codes, examples, and authentication details.

## Which documentation format did you find most effective?

The Markdown documentation was easiest to read, while the OpenAPI format was best for developers and API tools.

## How would you incorporate this approach into your development workflow?

I would use AI to generate an initial documentation draft whenever creating new endpoints and then review the output for accuracy before publishing.
