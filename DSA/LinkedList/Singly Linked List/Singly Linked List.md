---
tags:
  - DSA
  - LinkedList
---
# Singly Linked List
A **singly linked list** is a fundamental data structure in computer science and programming, it consists of ***nodes*** where each node contains a ***data*** field and a ***reference*** to the next node in the node. The last node points to ***null***, indicating the end of the list. This linear structure supports efficient insertion and deletion operations, making it widely used in various applications. In this tutorial, we’ll explore the node structure, understand the operations on singly linked lists (traversal, searching, length determination, insertion, and deletion), and provide detailed explanations and code examples to implement these operations effectively.
## What is Singly Linked List?
A ***singly linked list*** is a fundamental data structure in computer science and programming. It is a collection of nodes where each node contains a ***data field*** and a ***reference*** (link) to the next node in the sequence. The last node in the list points to ***null***, indicating the end of the list. This linear data structure allows for efficient insertion and deletion operations, making it a popular choice for various applications.
## Understanding Node Structure
In a singly linked list, each node consists of two parts: data and a pointer to the next node. The data part stores the actual information, while the pointer (or reference) part stores the address of the next node in the sequence. This structure allows nodes to be dynamically linked together, forming a chain-like sequence.

![[images/Singly-Linked-List.webp| center]]
In this representation, each box represents a node, with an arrow indicating the link to the next node. The last node points to NULL, indicating the end of the list.

````tabs

tab: C++
```cpp
// Definition of a Node in a singly linked list
struct Node {
  
    // Data part of the node
    int data;

    // Pointer to the next node in the list
    Node* next;

    // Constructor to initialize the node with data
    Node(int data)
    {
        this->data = data;
        this->next = nullptr;
    }
};
```
tab: C
```c
// Definition of a Node in a singly linked list
struct Node {
    int data;          
    struct Node* next;
};

// Function to create a new Node
struct Node* newNode(int data) {
    struct Node* temp = 
      (struct Node*)malloc(sizeof(struct Node));
    temp->data = data;
    temp->next = NULL;
    return temp;
}
```
tab: Java
```java
// Definition of a Node in a singly linked list
public class Node {
    int data;
    Node next;

    // Constructor to initialize the node with data
    public Node(int data)
    {
        this.data = data;
        this.next = null;
    }
}
```
tab: Python
```python
# Definition of a Node in a singly linked list
class Node:
    def __init__(self, data):
       # Data part of the node
        self.data = data   
        self.next = None   
```
tab: Javascript
```javascript
// Definition of a Node in a singly linked list
class Node {
    constructor(data) {
    // Data part of the node
        this.data = data;   
        this.next = null;   
    }
}
```
````
In this example, the Node class contains an integer data field (***data***) to store the information and a pointer to another Node (***next***) to establish the link to the next node in the list.
## Operations on Singly Linked List
- **Traversal**
- **Searching**
- **Length**
- **Insertion:**
    - Insert at the beginning
    - Insert at the end
    - Insert at a specific position
- **Deletion:**
    - Delete from the beginning
    - Delete from the end
    - Delete a specific node

Let’s go through each of the operations mentioned above, one by one.
## ***Traversal*** in Singly Linked List
Traversal involves visiting each node in the linked list and performing some operation on the data. A simple traversal function would print or process the data of each node.

Step-by-step approach:

- Initialize a pointer current to the head of the list.
- Use a while loop to iterate through the list until the current pointer reaches NULL.
- Inside the loop, print the data of the current node and move the current pointer to the next node.

Below is the function for traversal in singly Linked List:
````tabs

