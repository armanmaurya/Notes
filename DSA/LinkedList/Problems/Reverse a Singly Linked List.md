---
tags:
  - DSA
  - LinkedList
---
# Reverse a Singly Linked List
Given a linked list, the task is to reverse the linked list by changing the links between nodes.
**Examples:**

> [!info] 
> ***Input***: Linked List = 1 -> 2 -> 3 -> 4 -> NULL   
***Output***: Reversed Linked List = 4 -> 3 -> 2 -> 1 -> NULL
>
***Input***: Linked List = 1 -> 2 -> 3 -> 4 -> 5 -> NULL   
***Output***: Reversed Linked List = 5 -> 4 -> 3 -> 2 -> 1 -> NULL
>
***Input***: Linked List = NULL   
***Output***: Reversed Linked List = NULL
>
***Input***: Linked List = 1->NULL   
***Output***: Reversed Linked List = 1->NULL
### 1. Expected Approach
[**Using Iterative Method -- O(n) Time and O(1) Space:**]

> [!info] 
> The idea is to reverse the links of all nodes using **three** pointers:
> - **prev:** pointer to keep track of the previous node
> - **curr**: pointer to keep track of the current node
> - **next:** pointer to keep track of the next node
> 
> Starting from the first node, initialize **curr** with the head of linked list and **next** with the next node of **curr.** Update the next pointer of curr with **prev.** Finally, move the three pointer by updating **prev** with **curr** and **curr** and **next**.

![Reverse-Linked-List-Using-Iterative-Method-1z|center](images/Reverse-Linked-List-Using-Iterative-Method-1.webp)

![Reverse-Linked-List-Using-Iterative-Method-2|center](images/Reverse-Linked-List-Using-Iterative-Method-2.webp) 

![Reverse-Linked-List-Using-Iterative-Method-3|center](images/Reverse-Linked-List-Using-Iterative-Method-3.webp)

![Reverse-Linked-List-Using-Iterative-Method-4|center](images/Reverse-Linked-List-Using-Iterative-Method-4.webp)

![Reverse-Linked-List-Using-Iterative-Method-5|center](images/Reverse-Linked-List-Using-Iterative-Method-5.webp) 

![Reverse-Linked-List-Using-Iterative-Method-6|center](images/Reverse-Linked-List-Using-Iterative-Method-6.webp)
Follow the steps below to solve the problem:
- Initialize three pointers **prev** as *NULL*, **curr** as **head**, and **next** as *NULL*. 
- Iterate through the linked list. In a loop, do the following:
	- Store the next node, **next = curr -> next**
	- Update the next pointer of **curr** to **prev**, **curr -> next = prev**
	- Update the prev as curr and curr as next, **prev = curr** and **curr = next**.
Below is the implementation of the above approach:
````tabs

