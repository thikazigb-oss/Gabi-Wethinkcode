# Applying AI to Deepen Programming Language Understanding

## Language Chosen

I chose **Python** because I have been using Python throughout most of the exercises.

# Activity 1: Idiomatic Code Transformation

## Code Selected

For this activity, I used a simple Python function that calculates a cart total.

```python
def calculate_total(cart):
    total = 0
    for item in cart:
        total = total + item["price"] * item["quantity"]
    return total
```

## Improved Version

```python
def calculate_total(cart):
    return sum(item["price"] * item["quantity"] for item in cart)
```

## What Changed

The improved version uses Python’s built-in `sum()` function and a generator expression. This is more idiomatic Python because it is shorter, clearer, and focuses directly on the calculation.

## Three Key Learnings

1. Python has built-in functions like `sum()` that can make code shorter and clearer.
2. Generator expressions are useful when calculating values from a list.
3. Idiomatic Python often means writing code that is simple, readable, and uses language features properly.

---

# Activity 2: Code Quality Detective

## Code Reviewed

For this activity, I reviewed code similar to the discount calculation function from the readability exercise.

## Quality Issues Identified

| Issue                                 | Why It Matters                                                        |
| ------------------------------------- | --------------------------------------------------------------------- |
| Short variable names                  | Makes the code harder to understand                                   |
| Too much logic in one function        | Makes testing and maintenance harder                                  |
| Poor formatting                       | Makes the code difficult to scan                                      |
| Repeated calculations                 | Can make the code harder to update                                    |
| No comments explaining business rules | Makes it harder for new developers to understand why the logic exists |

## Code Review Checklist

In future code reviews, I would check:

* Are variable names clear?
* Is the function doing only one main thing?
* Is the formatting consistent?
* Are repeated patterns extracted into helper functions?
* Are business rules explained clearly?
* Are there tests to confirm the behavior?

## Three Key Learnings

1. Code quality is not only about whether the code works; it is also about whether other developers can understand it.
2. Clear variable names make a big difference in readability.
3. Breaking large functions into smaller functions makes the code easier to test and maintain.

---

# Activity 3: Understanding a Language Feature

## Feature Chosen

I chose to learn more about **Python list comprehensions**.

## My Understanding

A list comprehension is a shorter way to create a list from another list or iterable.

Example:

```python
numbers = [1, 2, 3, 4]

squares = [number * number for number in numbers]
```

This creates:

```python
[1, 4, 9, 16]
```

## Practical Use Cases

1. Creating a list of transformed values.
2. Filtering items from a list.
3. Extracting specific fields from dictionaries.

## Small Practice Example

```python
tasks = [
    {"title": "Study", "status": "pending"},
    {"title": "Submit assignment", "status": "completed"},
    {"title": "Review notes", "status": "pending"}
]

pending_tasks = [task for task in tasks if task["status"] == "pending"]

print(pending_tasks)
```
## Common Mistakes to Avoid

* Making list comprehensions too long or hard to read.
* Using them when a normal loop would be clearer.
* Forgetting that readability is more important than being clever.

## Three Key Learnings

1. List comprehensions are useful for creating new lists in a clean way.
2. They are best used for simple transformations or filters.
3. If the logic becomes too complex, a normal loop is easier to understand.

# Group Discussion Reflection

Although there was no formal group discussion at the time of writing, the virtual session and AI-guided exercises helped me identify common themes.

## Common Themes

* Clear naming improves understanding.
* Smaller functions are easier to test and maintain.
* Python has helpful built-in features that reduce unnecessary code.
* AI is useful for explanations, but I still need to verify and understand the suggestions.

# Final Reflection

This exercise helped me understand that learning a programming language is not only about knowing syntax. It is also about learning the language’s style, best practices, and common patterns.

AI helped me see how Python code can be written more clearly and naturally. The biggest lesson I learned is that good code should be understandable to both the computer and the people who read it.
