# Learning a New Programming Language with AI

## Source Language

Python

## Target Language

JavaScript

## Why I Chose JavaScript

I chose JavaScript as my target language because it is commonly used for web development and can help me understand frontend and backend development better. Since I have been working with Python in previous exercises, learning JavaScript will help me compare how different programming languages solve problems.

# Part 1: Learning Journey Plan

## Learning Goals

1. Understand JavaScript syntax and how it differs from Python.
2. Learn how JavaScript handles functions, objects, arrays, and asynchronous code.
3. Build a simple command-line task tracker using JavaScript.

## Learning Plan

### Phase 1: JavaScript Basics

Prerequisites:

* Basic understanding of Python variables, loops, and functions.

Learning Steps:

* Learn JavaScript variables using `let` and `const`.
* Learn JavaScript functions.
* Learn arrays and objects.
* Compare JavaScript syntax with Python syntax.

Verification Activities:

* Write a simple function.
* Create an array of tasks.
* Print task information to the console.

### Phase 2: Working with Data

Prerequisites:

* Understanding of JavaScript basics.

Learning Steps:

* Learn how objects store data.
* Learn how arrays store collections.
* Practice filtering and mapping arrays.
* Learn how JSON is used in JavaScript.

Verification Activities:

* Create a list of task objects.
* Filter tasks by status.
* Display only completed tasks.

### Phase 3: Building a Small CLI Project

Prerequisites:

* Understanding of functions, arrays, and objects.

Learning Steps:

* Create a simple task tracker.
* Add tasks to a list.
* Mark tasks as complete.
* Display all tasks.

Verification Activities:

* Run the program.
* Add sample tasks.
* Confirm that completed tasks are updated correctly.

### Phase 4: Understanding Asynchronous JavaScript

Prerequisites:

* Basic JavaScript project experience.

Learning Steps:

* Learn what asynchronous code means.
* Understand callbacks, promises, and async/await.
* Compare async/await with normal Python functions.
* Practice with a simple delayed function.

Verification Activities:

* Write a function using `setTimeout`.
* Write a promise.
* Use `async` and `await`.

---

# Part 2: Four-Step Prompting Strategy

## Topic Chosen

JavaScript functions and objects.

## Step 1: Conceptual Understanding

Prompt used:

I am currently learning JavaScript after working with Python. Before writing code, I want to understand the main differences between Python and JavaScript.

Please explain:

1. The key differences between Python and JavaScript.
2. What JavaScript was designed to solve.
3. What mental models I should adjust coming from Python.
4. Common misconceptions Python learners may have about JavaScript.

### What I Learned

JavaScript is commonly used to make websites interactive and can also be used on servers through Node.js. Unlike Python, JavaScript is heavily connected to web development and uses different syntax for functions, objects, and asynchronous programming.

## Step 2: Step-by-Step Breakdown

Prompt used:

I want to understand JavaScript objects and how they compare to Python dictionaries. Please explain:

1. How objects work in JavaScript.
2. How they compare to dictionaries in Python.
3. The key syntax I need to understand.
4. Common patterns and best practices.

### What I Learned

JavaScript objects are similar to Python dictionaries because both store key-value pairs. However, JavaScript objects are used very commonly to represent structured data and are often used with arrays.

Example:

```javascript
const task = {
  title: "Study JavaScript",
  completed: false
};
```

## Step 3: Guided Implementation

Prompt used:

I am ready to create a simple JavaScript task object and task list. Please guide me through creating a small example and explain each part of the syntax, especially how it differs from Python.

### Implementation

```javascript
const tasks = [
  {
    title: "Learn JavaScript basics",
    completed: false
  },
  {
    title: "Practice objects",
    completed: true
  }
];

function showTasks(tasks) {
  for (const task of tasks) {
    console.log(`${task.title} - Completed: ${task.completed}`);
  }
}

showTasks(tasks);
```

### What I Learned

I learned that JavaScript uses curly braces for objects and functions. I also learned that `const` is used when a variable should not be reassigned.

---

## Step 4: Understanding Verification

Prompt used:

I created this JavaScript implementation. Please verify whether I followed JavaScript best practices, explain improvements I should make, suggest what I should learn next, and point out any Python habits that may be showing in my code.

### AI Feedback Summary

The code was simple and understandable. A possible improvement would be to separate display logic from data logic and to practice array methods such as `map()` and `filter()`.

---

# Part 3: Advanced Prompting Techniques

## Technique 1: Using Context Effectively

Prompt used:

I am learning JavaScript objects coming from Python dictionaries. Can you explain JavaScript objects by comparing them to concepts I already know in Python?

### Key Learning

Comparing JavaScript objects to Python dictionaries helped me understand the concept faster because I could connect new knowledge to something familiar.

---

## Technique 2: Learning Through Teaching

Prompt used:

Could you verify my understanding? Here is how I would explain JavaScript objects to another beginner:

A JavaScript object is like a Python dictionary because it stores information using key-value pairs. It is useful for grouping related data together.

What parts of my understanding are correct, and what am I missing?

### Key Learning

My explanation was mostly correct, but I learned that JavaScript objects can also contain functions, which are called methods. This makes objects more powerful than simple data containers.

---

# Part 4: Mini Project

## Project Description

I built a simple JavaScript command-line task tracker concept.

The task tracker can:

* Store tasks
* Display tasks
* Mark a task as complete

## Project Plan

Components:

1. Task list array
2. Function to add tasks
3. Function to list tasks
4. Function to mark tasks as complete

## Code Sample

```javascript
const tasks = [];

function addTask(title) {
  tasks.push({
    title: title,
    completed: false
  });
}

function completeTask(index) {
  if (tasks[index]) {
    tasks[index].completed = true;
  }
}

function listTasks() {
  for (const task of tasks) {
    console.log(`${task.title} - Completed: ${task.completed}`);
  }
}

addTask("Learn JavaScript");
addTask("Practice functions");
completeTask(0);
listTasks();
```

## Review and Refactor Notes

The project helped me practice JavaScript arrays, objects, and functions. A future improvement would be to add user input, save tasks to a file, and use better error messages for invalid task indexes.

# Reflection Questions

## Which prompting strategies were most effective?

The step-by-step breakdown and guided implementation were the most helpful because they allowed me to understand the concept before writing code.

## What surprised me about JavaScript?

I was surprised that JavaScript objects are similar to Python dictionaries, but JavaScript uses them more heavily in everyday programming.

## How did Python help or hinder my learning?

Python helped because I already understood variables, functions, lists, and dictionaries. However, JavaScript syntax felt unfamiliar because of curly braces, semicolons, and different function styles.

## What would I do differently next time?

Next time, I would spend more time practicing small examples before trying to build a project.

## What gaps remain?

I still need to learn more about:

* Node.js
* Modules
* Async/await
* Error handling
* Working with files

# Final Reflection

This exercise helped me understand how AI can support learning a new programming language. Instead of only asking AI for answers, I used AI to create a learning plan, explain concepts, guide implementation, and review my understanding.

The biggest lesson I learned is that learning a new language becomes easier when I compare it with a language I already know.