tab: C++
```cpp
// Iterative C++ program to reverse a linked list

#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;

    Node(int new_data) {
        data = new_data;
        next = nullptr;
    }
};

// Given the head of a list, reverse the list and return the
// head of reversed list
Node* reverseList(Node* head) {
    
      // Initialize three pointers: curr, prev and next
    Node *curr = head, *prev = nullptr, *next;

      // Traverse all the nodes of Linked List
    while (curr != nullptr) {
      
        // Store next
        next = curr->next;
      
        // Reverse current node's next pointer
        curr->next = prev;
      
        // Move pointers one position ahead
        prev = curr;
        curr = next;
    }
      
      // Return the head of reversed linked list
    return prev;
}

void printList(Node* node) {
    while (node != nullptr) {
        cout << " " << node->data;
        node = node->next;
    }
}

int main() {

    // Create a hard-coded linked list:
    // 1 -> 2 -> 3 -> 4 -> 5
    Node* head = new Node(1);
    head->next = new Node(2);
    head->next->next = new Node(3);
    head->next->next->next = new Node(4);
    head->next->next->next->next = new Node(5);

    cout << "Given Linked list:";
    printList(head);

    head = reverseList(head);

    cout << "\nReversed Linked List:";
    printList(head);

    return 0;
}
```
tab: C
```c
// Iterative C program to reverse a linked list

#include <stdio.h>

struct Node {
    int data;
    struct Node* next;
};

// Given the head of a list, reverse the list and return the
// head of reversed list
struct Node* reverseList(struct Node* head) {

    // Initialize three pointers: curr, prev and next
    struct Node *curr = head, *prev = NULL, *next;

    // Traverse all the nodes of Linked List
    while (curr != NULL) {

        // Store next
        next = curr->next;

        // Reverse current node's next pointer
        curr->next = prev;

        // Move pointers one position ahead
        prev = curr;
        curr = next;
    }

    // Return the head of reversed linked list
    return prev;
}

void printList(struct Node* node) {
    while (node != NULL) {
        printf(" %d", node->data);
        node = node->next;
    }
}


struct Node* createNode(int new_data) {
    struct Node* new_node
        = (struct Node*)malloc(sizeof(struct Node));
    new_node->data = new_data;
    new_node->next = NULL;
    return new_node;
}

int main() {

    // Create a hard-coded linked list:
    // 1 -> 2 -> 3 -> 4 -> 5
    struct Node* head = createNode(1);
    head->next = createNode(2);
    head->next->next = createNode(3);
    head->next->next->next = createNode(4);
    head->next->next->next->next = createNode(5);

    printf("Given Linked list:");
    printList(head);

    head = reverseList(head);

    printf("\nReversed Linked List:");
    printList(head);

    return 0;
}
```
tab: Java
```java
// Iterative Java program to reverse a linked list

class Node {
    int data;
    Node next;

    Node(int new_data) {
        data = new_data;
        next = null;
    }
}

// Given the head of a list, reverse the list and return the
// head of reversed list
public class GfG {
     static Node reverseList(Node head) {
        
        // Initialize three pointers: curr, prev and next
        Node curr = head, prev = null, next;

        // Traverse all the nodes of Linked List
        while (curr != null) {
            
            // Store next
            next = curr.next;
            
            // Reverse current node's next pointer
            curr.next = prev;
            
            // Move pointers one position ahead
            prev = curr;
            curr = next;
        }
        
        // Return the head of reversed linked list
        return prev;
    }

    // This function prints the contents
    // of the linked list starting from the head
    static void printList(Node node) {
        while (node != null) {
            System.out.print(" " + node.data);
            node = node.next;
        }
    }

    public static void main(String[] args) {

        // Create a hard-coded linked list:
        // 1 -> 2 -> 3 -> 4 -> 5
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        System.out.print("Given Linked list:");
        printList(head);
        
        head = reverseList(head);

        System.out.print("\nReversed Linked List:");
        printList(head);
    }
}
```
tab: Python
```python
# Iterative Python program to reverse a linked list
class Node:
    def __init__(self, new_data):
        self.data = new_data
        self.next = None

# Given the head of a list, reverse the list and return the
# head of reversed list
def reverse_list(head):

    # Initialize three pointers: curr, prev and next
    curr = head
    prev = None

    # Traverse all the nodes of Linked List
    while curr is not None:

        # Store next
        next_node = curr.next

        # Reverse current node's next pointer
        curr.next = prev

        # Move pointers one position ahead
        prev = curr
        curr = next_node

    # Return the head of reversed linked list
    return prev

def print_list(node):
    while node is not None:
        print(f" {node.data}", end="")
        node = node.next
    print()

if __name__ == "__main__":

    # Create a hard-coded linked list:
    # 1 -> 2 -> 3 -> 4 -> 5
    head = Node(1)
    head.next = Node(2)
    head.next.next = Node(3)
    head.next.next.next = Node(4)
    head.next.next.next.next = Node(5)

    print("Given Linked list:", end="")
    print_list(head)

    head = reverse_list(head)

    print("Reversed Linked List:", end="")
    print_list(head)
```
tab: Javascript
```javascript
// Iterative JavaScript program to reverse a linked list

class Node {
    constructor(newData) {
        this.data = newData;
        this.next = null;
    }
}

// Given the head of a list, reverse the list and return the
// head of reversed list
function reverseList(head) {

    // Initialize three pointers: curr, prev and next
    let curr = head;
    let prev = null;
    let next;

    // Traverse all the nodes of Linked List
    while (curr !== null) {
        // Store next
        next = curr.next;

        // Reverse current node's next pointer
        curr.next = prev;

        // Move pointers one position ahead
        prev = curr;
        curr = next;
    }

    // Return the head of reversed linked list
    return prev;
}

function printList(node) {
    while (node !== null) {
        console.log(" " + node.data);
        node = node.next;
    }
    console.log();
}

// Create a hard-coded linked list:
// 1 -> 2 -> 3 -> 4 -> 5
let head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
head.next.next.next = new Node(4);
head.next.next.next.next = new Node(5);

console.log("Given Linked list:");
printList(head);

head = reverseList(head);

console.log("Reversed Linked List:");
printList(head);
```
tab: C#
```csharp
// Iterative JavaScript program to reverse a linked list

class Node {
    constructor(newData) {
        this.data = newData;
        this.next = null;
    }
}

// Given the head of a list, reverse the list and return the
// head of reversed list
function reverseList(head) {

    // Initialize three pointers: curr, prev and next
    let curr = head;
    let prev = null;
    let next;

    // Traverse all the nodes of Linked List
    while (curr !== null) {
        // Store next
        next = curr.next;

        // Reverse current node's next pointer
        curr.next = prev;

        // Move pointers one position ahead
        prev = curr;
        curr = next;
    }

    // Return the head of reversed linked list
    return prev;
}

function printList(node) {
    while (node !== null) {
        console.log(" " + node.data);
        node = node.next;
    }
    console.log();
}

// Create a hard-coded linked list:
// 1 -> 2 -> 3 -> 4 -> 5
let head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
head.next.next.next = new Node(4);
head.next.next.next.next = new Node(5);

console.log("Given Linked list:");
printList(head);

head = reverseList(head);

console.log("Reversed Linked List:");
printList(head);

```
````
**Output:**
```
Given Linked list: 1 2 3 4 5
Reversed Linked List: 5 4 3 2 1
```
**Time Complexity:** O(n), Traversing over the linked list of size *n*.
**Auxiliary Space:** O(1)

