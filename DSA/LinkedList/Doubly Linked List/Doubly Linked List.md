---
tags:
  - "#DSA"
  - "#LinkedList"
---
# Doubly Linked List
A **doubly linked list** is a more complex data structure than a [Singly Linked List](../Singly%20Linked%20List/Singly%20Linked%20List.md), but it offers several advantages. The main advantage of a doubly linked list is that it allows for efficient traversal of the list in both directions. This is because each node in the list contains a pointer to the previous node and a pointer to the next node. This allows for quick and easy [Insertion](#Insertion%20At%20the%20Beginning) and [Deletion](#Deletion%20at%20the%20Beginning) of nodes form the list, as well as efficient traversal of the list in both directions.
## What is a Doubly Linked List?
A **doubly linked list** is a data structure that consists of a set of nodes, each of which contains a **value** and two pointers, on pointing to the **previous node** in the list and one pointing to the **next node** in the list. This allows for efficient traversal of the list in **both directions,** making it suitable for applications where frequent **insertions** and **deletions** are required.
![[images/Insertion-at-the-End-in-Doubly-Linked-List-copy.webp|center]]
## Representing of Doubly Linked List in Data Structure
In a data structure, a doubly linked list is represented using nodes that have three fields:
1. Data
2. A pointer to the next node (**next**)
3. A pointer to the previous node (**prev**)

![[images/Node-Structure-of-Doubly-Linked-List.webp|center]]
## Node Definition
Here is how a node in a Doubly Linked List is typically represented:
````tabs

tab: C++
```cpp
struct Node {

    // To store the Value or data.
    int data;

    // Pointer to point the Previous Element
    Node* prev;

    // Pointer to point the Next Element
    Node* next;
  
    // Constructor
    Node(int d) {
       data = d;
       prev = next = nullptr;      
    }
};
```
tab: C
```c
struct Node {

    // To store the Value or data.
    int data;

    // Pointer to point the Previous Element
    Node* prev;

    // Pointer to point the Next Element
    Node* next;
};

// Function to create a new node
struct Node *createNode(int new_data) {
    struct Node *new_node = (struct Node *)
    malloc(sizeof(struct Node));
    new_node->data = new_data;
    new_node->next = NULL;
    new_node->prev = NULL;
    return new_node;
}
```
tab: Java
```java
class Node {

    // To store the Value or data.
    int data;

    // Reference to the Previous Node
    Node prev;
  
    // Reference to the next Node
    Node next;
  
    // Constructor
    Node(int d) {
       data = d;
       prev = next = null;      
    }
};
```
tab: Python
```python
class Node:
  
    def __init__(self, data):
        # To store the value or data.
        self.data = data

        # Reference to the previous node
        self.prev = None

        # Reference to the next node
        self.next = None
```
tab: Javascript
```javascript
class Node {
    constructor(data)
    {
        // To store the value or data.
        this.data = data;

        // Reference to the previous node
        this.prev = null;

        // Reference to the next node
        this.next = null;
    }
}
```
tab: C#
```csharp
class Node
{
  	// To store the value or data
    public int Data; 
  
  	// Pointer to the next node
    public Node Next; 
  
  	// Pointer to the previous node
    public Node Prev; 

    // Constructor
    public Node(int d)
    {
        Data = d;
        Prev = Next = null;      
    }
}
```
````
Each node in a **Doubly Linked List** contains the **data** it holds, a pointer to the **next** node in the list, and a pointer to the **previous** node in the list. By linking these nodes together through the **next** and **prev** pointers, we can traverse the list in both directions (forward and backward), which is a key feature of a Doubly Linked List.
## Operations
- [**Traversal**](#Traversal)
- **Searching**
- [**Finding Length**](#Finding%20Length)
- **Insertion**
	- [Insertion At the Beginning](#Insertion%20At%20the%20Beginning)
	- [Insertion at the End](#Insertion%20at%20the%20End)
	- [Insertion at the Specific Position](#Insertion%20at%20the%20Specific%20Position)
- **Deletion**
	- [Deletion at the Beginning](#Deletion%20at%20the%20Beginning)
	- [Deletion at the End](#Deletion%20at%20the%20End)
	- [Deletion at a Specific Position](#Deletion%20at%20a%20Specific%20Position)

Let's go through each of the operations mentioned above, one by one. 
### Traversal
To Traverse the doubly list, we can use the following steps:
1. **Forward Traversal:**
	- Initialize a pointer to the head of the linked list.
	- While the pointer is not null:
		- Visit the data at the current node.
		- Move the pointer to the next node.
2. **Backward Traversal:**
	- Initialize a pointer to the tail of the linked list.
	- While the pointer is not null:
		- Visit the data at the current node.
		- Move the pointer to the previous node.

Below are the implementation of the above approach:
````tabs

tab: C++
```cpp
#include <iostream>
using namespace std;

// Define the Node structure
struct Node {
    int data; 
    Node* next; 
    Node* prev; 
  
    // Constructor to initialize Node with data
    Node(int data) : data(data), next(nullptr),
  	prev(nullptr) {}
};

// Function to traverse the doubly linked list 
// in forward direction
void forwardTraversal(Node* head) {
  
    // Start traversal from the head of the list
    Node* curr = head;

    // Continue until current node is not null
    // (end of list)
    while (curr != nullptr) {
      
        // Output data of the current node
        cout << curr->data << " ";

        // Move to the next node
        curr = curr->next;
    }

    // Print newline after traversal
    cout << endl;
}

// Function to traverse the doubly linked list 
// in backward direction
void backwardTraversal(Node* tail) {
  
    // Start traversal from the tail of the list
    Node* curr = tail;

    // Continue until current node is not null 
    // (end of list)
    while (curr != nullptr) {
      
        // Output data of the current node
        cout << curr->data << " ";

        // Move to the previous node
        curr = curr->prev;
    }

    // Print newline after traversal
    cout << endl;
}

int main() {
  
    // Sample usage of the doubly linked list and 
    // traversal functions
    Node* head = new Node(1);
    Node* second = new Node(2);
    Node* third = new Node(3);

    head->next = second;
    second->prev = head;
    second->next = third;
    third->prev = second;

    cout << "Forward Traversal:" << endl;
    forwardTraversal(head);

    cout << "Backward Traversal:" << endl;
    backwardTraversal(third);

    return 0;
}
```
tab: C
```c
#include <stdio.h>
#include <stdlib.h>

// Define the Node structure
struct Node {
    int data; // Data stored in the node
    struct Node* next; // Pointer to the next node
    struct Node* prev; // Pointer to the previous node
};

// Function to create a new node
struct Node* createNode(int data) {
    struct Node* newNode = 
      (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    newNode->prev = NULL;
    return newNode;
}

// Function to traverse the doubly linked list 
// in forward direction
void forwardTraversal(struct Node* head) {
  
    // Start traversal from the head of the list
    struct Node* curr = head;

    // Continue until the current node is not
    // null (end of list)
    while (curr != NULL) {
      
        // Output data of the current node
        printf("%d ", curr->data);
      
        // Move to the next node
        curr = curr->next;
    }

    // Print newline after traversal
    printf("\n");
}

// Function to traverse the doubly linked list 
// in backward direction
void backwardTraversal(struct Node* tail) {
  
    // Start traversal from the tail of the list
    struct Node* curr = tail;

    // Continue until the current node is not 
    // null (end of list)
    while (curr != NULL) {
      
        // Output data of the current node
        printf("%d ", curr->data);
      
        // Move to the previous node
        curr = curr->prev;
    }

    // Print newline after traversal
    printf("\n");
}

int main() {
  
    // Sample usage of the doubly linked list and 
    // traversal functions
    struct Node* head = createNode(1);
    struct Node* second = createNode(2);
    struct Node* third = createNode(3);

    head->next = second;
    second->prev = head;
    second->next = third;
    third->prev = second;

    printf("Forward Traversal:\n");
    forwardTraversal(head);

    printf("Backward Traversal:\n");
    backwardTraversal(third);

    // Free memory allocated for nodes
    free(head);
    free(second);
    free(third);

    return 0;
}
```
tab: Java
```java
// Define the Node class
class Node {
    int data; // Data stored in the node
    Node next; // Pointer to the next node
    Node prev; // Pointer to the previous node

    // Constructor to initialize the node with data
    public Node(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

// Class to manage the doubly linked list
class GfG {

    // Function to traverse the doubly linked list 
    // in forward direction
    static void forwardTraversal(Node head) {
      
        // Start traversal from the head of the list
        Node curr = head;

        // Continue until the current node is 
        // null (end of the list)
        while (curr != null) {
          
            // Output data of the current node
            System.out.print(curr.data + " ");
          
            // Move to the next node
            curr = curr.next;
        }

        // Print newline after traversal
        System.out.println();
    }

    // Function to traverse the doubly linked list 
  	//in backward direction
    static void backwardTraversal(Node tail) {
      
        // Start traversal from the tail of the list
        Node curr = tail;

        // Continue until the current node is 
        // null (end of the list)
        while (curr != null) {
          
            // Output data of the current node
            System.out.print(curr.data + " ");
          
            // Move to the previous node
            curr = curr.prev;
        }

        // Print newline after traversal
        System.out.println();
    }

    public static void main(String[] args) {
      
        // Sample usage of the doubly linked
        // list and traversal functions
        Node head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);

        head.next = second;
        second.prev = head;
        second.next = third;
        third.prev = second;

        System.out.println("Forward Traversal:");
        forwardTraversal(head);

        System.out.println("Backward Traversal:");
        backwardTraversal(third);
    }
}
```
tab: Python
```python
# Define the Node class
class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

# Function to traverse the doubly linked list 
# in forward direction
def forward_traversal(head):
  
    # Start traversal from the head of the list
    curr = head
    
    # Continue until the current node is 
    # null (end of the list)
    while curr is not None:
      
        # Output data of the current node
        print(curr.data, end=" ")
        
        # Move to the next node
        curr = curr.next
        
    # Print newline after traversal
    print()

# Function to traverse the doubly linked 
# list in backward direction
def backward_traversal(tail):
  
    # Start traversal from the tail of the list
    curr = tail
    
    # Continue until the current node 
    # is null (end of the list)
    while curr is not None:
      
        # Output data of the current node
        print(curr.data, end=" ")
        
        # Move to the previous node
        curr = curr.prev
        
    # Print newline after traversal
    print()

# Sample usage of the doubly linked list 
# and traversal functions
if __name__ == "__main__":
  
    # Create a doubly linked list with 3 nodes
    head = Node(1)
    second = Node(2)
    third = Node(3)

    head.next = second
    second.prev = head
    second.next = third
    third.prev = second

    print("Forward Traversal:")
    forward_traversal(head)

    print("Backward Traversal:")
    backward_traversal(third)
```
tab: Javascript
```javascript
// Define the Node class
class Node {
    constructor(data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

// Function to traverse the doubly linked list 
// in forward direction
function forwardTraversal(head) {

    // Start traversal from the head of the list
    let curr = head;
    
    // Continue until the current node is null 
    // (end of the list)
    while (curr !== null) {
    
        // Output data of the current node
        console.log(curr.data + " ");
        
        // Move to the next node
        curr = curr.next;
    }
    
    // Print newline after traversal
    console.log();
}

// Function to traverse the doubly linked list 
// in backward direction
function backwardTraversal(tail) {

    // Start traversal from the tail of the list
    let curr = tail;
    
    // Continue until the current node is null 
    // (end of the list)
    while (curr !== null) {
    
        // Output data of the current node
        console.log(curr.data + " ");
        
        // Move to the previous node
        curr = curr.prev;
    }
    
    // Print newline after traversal
    console.log();
}

// Sample usage of the doubly linked list
//and traversal functions
// Create a doubly linked list with 3 nodes
const head = new Node(1);
const second = new Node(2);
const third = new Node(3);

head.next = second;
second.prev = head;
second.next = third;
third.prev = second;

console.log("Forward Traversal:");
forwardTraversal(head);

console.log("Backward Traversal:");
backwardTraversal(third);
```
tab: C#
```csharp
using System;

// Define the Node class
class Node
{
    public int Data; // Data stored in the node
    public Node Next; // Pointer to the next node
    public Node Prev; // Pointer to the previous node

    // Constructor to initialize the node with data
    public Node(int data)
    {
        Data = data;
        Next = null;
        Prev = null;
    }
}

// Class to manage the doubly linked list
class GfG
{
    // Function to traverse the doubly linked list 
  	//in forward direction
    static void ForwardTraversal(Node head)
    {
        // Start traversal from the head of the list
        Node curr = head;

        // Continue until the current node is null 
      	//(end of the list)
        while (curr != null)
        {
            // Output data of the current node
            Console.Write(curr.Data + " ");

            // Move to the next node
            curr = curr.Next;
        }

        // Print newline after traversal
        Console.WriteLine();
    }

    // Function to traverse the doubly linked list 
  	//in backward direction
    static void BackwardTraversal(Node tail)
    {
        // Start traversal from the tail of the list
        Node curr = tail;

        // Continue until the current node is null 
      	//(end of the list)
        while (curr != null)
        {
            // Output data of the current node
            Console.Write(curr.Data + " ");

            // Move to the previous node
            curr = curr.Prev;
        }

        // Print newline after traversal
        Console.WriteLine();
    }

    public static void Main()
    {
        // Sample usage of the doubly linked list
      	//and traversal functions
        Node head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);

        head.Next = second;
        second.Prev = head;
        second.Next = third;
        third.Prev = second;

        Console.WriteLine("Forward Traversal:");
        ForwardTraversal(head);

        Console.WriteLine("Backward Traversal:");
        BackwardTraversal(third);
    }
}
```
````
**Output**
> Forward Traversal
> 1 2 3
> Backward Traversal
> 3 2 1
### Finding Length
To find the length of doubly list, we can use the following steps:

- Start at the head of the list.
- Traverse through the list, counting each node visited.
- Return the total count of nodes as the length of the list.

Below are the implementation of the above approach:
````tabs

tab: C++
```cpp
#include <iostream>

using namespace std;

// Node structure for doubly linked list
struct Node {
    int data;
    Node * prev;
    Node * next;

    Node(int val) {
        data = val;
        prev = next = nullptr;
    }
};

// Function to find the length of a doubly 
//linked list
int findLength(Node * head) {
    int count = 0;
    for (Node * cur = head; cur != nullptr; cur = cur -> next)
        count++;
    return count;
}

int main() {

    // Create a DLL with 3 nodes
    Node * head = new Node(1);
    Node * second = new Node(2);
    Node * third = new Node(3);
    head -> next = second;
    second -> prev = head;
    second -> next = third;
    third -> prev = second;

    cout << "Length of the doubly linked list: " <<
        findLength(head) << endl;

    return 0;
}
```
tab: C
```c
#include <stdio.h>
#include <stdlib.h>

// Node structure for doubly linked list
struct Node {
    int data; // Data stored in the node
    struct Node* prev; // Pointer to the previous node
    struct Node* next; // Pointer to the next node
};

// Constructor function to create a new node
struct Node* createNode(int val) {
    struct Node* newNode = 
         (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

// Function to find the length of a doubly linked list
int findLength(struct Node* head) {
    int count = 0;
    for (struct Node* cur = head; cur != NULL; cur = cur->next)
        count++;
    return count;
}

int main() {
    // Create a DLL with 3 nodes
    struct Node* head = createNode(1);
    struct Node* second = createNode(2);
    struct Node* third = createNode(3);

    head->next = second; 
    second->prev = head;
    second->next = third; 
    third->prev = second;

    printf("Length of the doubly linked list: %d\n", 
           findLength(head));

    return 0;
}
```
tab: Java
```java
class Node {
    int data; 
    Node prev; 
    Node next;

    // Constructor
    public Node(int val) { 
        data = val; 
        prev = null; 
        next = null; 
    }
}

class GfG {

    // Function to find the length of 
    // a doubly linked list
    static int FindLength(Node head) {
        int count = 0;
        for (Node cur = head; cur != null; cur = cur.next)
            count++;
        return count;
    }

    // Driver code
    public static void main(String[] args) {
      
        // Create a doubly linked list 
        // with 3 nodes
        Node head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);
        
        head.next = second; 
        second.prev = head;
        second.next = third; 
        third.prev = second;

        System.out.println("Length of doubly linked list: " 
                           + FindLength(head));
    }
}
```
tab: Python
```python
class Node:
    def __init__(self, val):
        self.data = val
        self.prev = None
        self.next = None

# Function to find the length of 
# a doubly linked list
def find_length(head):
    count = 0
    cur = head
    while cur is not None:
        count += 1
        cur = cur.next
    return count

# Driver code
if __name__ == "__main__":
  
    # Create a doubly linked list 
    # with 3 nodes
    head = Node(1)
    second = Node(2)
    third = Node(3)

    head.next = second
    second.prev = head
    second.next = third
    third.prev = second

    print("Length of the doubly linked list: " +
          str(find_length(head)))
```
tab: Javascript
```javascript
class Node {
    constructor(val) {
        this.data = val;
        this.prev = null;
        this.next = null;
    }
}

// Function to find the length of
// a doubly linked list
function findLength(head) {
    let count = 0;
    let cur = head;
    while (cur !== null) {
        count++;
        cur = cur.next;
    }
    return count;
}

// Create a doubly linked list with 3 nodes
const head = new Node(1);
const second = new Node(2);
const third = new Node(3);

head.next = second;
second.prev = head;
second.next = third;
third.prev = second;

console.log("Length of the doubly linked list: " +
            findLength(head));
```
tab: C#
```csharp
using System;

class Node {
    public int data; 
    public Node prev; 
    public Node next;

    // Constructor
    public Node(int val) { 
        data = val; 
        prev = null; 
        next = null; 
    }
}

public class GfG {

    // Function to find the length of 
    // a doubly linked list
    static int FindLength(Node head) {
        int count = 0;
        for (Node cur = head; cur != null; cur = cur.next)
            count++;
        return count;
    }

    // Driver code
    public static void Main(string[] args) {
      
        // Create a doubly linked list 
        // with 3 nodes
        Node head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);
        
        head.next = second; 
        second.prev = head;
        second.next = third; 
        third.prev = second;

        Console.WriteLine("Length of doubly linked list: " 
                                 + FindLength(head));
    }
}
```
````
**Output**
> Length of the doubly linked list: 3
### Insertion At the Beginning
![Insertion-at-the-Beginning-in-Doubly-Linked-List|center](images/Insertion-at-the-Beginning-in-Doubly-Linked-List.webp)

To insert a new node at the beginning of the doubly list, we can use the following steps:

- Create a new node, say **new_node** with the given data and set its previous pointer to null, **new_node->prev =** **NULL**.
- Set the next pointer of **new_node** to current head, **new_node->next = head.**
- If the linked list is not empty, update the previous pointer of the current head to new_node, **head->prev = new_node**.
- Return new_node as the head of the updated linked list.

Below are the implementation of the above approach:
````tabs

tab: C++
```cpp
// C++ Program to insert a new node at the
// beginning of doubly linked list 

#include <iostream>
using namespace std;

// Node structure for the doubly linked list
struct Node {
    int data;
    Node* prev;
    Node* next;

    Node(int d) { 
      data = d; 
      prev = next = NULL;
    }
};

// Insert a node at the beginning
Node* insertBegin(Node* head, int data) {
    
    // Create a new node
    Node* new_node = new Node(data);
    
    // Make next of it as head
    new_node->next = head;
    
    // Set previous of head as new node
    if (head != NULL) {
        head->prev = new_node;
    }
    
    // Return new node as new head
    return new_node;
}

void printList(Node* head) {
    Node* curr = head;
    while (curr != NULL) {
        cout << curr->data << " ";
        curr = curr->next;
    }
  	cout << "\n";
}

int main() {
  
    // Create a hardcoded linked list:
  	// 2 <-> 3 <-> 4
    Node* head = new Node(2);
    Node* temp1 = new Node(3);
    Node* temp2 = new Node(4);
    head->next = temp1;
    temp1->prev = head;
    temp1->next = temp2;
    temp2->prev = temp1;

  	// Print the original list
    cout << "Original Linked List: ";
    printList(head);

    // Insert a new node at the front of the list
    head = insertBegin(head, 1);

    // Print the updated list
  	cout << "After inserting Node 1 at the front: ";
    printList(head);
  	
    return 0;
}
```
tab: C
```c
// C Program to insert a node at the beginning
//of doubly linked list


#include <stdio.h>

// Node structure for the doubly linked list
struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

// Create a new node
struct Node* createNode(int data) {
    struct Node* new_node = 
      (struct Node*)malloc(sizeof(struct Node));
    new_node->data = data;
    new_node->prev = NULL;
    new_node->next = NULL;
    return new_node;
}

// Insert a node at the beginning
struct Node* insertBegin(struct Node* head, int data) {
    
    // Create a new node
    struct Node* new_node = createNode(data);
    
    // Make next of it as head
    new_node->next = head;
    
    // Set previous of head as new node
    if (head != NULL) {
        head->prev = new_node;
    }
    
    // Return new node as new head
    return new_node;
}

// Print the doubly linked list
void printList(struct Node* head) {
    struct Node* curr = head;
    while (curr != NULL) {
        printf("%d ", curr->data);
        curr = curr->next;
    }
  	printf("\n");
}

int main() {
  
    // Create a hardcoded doubly linked list:
    // 2 <-> 3 <-> 4 
    struct Node *head = createNode(2);
    head->next = createNode(3);
    head->next->prev = head;
    head->next->next = createNode(4);
    head->next->next->prev = head->next;

    // Print the original list
    printf("Original Linked List: ");
    printList(head);

    // Insert a new node at the front of the list
    head = insertBegin(head, 1);

    // Print the updated list
  	printf("After inserting Node 1 at the front: ");
    printList(head);

    return 0;
}
```
tab: Java
```java
// Java Program to insert a node at the beginning of a
// doubly linked list

class Node {
    int data;
    Node prev, next;

    // Node structure for the doubly linked list
    Node(int d) {
        data = d;
        prev = null;
        next = null;
    }
}

class GfG {
    
    // Insert a node at the beginning
    static Node insertBegin(Node head, int data) {
        
        // Create a new node
        Node new_node = new Node(data);
        
        // Make next of it as head
        new_node.next = head;
        
        // Set previous of head as new node
        if (head != null) {
            head.prev = new_node;
        }
        
        // Return new node as new head
        return new_node;
    }

    // Print the doubly linked list
    static void printList(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
      	System.out.println();
    }

    public static void main(String[] args) {
        
        // Create a hardcoded doubly linked list:
        // 2 <-> 3 <-> 4
        Node head = new Node(2);
        head.next = new Node(3);
        head.next.prev = head;
        head.next.next = new Node(4);
        head.next.next.prev = head.next;

        // Print the original list
        System.out.print("Original Linked List: ");
        printList(head);

        // Insert a new node at the front of the list
        head = insertBegin(head, 1);

        // Print the updated list
      	System.out.print(
            "After inserting Node 1 at the front: ");
        printList(head);
    }
}
```
tab: Python
```python
# Python Program to insert a node at the beginning 
#of doubly linked list

# Node structure for the doubly linked list
class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

# Insert a node at the beginning
def insertBegin(head, data):
    
    # Create a new node
    new_node = Node(data)
    
    # Make next of it as head
    new_node.next = head
    
    # Set previous of head as new node
    if head is not None:
        head.prev = new_node
    
    # Return new node as new head
    return new_node

# Print the doubly linked list
def printList(head):
    curr = head
    while curr is not None:
        print(curr.data, end=" ")
        curr = curr.next
    print()

if __name__ == "__main__":
  
    # Create a hardcoded doubly linked list:
    # 2 <-> 3 <-> 4
    head = Node(2)
    head.next = Node(3)
    head.next.prev = head
    head.next.next = Node(4)
    head.next.next.prev = head.next

    # Print the original list
    print("Original Linked List:", end=' ')
    printList(head)

    # Insert a new node at the front of the list
    head = insertBegin(head, 1)

    # Print the updated list
    print("After inserting Node 1 at the front:", end=' ')
    printList(head)
```
tab: Javascript
```javascript
// JavaScript Program to insert a node at the 
//beginning of doubly linked list

// Node structure for the doubly linked list
function Node(data) {
    this.data = data;
    this.prev = null;
    this.next = null;
}

// Insert a node at the beginning
function insertBegin(head, data) {
    
    // Create a new node
    const new_node = new Node(data);
    
    // Make next of it as head
    new_node.next = head;
    
    // Set previous of head as new node
    if (head !== null) {
        head.prev = new_node;
    }
    
    // Return new node as new head
    return new_node;
}

// Print the doubly linked list
function printList(head) {
    let curr = head;
    while (curr !== null) {
        console.log(curr.data);
        curr = curr.next;
    }
}

// Create a hardcoded doubly linked list:
// 2 <-> 3 <-> 4
let head = new Node(2);
head.next = new Node(3);
head.next.prev = head;
head.next.next = new Node(4);
head.next.next.prev = head.next;

// Print the original list
console.log("Original Linked List:");
printList(head);

// Insert a new node at the front of the list
console.log
("After inserting Node 1 at the front:");
let data = 1;
head = insertBegin(head, data);

// Print the updated list
printList(head);
```
tab: C#
```csharp
// C# Program to insert a node at the beginning of a
// doubly linked list

using System;

// Node structure for the doubly linked list
class Node {
    public int data;
    public Node prev, next;

    // Constructor for creating a new node
    public Node(int d) {
        data = d;
        prev = null;
        next = null;
    }
}

class GfG {
    
    // Insert a node at the beginning
    public static
    Node insertBegin(Node head, int data) {
        
        // Create a new node
        Node new_node = new Node(data);
        
        // Make next of it as head
        new_node.next = head;
        
        // Set previous of head as new node
        if (head != null) {
            head.prev = new_node;
        }
        
        // Return new node as new head
        return new_node;
    }

    // Print the doubly linked list
    public static void printList(Node head) {
        Node curr = head;
        while (curr != null) {
            Console.Write(curr.data + " ");
            curr = curr.next;
        }
      	Console.WriteLine();
    }

    public static void Main(string[] args) {
        
        // Create a hardcoded doubly linked list:
        // 2 <-> 3 <-> 4
        Node head = new Node(2);
        head.next = new Node(3);
        head.next.prev = head;
        head.next.next = new Node(4);
        head.next.next.prev = head.next;

        // Print the original list
        Console.Write("Original Linked List: ");
        printList(head);

        // Insert a new node at the front of the list
        head = insertBegin(head, 1);

        // Print the updated list
      	Console.Write
        ("After inserting Node 1 at the front: ");
        printList(head);
    }
}
```
````
**Output:**
> Original Linked List: 2 3 4
> After inserting Node 1 at the front: 1 2 3 4
### Insertion at the End
![Insertion-at-the-End-in-Doubly-Linked-List|center](images/Insertion-at-the-End-in-Doubly-Linked-List.webp)
To insert a new node at the end of the doubly linked list, we can use the following steps:
- Allocate memory for a new node and assign the provided value to its data field.
- Initialize the next pointer of the new node to nullptr.
- If the list is empty:
    - Set the previous pointer of the new node to nullptr.
    - Update the head pointer to point to the new node.
- If the list is not empty:
    - Traverse the list starting from the head to reach the last node.
    - Set the next pointer of the last node to point to the new node.
    - Set the previous pointer of the new node to point to the last node.

Below are the implementation of the above approach:
````tabs

tab: C++
```cpp
// C++ Program to insert a node at the end of
//doubly linked list

#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    Node *next, *prev;

    Node(int new_data) {
        data = new_data;
        next = prev = nullptr;
    }
};

// Function to insert a new node at the end of 
//doubly linked list
Node *insertEnd(Node *head, int new_data) {

    // Create a new node
    Node *new_node = new Node(new_data);

    // If the linked list is empty, set the new 
  	//node as the head of linked list
    if (head == NULL) {
        head = new_node;
    }
    else {
          Node *curr = head;
        while (curr->next != NULL) {
            curr = curr->next;
        }

        // Set the next of last node to new node
        curr->next = new_node;

        // Set prev of new node to last node
        new_node->prev = curr;
    }

    // Return the head of the doubly linked list
    return head;
}

void printList(Node *head) {
    Node *curr = head;
    while (curr != NULL) {
        cout << curr->data << " ";
        curr = curr->next;
    }
    cout << endl;
}

int main() {

    // Create a harcoded doubly linked list:
    // 1 <-> 2 <-> 3
    Node *head = new Node(1);
    head->next = new Node(2);
    head->next->prev = head;
    head->next->next = new Node(3);
    head->next->next->prev = head->next;

    // Print the original list
    cout << "Original Linked List: ";
    printList(head);

    // Insert a new node with data 4 at the end
    cout << "Inserting Node with data 4 at the end: ";
    int data = 4;
    head = insertEnd(head, data);

    // Print the updated list
    printList(head);

    return 0;
}
```
tab: C
```c
// C Program to insert a node at the end of 
//doubly linked list

#include <stdio.h>

struct Node {
    int data;
    struct Node *next;
    struct Node *prev;
};

// Function to create a new node with the given data
struct Node *createNode(int new_data) {
    struct Node *new_node =
    (struct Node *)malloc(sizeof(struct Node));
    new_node->data = new_data;
    new_node->next = NULL;
    return new_node;
}

// Function to insert a new node at the end of the 
//doubly linked list
struct Node* insertEnd(struct Node *head, int new_data) {
    struct Node *new_node = createNode(new_data);

    // If the linked list is empty, set the
 	//new node as the head
    if (head == NULL) {
        head = new_node;
    } else {
        struct Node *curr = head;
        while (curr->next != NULL) {
            curr = curr->next;
        }

        // Set the next of last node to new node
        curr->next = new_node;
        // Set prev of new node to last node
        new_node->prev = curr;
    }

    return head;
}

void printList(struct Node *head) {
    struct Node *curr = head;
    while (curr != NULL) {
        printf("%d ", curr->data);
        curr = curr->next;
    }
    printf("\n");
}

int main() {
  
    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node *head = createNode(1);
    head->next = createNode(2);
    head->next->prev = head;
    head->next->next = createNode(3);
    head->next->next->prev = head->next;

    // Print the original list
    printf("Original Linked List: ");
    printList(head);

    // Insert a new node with data 4 at the end
    printf("Inserting Node with data 4 at the end: ");
    head = insertEnd(head, 4);

    // Print the updated list
    printList(head);

    return 0;
}
```
tab: Java
```java
// Java Program to insert a node at the end of 
// doubly linked list

class Node {
    int data;
    Node next, prev;

    Node(int newData) {
        data = newData;
        next = prev = null;
    }
}

class GFG {

    // Function to insert a new node at the end of the
    // doubly linked list
    public static Node insertEnd(Node head, int newData) {
      
        // Create a new node
        Node newNode = new Node(newData);

        // If the linked list is empty, set the new node as
        // the head
        if (head == null) {
            head = newNode;
        }
        else {
            Node curr = head;
            while (curr.next != null) {
                curr = curr.next;
            }

            // Set the next of last node to the new node
            curr.next = newNode;

            // Set the prev of new node to the last node
            newNode.prev = curr;
        }

        return head;
    }

    // Function to print the doubly linked list
    public static void printList(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
      
        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 3
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.prev = head;
        head.next.next = new Node(3);
        head.next.next.prev = head.next;

        // Print the original list
        System.out.println("Original Linked List: ");
        printList(head);

        // Insert a new node with data 4 at the end
        System.out.println(
            "Inserting Node with data 4 at the end: ");
        int data = 4;
        head = insertEnd(head, data);

        // Print the updated list
        printList(head);
    }
}
```
tab: Python
```python
# Python Program to insert a node at the end of 
#doubly linked list

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None

# Function to insert a new node at the end of the 
#doubly linked list
def insert_end(head, new_data):
      
    # Create a new node
    new_node = Node(new_data)
    
    # If the linked list is empty, set the new node
    #as the head
    if head is None:
        head = new_node
    else:
        curr = head
        while curr.next is not None:
            curr = curr.next
        
        # Set the next of the last node to the new node
        curr.next = new_node
        
        # Set the prev of the new node to the last node
        new_node.prev = curr
    
    return head

def print_list(head):
    curr = head
    while curr is not None:
        print(curr.data, end=" ")
        curr = curr.next
    print()

if __name__ == "__main__":
  
    # Create a hardcoded doubly linked list:
    # 1 <-> 2 <-> 3
    head = Node(1)
    head.next = Node(2)
    head.next.prev = head
    head.next.next = Node(3)
    head.next.next.prev = head.next

    # Print the original list
    print("Original Linked List: ", end="")
    print_list(head)

    # Insert a new node with data 4 at the end
    print("Inserting Node with data 4 at the end: ", end="")
    data = 4
    head = insert_end(head, data)

    # Print the updated list
    print_list(head)
```
tab: Javascript
```javascript
// Javascript Program to insert a node at the end of 
//doublylinked list

class Node {
    constructor(data)
    {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

function insertEnd(head, newData) {

    // Create a new node
    const newNode = new Node(newData);

    // If the linked list is empty, set the 
    //new node as the head
    if (head === null) {
        head = newNode;
    }
    else {
        let curr = head;
        while (curr.next !== null) {
            curr = curr.next;
        }

        // Set the next of the last node to the 
        //new node
        curr.next = newNode;

        // Set the prev of the new node to the 
        //last node
        newNode.prev = curr;
    }

    return head;
}

function printList(head)
{
    let curr = head;
    let result = "";
    while (curr !== null) {
        result += curr.data + " ";
        curr = curr.next;
    }
    console.log(result.trim());
}

// Create a hardcoded doubly linked list:
// 1 <-> 2 <-> 3
let head = new Node(1);
head.next = new Node(2);
head.next.prev = head;
head.next.next = new Node(3);
head.next.next.prev = head.next;

// Print the original list
console.log("Original Linked List: ");
printList(head);

// Insert a new node with data 4 at the end
console.log("Inserting Node with data 4 at the end: ");
const data = 4;
head = insertEnd(head, data);

// Print the updated list
printList(head);
```
tab: C#
```csharp
// C# Program to insert a node at the end of 
//doubly linked list

using System;

class Node {
    public int Data;
    public Node Next;
    public Node Prev;

    public Node(int data) {
        Data = data;
        Next = null;
        Prev = null;
    }
}

class GFG {
  
    // Function to insert a new node at the end
  	//of the doubly linked list
    public static Node InsertEnd(Node head, int newData) {
        
          // Create a new node
        Node newNode = new Node(newData);

        // If the linked list is empty, set the 
      	//new node as the head
        if (head == null) {
            head = newNode;
        }
        else {
            Node curr = head;
            while (curr.Next != null) {
                curr = curr.Next;
            }

            // Set the next of the last node to 
          	//the new node
            curr.Next = newNode;

            // Set the prev of the new node to 
          	//the last node
            newNode.Prev = curr;
        }

        return head;
    }

    // Function to print the doubly linked list
    public static void PrintList(Node head) {
        Node curr = head;
        while (curr != null) {
            Console.Write(curr.Data + " ");
            curr = curr.Next;
        }
        Console.WriteLine();
    }

    static void Main() {
      
        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 3
        Node head = new Node(1);
        head.Next = new Node(2);
        head.Next.Prev = head;
        head.Next.Next = new Node(3);
        head.Next.Next.Prev = head.Next;

        // Print the original list
        Console.Write("Original Linked List: ");
        PrintList(head);

        // Insert a new node with data 4 at the end
        Console.Write("Inserting Node with data 4 at the end: ");
        int data = 4;
        head = InsertEnd(head, data);

        // Print the updated list
        PrintList(head);
    }
}
```
````
**Output**
>Original Linked List: 1 2 3
>Inserting Node with data 4 at the end: 1 2 3 4
### Insertion at the Specific Position
![Insertion-at-a-Specific-Position-in-Doubly-Linked-List|center](images/Insertion-at-a-Specific-Position-in-Doubly-Linked-List.webp)
To insert a new node at a specific position,

- If position = 1, create a new node and make it the head of the linked list and return it.
- Otherwise, traverse the list to reach the node at position – 1, say **curr**.
- If the position is valid, create a new node with given data, say **new_node**.
- Update the next pointer of new node to the next of current node and prev pointer of new node to current node, **new_node->next = curr->next** and **new_node->prev = curr.**
- Similarly, update next pointer of current node to the new node, **curr->next = new_node**.
- If the new node is not the last node, update prev pointer of new node’s next to the new node, **new_node->next->prev = new_node.**

Below is the implementation of the above approach:
````tabs

tab: C++
```cpp
// C++ Program to insert a node at a given position

#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    Node *next, *prev;

    Node(int new_data) {
        data = new_data;
        next = prev = nullptr;
    }
};

// Function to insert a new node at a given position
Node *insertAtPosition(Node *head, int pos, int new_data) {

    // Create a new node
    Node *new_node = new Node(new_data);

    // Insertion at the beginning
    if (pos == 1) {
        new_node->next = head;

        // If the linked list is not empty, set the prev
      	//of head to new node
        if (head != NULL)
            head->prev = new_node;

        // Set the new node as the head of linked list
        head = new_node;
        return head;
    }

    Node *curr = head;
    // Traverse the list to find the node before the
    // insertion point
    for (int i = 1; i < pos - 1 && curr != NULL; ++i) {
        curr = curr->next;
    }

    // If the position is out of bounds
    if (curr == NULL) {
        cout << "Position is out of bounds." << endl;
        delete new_node;
        return head;
    }

    // Set the prev of new node to curr
    new_node->prev = curr;

    // Set the new of new node to next of curr
    new_node->next = curr->next;

    // Update the next of current node to new node
    curr->next = new_node;

    // If the new node is not the last node, update prev
 	 //of next node to new node
    if (new_node->next != NULL)
        new_node->next->prev = new_node;

    // Return the head of the doubly linked list
    return head;
}

void printList(Node *head) {
    Node *curr = head;
    while (curr != NULL) {
        cout << curr->data << " ";
        curr = curr->next;
    }
    cout << endl;
}

int main() {

    // Create a harcoded doubly linked list:
    // 1 <-> 2 <-> 4
    Node *head = new Node(1);
    head->next = new Node(2);
    head->next->prev = head;
    head->next->next = new Node(4);
    head->next->next->prev = head->next;

    // Print the original list
    cout << "Original Linked List: ";
    printList(head);

    // Insert new node with data 3 at position 3
    cout << "Inserting Node with data 3 at position 3: ";
    int data = 3;
    int pos = 3;
    head = insertAtPosition(head, pos, data);

    // Print the updated list
    printList(head);

    return 0;
}
```
tab: C
```c
// C Program to insert a node at a given position

#include <stdio.h>

struct Node {
    int data;
    struct Node * next;
    struct Node * prev;
};

// Function to create a new node with the given data
struct Node * createNode(int new_data) {
    struct Node * new_node =
        (struct Node * ) malloc(sizeof(struct Node));
    new_node -> data = new_data;
    new_node -> next = NULL;
    return new_node;
}

// Function to insert a new node at a given position
struct Node * insertAtPosition(struct Node * head, int pos, int new_data) {
    // Create a new node
    struct Node * new_node = createNode(new_data);

    // Insertion at the beginning
    if (pos == 1) {
        new_node -> next = head;

        // If the linked list is not empty, set the 
      //prev of head to new node
        if (head != NULL) {
            head -> prev = new_node;
        }

        // Set the new node as the head of linked list
        head = new_node;
        return head;
    }

    struct Node * curr = head;

    // Traverse the list to find the node before the insertion point
    for (int i = 1; i < pos - 1 && curr != NULL; ++i) {
        curr = curr -> next;
    }

    // If the position is out of bounds
    if (curr == NULL) {
        printf("Position is out of bounds.\n");
        free(new_node);
        return head;
    }

    // Set the prev of new node to curr
    new_node -> prev = curr;

    // Set the next of new node to next of curr
    new_node -> next = curr -> next;

    // Update the next of current node to new node
    curr -> next = new_node;

    // If the new node is not the last node, update
  	//the prev of next node to new node
    if (new_node -> next != NULL) {
        new_node -> next -> prev = new_node;
    }

    // Return the head of the doubly linked list
    return head;
}

// Function to print the linked list
void printList(struct Node * head) {
    struct Node * curr = head;
    while (curr != NULL) {
        printf("%d ", curr -> data);
        curr = curr -> next;
    }
    printf("\n");
}

int main() {

    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 4
    struct Node * head = createNode(1);
    head -> next = createNode(2);
    head -> next -> prev = head;
    head -> next -> next = createNode(4);
    head -> next -> next -> prev = head -> next;

    // Print the original list
    printf("Original Linked List: ");
    printList(head);

    // Insert new node with data 3 at position 3
    printf("Inserting Node with data 3 at position 3: ");
    int data = 3;
    int pos = 3;
    head = insertAtPosition(head, pos, data);

    // Print the updated list
    printList(head);

    return 0;
}
```
tab: Java
```java
// Java Program to insert a node at a given position

class Node {
    int data;
    Node next;
    Node prev;

    Node(int new_data) {
        data = new_data;
        next = prev = null;
    }
}

class GFG {

    // Function to insert a new node at a given position
    public static Node insertAtPosition(Node head, int pos, int new_data) {
        // Create a new node
        Node new_node = new Node(new_data);

        // Insertion at the beginning
        if (pos == 1) {
            new_node.next = head;

            // If the linked list is not empty, set 
          	//the prev of head to new node
            if (head != null) {
                head.prev = new_node;
            }

            // Set the new node as the head of linked list
            head = new_node;
            return head;
        }

        Node curr = head;
      
        // Traverse the list to find the node before 
      	//the insertion point
        for (int i = 1; i < pos - 1 && curr != null; ++i) {
            curr = curr.next;
        }

        // If the position is out of bounds
        if (curr == null) {
            System.out.println("Position is out of bounds.");
            return head;
        }

        // Set the prev of new node to curr
        new_node.prev = curr;

        // Set the next of new node to next of curr
        new_node.next = curr.next;

        // Update the next of current node to new node
        curr.next = new_node;

        // If the new node is not the last node, update 
      	//prev of next node to new node
        if (new_node.next != null) {
            new_node.next.prev = new_node;
        }

        // Return the head of the doubly linked list
        return head;
    }

    // Function to print the linked list
    public static void printList(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
      
        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 4
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.prev = head;
        head.next.next = new Node(4);
        head.next.next.prev = head.next;

        // Print the original list
        System.out.print("Original Linked List: ");
        printList(head);

        // Insert new node with data 3 at position 3
        System.out.print("Inserting Node with data 3 at position 3: ");
        int data = 3;
        int pos = 3;
        head = insertAtPosition(head, pos, data);

        // Print the updated list
        printList(head);
    }
}
```
tab: Python
```python
# Python Program to insert a node at a given position

class Node:
    def __init__(self, new_data):
        self.data = new_data
        self.next = None
        self.prev = None

def insert_at_position(head, pos, new_data):
  
    # Create a new node
    new_node = Node(new_data)

    # Insertion at the beginning
    if pos == 1:
        new_node.next = head

        # If the linked list is not empty, set the
        #prev of head to new node
        if head is not None:
            head.prev = new_node

        # Set the new node as the head of the linked list
        head = new_node
        return head

    curr = head
    
    # Traverse the list to find the node before the 
    #insertion point
    for _ in range(1, pos - 1):
        if curr is None:
            print("Position is out of bounds.")
            return head
        curr = curr.next

    # If the position is out of bounds
    if curr is None:
        print("Position is out of bounds.")
        return head

    # Set the prev of new node to curr
    new_node.prev = curr

    # Set the next of new node to next of curr
    new_node.next = curr.next

    # Update the next of current node to new node
    curr.next = new_node

    # If the new node is not the last node, update 
    #prev of next node to new node
    if new_node.next is not None:
        new_node.next.prev = new_node

    return head

def print_list(head):
    curr = head
    while curr is not None:
        print(curr.data, end=" ")
        curr = curr.next
    print()

if __name__ == "__main__":
  
    # Create a hardcoded doubly linked list:
    # 1 <-> 2 <-> 4
    head = Node(1)
    head.next = Node(2)
    head.next.prev = head
    head.next.next = Node(4)
    head.next.next.prev = head.next

    # Print the original list
    print("Original Linked List: ", end="")
    print_list(head)

    # Insert new node with data 3 at position 3
    print("Inserting Node with data 3 at position 3: ", end="")
    data = 3
    pos = 3
    head = insert_at_position(head, pos, data)

    # Print the updated list
    print_list(head)
```
tab: Javascript
```javascript
// Javascript Program to insert a node at a given position

class Node {
    constructor(data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

// Function to insert a new node at a given position
function insertAtPosition(head, pos, newData) {

    // Create a new node
    let newNode = new Node(newData);

    // Insertion at the beginning
    if (pos === 1) {
        newNode.next = head;
        if (head !== null) {
            head.prev = newNode;
        }
        head = newNode;
        return head;
    }

    let curr = head;
    
    // Traverse the list to find the node
    //before the insertion point
    for (let i = 1; i < pos - 1 && curr !== null; ++i) {
        curr = curr.next;
    }

    // If the position is out of bounds
    if (curr === null) {
        console.log("Position is out of bounds.");
        return head;
    }

    // Set the prev of new node to curr
    newNode.prev = curr;

    // Set the next of new node to the next of curr
    newNode.next = curr.next;

    // Update the next of current node to new node
    curr.next = newNode;

    // If the new node is not the last node, 
    // update prev of next node to new node
    if (newNode.next !== null) {
        newNode.next.prev = newNode;
    }

    return head;
}

// Function to print the list
function printList(head) {
    let curr = head;
    while (curr !== null) {
        console.log(curr.data + " ");
        curr = curr.next;
    }
    console.log();
}

// Create a hardcoded doubly linked list:
// 1 <-> 2 <-> 4
let head = new Node(1);
head.next = new Node(2);
head.next.prev = head;
head.next.next = new Node(4);
head.next.next.prev = head.next;

// Print the original list
console.log("Original Linked List:");
printList(head);

// Insert new node with data 3 at position 3
console.log("Inserting Node with data 3 at position 3:");
head = insertAtPosition(head, 3, 3);

// Print the updated list
printList(head);
```
tab: C#
```csharp
// C# Program to insert a node at a given position

using System;

class Node {
    public int Data;
    public Node Next;
    public Node Prev;

    public Node(int data) {
        Data = data;
        Next = null;
        Prev = null;
    }
}

class GFG {
  
    // Function to insert a new node at a given position
    static Node InsertAtPosition(Node head, int pos, int newData) {
      
        // Create a new node
        Node newNode = new Node(newData);

        // Insertion at the beginning
        if (pos == 1) {
            newNode.Next = head;
            if (head != null)
                head.Prev = newNode;
            head = newNode;
            return head;
        }

        Node curr = head;
        
          // Traverse the list to find the node
      	 //before the insertion point
        for (int i = 1; i < pos - 1 && curr != null; ++i) {
            curr = curr.Next;
        }

        // If the position is out of bounds
        if (curr == null) {
            Console.WriteLine("Position is out of bounds.");
            return head;
        }

        // Set the prev of new node to curr
        newNode.Prev = curr;

        // Set the next of new node to the next of curr
        newNode.Next = curr.Next;

        // Update the next of current node to new node
        curr.Next = newNode;

        // If the new node is not the last node, update 
      	//prev of next node to new node
        if (newNode.Next != null)
            newNode.Next.Prev = newNode;

        return head;
    }

    // Function to print the list
    static void PrintList(Node head) {
        Node curr = head;
        while (curr != null) {
            Console.Write(curr.Data + " ");
            curr = curr.Next;
        }
        Console.WriteLine();
    }

    static void Main() {
      
        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 4
        Node head = new Node(1);
        head.Next = new Node(2);
        head.Next.Prev = head;
        head.Next.Next = new Node(4);
        head.Next.Next.Prev = head.Next;

        // Print the original list
        Console.WriteLine("Original Linked List: ");
        PrintList(head);

        // Insert new node with data 3 at position 3
        Console.WriteLine("Inserting Node with data 3 at position 3: ");
        head = InsertAtPosition(head, 3, 3);

        // Print the updated list
        PrintList(head);
    }
}
```
````
**Output:**
> Original Linked List: 1 2 3 4
> Inserting Node with data 3 at position 3: 1 2 3 4
### Deletion at the Beginning
![Deletion-at-the-Beginning-of-Doubly-Linked-List](images/Deletion-at-the-Beginning-of-Doubly-Linked-List.webp)
To delete a node at the beginning in doubly linked list, we can use the following steps:
- Check if the list is empty, there is nothing to delete. Return.
- Store the head pointer in a variable, say **temp**.
- Update the head of linked list to the node next to the current head, **head = head->next**.
- If the new head is not NULL, update the previous pointer of new head to NULL, **head->prev = NULL**.

Below is the implementation of the above approach:
````tabs

tab: C++
```cpp
// C++ Program to delete a node from the 
// beginning of Doubly Linked List

#include <bits/stdc++.h>
using namespace std;

struct Node{
    int data;
    Node *prev;
    Node *next;
    Node(int d) {
      	data = d;
      	prev = next = nullptr;
    }
};

// Deletes the first node (head) of the list
// and returns the second node as new head
Node *delHead(Node *head) {

    // If empty, return
    if (head == nullptr)
        return nullptr;

    // Store in temp for deletion later
    Node *temp = head;

    // Move head to the next node
    head = head->next;

    // Set prev of the new head
    if (head != nullptr)
        head->prev = nullptr;

    // Free memory and return new head
    delete temp;
    return head;
}

void printList(Node *head) {
    for (Node *curr = head; curr != nullptr; curr = curr->next)
        cout << curr->data << " ";
    cout << endl;
}

int main() {

    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node *head = new Node(1);
    head->next = new Node(2);
    head->next->prev = head;
    head->next->next = new Node(3);
    head->next->next->prev = head->next;

    printf("Original Linked List: ");
    printList(head);

    printf("After Deletion at the beginning: ");
    head = delHead(head);

    printList(head);

    return 0;
}
```
tab: C
```c
// C Program to delete a node from the
// beginning of Doubly Linked List

#include <stdio.h>

struct Node {
    int data;
    struct Node *prev;
    struct Node *next;
};

// Function to create a new node
struct Node *createNode(int data) {
    struct Node *newNode = (struct Node *)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

// Function to delete the first node (head) of the list
// and return the second node as the new head
struct Node *delHead(struct Node *head) {
    // If empty, return NULL
    if (head == NULL)
        return NULL;

    // Store in temp for deletion later
    struct Node *temp = head;

    // Move head to the next node
    head = head->next;

    // Set prev of the new head
    if (head != NULL)
        head->prev = NULL;

    // Free memory and return new head
    free(temp);
    return head;
}

void printList(struct Node *head) {
    struct Node *curr = head;
    while (curr != NULL) {
        printf("%d ", curr->data);
        curr = curr->next;
    }
    printf("\n");
}

int main() {

    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node *head = createNode(1);
    head->next = createNode(2);
    head->next->prev = head;
    head->next->next = createNode(3);
    head->next->next->prev = head->next;

    printf("Original Linked List: ");
    printList(head);

    printf("After Deletion at the beginning: ");
    head = delHead(head);

    printList(head);

    return 0;
}
```
tab: Java
```java
// C Program to delete a node from the
// beginning of Doubly Linked List

#include <stdio.h>

struct Node {
    int data;
    struct Node *prev;
    struct Node *next;
};

// Function to create a new node
struct Node *createNode(int data) {
    struct Node *newNode = (struct Node *)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

// Function to delete the first node (head) of the list
// and return the second node as the new head
struct Node *delHead(struct Node *head) {
    // If empty, return NULL
    if (head == NULL)
        return NULL;

    // Store in temp for deletion later
    struct Node *temp = head;

    // Move head to the next node
    head = head->next;

    // Set prev of the new head
    if (head != NULL)
        head->prev = NULL;

    // Free memory and return new head
    free(temp);
    return head;
}

void printList(struct Node *head) {
    struct Node *curr = head;
    while (curr != NULL) {
        printf("%d ", curr->data);
        curr = curr->next;
    }
    printf("\n");
}

int main() {

    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node *head = createNode(1);
    head->next = createNode(2);
    head->next->prev = head;
    head->next->next = createNode(3);
    head->next->next->prev = head->next;

    printf("Original Linked List: ");
    printList(head);

    printf("After Deletion at the beginning: ");
    head = delHead(head);

    printList(head);

    return 0;
}
```
tab: Python
```python
# Python Program to delete a node from the 
# beginning of Doubly Linked List

class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

# Function to delete the first node (head) of the list
# and return the second node as the new head
def del_head(head):
  
    # If empty, return None
    if head is None:
        return None

    # Store in temp for deletion later
    temp = head

    # Move head to the next node
    head = head.next

    # Set prev of the new head
    if head is not None:
        head.prev = None

    # Return new head
    return head

def print_list(head):
    curr = head
    while curr is not None:
        print(curr.data, end=" ")
        curr = curr.next
    print()
    

if __name__ == "__main__":
  
	# Create a hardcoded doubly linked list:
    # 1 <-> 2 <-> 3
    head = Node(1)
    head.next = Node(2)
    head.next.prev = head
    head.next.next = Node(3)
    head.next.next.prev = head.next

    print("Original Linked List: ", end="")
    print_list(head)

    print("After Deletion at the beginning: ", end="")
    head = del_head(head)

    print_list(head)
```
tab: Javascript
```javascript
// JavaScript Program to delete a node from the 
// beginning of Doubly Linked List
class Node {
    constructor(data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

// Deletes the first node (head) of the list and returns the second node as the new head
function delHead(head) {
    // If empty, return null
    if (head === null) {
        return null;
    }

    // Store in temp for deletion later
    let temp = head;

    // Move head to the next node
    head = head.next;

    // Set prev of the new head
    if (head !== null) {
        head.prev = null;
    }

    // Return new head
    return head;
}

// Function to print the list
function printList(head) {
    let curr = head;
    let output = '';
    while (curr !== null) {
        output += curr.data + ' ';
        curr = curr.next;
    }
    console.log(output.trim());
}

// Create a hardcoded doubly linked list:
// 1 <-> 2 <-> 3
let head = new Node(1);
head.next = new Node(2);
head.next.prev = head;
head.next.next = new Node(3);
head.next.next.prev = head.next;

console.log("Original Linked List: ");
printList(head);

console.log("After Deletion at the beginning: ");
head = delHead(head);

printList(head);
```
tab: C#
```csharp
// C# Program to delete a node from the
// beginning of Doubly Linked List

using System;

class Node {
    public int Data;
    public Node Prev;
    public Node Next;

    public Node(int data) {
        Data = data;
        Prev = null;
        Next = null;
    }
}

class GFG {
  	
    // Deletes the first node (head) of the list
    // and returns the second node as the new head
    public static Node DelHead(Node head) {
      
        // If empty, return null
        if (head == null)
            return null;

        // Move head to the next node
        head = head.Next;

        // Set prev of the new head
        if (head != null)
            head.Prev = null;

        // Return new head
        return head;
    }

    public static void PrintList(Node head) {
        Node curr = head;
        while (curr != null) {
            Console.Write(curr.Data + " ");
            curr = curr.Next;
        }
        Console.WriteLine();
    }

    static void Main() {
      
        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 3
        Node head = new Node(1);
        head.Next = new Node(2);
        head.Next.Prev = head;
        head.Next.Next = new Node(3);
        head.Next.Next.Prev = head.Next;

        Console.Write("Original Linked List: ");
        PrintList(head);

        Console.Write("After Deletion at the beginning: ");
        head = DelHead(head);

        PrintList(head);
    }
}
```
````
**Output**
> Original Linked List: 1 2 3
> After Deletion at the beginning: 2 3
### Deletion at the End
![Deletion-at-the-End-in-Doubly-Linked-List](images/Deletion-at-the-End-in-Doubly-Linked-List.webp)
To delete a node at the end in doubly linked list, we can use the following steps:
- Check if the doubly linked list is empty. If it is empty, then there is nothing to delete.
- If the list is not empty, then move to the last node of the doubly linked list, say **curr**.
- Update the second-to-last node’s next pointer to NULL, **curr->prev->next = NULL**.
- Free the memory allocated for the node that was deleted.

Below is the implementation of the above approach:
````tabs

tab: C++
```cpp
// C++ Program to delete a node from the end of
//Doubly Linked List

#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    Node *prev;
    Node *next;
    Node(int d) {
        data = d;
        prev = NULL;
        next = NULL;
    }
};

// Function to delete the last node of the doubly
// linked list
Node *delLast(Node *head) {

    // Corner cases
    if (head == NULL)
        return NULL;
    if (head->next == NULL) {
        delete head;
        return NULL;
    }

    // Traverse to the last node
    Node *curr = head;
    while (curr->next != NULL)
        curr = curr->next;

    // Update the previous node's next pointer
    curr->prev->next = NULL;

  	// Delete the last node
    delete curr; 

    // Return the updated head
    return head;
}

void printList(Node *head) {
    Node *curr = head;
    while (curr != NULL) {
        cout << curr->data << " ";
        curr = curr->next;
    }
    cout << endl;
}

int main() {
  	
    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node *head = new Node(1);
    head->next = new Node(2);
    head->next->prev = head;
    head->next->next = new Node(3);
    head->next->next->prev = head->next;

    printf("Original Linked List: ");
    printList(head);

    printf("After Deletion at the end: ");
    head = delLast(head);

    printList(head);

    return 0;
}
```
tab: C
```c
// C Program to delete a node from the end of 
//Doubly Linked List

#include <stdio.h>

struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

// Function to delete the last node of the 
//doubly linked list
struct Node* delLast(struct Node *head) {
  
    // Corner cases
    if (head == NULL)
        return NULL;
    if (head->next == NULL) {
        free(head);
        return NULL;
    }

    // Traverse to the last node
    struct Node *curr = head;
    while (curr->next != NULL)
        curr = curr->next;

    // Update the previous node's next pointer
    curr->prev->next = NULL;

    // Delete the last node
    free(curr);

    // Return the updated head
    return head;
}

// Function to print the list
void printList(struct Node *head) {
    struct Node *curr = head;
    while (curr != NULL) {
        printf("%d ", curr->data);
        curr = curr->next;
    }
    printf("\n");
}

// Function to create a new node
struct Node* createNode(int data) {
    struct Node *newNode =
      (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

int main() {
  
    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node *head = createNode(1);
    head->next = createNode(2);
    head->next->prev = head;
    head->next->next = createNode(3);
    head->next->next->prev = head->next;

    printf("Original Linked List: ");
    printList(head);

    printf("After Deletion at the end: ");
    head = delLast(head);

    printList(head);

    return 0;
}
```
tab: Java
```java
// Java Program to delete a node from the end of 
//Doubly Linked List

class Node {
    int data;
    Node prev;
    Node next;

    Node(int data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

class GFG {
  
    // Function to delete the last node of the 
  	//doubly linked list
    public static Node delLast(Node head) {
      
        // Corner cases
        if (head == null) {
            return null;
        }
        if (head.next == null) {
            return null;
        }

        // Traverse to the last node
        Node curr = head;
        while (curr.next != null) {
            curr = curr.next;
        }

        // Update the previous node's next pointer
        if (curr.prev != null) {
            curr.prev.next = null;
        }

        // Return the updated head
        return head;
    }

    // Function to print the list
    public static void printList(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
      
        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 3
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.prev = head;
        head.next.next = new Node(3);
        head.next.next.prev = head.next;

        System.out.print("Original Linked List: ");
        printList(head);

        System.out.print("After Deletion at the end: ");
        head = delLast(head);

        printList(head);
    }
}
```
tab: Python
```python
# Python Program to delete a node from the end of 
#Doubly Linked List

class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

def del_last(head):
  
    # Corner cases
    if head is None:
        return None
    if head.next is None:
        return None

    # Traverse to the last node
    curr = head
    while curr.next is not None:
        curr = curr.next

    # Update the previous node's next pointer
    if curr.prev is not None:
        curr.prev.next = None

    # Return the updated head
    return head

def print_list(head):
    curr = head
    while curr is not None:
        print(curr.data, end=" ")
        curr = curr.next
    print()

if __name__ == "__main__":
  
    # Create a hardcoded doubly linked list:
    # 1 <-> 2 <-> 3
    head = Node(1)
    head.next = Node(2)
    head.next.prev = head
    head.next.next = Node(3)
    head.next.next.prev = head.next

    print("Original Linked List: ", end="")
    print_list(head)

    print("After Deletion at the end: ", end="")
    head = del_last(head)

    print_list(head)
```
tab: Javascript
```javascript
class Node {
    constructor(data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

// Function to delete the last node of the
//doubly linked list
function delLast(head) {
    // Corner cases
    if (head === null) return null;
    if (head.next === null) {
        // Only one node in the list
        return null;
    }

    // Traverse to the last node
    let curr = head;
    while (curr.next !== null) {
        curr = curr.next;
    }

    // Update the previous node's next pointer
    if (curr.prev !== null) {
        curr.prev.next = null;
    }

    // Node curr is now deleted (garbage collected in JS)
    return head;
}

// Function to print the list
function printList(head) {
    let curr = head;
    while (curr !== null) {
        console.log(curr.data + " ");
        curr = curr.next;
    }
}

// Create a hardcoded doubly linked list:
// 1 <-> 2 <-> 3
let head = new Node(1);
head.next = new Node(2);
head.next.prev = head;
head.next.next = new Node(3);
head.next.next.prev = head.next;

console.log("Original Linked List:");
printList(head);

console.log("After Deletion at the end:");
head = delLast(head);

printList(head);
```
tab: C#
```csharp
// C# Program to delete a node from the end of 
//Doubly Linked List

using System;

class Node {
    public int Data;
    public Node Prev;
    public Node Next;

    public Node(int data) {
        Data = data;
        Prev = null;
        Next = null;
    }
}

class GFG {
  
    // Function to delete the last node of the
  	//doubly linked list
    static Node DelLast(Node head) {
        
      	// Corner cases
        if (head == null)
            return null;
        if (head.Next == null) {
            return null;
        }

        // Traverse to the last node
        Node curr = head;
        while (curr.Next != null)
            curr = curr.Next;

        // Update the previous node's next pointer
        if (curr.Prev != null)
            curr.Prev.Next = null;

        // Delete the last node
        curr = null;

        // Return the updated head
        return head;
    }

    // Function to print the list
    static void PrintList(Node head) {
        Node curr = head;
        while (curr != null) {
            Console.Write(curr.Data + " ");
            curr = curr.Next;
        }
        Console.WriteLine();
    }

    static void Main() {
      
        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 3
        Node head = new Node(1);
        head.Next = new Node(2);
        head.Next.Prev = head;
        head.Next.Next = new Node(3);
        head.Next.Next.Prev = head.Next;

        Console.Write("Original Linked List: ");
        PrintList(head);

        Console.Write("After Deletion at the end: ");
        head = DelLast(head);

        PrintList(head);
    }
}
```
````
### Deletion at a Specific Position
![Deletion-at-a-Specific-Position-in-Doubly-Linked-List](images/Deletion-at-a-Specific-Position-in-Doubly-Linked-List.webp)
To delete a node at a specific position in doubly linked list, we can use the following steps:

- Traverse to the node at the specified position, say **curr**.
- If the position is valid, adjust the pointers to skip the node to be deleted.
    - If curr is not the head of the linked list, update the next pointer of the node before curr to point to the node after curr, **curr->prev->next = curr-next**.
    - If curr is not the last node of the linked list, update the previous pointer of the node after curr to the node before curr, **curr->next->prev = curr->prev**.
- Free the memory allocated for the deleted node.

Below is the implementation of the above approach:
````tabs

tab: C++
```cpp
// C++ Program to delete node at a specific position
// in Doubly Linked List

#include <iostream>

using namespace std;

struct Node {
    int data;
    Node * prev;
    Node * next;
    Node(int d) {
        data = d;
        prev = next = NULL;
    }
};

// Function to delete a node at a specific position 
// in the doubly linked list
Node * delPos(Node * head, int pos) {

    // If the list is empty
    if (!head)
        return head;

    Node * curr = head;

    // Traverse to the node at the given position
    for (int i = 1; curr && i < pos; ++i) {
        curr = curr -> next;
    }

    // If the position is out of range
    if (!curr)
        return head;

    // Update the previous node's next pointer
    if (curr -> prev)
        curr -> prev -> next = curr -> next;

    // Update the next node's prev pointer
    if (curr -> next)
        curr -> next -> prev = curr -> prev;

    // If the node to be deleted is the head node
    if (head == curr)
        head = curr -> next;

    // Deallocate memory for the deleted node
    delete curr;
    return head;
}

// Function to print the doubly linked list
void printList(Node * head) {
    Node * curr = head;
    while (curr != nullptr) {
        cout << curr -> data << " ";
        curr = curr -> next;
    }
    cout << endl;
}

int main() {

    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node * head = new Node(1);
    head -> next = new Node(2);
    head -> next -> prev = head;
    head -> next -> next = new Node(3);
    head -> next -> next -> prev = head -> next;

    cout << "Original Linked List: ";
    printList(head);

    cout << "After Deletion at the position 2: ";
    head = delPos(head, 2);

    printList(head);

    return 0;
}
```
tab: C
```c
// C Program to delete node at a specific position
//in Doubly Linked List

#include <stdio.h>

struct Node {
    int data;
    struct Node * prev;
    struct Node * next;
};

struct Node * createNode(int data) {
    struct Node * newNode = (struct Node * )
    malloc(sizeof(struct Node));
    newNode -> data = data;
    newNode -> prev = NULL;
    newNode -> next = NULL;
    return newNode;
}

// Function to delete a node at a specific 
//position in the doubly linked list
struct Node * delPos(struct Node * head, int pos) {

    // If the list is empty
    if (head == NULL)
        return head;

    struct Node * curr = head;

    // Traverse to the node at the given position
    for (int i = 1; curr && i < pos; ++i) {
        curr = curr -> next;
    }

    // If the position is out of range
    if (curr == NULL)
        return head;

    // Update the previous node's next pointer
    if (curr -> prev)
        curr -> prev -> next = curr -> next;

    // Update the next node's prev pointer
    if (curr -> next)
        curr -> next -> prev = curr -> prev;

    // If the node to be deleted is the head node
    if (head == curr)
        head = curr -> next;

    // Deallocate memory for the deleted node
    free(curr);
    return head;
}

// Function to print the doubly linked list
void printList(struct Node * head) {
    struct Node * curr = head;
    while (curr != NULL) {
        printf("%d ", curr -> data);
        curr = curr -> next;
    }
    printf("\n");
}

int main() {

    // Create a hardcoded doubly linked list:
    // 1 <-> 2 <-> 3
    struct Node * head = createNode(1);
    struct Node * temp1 = createNode(2);
    struct Node * temp2 = createNode(3);

    // Link the nodes together
    head -> next = temp1;
    temp1 -> prev = head;
    temp1 -> next = temp2;
    temp2 -> prev = temp1;

    printf("Original Linked List: ");
    printList(head);

    // Delete node at position 2
    head = delPos(head, 2);

    printf("After Deletion at position 2: ");
    printList(head);

    return 0;
}
```
tab: Java
```java
// Java Program to delete node at a specific position in Doubly Linked List

class Node {
    int data;
    Node prev;
    Node next;

    Node(int d) {
        data = d;
        prev = null;
        next = null;
    }
}

class GFG {

    // Function to delete a node at a 
  	//specific position in the doubly linked list
    public static Node delPos(Node head, int pos) {

        // If the list is empty
        if (head == null) {
            return head;
        }

        Node curr = head;

        // Traverse to the node at the given position
        for (int i = 1; curr != null && i < pos; ++i) {
            curr = curr.next;
        }

        // If the position is out of range
        if (curr == null) {
            return head;
        }

        // Update the previous node's next pointer
        if (curr.prev != null) {
            curr.prev.next = curr.next;
        }

        // Update the next node's prev pointer
        if (curr.next != null) {
            curr.next.prev = curr.prev;
        }

        // If the node to be deleted is the head node
        if (head == curr) {
            head = curr.next;
        }

        // Return the updated head
        return head;
    }

    // Function to print the doubly linked list
    public static void printList(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {

        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 3
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.prev = head;
        head.next.next = new Node(3);
        head.next.next.prev = head.next;

        System.out.print("Original Linked List: ");
        printList(head);

        System.out.print("After Deletion at position 2: ");
        head = delPos(head, 2);

        printList(head);
    }
}
```
tab: Python
```python
# Python Program to delete node at a specific position
#in Doubly Linked List


class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None


# Function to delete a node at a specific position 
#in the doubly linked list
def del_pos(head, pos):
    # If the list is empty
    if head is None:
        return head

    curr = head

    # Traverse to the node at the given position
    for i in range(1, pos):
        if curr is None:
            return head
        curr = curr.next

    # If the position is out of range
    if curr is None:
        return head

    # Update the previous node's next pointer
    if curr.prev is not None:
        curr.prev.next = curr.next

    # Update the next node's prev pointer
    if curr.next is not None:
        curr.next.prev = curr.prev

    # If the node to be deleted is the head node
    if head == curr:
        head = curr.next

    # Return the updated head
    return head


def print_list(head):
    curr = head
    while curr is not None:
        print(curr.data, end=" ")
        curr = curr.next
    print()


if __name__ == "__main__":
  
    # Create a hardcoded doubly linked list:
    # 1 <-> 2 <-> 3
    head = Node(1)
    head.next = Node(2)
    head.next.prev = head
    head.next.next = Node(3)
    head.next.next.prev = head.next

    print("Original Linked List: ", end="")
    print_list(head)

    print("After Deletion at the position 2: ", end="")
    head = del_pos(head, 2)

    print_list(head)
```
tab: Javascript
```javascript
class Node {
	constructor(data) {
		this.data = data;
		this.prev = null;
		this.next = null;
	}
}

// Function to delete a node at a specific position
// in the doubly linked list
function delPos(head, pos) {
	// If the list is empty
	if (head === null) return head;

	let curr = head;

	// Traverse to the node at the given position
	for (let i = 1; curr && i < pos; ++i) {
		curr = curr.next;
	}

	// If the position is out of range
	if (curr === null) return head;

	// Update the previous node's next pointer
	if (curr.prev) {
		curr.prev.next = curr.next;
	}

	// Update the next node's prev pointer
	if (curr.next) {
		curr.next.prev = curr.prev;
	}

	// If the node to be deleted is the head node
	if (head === curr) {
		head = curr.next;
	}

	// Deallocate memory for the deleted node
	// In JavaScript, garbage collection handles 
    //this automatically

	return head;
}

// Function to print the doubly linked list
function printList(head) {
	let curr = head;
	let result = [];
	while (curr !== null) {
		result.push(curr.data);
		curr = curr.next;
	}
	console.log(result.join(' '));
}


// Create a hardcoded doubly linked list:
// 1 <-> 2 <-> 3
let head = new Node(1);
head.next = new Node(2);
head.next.prev = head;
head.next.next = new Node(3);
head.next.next.prev = head.next;

console.log("Original Linked List:");
printList(head);

console.log("After Deletion at the position 2:");
head = delPos(head, 2);

printList(head);
```
tab: C#
```csharp
// C# Program to delete node at a specific position
//in Doubly Linked List

using System;

class Node {
    public int Data;
    public Node Prev;
    public Node Next;

    public Node(int data) {
        Data = data;
        Prev = null;
        Next = null;
    }
}

class Program {
    // Function to delete a node at a specific position
    // in the doubly linked list
    static Node DelPos(Node head, int pos) {
        // If the list is empty
        if (head == null)
            return head;

        Node curr = head;

        // Traverse to the node at the given position
        for (int i = 1; curr != null && i < pos; ++i) {
            curr = curr.Next;
        }

        // If the position is out of range
        if (curr == null)
            return head;

        // Update the previous node's next pointer
        if (curr.Prev != null)
            curr.Prev.Next = curr.Next;

        // Update the next node's prev pointer
        if (curr.Next != null)
            curr.Next.Prev = curr.Prev;

        // If the node to be deleted is the head node
        if (head == curr)
            head = curr.Next;

        // Deallocate memory for the deleted node
        // In C#, garbage collection will handle this
      	//automatically

        return head;
    }

    // Function to print the doubly linked list
    static void PrintList(Node head) {
        Node curr = head;
        while (curr != null) {
            Console.Write(curr.Data + " ");
            curr = curr.Next;
        }
        Console.WriteLine();
    }

    static void Main() {

        // Create a hardcoded doubly linked list:
        // 1 <-> 2 <-> 3
        Node head = new Node(1);
        head.Next = new Node(2);
        head.Next.Prev = head;
        head.Next.Next = new Node(3);
        head.Next.Next.Prev = head.Next;

        Console.Write("Original Linked List: ");
        PrintList(head);

        Console.Write("After Deletion at position 2: ");
        head = DelPos(head, 2);

        PrintList(head);
    }
}
```
````
**Output**
>Original Linked List: 1 2 3
>After Deletion at the position 2: 1 3
## Advantages
- **Efficient traversal in both directions:** Doubly linked lists allow for efficient traversal of the list in both directions, making it suitable for applications where frequent insertions and deletions are required.
- **Easy insertion and deletion of nodes:** The presence of pointers to both the previous and next nodes makes it easy to insert or delete nodes from the list, without having to traverse the entire list.
- **Can be used to implement a stack or queue:** Doubly linked lists can be used to implement both stacks and queues, which are common data structures used in programming.
## Disadvantages 
- **More complex than singly linked lists:** Doubly linked lists are more complex than singly linked lists, as they require additional pointers for each node.
- **More memory overhead:** Doubly linked lists require more memory overhead than singly linked lists, as each node stores two pointers instead of one.
## Application
- Implementation of undo and redo functionality in text editors.
- Cache implementation where quick insertion and deletion of elements are required.
- Browser history management to navigate back and forth between visited pages.
- Music player applications to manage playlists and navigate through songs efficiently.
- Implementing data structures like [Deque](https://www.geeksforgeeks.org/deque-set-1-introduction-applications) (double-ended queue) for efficient insertion and deletion at both ends.
---
**Related Links:-**
- Concepts
	- [LinkedList](../LinkedList.md)
	- [Singly Linked List](../Singly%20Linked%20List/Singly%20Linked%20List.md)
- 