tab: C++
```cpp
/// C++ Function to traverse and print the elements of the linked
// list
void traverseLinkedList(Node* head)
{
    // Start from the head of the linked list
    Node* current = head;

    // Traverse the linked list until reaching the end
    // (nullptr)
    while (current != nullptr) {
      
        // Print the data of the current node
        cout << current->data << " ";

        // Move to the next node
        current = current->next;
    }

    cout << std::endl;
}
```
tab: C
```c
// Function to traverse and print the elements 
// of the linked list
void traverseLinkedList(struct Node* head)
{
    // Start from the head of the linked list
    struct Node* current = head;

    // Traverse the linked list until reaching the end (NULL)
    while (current != NULL) {

        // Print the data of the current node
        printf("%d ", current->data);

        // Move to the next node
        current = current->next;
    }

    printf("\n");
}
```
tab: Java
```java
// Java Function to traverse and print the elements of the
// linked list
public static void traverseLinkedList(Node head)
{
    // Start from the head of the linked list
    Node current = head;

    // Traverse the linked list until reaching the end
    // (null)
    while (current != null) {

        // Print the data of the current node
        System.out.print(current.data + " ");

        // Move to the next node
        current = current.next;
    }

    System.out.println();
}
```
tab: Python
```python
# Python Function to traverse and print the elements of the linked list
def traverse_linked_list(head):
    # Start from the head of the linked list
    current = head

    # Traverse the linked list until reaching the end (None)
    while current is not None:

        # Print the data of the current node followed by a space
        print(current.data),

        # Move to the next node
        current = current.next

    print()  # Print a new line after traversing the linked list
```
tab: Javascript
```javascript
// Javascript Function to traverse and print the elements
// of the linked list
function traverseLinkedList(head) {

    // Start from the head of the linked list
    let current = head;

    // Traverse the linked list until reaching the
    // end (null)
    while (current !== null) {
    
        // Print the data of the current node
        console.log(current.data + " ");

        // Move to the next node
        current = current.next;
    }

    console.log();
}
```
````
## Searching in Singly Linked List
Searching in a Singly Linked List refers to the process of looking for a specific element or value within the elements of the linked list.

Step-by-step approach:

1. Traverse the Linked List starting from the head.
2. Check if the current node’s data matches the target value.
    - If a match is found, return ***true***.
3. Otherwise, Move to the next node and repeat steps 2.
4. If the end of the list is reached without finding a match, return ***false***.

Below is the function for searching in singly linked list:
````tabs

tab: C++
```cpp
// Function to search for a value in the Linked List
bool searchLinkedList(struct Node* head, int target)
{
    // Traverse the Linked List
    while (head != nullptr) {

        // Check if the current node's
        // data matches the target value
        if (head->data == target) {
            return true; // Value found
        }

        // Move to the next node
        head = head->next;
    }

    return false; // Value not found
}

```
tab: C
```c
// Function to search for a value in the Linked List
bool searchLinkedList(struct Node* head, int target)
{
    // Traverse the Linked List
    while (head != NULL) {

        // Check if the current node's
        // data matches the target value
        if (head->data == target) {
            return true; // Value found
        }

        // Move to the next node
        head = head->next;
    }

    return false; // Value not found
}

```
tab: Java
```java
// Java function to search for a value in the Linked List
public boolean searchLinkedList(Node head, int target)
{
    // Traverse the Linked List
    while (head != null) {

        // Check if the current node's data matches the
        // target value
        if (head.data == target) {

            // Value found
            return true;
        }

        // Move to the next node
        head = head.next;
    }

    // Value not found
    return false;
}

```
tab: Python
```python
# Python function to search for a value in the Linked List
def search_linked_list(head, target):

    # Traverse the Linked List
    while head is not None:

        # Check if the current node's data matches the target value
        if head.data == target:

            return True  # Value found
        # Move to the next node
        head = head.next

    return False  # Value not found

```
tab: Javascript
```javascript
// Javascript function to search for a value in the Linked List
function searchLinkedList(head, target) {

    // Traverse the Linked List
    while (head !== null) {
    
        // Check if the current node's data matches the target value
        if (head.data === target) {
            return true;  // Value found
        }
        
        // Move to the next node
        head = head.next;
    }
    
    return false;  // Value not found
}

```
````
## Finding Length in Singly Linked List
Finding Length in Singly Linked List refers to the process of determining the total number of nodes in a singly linked list.

Step-by-step approach:

- Initialize a counter ***length*** to 0.
- Start from the head of the list, assign it to current.
- Traverse the list:
    - Increment ***length*** for each node.
    - Move to the next node (***current = current->next***).
- Return the final value of ***length***.

Below is the function for finding length in Singly Linked List:
````tabs

