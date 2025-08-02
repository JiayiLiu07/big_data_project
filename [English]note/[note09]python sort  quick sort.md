# python sort
python sort \ quick sort

## I. Sorting in Python

### 1. Using the sorted() Function

`sorted()` is a built-in Python function that sorts any iterable object (such as a list, tuple, etc.) and returns a new list.

- **Example**

```Python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
sorted_numbers = sorted(numbers)
print(sorted_numbers) # Output: [1, 1, 2, 3, 4, 5, 6, 9]
````
- Features:
- Does not modify the original list, but returns a new sorted list.
- Can sort any iterable object.
- You can specify the sorting criteria using the key parameter, for example, sorting by string length:

```Python
words = ["apple", "banana", "cherry", "date"]
sorted_words = sorted(words, key=len) #key followed by a function
print(sorted_words) # Output: ['date', 'apple', 'banana', 'cherry']
```

### 2. Using the sort() Method on Lists

The `sort()` method on lists directly sorts the list, modifying the original list.

**Example**
```Python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
numbers.sort()
print(numbers) # Output: [1, 1, 2, 3, 4, 5, 6, 9]
```

- Features:
- Sorting directly on the original list does not return a new list. - You can also specify the sorting criteria using the key parameter.

## 2. Quick Sort

Quick Sort is an efficient sorting algorithm. Its basic idea is to break down a large problem into multiple smaller ones using a divide-and-conquer approach. Specifically, Quick Sort selects a "pivot" value, divides the list into two parts: one containing elements smaller than the pivot and the other containing elements larger than the pivot, and then recursively sorts these two parts.

**Quick Sort Steps**

1. **Pivot Selection**: Select an element from the list as the pivot. Typically, you would choose the first, last, or middle element.

2. **Partitioning**: Rearrange the list, placing all elements smaller than the pivot to the left and all elements larger to the right. This process is called partitioning.

3. **Recursive Sorting**: Recursively sort the sublists to the left and right of the pivot.

**Sample Code**
```Python
def quick_sort(arr):
# Return if the list is empty or has only one element
if len(arr) <= 1:
return arr
else:
# Select the last element in the list as the pivot
pivot = arr[-1]
# Elements less than the pivot
less = [x for x in arr[:-1] if x <= pivot]
# Elements greater than the pivot
greater = [x for x in arr[:-1] if x > pivot]
# Recursively sort the list less than and greater than the pivot, concatenating the results
return quick_sort(less) + [pivot] + quick_sort(greater)
# Test quick sort
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
sorted_numbers = quick_sort(numbers)
print(sorted_numbers) # Output: [1, 1, 2, 3, 4, 5, 6, 9]
````

**Detailed Explanation**

1. Pivot Selection:
- In this example, we choose the last element of the list as the pivot. There are various ways to choose the pivot, and different methods can affect the performance of the algorithm.

2. Partitioning:
- Use the list comprehension [x for x in arr[:-1] if x <= pivot] to create a list less containing all elements less than or equal to the pivot.
- Use the list comprehension [x for x in arr[:-1] if x > pivot] to create a list greater containing all elements greater than the pivot.

3. Recursive Sorting:
- Recursively call the quick_sort function on the less and greater sublists.
- Concatenate the sorted less list, the pivot value [pivot], and the sorted greater list to form the final sorted result.

**Quick Sort Performance**
- Average time complexity: O(nlogn)
- Worst-case time complexity: O(n^2). Performance degrades when the input list is already sorted or nearly sorted.
- Space complexity: O(logn), stack space required for recursive calls.

**Optimization**

To improve quick sort's performance, the following optimization methods can be used:

1. **Randomizing the pivot**: Randomly selecting an element as the pivot can reduce the probability of the worst-case scenario.

2. **Middle of Three**: Select the median of the first, middle, and last elements of the list as the pivot.

3. **Tail Recursion Optimization**: Reduce stack space required for recursive calls.

4. **Using Insertion Sort for Small Arrays**: For small subarrays, using a simple sorting algorithm such as insertion sort can improve efficiency.

## Summary
- **Python Sorting**:
- sorted(): Returns a new sorted list without changing the original.
- list.sort(): Sorts the original list directly without returning a new one.
- **Quick Sort**:
- Choose a pivot value.
- Split the list into two parts: one smaller than the pivot and one larger than the pivot.
- Recursively sort these two parts.
- Performance can be improved through optimization methods.