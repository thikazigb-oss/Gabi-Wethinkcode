# README and User Guide Documentation

## Project Information Chosen

**Project Name:** Python Task Manager
**Project Used:** Task Manager system from the Code Comprehension exercise
**Language Chosen:** Python

## Project Description

Python Task Manager is a command-line task management application that allows users to create, update, prioritize, complete, and store tasks. I chose this project because it connects with the previous code comprehension exercises and helps me continue building my understanding of the same codebase.

## Technologies Used

* Python
* Command Line Interface
* JSON-based storage
* Object-Oriented Programming
* Unit testing

## Project Structure

```text
TaskManager/
├── cli.py
├── task_manager.py
├── models.py
├── storage.py
├── tests/
└── README.md

# Prompt 1 Output: Comprehensive README

# Python Task Manager

Python Task Manager is a simple command-line application for managing tasks. It allows users to create tasks, update task information, manage priorities, mark tasks as complete, and store task data for future use.

## Features

* Create new tasks
* View all tasks
* Update task status
* Update task priority
* Update task due dates
* Mark tasks as complete
* Store task data for later use
* Organize tasks by priority and status

## Technologies Used

* Python
* Command Line Interface
* JSON-based storage
* Object-Oriented Programming
* Unit testing

## Installation Requirements

Before using the project, make sure the following are installed:

* Python 3
* A terminal or command prompt
* Git, if cloning the repository

## Installation Instructions

1. Clone or download the project repository.

```bash
git clone https://github.com/wethinkcode/ai-code-exercises.git
```

2. Navigate to the Task Manager project folder.

```bash
cd ai-code-exercises/use-cases/code-comprehension-001/python/TaskManager
```

3. Confirm Python is installed.

```bash
python --version
```

4. Run the application using the CLI file.

```bash
python cli.py
```

## Basic Usage Examples

Create a task:

```bash
python cli.py create
```

List tasks:

```bash
python cli.py list
```

Update task status:

```bash
python cli.py update-status
```

Update task priority:

```bash
python cli.py update-priority
```

Mark a task as complete:

```bash
python cli.py complete
```

## Code Structure Overview

| File or Folder    | Purpose                                                      |
| ----------------- | ------------------------------------------------------------ |
| `cli.py`          | Handles user commands from the terminal                      |
| `task_manager.py` | Contains the main task management logic                      |
| `models.py`       | Defines entities such as Task, TaskStatus, and TaskPriority  |
| `storage.py`      | Handles saving and retrieving task data                      |
| `tests/`          | Contains tests that check if the application works correctly |
| `README.md`       | Provides project information and instructions                |

## Configuration Options

The project may use default storage settings for saving task data. If storage settings are changed, the user should confirm that the correct file path is being used and that the storage file is accessible.

## Troubleshooting

### Command does not work

Check that:

* Python is installed
* You are in the correct project folder
* The command was typed correctly

### Task does not appear after creating it

Check that:

* The task was saved successfully
* The storage file is available
* You are listing tasks from the same project folder

### Python command not found

Try using:

```bash
python3 --version
```

instead of:

```bash
python --version
```

## Contributing Guidelines

This project is used for learning, but contributions can follow a normal GitHub workflow:

1. Fork the repository.
2. Create a new branch.
3. Make your changes.
4. Commit your changes.
5. Submit a pull request.

## License Information

This project is used for educational purposes as part of the WeThinkCode AI Code Exercises.

# Prompt 2 Output: Step-by-Step Guide

# How to Create a New Task in Python Task Manager

## Purpose of This Guide

This guide explains how to create a new task using the Python Task Manager command-line application.

## User Experience Level

Beginner

## Prerequisites

Before creating a task, make sure:

* Python is installed on your computer
* The Task Manager project has been downloaded or cloned
* You are inside the correct Task Manager folder
* The file `cli.py` exists in the project folder

## Step 1: Open the Terminal

Open Command Prompt, PowerShell, Terminal, or the terminal inside your code editor.

## Step 2: Navigate to the Project Folder

Move into the Task Manager project folder.

Example:

```bash
cd ai-code-exercises/use-cases/code-comprehension-001/python/TaskManager
```

## Step 3: Confirm the Project Files Are Present

Check that files such as the following exist:

```text
cli.py
task_manager.py
models.py
storage.py
```

These files are important because they work together to create and save tasks.

## Step 4: Run the Create Command

Run:

```bash
python cli.py create
```

If your system uses `python3`, run:

```bash
python3 cli.py create
```

## Step 5: Enter Task Details

When prompted, enter the task information such as:

* Task title
* Description
* Priority
* Due date
* Status, if required

## Step 6: Confirm the Task Was Created

After entering the task details, check for a success message or run:

```bash
python cli.py list
```

This should show the task you created.

## Common Mistakes

* Running the command from the wrong folder
* Typing the command incorrectly
* Using `python` when the system expects `python3`
* Forgetting required task details
* Not checking whether the task was saved

## Troubleshooting

### I get “python is not recognized”

Python may not be installed or may not be added to your PATH.

Try:

```bash
python3 --version
```

### I get “file not found”

Check that you are inside the correct folder and that `cli.py` exists.

### My task does not show when I list tasks

Check whether the task was saved correctly and whether the storage file is available.

# Prompt 3 Output: FAQ Document

# Python Task Manager FAQ

## Getting Started

### What is Python Task Manager?

Python Task Manager is a command-line application for creating, updating, prioritizing, and completing tasks.

### Who is this project for?

This project is useful for learners who want to understand how a Python application manages tasks, state, and storage.

### Why did I choose this project?

I chose this project because it connects to my previous code comprehension exercises and helped me continue learning from the same codebase.

### Do I need advanced Python knowledge?

No. Basic Python knowledge is enough to start exploring the project.

## Installation and Setup

### What do I need before using the project?

You need Python installed and access to a terminal or command prompt.

### How do I check if Python is installed?

Run:

```bash
python --version
```

or:

```bash
python3 --version
```

### What should I do if Python is not recognized?

Install Python or check whether it is added to your system PATH.

## Basic Usage

### How do I create a task?

Run:

```bash
python cli.py create
```

### How do I list tasks?

Run:

```bash
python cli.py list
```

### How do I update a task status?

Run:

```bash
python cli.py update-status
```

### How do I update task priority?

Run:

```bash
python cli.py update-priority
```

### How do I mark a task as complete?

Run:

```bash
python cli.py complete
```

## Features and Functionality

### What is task priority?

Task priority shows how important or urgent a task is.

### What is task status?

Task status shows the current state of the task, such as pending, in progress, or completed.

### Where is task data stored?

Task data is handled through the storage layer. The `storage.py` file is responsible for saving and retrieving task information.

### Which file handles the main task logic?

The main task logic is handled in `task_manager.py`.

### Which file defines the task structure?

The task structure and related entities are defined in `models.py`.

## Troubleshooting

### Why is my command not working?

Possible reasons include:

* You are in the wrong folder
* Python is not installed
* The command was typed incorrectly
* The required file does not exist

### Why can I not see my task after creating it?

The task may not have been saved correctly, or you may need to run the list command again.

### What should I do if I feel lost in the codebase?

Start by reading the README, then look at the file names and their responsibilities before reading the code line by line.

# Reflection

## Which aspects of the project were most challenging to document?

The most challenging part was explaining how the different files work together because the project has separate files for CLI commands, business logic, models, and storage.

## How did I adjust my prompts to get better results?

I made the prompts more specific by including the project name, chosen language, technologies, project structure, and main features. This helped the AI generate documentation that was more relevant to the Task Manager project.

## What did I learn about document structure and organization?

I learned that good documentation should be organized into clear sections such as overview, installation, usage, project structure, troubleshooting, and FAQ. This makes it easier for beginners to follow.

## How would I use this approach in my development workflow?

In future, I would use AI to generate an initial draft of documentation and then review it against the actual project. This would help me save time while still ensuring the final documentation is accurate.

## Final Learning Reflection

This exercise helped me understand that documentation is not only for users but also for developers who need to understand a project quickly. I also learned that AI can help create a strong first draft, but the developer must still check the details and make sure the documentation matches the actual project.