tab: C++
```cpp
// C++ function to find the length of the linked list
int findLength(Node* head)
{
    // Initialize a counter for the length
    int length = 0;

    // Start from the head of the list
    Node* current = head;

    // Traverse the list and increment the length for each
    // node
    while (current != nullptr) {
        length++;
        current = current->next;
    }

    // Return the final length of the linked list
    return length;
}
```
tab: C
```c
/#include <stdio.h>
#include <stdlib.h>

// Definition of a Node in a singly linked list
struct Node {
    int data;          // Data part of the node
    struct Node* next; // Pointer to the next node in the list
};

// Function to find the length of the linked list
int findLength(struct Node* head)
{
    // Initialize a counter for the length
    int length = 0;

    // Start from the head of the list
    struct Node* curr = head;

    // Traverse the list and increment
    // the length for each node
    while (curr != NULL) {
        length++;
        curr = curr->next;
    }

    // Return the final length of the linked list
    return length;
}
```
tab: Java
```java
// Java function to find the length of the linked list
public int findLength(Node head) {
  
    // Initialize a counter for the length
    int length = 0;

    // Start from the head of the list
    Node current = head;

    // Traverse the list and increment the length for each
    // node
    while (current != null) {
        length++;
        current = current.next;
    }

    // Return the final length of the linked list
    return length;
}
```
tab: Python
```python
# Python function to find the length of the linked list
def find_length(head):
  
    # Initialize a counter for the length
    length = 0

    # Start from the head of the list
    current = head

    # Traverse the list and increment the length for each
    # node
    while current is not None:
        length += 1
        current = current.next

    # Return the final length of the linked list
    return length
```
tab: Javascript
```javascript
// Javascript function to find the length of the linked list
function findLength(head) {

    // Initialize a counter for the length
    let length = 0;

    // Start from the head of the list
    let current = head;

    // Traverse the list and increment the length for each
    // node
    while (current !== null) {
        length++;
        current = current.next;
    }

    // Return the final length of the linked list
    return length;
}
```
````
## Insertion in Singly Linked List
Insertion is a fundamental operation in linked lists that involves adding a new node to the list. There are several scenarios for insertion:
#### 1. Insertion at the Beginning of Singly Linked List:
   ![[images/Insertion-at-the-Beginning-of-Singly-Linked-List.webp|center]]

Step-by-Step approach:
  - Create a new node with the given value
  - Set the **next** pointer of the new node to the current head.
  - Move the head to point to the new node.
  - Return the new head of the linked list.
````tabs

tab: C++
```cpp
// C++ function to insert a new node at the beginning of the
// linked list
Node* insertAtBeginning(Node* head, int value)
{
    // Create a new node with the given value
    Node* newNode = new Node(value);

    // Set the next pointer of the new node to the current
    // head
    newNode->next = head;

    // Move the head to point to the new node
    head = newNode;

    // Return the new head of the linked list
    return head;
}
```
tab: C
```c
// Function to insert a new node at the beginning of the linked list
struct Node* insertAtBeginning(struct Node* head, int value)
{
    // Create a new node with the given value
    struct Node* new_node = newNode(value);

    // Set the next pointer of the new node to the current head
    new_node->next = head;

    // Move the head to point to the new node
    head = new_node;

    // Return the new head of the linked list
    return head;
}
```
tab: Java
```java
// Java function to insert a new node at the beginning of the
// linked list
public Node insertAtBeginning(Node head, int value) {
    // Create a new node with the given value
    Node newNode = new Node(value);

    // Set the next pointer of the new node to the current
    // head
    newNode.next = head;

    // Move the head to point to the new node
    head = newNode;

    // Return the new head of the linked list
    return head;
}

```
tab: Python
```python
# Python function to insert a new node at the beginning of the
# linked list
def insert_at_beginning(head, value):
  
    # Create a new node with the given value
    new_node = Node(value)

    # Set the next pointer of the new node to the current
    # head
    new_node.next = head

    # Move the head to point to the new node
    head = new_node

    # Return the new head of the linked list
    return head
```
tab: Javascript
```javascript
// Javascript function to insert a new node at the beginning of the
// linked list
function insertAtBeginning(head, value) {

    // Create a new node with the given value
    let newNode = new Node(value);

    // Set the next pointer of the new node to the current
    // head
    newNode.next = head;

    // Move the head to point to the new node
    head = newNode;

    // Return the new head of the linked list
    return head;
}
```
````
#### 2. Insertion at the End of Singly Linked List:
   ![[images/Insertion-at-the-End-of-Singly-Linked-List.webp|center]]
   Insertion at the End of Singly Linked List
   Step-by-Step approach:
  - Create a new node with the given value.
  - Check if the list is empty.
	  - If it is, make the new node the head and return.
