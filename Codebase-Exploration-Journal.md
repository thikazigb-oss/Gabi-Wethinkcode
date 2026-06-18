### Repository Exploration

While exploring the Python Task Manager project, I identified the following files and folders:

* cli.py
* task_manager.py
* models.py
* storage.py
* tests/
* README.md

### My Understanding of the Files

| File            | Purpose                                                                  |
| --------------- | ------------------------------------------------------------------------ |
| cli.py          | Provides the command-line interface for interacting with the application |
| task_manager.py | Contains the main task management logic                                  |
| models.py       | Defines the domain entities such as Task, TaskStatus and TaskPriority    |
| storage.py      | Handles saving and retrieving task data                                  |
| tests           | Contains automated tests for validating functionality                    |
| README.md       | Provides usage and setup instructions                                    |

### Technologies Identified
* Python
* Command Line Interface (CLI)
* JSON-based storage
* Unit Testing (unittest)
* Object-Oriented Programming (OOP)
### What I Learned

Before exploring the Task Manager project, I felt overwhelmed because I was unfamiliar with both GitHub and the codebase.

By reviewing the project structure first, I learned that I do not need to understand every line of code immediately. Instead, I can start by identifying the main files and understanding their responsibilities.

*I learned that:

* `cli.py` acts as the entry point for user commands.
* `task_manager.py` contains the core task management functionality.
* `models.py` defines the main entities used by the application.
* `storage.py` is responsible for saving and retrieving task data.
  ### Conclusiond
  

### The `tests` folder helps verify that the application behaves correctly.
 Manager application is organized and how its different parts work together.

 # Exercise Part 2: Deepen Understanding Through Guided Questions

## Exploring the Task Prioritization System

### Initial Understanding

While reviewing the codebase, I noticed references to `TaskPriority` in `models.py` and within the command examples in the README file.

My initial understanding was that task priority is used to determine the importance of a task and help users focus on urgent work first.

I observed the following priority levels:

- 1 = Low
- 2 = Medium
- 3 = High
- 4 = Urgent

### Guided Questions

To deepen my understanding, I asked the following questions:

1. Where is TaskPriority defined?
2. How is a priority assigned when a task is created?
3. Can task priorities be updated after creation?
4. How does the application use priorities when displaying tasks?

### What I Discovered

After exploring the code and documentation, I discovered that:

- TaskPriority is part of the domain model defined in `models.py`.
- A priority value can be assigned when creating a task.
- Task priorities can be updated using CLI commands.
- The system allows tasks to be filtered by priority.

### Initial Understanding vs Discovery

Initially, I believed priority was only a label attached to a task.

After further exploration, I learned that priority is an important part of task management because it can be used to organize, filter, and update tasks.

### Key Insights

The guided questions helped me understand that:

- Priority is part of the task's core data.
- The application provides commands for managing priorities.
- Priorities help users organize their work more effectively.

### Misconceptions Clarified

I originally assumed that priority only affected task creation.

After reviewing the project, I learned that priority can also be updated and used when listing tasks.

### What I Learned

This exercise taught me that asking focused questions helps uncover how a feature works. Instead of trying to understand everything at once, breaking the system into smaller questions made the codebase easier to understand.

# Exercise Part 3: Mapping Data Flow

## Task Completion Process

For this exercise, I explored how data flows through the application when a task is marked as complete.

### Entry Points and Components

The main components involved are:

- `cli.py`
- `task_manager.py`
- `models.py`
- `storage.py`

### Data Flow Diagram

User
↓
cli.py
↓
task_manager.py
↓
Task Status Updated
↓
storage.py
↓
Stored Task Data

### State Changes

When a task is marked as complete:

1. The user selects a task.
2. A status update command is issued.
3. The task status changes from its current state to a completed state.
4. The updated task information is saved.

### Potential Points of Failure

Possible issues that could occur include:

