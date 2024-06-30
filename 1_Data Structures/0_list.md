### Time Complexity of List Operations

1. **Indexing**

   - **Access (Reading) an element**: \(O(1)\)
   - **Assigning a value to an element**: \(O(1)\)

**Access (Reading) an element**
Time Complexity: \(O(1)\)

```python
lst = [1, 2, 3, 4, 5]
element = lst[2]  # Access element at index 2 (value is 3)
print(element)
```

**Assigning a value to an element**
Time Complexity: \(O(1)\)

```python
lst = [1, 2, 3, 4, 5]
lst[2] = 10  # Assign new value (10) to element at index 2
print(lst)
```

2. **Appending**

   - **Appending an element at the end**: \(O(1)\) on average
     - Note: Amortized \(O(1)\) because when the list's capacity is exceeded, it may need to allocate more space and copy the elements, which takes \(O(n)\).

**Appending an element at the end**
Time Complexity: \(O(1)\) (amortized)

```python
lst = [1, 2, 3, 4, 5]
lst.append(6)  # Append element 6 at the end
print(lst)
```

3. **Inserting**

   - **Inserting an element at a specific position**: \(O(n)\)
     - All elements after the insertion point need to be shifted.

**Inserting an element at a specific position**
Time Complexity: \(O(n)\)

```python
lst = [1, 2, 3, 4, 5]
lst.insert(2, 10)  # Insert element 10 at index 2
print(lst)
```

4. **Deleting**

   - **Deleting an element at the end**: \(O(1)\)
   - **Deleting an element at the beginning or middle**: \(O(n)\)
     - All elements after the deletion point need to be shifted.

**Deleting an element at the end**
Time Complexity: \(O(1)\)

```python
lst = [1, 2, 3, 4, 5]
lst.pop()  # Remove the last element
print(lst)
```

**Deleting an element at the beginning or middle**
Time Complexity: \(O(n)\)

```python
lst = [1, 2, 3, 4, 5]
lst.pop(2)  # Remove element at index 2
print(lst)
```

5. **Searching**

   - **Searching for an element by value**: \(O(n)\)
     - Linear search is required as lists are not inherently ordered.

**Searching for an element by value**
Time Complexity: \(O(n)\)

```python
lst = [1, 2, 3, 4, 5]
index = lst.index(3)  # Find the index of element 3
print(index)
```

6. **Slicing**

   - **Slice assignment**: \(O(k + n)\)
     - \(k\) is the length of the slice being assigned, and \(n\) is the number of elements being shifted.
   - **Slice retrieval**: \(O(k)\)
     - \(k\) is the length of the slice being retrieved.

**Slice assignment**
Time Complexity: \(O(k + n)\)

```python
lst = [1, 2, 3, 4, 5]
lst[1:3] = [8, 9, 10]  # Replace elements at slice 1:3 with new list
print(lst)
```

**Slice retrieval**
Time Complexity: \(O(k)\)

```python
lst = [1, 2, 3, 4, 5]
slice_lst = lst[1:4]  # Retrieve elements from index 1 to 3
print(slice_lst)
```

7. **Length**

   - **Getting the length**: \(O(1)\)

**Getting the length**
Time Complexity: \(O(1)\)

```python
lst = [1, 2, 3, 4, 5]
length = len(lst)  # Get the length of the list
print(length)
```

8. **Concatenation**

   - **Concatenating two lists**: \(O(k + n)\)
     - \(k\) is the length of the first list, and \(n\) is the length of the second list.

**Concatenation**
Time Complexity: \(O(k + n)\)

```python
lst1 = [1, 2, 3]
lst2 = [4, 5, 6]
lst3 = lst1 + lst2  # Concatenate two lists
print(lst3)
```

9. **Reversing**

   - **Reversing a list**: \(O(n)\)

**Reversing a list**
Time Complexity: \(O(n)\)

```python
lst = [1, 2, 3, 4, 5]
lst.reverse()  # Reverse the list
print(lst)
```

10. **Sorting**
    - **Sorting a list**: \(O(n \log n)\)
      - Python uses Timsort, which is a hybrid sorting algorithm derived from merge sort and insertion sort.

**Sorting a list**
Time Complexity: \(O(n \log n)\)

```python
lst = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
lst.sort()  # Sort the list
print(lst)
```

Reference table:

| Operation         | Time Complexity      |
| ----------------- | -------------------- |
| Access (indexing) | \(O(1)\)             |
| Assign (indexing) | \(O(1)\)             |
| Append            | \(O(1)\) (amortized) |
| Insert            | \(O(n)\)             |
| Delete            | \(O(n)\)             |
| Search            | \(O(n)\)             |
| Slice assignment  | \(O(k + n)\)         |
| Slice retrieval   | \(O(k)\)             |
| Length            | \(O(1)\)             |
| Concatenation     | \(O(k + n)\)         |
| Reversing         | \(O(n)\)             |
| Sorting           | \(O(n \log n)\)      |

### Explanation of Notations

- \(O(1)\): Constant time – the operation takes the same amount of time regardless of the size of the list.
- \(O(n)\): Linear time – the operation time increases linearly with the size of the list.
- \(O(n \log n)\): Log-linear time – more efficient than quadratic time but less efficient than linear time for large lists.
