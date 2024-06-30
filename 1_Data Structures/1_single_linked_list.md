## Linked List Overview

A linked list is a linear data structure where elements, called nodes, are linked together using pointers. Each node contains two parts:

1. **Data**: The value stored in the node.
2. **Next**: A pointer/reference to the next node in the sequence.

Linked lists are dynamic and can easily grow and shrink in size. They are particularly useful for scenarios where the size of the data structure is unknown or changes frequently.

### Types of Linked Lists

1. **Singly Linked List**: Each node points to the next node.
2. **Doubly Linked List**: Each node points to both the next and the previous node.
3. **Circular Linked List**: The last node points back to the first node, forming a circle.

### Operations on Linked Lists

#### 1. **Insertion**

- **At the beginning**: Inserting a new node at the start of the list.
- **At the end**: Inserting a new node at the end of the list.
- **After a given node**: Inserting a new node after a specific node in the list.

#### 2. **Deletion**

- **From the beginning**: Removing the first node from the list.
- **From the end**: Removing the last node from the list.
- **Given node**: Removing a specific node from the list.
- **By value**: Removing a node with a specific value.

#### 3. **Traversal**

- Accessing each node of the list sequentially.

#### 4. **Search**

- Finding a node with a specific value.

#### 5. **Update**

- Modifying the value of a node.

### Implementation in Python

Here's a basic implementation of a singly linked list in Python with various operations:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None

    # Insertion at the beginning
    def insert_at_beginning(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    # Insertion at the end
    def insert_at_end(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        last.next = new_node

    # Insertion after a given node
    def insert_after_node(self, prev_node, data):
        if not prev_node:
            print("Previous node must be in the list.")
            return
        new_node = Node(data)
        new_node.next = prev_node.next
        prev_node.next = new_node

    # Deletion by value
    def delete_node(self, key):
        temp = self.head

        if temp is not None:
            if temp.data == key:
                self.head = temp.next
                temp = None
                return

        while temp is not None:
            if temp.data == key:
                break
            prev = temp
            temp = temp.next

        if temp == None:
            return

        prev.next = temp.next
        temp = None

    # Traversal
    def traverse(self):
        temp = self.head
        while temp:
            print(temp.data, end=" -> ")
            temp = temp.next
        print("None")

    # Search for a node
    def search(self, key):
        current = self.head
        while current:
            if current.data == key:
                return True
            current = current.next
        return False

    # Update a node's data
    def update(self, old_data, new_data):
        temp = self.head
        while temp:
            if temp.data == old_data:
                temp.data = new_data
                return
            temp = temp.next
        print("Node with data", old_data, "not found.")

# Example usage
linked_list = SinglyLinkedList()
linked_list.insert_at_end(1)
linked_list.insert_at_end(2)
linked_list.insert_at_beginning(0)
linked_list.insert_after_node(linked_list.head.next, 1.5)
linked_list.traverse()  # Output: 0 -> 1 -> 1.5 -> 2 -> None

print("Search 1.5:", linked_list.search(1.5))  # Output: Search 1.5: True
linked_list.update(1.5, 1.75)
linked_list.traverse()  # Output: 0 -> 1 -> 1.75 -> 2 -> None

linked_list.delete_node(1)
linked_list.traverse()  # Output: 0 -> 1.75 -> 2 -> None
```

### Detailed Explanation

1. **Node Class**: Represents each node in the list, with `data` and `next` attributes.
2. **SinglyLinkedList Class**: Manages the linked list with the following methods:
   - **insert_at_beginning(data)**: Creates a new node and inserts it at the beginning.
   - **insert_at_end(data)**: Creates a new node and inserts it at the end.
   - **insert_after_node(prev_node, data)**: Creates a new node and inserts it after a given node.
   - **delete_node(key)**: Deletes the first occurrence of a node with the given data.
   - **traverse()**: Prints the entire list.
   - **search(key)**: Searches for a node with the given data.
   - **update(old_data, new_data)**: Updates the data of a node.

### Advantages of Linked Lists

- **Dynamic Size**: Can grow and shrink in size as needed.
- **Ease of Insertion/Deletion**: Can insert or delete nodes without rearranging the entire data structure.

### Disadvantages of Linked Lists

- **Memory Usage**: Requires extra memory for storing pointers.
- **Sequential Access**: Cannot directly access elements by index, leading to slower access times compared to arrays.

## Time Complexity

### 1. **Insertion**

- **At the Beginning**

  - **Time Complexity**: \( O(1) \)
  - **Explanation**: Inserting a node at the beginning involves updating the head pointer to the new node and setting the new node's next pointer to the old head. These are constant-time operations.

- **At the End**

  - **Time Complexity**: \( O(n) \)
  - **Explanation**: To insert at the end, you need to traverse the entire list to find the last node (which takes \( O(n) \) time) and then update its next pointer to the new node (which takes \( O(1) \) time).

- **After a Given Node**
  - **Time Complexity**: \( O(1) \)
  - **Explanation**: If you already have a reference to the node after which you want to insert, you only need to update the next pointers, which is a constant-time operation.

### 2. **Deletion**

- **From the Beginning**

  - **Time Complexity**: \( O(1) \)
  - **Explanation**: Deleting the first node involves updating the head pointer to the second node, which is a constant-time operation.

- **From the End**

  - **Time Complexity**: \( O(n) \)
  - **Explanation**: To delete the last node, you need to traverse the list to find the second last node (which takes \( O(n) \) time), and then update its next pointer to `None` (which takes \( O(1) \) time).

- **Given Node (by Value)**
  - **Time Complexity**: \( O(n) \)
  - **Explanation**: You need to search for the node containing the value to delete, which takes \( O(n) \) time in the worst case, and then update the pointers accordingly (which takes \( O(1) \) time).

### 3. **Traversal**

- **Time Complexity**: \( O(n) \)
- **Explanation**: Traversing the list involves visiting each node once, which takes linear time.

### 4. **Search**

- **Time Complexity**: \( O(n) \)
- **Explanation**: To find a node with a specific value, you may need to traverse the entire list in the worst case, which takes linear time.

### 5. **Update**

- **Time Complexity**: \( O(n) \)
- **Explanation**: To update a node with a specific value, you may need to search for the node first (which takes \( O(n) \) time) and then update the value (which takes \( O(1) \) time).

### Summary Table

| Operation               | Time Complexity |
| ----------------------- | --------------- |
| Insert at Beginning     | \( O(1) \)      |
| Insert at End           | \( O(n) \)      |
| Insert After Given Node | \( O(1) \)      |
| Delete from Beginning   | \( O(1) \)      |
| Delete from End         | \( O(n) \)      |
| Delete Given Node       | \( O(n) \)      |
| Traverse                | \( O(n) \)      |
| Search                  | \( O(n) \)      |
| Update                  | \( O(n) \)      |

### Explanation of Notations

- **\( O(1) \)**: Constant time – the operation takes the same amount of time regardless of the size of the list.
- **\( O(n) \)**: Linear time – the operation time increases linearly with the size of the list.

Understanding these time complexities helps you determine the efficiency of linked list operations and when a linked list might be a better choice compared to other data structures like arrays or dynamic arrays (e.g., Python lists). For instance, linked lists are particularly efficient for scenarios requiring frequent insertions and deletions at the beginning or middle of the list.