- Traverse the list until the last node the head and return.
- Link the new node to the current last node by setting the last node's next pointer to the new node.

Below is the function for insertion at the end of singly linked list:
````tabs

tab: C++
```cpp
// Javascript function to insert a node at the end of the linked
// list
function insertAtEnd(head, value) {

    // Create a new node with the given value
    let newNode = new Node(value);

    // If the list is empty, make the new node the head
    if (head === null) {
        return newNode;
    }

    // Traverse the list until the last node is reached
    let current = head;
    while (current.next !== null) {
        current = current.next;
    }

    // Link the new node to the current last node
    current.next = newNode;

    return head;
}
```
tab: C
```c
// Function to insert a node at the end of the linked list
struct Node* insertAtEnd(struct Node* head, int value)
{
    // Create a new node with the given value
    struct Node* new_node = newNode(value);

    // If the list is empty, make the new node the head
    if (head == NULL)
        return new_node;

    // Traverse the list until the last node is reached
    struct Node* curr = head;
    while (curr->next != NULL) {
        curr = curr->next;
    }

    // Link the new node to the current last node
    curr->next = new_node;

    return head;
}
```
tab: Java
```java
// Function to insert a node at the end of the linked list
public static Node insertAtEnd(Node head, int value)
{
    // Create a new node with the given value
    Node newNode = new Node(value);

    // If the list is empty, make the new node the head
    if (head == null)
        return newNode;

    // Traverse the list until the last node is reached
    Node curr = head;
    while (curr.next != null) {
        curr = curr.next;
    }

    // Link the new node to the current last node
    curr.next = newNode;

    return head;
}
```
tab: Python
```python
# Python function to insert a node at the end of the linked
# list
def insert_at_end(head, value):
  
    # Create a new node with the given value
    new_node = Node(value)

    # If the list is empty, make the new node the head
    if head is None:
        return new_node

    # Traverse the list until the last node is reached
    current = head
    while current.next is not None:
        current = current.next

    # Link the new node to the current last node
    current.next = new_node

    return head
```
tab: Javascript
```javascript
// Javascript function to insert a node at the end of the linked
// list
function insertAtEnd(head, value) {

    // Create a new node with the given value
    let newNode = new Node(value);

    // If the list is empty, make the new node the head
    if (head === null) {
        return newNode;
    }

    // Traverse the list until the last node is reached
    let current = head;
    while (current.next !== null) {
        current = current.next;
    }

    // Link the new node to the current last node
    current.next = newNode;

    return head;
}
```
````
#### 3. Insertion at a Specific Position of the Singly Linked List:
To insert a node at a specific position, traverse the list to the desired position, link the new node to the next node, and update the links accordingly.
   ![[images/Insertion-at-a-Specific-Position-of-the-Singly-Linked-List.webp|center]]
Insertion at a Specific Position of the Singly Linked List
We mainly find the node after which we need to insert the new node. If we encounter a NULL before reaching that node, it means that the given position is invalid.
   
Before is the function for insertion at specific position of the singly linked list:
````tabs

