 Code Comprehension Exercise

Name:Gabisile Buhle Thikazi

This repository contains my submission for the WeThinkCode AI Code Comprehension Exercise.

## Exercise Sections

- Exercise Part 1: Understanding Project Structure
- Exercise Part 2: Finding Feature Implementation
- Exercise Part 3: Understanding Domain Model
- Exercise Part 4: Practical Application
- Final Discussion and Reflection
- # Exercise: Knowing Where to Start

## Exercise Part 1: Understanding Project Structure

### Initial Understanding

For this exercise, I selected the Python implementation of the Task Manager application from the WeThinkCode AI Code Exercises repository.

Before exploring the codebase, I expected a Task Manager application to contain functionality for creating, updating, storing, and managing tasks.

As someone new to GitHub and software development, my goal was to understand the project structure before attempting to understand the implementation details.

### Repository Exploration

I explored the project structure and identified that the application is implemented in Python.

While reviewing the files and code references, I identified the following components:

* TaskManager
* Task
* TaskPriority
* TaskStatus
* TaskStorage

These names suggest that the application follows an object-oriented design and separates business logic from storage functionality.

### Technologies and Frameworks Identified

* Python
* Object-Oriented Programming (OOP)
* JSON storage (identified through references to tasks.json)

### Initial Questions

While exploring the project, I had the following questions:

* Where are tasks stored?
* What is the application's entry point?
* How are task priorities managed?
* How are task statuses updated?
* How does the storage component work?

### Applying the Project Structure Prompt

I used AI to help analyze the project structure and identify the main components, technologies, and responsibilities.

The AI suggested focusing on:

* Project structure
* Main components
* Storage layer
* Domain objects
* Application entry points

### Findings

| Component    | Responsibility                        |
| ------------ | ------------------------------------- |
| TaskManager  | Core task management functionality    |
| Task         | Represents a task entity              |
| TaskPriority | Handles task priority levels          |
| TaskStatus   | Handles task status management        |
| TaskStorage  | Stores and retrieves task information |

### Misconceptions

Initially, I thought I would need to understand every line of code before understanding the project.

Through this exercise, I learned that understanding the project structure and component names first provides a high-level understanding of the application before diving into implementation details.

### Conclusion

This exercise taught me the importance of exploring a codebase systematically by examining its structure, identifying key components, and using AI to accelerate understanding. Understanding the project structure first makes it easier to understand the implementation later.


- ### What I Observed

The new feature requested is **Task Export to CSV**.

Before writing code, I first need to understand whether the project already has anything similar, such as saving tasks, loading tasks, or working with files.

From the Python Task Manager project, I noticed these related components:

- `TaskManager`
- `TaskStorage`
- `Task`
- `TaskStatus`
- `TaskPriority`
- `tasks.json`

### Search Terms I Would Use

To find similar functionality, I would search for:

- `export`
- `csv`
- `file`
- `json`
- `save`
- `load`
- `storage`
- `tasks.json`
- `add_task`
- `get_tasks`

### My Understanding

I did not find an existing CSV export feature, but I noticed that the project already stores task information using `TaskStorage`.

This makes me think that the CSV export feature should probably work close to the storage or task management logic.

My beginner understanding is:

- `TaskManager` controls task actions.
- `TaskStorage` handles saving and retrieving task data.
- A CSV export feature would need to read task data and write it into a `.csv` file.

### My Hypothesis

I think the export feature could belong in one of two places:

1. In `TaskManager`, because exporting tasks is a task-related action.
2. In `TaskStorage`, because exporting involves writing task data to a file.

The better option might be to add the export logic to `TaskStorage`, because it already deals with files and stored task data.

### Components That Might Be Modified

| Component | Why it may be affected |
|----------|-------------------------|
| `TaskManager` | May need a new method like `export_tasks_to_csv()` |
| `TaskStorage` | May handle writing task data into a CSV file |
| `Task` | Its fields may be used as CSV columns |
| CLI/main file | May need a new command option for exporting tasks |

