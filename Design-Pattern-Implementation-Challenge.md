# Design Pattern Implementation Challenge

## Selected Pattern Opportunity

I selected the **Factory Pattern Opportunity (Python)** involving the Database Connection Manager.

The original code creates multiple database connection types using one large class with many conditional statements.

Supported databases include:

* MySQL
* PostgreSQL
* MongoDB
* Redis

# Step 1: Pattern Opportunity Analysis

## Problem with the Current Design

The `DatabaseConnection` class has several responsibilities:

* Stores configuration
* Builds connection strings
* Handles database-specific logic
* Creates connections

The `connect()` method contains multiple:

```python id="gmj9i4"
if
elif
else
```

statements that check the database type.

Example:

```python id="9ivqoq"
if self.db_type == "mysql":
```

```python id="g13iwu"
elif self.db_type == "postgresql":
```

```python id="r0mivh"
elif self.db_type == "mongodb":
```

As more database types are added, the method becomes larger and harder to maintain.

# Why the Factory Pattern Fits

The Factory Pattern is useful when:

* Object creation is complex.
* Multiple object types exist.
* The client should not need to know creation details.

In this case, different database connections require different initialization logic.

The Factory Pattern allows object creation to be separated from object usage.

# Step 2: Refactoring Approach

## Create Separate Connection Classes

Instead of one large class, create:

```python id="x9qjfi"
MySQLConnection
PostgreSQLConnection
MongoDBConnection
RedisConnection
```

Each class handles only its own database logic.

Example:

```python id="qz7ksh"
class MySQLConnection:
    def connect(self):
        pass
```

## Create DatabaseConnectionFactory

```python id="x7y8jk"
class DatabaseConnectionFactory:
```

Purpose:

* Receive the database type.
* Return the correct connection object.

Example:

```python id="chz8o9"
class DatabaseConnectionFactory:

    @staticmethod
    def create_connection(db_type):
        if db_type == "mysql":
            return MySQLConnection()

        elif db_type == "postgresql":
            return PostgreSQLConnection()

        elif db_type == "mongodb":
            return MongoDBConnection()

        elif db_type == "redis":
            return RedisConnection()

        else:
            raise ValueError("Unsupported database type")
```

# Step 3: Refactored Usage

### Before Refactoring

```python id="8v8tgd"
db = DatabaseConnection(
    db_type="mysql",
    host="localhost",
    port=3306
)
```

### After Refactoring

```python id="phz9ld"
db = DatabaseConnectionFactory.create_connection("mysql")
db.connect()
```

The client no longer needs to know how each database connection is created.

---

# Step 4: Tests

## Test 1 – MySQL Connection Creation

```python id="s2ms5f"
def test_mysql_factory():
    db = DatabaseConnectionFactory.create_connection("mysql")

    assert isinstance(db, MySQLConnection)
```

Expected Result:

* Factory returns a MySQLConnection object.

---

## Test 2 – PostgreSQL Connection Creation

```python id="t0u1ev"
def test_postgresql_factory():
    db = DatabaseConnectionFactory.create_connection("postgresql")

    assert isinstance(db, PostgreSQLConnection)
```

Expected Result:

* Factory returns a PostgreSQLConnection object.

---

## Test 3 – MongoDB Connection Creation

```python id="lklz03"
def test_mongodb_factory():
    db = DatabaseConnectionFactory.create_connection("mongodb")

    assert isinstance(db, MongoDBConnection)
```

Expected Result:

* Factory returns a MongoDBConnection object.

---

## Test 4 – Unsupported Database

```python id="sydlkw"
def test_invalid_database_type():
    with pytest.raises(ValueError):
        DatabaseConnectionFactory.create_connection("oracle")
```

Expected Result:

* ValueError is raised.

---

# Benefits Gained

## Improved Maintainability

Each database type has its own class.

Changes to MongoDB no longer affect MySQL code.

---

## Improved Readability

The client code becomes simpler.

Instead of large conditional blocks, the factory creates the correct object automatically.

---

## Improved Extensibility

Adding a new database becomes easier.

Example:

```python id="v4mf6z"
OracleConnection
```

Only requires:

1. New class
2. One factory update

## Improved Separation of Concerns

Object creation is separated from business logic.

Each class has one responsibility.

# Reflection Questions

## How did implementing the pattern improve maintainability?

The code became easier to maintain because database-specific logic is isolated into separate classes. Developers can modify one connection type without affecting others.

## What future changes will be easier?

Future additions such as:

* Oracle
* SQL Server
* MariaDB

can be added without rewriting the existing connection logic.

## Were there any unexpected challenges?

The biggest challenge was identifying where responsibilities should be split. Initially it seemed easier to keep everything in one class, but the Factory Pattern made the design cleaner and more scalable.

# What I Learned

This exercise taught me that design patterns help solve common software design problems.

The Factory Pattern is useful when object creation becomes complicated or when multiple object types share a common purpose.

AI helped identify the pattern opportunity and explain how object creation could be separated from the rest of the application.

The biggest lesson I learned is that design patterns are not about making code more complex. They are about making future changes easier and reducing maintenance effort.
