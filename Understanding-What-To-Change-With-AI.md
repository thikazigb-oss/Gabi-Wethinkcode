# Understanding What to Change with AI

## Exercise Overview

This exercise focused on using AI to analyze and improve code examples in Java, Python, and JavaScript. The goal was not to create runnable code, but to compare AI-assisted suggestions, understand the improvements, and document key learning points.

# Exercise 1: Code Readability Improvement

## Language

Java

## Problem Observed

The Java code was difficult to understand because it used unclear names such as:

* `UserMgr`
* `U`
* `u_list`
* `a`
* `f`
* `un`
* `pw`
* `em`

As a beginner, this made the code hard to read because the names did not clearly explain what the classes, variables, and methods were responsible for.

## AI Suggestions

The AI suggested improving readability by:

* Renaming `UserMgr` to `UserManager`
* Renaming `U` to `User`
* Renaming `u_list` to `users`
* Renaming `a()` to `addUser()` or `registerUser()`
* Renaming `f()` to `findUserByUsername()`
* Renaming `un`, `pw`, and `em` to `username`, `password`, and `email`

## What I Learned

I learned that readable code should explain itself through clear naming. Even if the code works, unclear names make it difficult for other developers to understand and maintain.

I also noticed that the code builds a SQL query by joining strings together, which can be risky. This helped me understand that readability improvements can also reveal possible security or design concerns.

---

# Exercise 2: Function Refactoring

## Language

Python

## Problem Observed

The `process_orders()` function does many things in one place:

* Checks inventory
* Checks quantity
* Checks customer data
* Calculates price
* Applies discount
* Updates inventory
* Calculates shipping
* Calculates tax
* Tracks revenue
* Builds the final result

This makes the function long and harder to test.

## AI Suggestions

The AI suggested breaking the function into smaller helper functions such as:

* `validate_order()`
* `calculate_price()`
* `apply_discount()`
* `calculate_shipping()`
* `calculate_tax()`
* `process_single_order()`

## My Understanding

My understanding is that each helper function should have one clear responsibility. This would make the code easier to read, test, and maintain.

For example:

```python
def calculate_tax(price):
    return price * 0.08
```

This is easier to understand than having tax logic hidden inside a long function.

## What I Learned

I learned that refactoring does not always mean changing what the code does. Sometimes it means organizing the code better so that each part has a clear purpose.

I also learned that smaller functions are easier to test because each function can be checked separately.

---

# Exercise 3: Code Duplication Detection

## Language

JavaScript

## Problem Observed

The JavaScript function repeats similar logic several times.

It calculates:

* Average age
* Average income
* Average score

Then it finds:

* Highest age
* Highest income
* Highest score

The pattern is repeated for each field.

## AI Suggestions

The AI suggested creating reusable helper functions such as:

```javascript
function calculateAverage(data, field) {
  let total = 0;

  for (let i = 0; i < data.length; i++) {
    total += data[i][field];
  }

  return total / data.length;
}
```

and:

```javascript
function findHighest(data, field) {
  let highest = data[0][field];

  for (let i = 1; i < data.length; i++) {
    if (data[i][field] > highest) {
      highest = data[i][field];
    }
  }

  return highest;
}
```

## My Understanding

Instead of repeating the same loop for age, income, and score, the code can use one reusable function and pass in the field name.

This reduces duplication and makes the code easier to update.

## What I Learned

I learned that duplicate code is a sign that the same logic may be reusable. Removing duplication can make the code shorter and easier to maintain.

However, I also learned that refactoring should still be readable, especially for junior developers. A solution that is too clever may become harder to understand.

---

# Reflection Questions

## Which prompting strategy did I find most useful?

The function refactoring prompt was the most useful because it helped me see how a large function can be broken down into smaller pieces. This made the code easier to understand.

## What improvements did AI suggest that I might not have thought of?

The AI helped me notice that unclear names and repeated logic are not just small issues. They can make the code harder to maintain, test, and safely change.

## Were there any AI suggestions I disagreed with?

I would be careful with suggestions that make code too abstract. Sometimes simpler code is better for junior developers, even if it is slightly longer.

## How might I adapt these prompts for my own codebase?

I would paste one function or class at a time and ask AI to explain what can be improved in readability, structure, and duplication. I would also ask AI to explain suggestions in beginner-friendly language.

## What safeguards would I use before applying AI refactoring to production code?

Before applying AI-suggested refactoring, I would:

* Make sure tests exist
* Review the suggested changes carefully
* Check that the behavior stays the same
* Ask another developer to review the changes
* Test the code before deploying it

# Final Reflection

This exercise helped me understand that improving code is not only about making it shorter. It is also about making it easier to read, easier to test, and safer to maintain.

The biggest lesson I learned is that AI can help identify improvements, but I still need to understand and verify the suggestions before applying them.
