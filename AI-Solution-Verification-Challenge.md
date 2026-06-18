# AI Solution Verification Challenge

## Selected Scenario

I selected the **buggy sorting function** scenario.

The function uses merge sort, but it contains a subtle bug inside the `merge()` function.

## Problem Description

The code is supposed to sort an array using merge sort.

Merge sort works by:

1. Splitting the array into smaller parts.
2. Sorting each part.
3. Merging the sorted parts back together.

The issue is found in the part of the code that merges the left and right arrays.

## Original Buggy Code

```javascript
function merge(left, right) {
  let result = [];
  let i = 0;
  let j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] < right[j]) {
      result.push(left[i]);
      i++;
    } else {
      result.push(right[j]);
      j++;
    }
  }

  while (i < left.length) {
    result.push(left[i]);
    j++; // Bug: should increment i
  }

  while (j < right.length) {
    result.push(right[j]);
    j++;
  }

  return result;
}
```

## AI Suggested Solution

The AI identified that the bug is in this section:

```javascript
while (i < left.length) {
  result.push(left[i]);
  j++;
}
```

The loop is processing the remaining items from the `left` array, so it should increment `i`, not `j`.

## Collaborative Solution Verification

I checked whether the AI solution matched the logic of the code.

Since this loop is reading from `left[i]`, the index `i` must move forward after each item is added.

The corrected version is:

```javascript
while (i < left.length) {
  result.push(left[i]);
  i++;
}
```

This makes sense because:

* `i` tracks the left array.
* `j` tracks the right array.
* When adding from the left array, `i` must increase.

## Learning Through Alternative Approaches

An alternative way to write the remaining merge logic is to use `concat()`:

```javascript
return result.concat(left.slice(i)).concat(right.slice(j));
```

This avoids manually writing two extra loops.

Another approach is to keep the loops but make sure each loop increments the correct index:

```javascript
while (i < left.length) {
  result.push(left[i]);
  i++;
}

while (j < right.length) {
  result.push(right[j]);
  j++;
}

This helped me understand that there is more than one correct way to solve the problem.

## Developing a Critical Eye

I did not accept the AI solution without checking it.

I verified the solution by asking:

* Which array is being read?
* Which index belongs to that array?
* Does the loop move toward ending?
* Would the loop get stuck or read the same value repeatedly?

The original bug would cause the loop to keep reading `left[i]` without increasing `i`, which could lead to incorrect behaviour or an infinite loop.

## Final Verified Solution

```javascript
function mergeSort(arr) {
  if (arr.length <= 1) return arr;

  const mid = Math.floor(arr.length / 2);
  const left = mergeSort(arr.slice(0, mid));
  const right = mergeSort(arr.slice(mid));

  return merge(left, right);
}

function merge(left, right) {
  let result = [];
  let i = 0;
  let j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] < right[j]) {
      result.push(left[i]);
      i++;
    } else {
      result.push(right[j]);
      j++;
    }
  }

  while (i < left.length) {
    result.push(left[i]);
    i++;
  }

  while (j < right.length) {
    result.push(right[j]);
    j++;
  }
  return result;
}

## Test Cases I Would Use

```javascript
console.log(mergeSort([5, 3, 8, 1, 2]));
// Expected output: [1, 2, 3, 5, 8]

console.log(mergeSort([1]));
// Expected output: [1]

console.log(mergeSort([]));
// Expected output: []

console.log(mergeSort([4, 4, 2, 1]));
// Expected output: [1, 2, 4, 4]
```
## Reflection Questions

### How did my confidence in the solution change after verification?

My confidence increased after I verified why the index needed to change from `j++` to `i++`. At first, the fix looked small, but checking the role of each variable helped me understand why it was correct.

### What aspects of the AI solution required the most scrutiny?

The most important part to check was whether the AI correctly identified which index belonged to which array. A small mistake in indexes can completely break a sorting algorithm.

### Which verification technique was most valuable?

The most valuable technique was developing a critical eye. Instead of only accepting the AI answer, I traced the variables and checked whether the loop made logical sense.

## What I Learned

This exercise taught me that AI can quickly identify a bug, but I still need to verify the solution.

I learned that small errors, such as incrementing the wrong variable, can cause serious issues in algorithms. I also learned that testing with different inputs helps confirm whether the solution works correctly.

The biggest lesson is that AI should be treated as a helpful assistant, not as the final authority. A developer still needs to understand, test, and verify the suggested solution.
