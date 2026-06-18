# AI Testing Exercise

## Selected Implementation

I selected the **Python implementation** of the task prioritization algorithm.

The main functions considered are:

* `calculateTaskScore`
* `sortTasksByImportance`
* `getTopPriorityTasks`

# Part 1: Understanding What to Test

## Exercise 1.1: Behavior Analysis

### My Understanding

The `calculateTaskScore` function gives each task a score based on factors such as:

* Priority
* Due date
* Status
* Tags
* Recent updates

A higher score means the task is more important.

### Test Cases I Should Write

| Test Case                | What It Checks                                          |
| ------------------------ | ------------------------------------------------------- |
| High priority task       | High priority should score higher than low priority     |
| Urgent task              | Urgent tasks should receive the highest priority weight |
| Overdue task             | Overdue tasks should receive extra points               |
| Completed task           | Completed tasks should have a reduced score             |
| Task with important tags | Tags like urgent or blocker should increase the score   |
| Recently updated task    | Recent activity should add a small score boost          |

---

## Exercise 1.2: Test Planning

### Testing Plan

| Priority | Test                                   | Type             | Expected Outcome                                |
| -------- | -------------------------------------- | ---------------- | ----------------------------------------------- |
| High     | calculateTaskScore with urgent task    | Unit test        | Returns a high score                            |
| High     | calculateTaskScore with completed task | Unit test        | Score is reduced                                |
| High     | sortTasksByImportance                  | Unit test        | Tasks sorted from highest to lowest score       |
| Medium   | getTopPriorityTasks                    | Unit test        | Returns only the requested number of tasks      |
| Medium   | Full priority workflow                 | Integration test | Top tasks are correctly calculated and returned |

### Test Dependencies

The tests depend on:

* A task object
* Priority values
* Status values
* Due date values
* Updated date values

# Part 2: Improving a Single Test

## Exercise 2.1: Basic Test

### Simple Test Idea

```python
def test_high_priority_task_gets_higher_score():
    low_task = create_task(priority="LOW")
    high_task = create_task(priority="HIGH")

    assert calculateTaskScore(high_task) > calculateTaskScore(low_task)
```

### Improved Test

```python
def test_high_priority_task_scores_higher_than_low_priority_task():
    low_task = create_task(priority="LOW", status="PENDING")
    high_task = create_task(priority="HIGH", status="PENDING")

    low_score = calculateTaskScore(low_task)
    high_score = calculateTaskScore(high_task)

    assert high_score > low_score
```

### What Improved

The improved test is clearer because it explains exactly what behavior is being tested. It checks the outcome instead of focusing only on how the function works internally.

## Exercise 2.2: Due Date Test

### Test Idea

I wanted to test whether overdue tasks receive a higher score than tasks due later.

### Example Test

```python
def test_overdue_task_gets_higher_score_than_future_task():
    overdue_task = create_task(priority="MEDIUM", due_date="past_date")
    future_task = create_task(priority="MEDIUM", due_date="future_date")

    overdue_score = calculateTaskScore(overdue_task)
    future_score = calculateTaskScore(future_task)

    assert overdue_score > future_score
```

### What This Tests

This test checks that the due date affects the task score correctly.

---

# Part 3: Test-Driven Development Practice

## Exercise 3.1: TDD for New Feature

### New Feature

Tasks assigned to the current user should get a score boost of `+12`.

### Failing Test First

```python
def test_task_assigned_to_current_user_gets_score_boost():
    task = create_task(priority="MEDIUM", assigned_to="gabisile")

    score_without_boost = calculateTaskScore(task, current_user=None)
    score_with_boost = calculateTaskScore(task, current_user="gabisile")

    assert score_with_boost == score_without_boost + 12
```

### Minimal Code Change

The function would need to check whether the task is assigned to the current user.

```python
if task.assigned_to == current_user:
    score += 12
```

### What I Learned

TDD means writing the test before writing the feature. This helps define the expected behavior clearly before changing the code.

---

## Exercise 3.2: TDD for Bug Fix

### Bug

The calculation for days since update is incorrect.

### Test to Reproduce Bug

```python
def test_days_since_update_is_calculated_correctly():
    task = create_task(last_updated="7_days_ago")

    score = calculateTaskScore(task)

    assert score is not None
```

### Minimal Fix

The code should calculate date differences using the correct date method instead of an incorrect time conversion.

### Regression Test

A regression test should be kept so that the same bug does not return in future changes.

---

# Part 4: Integration Testing

## Exercise 4.1: Testing the Full Workflow

### Workflow Tested

This test checks that:

1. Tasks receive scores.
2. Tasks are sorted by importance.
3. Top priority tasks are returned correctly.

### Integration Test Example

```python
def test_priority_workflow_returns_top_tasks():
    tasks = [
        create_task(priority="LOW"),
        create_task(priority="HIGH"),
        create_task(priority="URGENT")
    ]

    sorted_tasks = sortTasksByImportance(tasks)
    top_tasks = getTopPriorityTasks(sorted_tasks, limit=2)

    assert len(top_tasks) == 2
    assert top_tasks[0].priority == "URGENT"

### What This Verifies

This test verifies that the main priority functions work together correctly.

# Reflection

## What I Learned About Testing

Before this exercise, I thought testing was mainly about checking whether code runs without errors.

I learned that good testing is about checking behavior. A test should confirm that the function does what the user or business expects.

## Most Important Lessons

* Start by understanding what the function should do.
* Test behavior, not just implementation.
* Include edge cases.
* Use TDD to define expected behavior before writing code.
* Integration tests help confirm that multiple functions work together.

## How AI Helped

AI helped me think about what to test, what edge cases I might miss, and how to make my test cases clearer.

## Future Approach

In future, I would first write down the expected behavior, then create test cases for normal cases, edge cases, and possible failure cases before changing the code.