### AI Feature Location Prompt Used

I would ask AI:

> I am working on a Python Task Manager project. I need to add a new feature called "Task Export to CSV". I have seen components such as TaskManager, TaskStorage, Task, TaskStatus and TaskPriority. I also noticed that tasks are stored using tasks.json. Based on this structure, where should I look for similar file-related functionality, and where would be the best place to implement CSV export?

### AI Guidance Summary

The AI helped me understand that I should first look for existing file storage logic before creating a new feature.

The export feature should reuse the existing task data instead of creating a separate task list.

### Implementation Plan

My plan for adding the CSV export feature would be:

1. Look at how tasks are currently saved and loaded.
2. Identify the task fields that should appear in the CSV file.
3. Add a method to export task data to CSV.
4. Decide whether the method belongs in `TaskManager` or `TaskStorage`.
5. Add a command-line option so the user can trigger the export.
6. Test that the CSV file is created correctly.

### What I Learned

I learned that before adding a new feature, I should not immediately start coding.

First, I should search for similar functionality, understand where related logic already exists, and then decide where the new feature belongs.

This helps avoid placing code in the wrong file or duplicating existing logic.

## Exercise Part 3: Understanding Domain Model

### What I Observed

For this part, I focused on understanding the main business objects in the Task Manager application.

The main domain concepts I identified are:

- `Task`
- `TaskStatus`
- `TaskPriority`
- `TaskManager`
- `TaskStorage`

### My Beginner Understanding

A domain model is the way the application represents real-world ideas in code.

In this project, the real-world idea is managing tasks. A task can have information such as a title, description, priority, status, due date, and tags.

### Simple Domain Diagram