- Invalid task ID entered by the user.
- Invalid status value provided.
- Failure to save updated task information.
- Missing task data.

### Persistence of Changes

The application persists changes through the storage layer.

My understanding is that `storage.py` is responsible for ensuring that updates remain available when the application is restarted.

### What I Learned

This exercise helped me understand how information moves through multiple components before being stored. Mapping the flow made it easier to see how each file contributes to the overall functionality of the application.

# Exercise Part 3: Mapping Data Flow

## Task Completion Process

For this exercise, I explored how data flows through the application when a task is marked as complete.

### Entry Points and Components

The main components involved are:

- `cli.py`
- `task_manager.py`
- `models.py`
- `storage.py`

### Data Flow Diagram

User
↓
cli.py
↓
task_manager.py
↓
Task Status Updated
↓
storage.py
↓
Stored Task Data

### State Changes

When a task is marked as complete:

1. The user selects a task.
2. A status update command is issued.
3. The task status changes from its current state to a completed state.
4. The updated task information is saved.

### Potential Points of Failure

Possible issues that could occur include:

- Invalid task ID entered by the user.
- Invalid status value provided.
- Failure to save updated task information.
- Missing task data.

### Persistence of Changes

The application persists changes through the storage layer.

My understanding is that `storage.py` is responsible for ensuring that updates remain available when the application is restarted.

### What I Learned

This exercise helped me understand how information moves through multiple components before being stored. Mapping the flow made it easier to see how each file contributes to the overall functionality of the application.


This exercise taught me that understanding a codebase starts with understanding its structure and the purpose of its main components before diving into implementation details.

# Exercise Part 4: Reflection and Presentation

## Application Architecture Overview

The Task Manager application follows a structured design where different files have different responsibilities.

- `cli.py` handles user interaction through the command line.
- `task_manager.py` contains the core business logic.
- `models.py` defines the application's entities and data structures.
- `storage.py` manages data storage and retrieval.
- `tests` contains automated tests that validate functionality.

This separation of responsibilities makes the application easier to understand and maintain.

## How the Key Features Work

### Task Creation

A user creates a task through the command-line interface. The request is processed by the task manager, a task object is created, and the information is saved through the storage layer.

### Task Prioritization

Task priorities help categorize tasks according to importance. Priorities can be assigned during task creation and updated later if required.

### Task Completion

When a task is marked as complete, the status is updated and the changes are saved through the storage component so they remain available for future use.

## Most Challenging Aspect

The most challenging part was understanding how the different files work together. Initially, I focused on individual files, but I later realized that understanding the flow between components was more important than understanding every line of code.

## How the AI Prompts Helped

The AI prompts helped me break the application into smaller pieces that were easier to understand. Instead of trying to understand the entire codebase at once, I focused on project structure, feature implementation, and data flow separately.

## What I Learned

I learned that understanding a new codebase starts with exploring the project structure before diving into implementation details. I also learned that asking targeted questions can make learning unfamiliar code much easier.

# Final Submission Summary

## Initial vs Final Understanding

Initially, I had very little understanding of the Task Manager application and felt overwhelmed by both GitHub and the codebase structure.

After completing the exercises, I gained a much clearer understanding of how the application is organized, how tasks are created and updated, how priorities work, and how data flows through the system.

## Most Valuable Insights

- Understanding the project structure before reading code.
- Identifying the responsibilities of each file.
- Following the flow of data through the application.
- Using guided questions to understand specific features.

## Strategies for Approaching Unfamiliar Code

In future, I will:

1. Start by exploring the project structure.
2. Identify the main files and their responsibilities.
3. Follow the flow of data through the application.
4. Use diagrams and notes to document my understanding.
5. Use AI prompts to guide my exploration and validate my understanding.

## Conclusion

This exercise showed me that understanding a codebase does not require knowing every line of code immediately. By exploring the structure, understanding the components, and asking focused questions, I was able to build confidence in navigating an unfamiliar project.