#### [Alternative Approach] Recursion

> [!note] Title
> The idea is to reach the **last node** of the linked list using recursion then start **reversing** the linked list from the last node.

Follow the steps below to solve the problem:
- Divide the list in two parts- first node and rest of the linked list.
- Call **reverse** for the rest of the linked list.
- Link the rest linked list to first
- Fix head pointer to NULL.



![center](images/1.webp)
![center](images/2.webp) ![center](images/3.webp) ![center](images/4.webp) ![center](images/5.webp) ![center](images/6.webp)
![center](images/7.webp) ![center](images/8.webp) ![center](images/9.webp) ![center](images/10.webp)

````tabs

tab: C++
```cpp
// Recursive C++ program to reverse a linked list

#include <bits/stdc++.h>
using namespace std;

class Node {
public:
    int data;
    Node* next;

    Node(int new_data) {
        data = new_data;
        next = nullptr;
    }
};

// Given the head of a list, reverse the list and return the
// head of reversed list
Node* reverseList(Node* head) {
    if (head == NULL || head->next == NULL)
        return head;

    // reverse the rest of linked list and put the first element at the end 
    Node* rest = reverseList(head->next);
  
      // Make the current head as last node of remaining linked list
    head->next->next = head;

      // Update next of current head to NULL
    head->next = NULL;

       // Return the reversed linked list
    return rest;
}

void printList(Node* node) {
    while (node != nullptr) {
        cout << " " << node->data;
        node = node->next;
    }
}

int main() {

    // Create a hard-coded linked list:
    // 1 -> 2 -> 3 -> 4 -> 5
    Node* head = new Node(1);
    head->next = new Node(2);
    head->next->next = new Node(3);
    head->next->next->next = new Node(4);
    head->next->next->next->next = new Node(5);

    cout << "Given Linked List:";
    printList(head);

    head = reverseList(head);

    cout << "\nReversed Linked List:";
    printList(head);

    return 0;
}
```
tab: C
```c
// Recursive C program to reverse a linked list
#include <stdio.h>

struct Node {
    int data;
    struct Node* next;
};

// Given the head of a list, reverse the list and return the
// head of reversed list
struct Node* reverseList(struct Node* head) {
    if (head == NULL || head->next == NULL)
        return head;

    // reverse the rest of linked list and put the first element at the end
    struct Node* rest = reverseList(head->next);

    // Make the current head as last node of remaining linked list
    head->next->next = head;

    // Update next of current head to NULL
    head->next = NULL;

    // Return the reversed linked list
    return rest;
}


// This function prints the contents
// of the linked list starting from the head
void printList(struct Node* node) {
    while (node != NULL) {
        printf(" %d", node->data);
        node = node->next;
    }
    printf("\n");
}

struct Node* createNode(int new_data) {
    struct Node* new_node = 
       (struct Node*)malloc(sizeof(struct Node));
    new_node->data = new_data;
    new_node->next = NULL;
    return new_node;
}

int main() {
  
    // Create a hard-coded linked list:
    // 1 -> 2 -> 3 -> 4 -> 5
    struct Node* head = createNode(1);
    head->next = createNode(2);
    head->next->next = createNode(3);
    head->next->next->next = createNode(4);
    head->next->next->next->next = createNode(5);

    printf("Given Linked List:");
    printList(head);

    head = reverseList(head);

    printf("Reversed Linked List:");
    printList(head);

    return 0;
}
```
tab: Java
```java
// Recursive Java program to reverse a linked list

class Node {
    int data;
    Node next;

    Node(int new_data) {
        data = new_data;
        next = null;
    }
}

class GfG {
    // Given the head of a list, reverse the list and return
    // the head of reversed list
    static Node reverseList(Node head) {

        // If we have reached the last node or the linked
        // list is empty, simply return the head of linked
        // list
        if (head == null || head.next == null)
            return head;

        // reverse the rest of linked list and put the first
        // element at the end
        Node rest = reverseList(head.next);

        // Make the current head as last node of remaining
        // linked list
        head.next.next = head;

        // Update next of current head to NULL
        head.next = null;

        // Return the reversed linked list
        return rest;
    }

    // This function prints the contents
    // of the linked list starting from the head
    static void printList(Node node) {
        while (node != null) {
            System.out.print(" " + node.data);
            node = node.next;
        }
    }

    public static void main(String[] args)
    {

        // Create a hard-coded linked list:
        // 1 -> 2 -> 3 -> 4 -> 5
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);

        System.out.print("Given Linked List:");
        printList(head);

        head = reverseList(head);

        System.out.print("\nReversed Linked List:");
        printList(head);
    }
}
```
tab: Python
```python
# Recursive Python program to reverse a linked list

class Node:
    def __init__(self, new_data):
        self.data = new_data
        self.next = None

# Given the head of a list, reverse the list and return the
# head of reversed list
def reverse_list(head):
    if head is None or head.next is None:
        return head

    # reverse the rest of linked list and put the 
    # first element at the end
    rest = reverse_list(head.next)

    # Make the current head as last node of remaining linked list
    head.next.next = head

    # Update next of current head to NULL
    head.next = None

    # Return the reversed linked list
    return rest

def print_list(node):
    while node is not None:
        print(f" {node.data}", end='')
        node = node.next
    print()


if __name__ == "__main__":

    # Create a hard-coded linked list:
    # 1 -> 2 -> 3 -> 4 -> 5
    head = Node(1)
    head.next = Node(2)
    head.next.next = Node(3)
    head.next.next.next = Node(4)
    head.next.next.next.next = Node(5)

    print("Given Linked List:", end='')
    print_list(head)

    head = reverse_list(head)

    print("\nReversed Linked List:", end='')
    print_list(head)
```
tab: Javascript
```javascript
// Recursive javascript program to reverse a linked list

class Node {
    constructor(new_data) {
        this.data = new_data;
        this.next = null;
    }
}

// Given the head of a list, reverse the list and return the
// head of reversed list
function reverseList(head) {
    if (head === null || head.next === null)
        return head;

    // reverse the rest of linked list and put the first
    // element at the end
    let rest = reverseList(head.next);

    // Make the current head as last node of remaining
    // linked list
    head.next.next = head;

    // Update next of current head to NULL
    head.next = null;

    // Return the reversed linked list
    return rest;
}

function printList(node) {
    while (node !== null) {
        console.log(` ${node.data}`);
        node = node.next;
    }
    console.log();
}


// Create a hard-coded linked list:
// 1 -> 2 -> 3 -> 4 -> 5
let head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
head.next.next.next = new Node(4);
head.next.next.next.next = new Node(5);

console.log("Given Linked List:");
printList(head);

head = reverseList(head);

console.log("\nReversed Linked List:");
printList(head);
```
tab: C#
```csharp
// Recursive C# program to reverse a linked list

using System;

class Node {
    public int Data;
    public Node Next;

    public Node(int newData) {
        Data = newData;
        Next = null;
    }
}

class GfG {
      // Given the head of a list, reverse the list and return the
    // head of reversed list
    static Node ReverseList(Node head) {
        if (head == null || head.Next == null)
            return head;

        // reverse the rest of linked list and put the first
        // element at the end
        Node rest = ReverseList(head.Next);

        // Make the current head as last node of remaining
        // linked list
        head.Next.Next = head;

        // Update next of current head to NULL
        head.Next = null;

        // Return the reversed linked list
        return rest;
    }

    // This function prints the contents
    // of the linked list starting from the head
    static void PrintList(Node node) {
        while (node != null) {
            Console.Write(" " + node.Data);
            node = node.Next;
        }
          Console.WriteLine();
    }
  
    static void Main() {
      
        // Create a hard-coded linked list:
        // 1 -> 2 -> 3 -> 4 -> 5
        Node head = new Node(1);
        head.Next = new Node(2);
        head.Next.Next = new Node(3);
        head.Next.Next.Next = new Node(4);
        head.Next.Next.Next.Next = new Node(5);

        Console.Write("Given Linked List:");
        PrintList(head);

        head = ReverseList(head);

        Console.Write("\nReversed Linked List:");
        PrintList(head);
    }
}
```
````


---
**Related Links:-**
- Concepts:-
	- [Singly Linked List](../Singly%20Linked%20List/Singly%20Linked%20List.md)
- Problems:-
	- [Find Middle of the Singly Linked List](Find%20Middle%20of%20the%20Singly%20Linked%20List.md)