tab: C++
```cpp
// Function to insert a Node at a specified position
// without using a double pointer
Node* insertPos(Node* head, int pos, int data)
{
    if (pos < 1) {
        cout << "Invalid position!" << endl;
        return head;
    }

    // Special case for inserting at the head
    if (pos == 1) {        
        Node* temp = new Node(data);
        temp->next = head;
        return temp;
    }

    // Traverse the list to find the node
    // before the insertion point
    Node* prev = head;
    int count = 1;
    while (count < pos - 1 && prev != nullptr) {
        prev = prev->next;
        count++;
    }

    // If position is greater than the number of nodes
    if (prev == nullptr) {
        cout << "Invalid position!" << endl;
        return head;
    }

    // Insert the new node at the specified position
    Node* temp = new Node(data);
    temp->next = prev->next;
    prev->next = temp;

    return head;
}
```
tab: C
```c
// Function to insert a node at a specified position
struct Node* insertPos(struct Node* head, int pos, int data) {
    if (pos < 1) {
        printf("Invalid position!\n");
        return head;
    }

    // Special case for inserting at the head
    if (pos == 1) {
        struct Node* temp = getNode(data);
        temp->next = head;
        return temp;
    }

    // Traverse the list to find the node 
    // before the insertion point
    struct Node* prev = head;
    int count = 1;
    while (count < pos - 1 && prev != NULL) {
        prev = prev->next;
        count++;
    }

    // If position is greater than the number of nodes
    if (prev == NULL) {
        printf("Invalid position!\n");
        return head;
    }

    // Insert the new node at the specified position
    struct Node* temp = getNode(data);
    temp->next = prev->next;
    prev->next = temp;

    return head;
}
```
tab: Java
```java
public static Node insertPos(Node head, int pos, int data)
{
    if (pos < 1) {
        System.out.println("Invalid position!");
        return head;
    }

    // Special case for inserting at the head
    if (pos == 1) {
        Node temp = new Node(data);
        temp.next = head;
        return temp;
    }

    // Traverse the list to find the node before the
    // insertion point
    Node prev = head;
    int count = 1;
    while (count < pos - 1 && prev != null) {
        prev = prev.next;
        count++;
    }

    // If position is greater than the number of nodes
    if (prev == null) {
        System.out.println("Invalid position!");
        return head;
    }

    // Insert the new node at the specified position
    Node temp = new Node(data);
    temp.next = prev.next;
    prev.next = temp;

    return head;
}
```
tab: Python
```python
# Function to insert a node at a specified position
def insertPos(head, pos, data):
    if pos < 1:
        print("Invalid position!")
        return head

    # Special case for inserting at the head
    if pos == 1:
        new_node = Node(data)
        new_node.next = head
        return new_node

    # Traverse the list to find the node before 
    # the insertion point
    prev = head
    count = 1
    while count < pos - 1 and prev is not None:
        prev = prev.next
        count += 1

    # If position is greater than the number of nodes
    if prev is None:
        print("Invalid position!")
        return head

    # Insert the new node at the specified position
    new_node = Node(data)
    new_node.next = prev.next
    prev.next = new_node

    return head
```
tab: Javascript
```javascript
// Function to insert a node at a specified position
function insertPos(head, pos, data) {
    if (pos < 1) {
        console.log("Invalid position!");
        return head;
    }

    // Special case for inserting at the head
    if (pos === 1) {
        const newNode = new Node(data);
        newNode.next = head;
        return newNode;
    }

    // Traverse the list to find the node
    // before the insertion point
    let prev = head;
    let count = 1;
    while (count < pos - 1 && prev !== null) {
        prev = prev.next;
        count++;
    }

    // If position is greater than the number of nodes
    if (prev === null) {
        console.log("Invalid position!");
        return head;
    }

    // Insert the new node at the specified position
    const newNode = new Node(data);
    newNode.next = prev.next;
    prev.next = newNode;

    return head;
}
```
````
## Deletion in Singly Linked List
Deletion involves removing a node form the linked list. Similar to insertion, there are different scenarios for deletion:
#### 1. Deletion at the Beginning of Singly Linked List:
To delete the first node, update the head to point to the second node in the list.
![[images/Deletion-at-the-Beginning-of-Singly-Linked-List.webp|center]]
Deletion at the Beginning of Singly Linked List
Steps-by-Steps approach:
- Check if the head is **NULL**.
	- If it is, return **NULL** (the list is empty)
- Store the current head node in a temporary variable **temp**.
- Move the head pointer to the next node.
- Delete the temporary node.
- Return the new head of the linked list.

Below is the function for deletion at the beginning of singly linked list:
````tabs

tab: C++
```cpp
// C++ Function to remove the first node of the linked
// list
Node* removeFirstNode(Node* head)
{
    if (head == nullptr)
        return nullptr;

    // Move the head pointer to the next node
    Node* temp = head;
    head = head->next;

    delete temp;

    return head;
}
```
tab: C
```c
// Function to remove the first node of the linked list
struct Node* removeFirstNode(struct Node* head)
{
    if (head == NULL)
        return NULL;

    // Move the head pointer to the next node
    struct Node* temp = head;
    head = head->next;

    // Free the memory of the old head
    free(temp);

    return head;
}
```
tab: Java
```java
/// Java Function to remove the first node
// of the linked list
static Node removeFirstNode(Node head)
{
    if (head == null)
        return null;

    // Move the head pointer to the next node
    Node temp = head;
    head = head.next;

    return head;
}
```
tab: Python
```python
# Python Function to remove the first node
# of the linked list
def removeFirstNode(head):
    if not head:
        return None
    temp = head

    # Move the head pointer to the next node
    head = head.next
    temp = None
    return head
```
tab: Javascript
```javascript
// Javascript Function to remove the first node
// of the linked list /
function removeFirstNode(head) {
  if (head == null) return null;

  // Move the head pointer to the next node
  temp = head;
  head = head.next;

  return head;
}
```
````
#### 2. Deletion at the End of Singly Linked List:
To delete the last node, traverse the list until the second-to-last node and update its next field to Node.
![[images/Deletion-at-the-End-of-Singly-Linked-List.webp|center]]
Deletion at the End of Singly Linked List:
Step-by-Step approach:
- Check if the head is **NULL**.
	- If it is, return **NULL** (the list is empty)