```text
TaskManager
    |
    | manages
    v
Task
    |
    | has a
    v
TaskStatus

Task
    |
    | has a
    v
TaskPriority

TaskManager
    |
    | uses
    v
TaskStorage

| Entity         | My Understanding                                                               |
| -------------- | ------------------------------------------------------------------------------ |
| `Task`         | Represents one task that the user wants to manage                              |
| `TaskStatus`   | Represents the current state of a task, such as pending or completed           |
| `TaskPriority` | Represents how important or urgent a task is                                   |
| `TaskManager`  | Controls task actions such as creating, listing, completing, or updating tasks |
| `TaskStorage`  | Handles saving and loading tasks from storage                                  |

*Business Logic I Noticed

The business logic appears to be about managing tasks correctly.

Examples of task-related business logic include:

Creating a new task
Listing existing tasks
Filtering tasks by status
Filtering tasks by priority
Checking overdue tasks
Updating task status
Storing tasks so they can be used later

*Questions I Had
While exploring the domain model, I had these questions:

What statuses can a task have?
What priority levels are allowed?
Can a task exist without a due date?
Where is the rule for overdue tasks handled?
Does the application validate task information before saving it?

*Domain Understanding Prompt Used
I used AI with this prompt:

I am learning a Python Task Manager project as a beginner. I have identified domain concepts such as Task, TaskStatus, TaskPriority, TaskManager and TaskStorage. Please explain how these entities relate to each other, what business rules may exist, and ask me questions to test my understanding.

*AI Questions and My Answers

First Question: What is the main entity in the Task Manager domain?

My answer:
The main entity is Task because the application is built around creating and managing tasks.

2nd Question: Why does a task need a status?

My answer:
A task needs a status so the system can know whether the task is still pending, completed, or in another state.

3rd Question: Why does a task need a priority?

My answer:
A priority helps show how important or urgent a task is.

4th Question: Why is TaskStorage separate from TaskManager?

My answer:
TaskManager focuses on task actions, while TaskStorage focuses on saving and loading task data. This separation makes the code easier to understand and maintain.

Revised Understanding

After reviewing the domain model, my understanding improved.

I now understand that:

Task is the main business object.
TaskStatus and TaskPriority describe important properties of a task.
TaskManager controls how tasks are managed.
TaskStorage handles persistence, meaning saving and retrieving tasks.
The project separates responsibilities so one component does not do everything.

Glossary of Domain Terms

Term -        Meaning
Task	-        A piece of work that needs to be completed
Status	-      The current state of a task
Priority	-    The importance level of a task
Due Date	-    The date by which the task should be completed
Overdue-	      A task that has passed its due date
Storage-	      Where task data is saved
Domain Model	- The main business ideas represented in code
Business Rule	- A rule that controls how the application should behave

### What I Learned

Before this exercise, I thought understanding a codebase meant reading every line of code.

Through this exercise, I learned that it is more effective to first identify the main entities, understand their responsibilities, and see how they relate to each other.

By understanding the domain model, I was able to get a clearer picture of how the Task Manager application works without needing to understand every implementation detail.

## Final Discussion and Reflection

### My Initial Understanding

At the beginning of this exercise, I was unfamiliar with the Task Manager codebase and still learning how to use GitHub.

Initially, I thought understanding a project meant reading every line of code from start to finish before making any changes.

### My Final Understanding

By the end of the exercise, I learned that understanding a codebase starts with understanding its structure.

I learned to identify:

* The main folders and files
* Core entities such as Task, TaskStatus, and TaskPriority
* Storage components
* Business rules
* Areas where new features could be implemented

This helped me gain a clearer understanding of how the Task Manager application works.

### Most Valuable Insights Gained

#### Understanding Project Structure

This prompt taught me to start with the folder structure and component names before reading code in detail.

#### Finding Feature Implementation

This prompt helped me understand how to search for existing functionality before adding a new feature. It showed me the importance of reusing existing components rather than creating duplicate logic.

#### Understanding Domain Model

This prompt helped me identify the core business concepts in the application and understand how they relate to each other.

### My Approach to Implementing the New Business Rule

The new business rule stated that tasks overdue by more than seven days should automatically be marked as abandoned unless they are high priority.

My approach would be:

1. Review the Task entity to understand how due dates are stored.
2. Check the available task statuses.
3. Identify where overdue task logic is handled.
4. Add logic to check if a task has been overdue for more than seven days.
5. Exclude high-priority tasks from the automatic update.
6. Save the updated task information through the storage component.
7. Test different scenarios to ensure the rule works correctly.

### Challenges I Encountered

One of the biggest challenges was understanding where to start when looking at an unfamiliar codebase.

As someone new to GitHub and software development, it was initially overwhelming to navigate repositories and understand how different components fit together.

I overcame this by focusing on the project structure first and documenting my observations before attempting to understand implementation details.

### Insights from the Virtual Session

Although there was no formal group discussion, the virtual session helped me understand how developers approach unfamiliar codebases.

One important lesson I learned was that I do not need to understand every line of code immediately. Instead, I can start by understanding the structure, identifying the main entities, and asking questions about the business logic.

The session also showed that developers use different approaches when exploring projects. Some begin with the folder structure, while others focus on identifying the main business concepts first.

### What I Would Do Differently Next Time

When approaching an unfamiliar codebase in the future, I would:

* Read the README file first
* Review the folder structure
* Identify configuration files
* Search for important keywords
* Document my questions early
* Use AI prompts to guide my investigation

### Additional Tools and Resources

The following resources would help me understand unfamiliar projects more effectively:

* GitHub search
* VS Code search
* Project documentation
* AI prompts
* Diagrams
* Unit tests
* Sample data

### Personal Reflection

The most helpful prompt for me was the Project Structure prompt because it gave me a clear starting point and reduced the feeling of being overwhelmed.

This exercise taught me that understanding a codebase is a gradual process. I do not need to understand everything immediately. By breaking the project into smaller parts and exploring it systematically, I can build my understanding over time.

The biggest lesson I learned is that understanding the structure and business concepts of an application is often more important than immediately focusing on the code itself.