- Check if the head's **next** is **NULL** (only one node in the list).
	- If true, delete the head and return **NULL**
- Traverse the list to find the second last node (**second_last**)
- Delete the last node (the node after **second_last**).
- Set the **next** pointer of the second last node to **NULL**
- Return the head of the linked list.

Below is the function for deletion at the end of singly linked list:
````tabs

tab: C++
```cpp
// C++ Function to remove the last node of the linked list
Node* removeLastNode(Node* head)
{
    if (head == nullptr)
        return nullptr;
 
    if (head->next == nullptr) {
        delete head;
        return nullptr;
    }
 
    // Find the second last node
    Node* second_last = head;
    while (second_last->next->next != nullptr)
        second_last = second_last->next;
 
    // Delete last node
    delete (second_last->next);
 
    // Change next of second last
    second_last->next = nullptr;
 
    return head;
}
```
tab: C
```c
// Function to remove the last node of the linked list
struct Node* removeLastNode(struct Node* head)
{
    if (head == NULL)
        return NULL;

    if (head->next == NULL) {
        free(head);
        return NULL;
    }

    // Find the second last node
    struct Node* second_last = head;
    while (second_last->next->next != NULL)
        second_last = second_last->next;

    // Delete last node
    free(second_last->next);

    // Change next of second last
    second_last->next = NULL;

    return head;
}
```
tab: Java
```java
// Java Function to remove the last node of the linked list
Node removeLastNode(Node head)
{
    // If the list is empty, return null
    if (head == null)
        return null;

    // If the list has only one node, delete it and return
    // null
    if (head.next == null) {
        head = null;
        return null;
    }

    // Find the second last node
    Node second_last = head;
    while (second_last.next.next != null)
        second_last = second_last.next;

    // Remove the last node
    second_last.next = null;

    // Return the modified list
    return head;
}
```
tab: Python
```python
# Python Function to remove the last node of the linked list
def removeLastNode(head):
    # If the list is empty, return None
    if head is None:
        return None

    # If the list has only one node, delete it and return None
    if head.next is None:
        head = None
        return None

    # Find the second last node
    second_last = head
    while second_last.next.next is not None:
        second_last = second_last.next

    # Remove the last node
    second_last.next = None

    # Return the modified list
    return head
```
tab: Javascript
```javascript
// Javascript Function to remove the last node of the linked list
function removeLastNode(head) {
    // If the list is empty, return null
    if (head === null)
        return null;

    // If the list has only one node, delete it
    // and return null
    if (head.next === null) {
        head = null;
        return null;
    }

    // Find the second last node
    let second_last = head;
    while (second_last.next.next !== null)
        second_last = second_last.next;

    // Remove the last node
    second_last.next = null;
    
    // Return the modified list
    return head;
}
```
````
## Deletion at a Specific Position of Singly Linked List:
To delete a node at specific position, traverse the list to the desired position, update the links to bypass the node to be deleted.

![[images/Deletion-at-a-Specific-Position-of-Singly-Linked-List.webp]]
Deletion at a Specific Position of Singly Linked List
Step-by-Step approach:
- Check if the list is empty or the position is invalid, return if so.
- If the head needs to be deleted, update the head and delete the node.
- Traverse to the node before the position to be deleted.
- If the position is out of range, return.
- Store the node to be deleted.
- Update the links to bypass the node.
- Delete the stored node.

Below is the function for deletion at a specific position of singly linked list:
````tabs

tab: C++
```cpp
// C++ function to delete a node at a specific position
Node* deleteAtPosition(Node* head, int position)
{
    // If the list is empty or the position is invalid
    if (head == nullptr || position < 1) {
        return head;
    }

    // If the head needs to be deleted
    if (position == 1) {
        Node* temp = head;
        head = head->next;
        delete temp;
        return head;
    }

    // Traverse to the node before the position to be
    // deleted
    Node* current = head;
    for (int i = 1; i < position - 1 && current != nullptr;
         i++) {
        current = current->next;
    }

    // If the position is out of range
    if (current == NULL || current->next == nullptr) {
        return;
    }

    // Store the node to be deleted
    Node* temp = current->next;

    // Update the links to bypass the node to be deleted
    current->next = current->next->next;

    // Delete the node
    delete temp;
  
    return head;
}
```
tab: C
```c
// Function to delete a node at a specific position
struct Node* deleteAtPosition(struct Node* head, int position)
{
    // If the list is empty or the position is invalid
    if (head == NULL || position < 1) {
        return head;
    }

    // If the head needs to be deleted
    if (position == 1) {
        struct Node* temp = head;
        head = head->next;
        free(temp);
        return head;
    }

    // Traverse to the node before the position to be deleted
    struct Node* curr = head;
    for (int i = 1; i < position - 1 && curr != NULL; i++) {
        curr = curr->next;
    }

    // If the position is out of range
    if (curr == NULL || curr->next == NULL) {
        return head;
    }

    // Store the node to be deleted
    struct Node* temp = curr->next;

    // Update the links to bypass the node to be deleted
    curr->next = curr->next->next;

    // Delete the node
    free(temp);
  
    return head;
}
```
tab: Java
```java
// Java function to delete a node at a specific position
public void deleteAtPosition(Node head, int position)
{
    // If the list is empty or the position is invalid
    if (head == null || position < 1) {
        return;
    }

    // If the head needs to be deleted
    if (position == 1) {
        Node temp = head;
        head = head.next;
        temp = null;
        return;
    }

    // Traverse to the node before the position to be
    // deleted
    Node current = head;
    for (int i = 1; i < position - 1 && current != null;
         i++) {
        current = current.next;
    }

    // If the position is out of range
    if (current == null || current.next == null) {
        return;
    }

    // Store the node to be deleted
    Node temp = current.next;

    // Update the links to bypass the node to be deleted
    current.next = current.next.next;

    // Delete the node
    temp = null;
}
```
tab: Python
```python
# Python function to delete a node at a specific position
def delete_at_position(head, position):
    # If the list is empty or the position is invalid
    if head is None or position < 1:
        return head

    # If the head needs to be deleted
    if position == 1:
        temp = head
        head = head.next
        temp = None
        return head

    # Traverse to the node before the position to be deleted
    current = head
    for i in range(1, position - 1):
        if current is not None:
            current = current.next

    # If the position is out of range
    if current is None or current.next is None:
        return head

    # Store the node to be deleted
    temp = current.next

    # Update the links to bypass the node to be deleted
    current.next = current.next.next

    # Delete the node
    temp = None
    return head
```
tab: Javascript
```javascript
// Javascript function to delete a node at a specific position
function deleteAtPosition(head, position) {
    // If the list is empty or the position is invalid
    if (head === null || position < 1) {
        return head;
    }

    // If the head needs to be deleted
    if (position === 1) {
        let temp = head;
        head = head.next;
        temp = null;
        return head;
    }

    // Traverse to the node before the position to be deleted
    let current = head;
    for (let i = 1; i < position - 1 && current !== null; i++) {
        current = current.next;
    }

    // If the position is out of range
    if (current === null || current.next === null) {
        return head;
    }

    // Store the node to be deleted
    let temp = current.next;

    // Update the links to bypass the node to be deleted
    current.next = current.next.next;

    // Delete the node
    temp = null;
    return head;
}
```
````

---
**Related Links**:-
- **Concept:-**
	- [LinkedList](../LinkedList.md)
	- [Doubly Linked List](../Doubly%20Linked%20List/Doubly%20Linked%20List.md) 
- Problems:-
	- [Find Middle of the Singly Linked List](../Problems/Find%20Middle%20of%20the%20Singly%20Linked%20List.md)
	- [Reverse a Linked Singly List](../Problems/Reverse%20a%20Singly%20Linked%20List.md)