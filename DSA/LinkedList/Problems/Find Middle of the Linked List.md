# Find Middle of the Linked List
Given a singly linked list, the task is to find the middle of the linked list. If the number of nodes are even, then there would be two middle nodes, so return the second middle node.
**Example:**

> [!info] Info
> ***Input:*** linked list: 1->2->3->4->5  
***Output:*** 3   
***Explanation:*** There are 5 nodes in the linked list and there is one middle node whose value is 3.
>
***Input:*** linked list = 10 -> 20 -> 30 -> 40 -> 50 -> 60  
***Output:*** 40  
***Explanation:*** There are 6 nodes in the linked list, so we have two middle nodes: 30 and 40, but we will return the second middle node which is 40.
>
> ![[images/Middle-of-a-Linked-List4.webp|center]]

## Solution:-
#### 1. Native Approach
By Counting Nodes- O(n) time and O(1) space:

> [!note] Note
> The idea is to traversing the entire linked list once to count the total number of nodes. After determining the total count, traverse the list again and stop at the **(count/2)th** node to return its value. This method requires two passes through the linked list to find the middle element.

````tabs

tab: C++
```cpp
/// C++ program to illustrate how to find the middle element
// by counting the number of nodes
#include <bits/stdc++.h>
using namespace std;

class Node {
public:
    int data;
    Node* next;
  
    Node(int x) {
        this->data = x;
        this->next = nullptr;
    }
};

// Helper function to find length of linked list
int getLength(Node* head) {

    // Variable to store length
    int length = 0;

    // Traverse the entire linked list and increment length by
    // 1 for each node
    while (head) {
        length++;
        head = head->next;
    }

    // Return the number of nodes in the linked list
    return length;
}

// Function to find the middle element of the linked list
int getMiddle(Node* head) {

    // Finding length of the linked list
    int length = getLength(head);

    // traverse till we reached half of length
    int mid_index = length / 2;
    while (mid_index--) {
        head = head->next;
    }

    // Head now will be pointing to the middle element
    return head->data;
}

int main() {

    // Create a hard-coded linked list:
    // 10 -> 20 -> 30 -> 40 -> 50 -> 60 
    Node* head = new Node(10);
    head->next = new Node(20);
    head->next->next = new Node(30);
    head->next->next->next = new Node(40);
    head->next->next->next->next = new Node(50);
    head->next->next->next->next->next = new Node(60);

    cout << getMiddle(head);

    return 0;
}
```
tab: C
```c
// C program to illustrate how to find the middle element
// by counting the number of nodes
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

// Helper function to find length of linked list
int getLength(struct Node* head) {

    // Variable to store length
    int length = 0;

    // Traverse the entire linked list and increment length
    // by 1 for each node
    while (head) {
        length++;
        head = head->next;
    }

    // Return the number of nodes in the linked list
    return length;
}

// Function to find the middle element of the linked list
int getMiddle(struct Node* head) {

    // Finding length of the linked list
    int length = getLength(head);

    // Traverse till we reach half of the length
    int mid_index = length / 2;
    while (mid_index--) {
        head = head->next;
    }

    // Head now will be pointing to the middle element
    return head->data;
}

struct Node* createNode(int x) {
    struct Node* newNode
        = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = x;
    newNode->next = NULL;
    return newNode;
}

int main() {

    // Create a hard-coded linked list:
    // 10 -> 20 -> 30 -> 40 -> 50 -> 60 
    struct Node* head = createNode(10);
    head->next = createNode(20);
    head->next->next = createNode(30);
    head->next->next->next = createNode(40);
    head->next->next->next->next = createNode(50);
    head->next->next->next->next->next = createNode(60);

    printf("%d\n", getMiddle(head));

    return 0;
}
```
tab: Java
```java
// Java program to illustrate how to find the middle element
// by counting the number of nodes

// A singly linked list node
class Node {
    int data;
    Node next;

    // Constructor to initialize a new node with data
    Node(int x) {
        this.data = x;
        this.next = null;
    }
}

class GfG {

    // Helper function to find length of linked list
    static int getLength(Node head) {

        // Variable to store length
        int length = 0;

        // Traverse the entire linked list and increment
        // length by 1 for each node
        while (head != null) {
            length++;
            head = head.next;
        }

        // Return the number of nodes in the linked list
        return length;
    }

    // Function to get the middle value of the linked list
    static int getMiddle(Node head) {
      
        // Finding the length of the list
        int length = getLength(head);

        // traverse till we reached half of length
        int mid_index = length / 2;
        while (mid_index > 0) {
            head = head.next;
            mid_index--;
        }
        // temp will be storing middle element
        return head.data;
    }

    public static void main(String[] args) {

        // Create a hard-coded linked list:
        // 10 -> 20 -> 30 -> 40 -> 50 -> 60 
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(50);
        head.next.next.next.next.next = new Node(60);

        System.out.println(getMiddle(head));
    }
}
```
tab: Python
```python
# Java program to illustrate how to find the middle element
# by counting the number of nodes

class Node:
    def __init__(self, x):
        self.data = x
        self.next = None

# Helper function to find length of linked list
def getLength(head):

    # Variable to store length
    length = 0

    # Traverse the entire linked list and increment length
    # by 1 for each node
    while head:
        length += 1
        head = head.next

    # Return the number of nodes in the linked list
    return length

# Function to find the middle element of the linked list
def getMiddle(head):

    # Finding length of the linked list
    length = getLength(head)

    # Traverse till we reach half of the length
    mid_index = length // 2
    while mid_index:
        head = head.next
        mid_index -= 1

    # Head now will be pointing to the middle element
    return head.data

def main():

    # Create a hard-coded linked list:
    # 10 -> 20 -> 30 -> 40 -> 50 -> 60
    head = Node(10)
    head.next = Node(20)
    head.next.next = Node(30)
    head.next.next.next = Node(40)
    head.next.next.next.next = Node(50)
    head.next.next.next.next.next = Node(60)

    print(getMiddle(head))

if __name__ == "__main__":
    main()
```
tab: Javascript
```javascript
// Javascript program to illustrate how to find the middle
// element by counting the number of nodes

class Node {
    constructor(x) {
        this.data = x;
        this.next = null;
    }
}

// Helper function to find length of linked list
function getLength(head) {

    // Variable to store length
    let length = 0;

    // Traverse the entire linked list and increment length
    // by 1 for each node
    while (head) {
        length++;
        head = head.next;
    }

    // Return the number of nodes in the linked list
    return length;
}

// Function to find the middle element of the linked list
function getMiddle(head) {

    // Finding length of the linked list
    const length = getLength(head);

    // Traverse till we reach half of the length
    let mid_index = Math.floor(length / 2);
    while (mid_index-- > 0) {
        head = head.next;
    }

    // Head now will be pointing to the middle element
    return head.data;
}

function main() {

    // Create a hard-coded linked list:
    // 10 -> 20 -> 30 -> 40 -> 50 -> 60
    const head = new Node(10);
    head.next = new Node(20);
    head.next.next = new Node(30);
    head.next.next.next = new Node(40);
    head.next.next.next.next = new Node(50);
    head.next.next.next.next.next = new Node(60);

    console.log(getMiddle(head));
}

main();
```
tab: C#
```csharp
// C# program to illustrate how to find the middle element
// by counting the number of nodes
using System;

class Node {
    public int data;
    public Node next;
    public Node(int x) {
        this.data = x;
        this.next = null;
    }
}

class GfG {

    // Helper function to find length of linked list
    static int getLength(Node head) {

        // Variable to store length
        int length = 0;

        // Traverse the entire linked list and increment
        // length by 1 for each node
        while (head != null) {
            length++;
            head = head.next;
        }

        // Return the number of nodes in the linked list
        return length;
    }

    // Function to find the middle element of the linked
    // list
    static int getMiddle(Node head) {

        // Finding length of the linked list
        int length = getLength(head);

        // Traverse till we reach half of the length
        int mid_index = length / 2;
        while (mid_index-- > 0) {
            head = head.next;
        }

        // Head now will be pointing to the middle element
        return head.data;
    }

    static void Main() {

        // Create a hard-coded linked list:
        // 10 -> 20 -> 30 -> 40 -> 50 -> 60
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(50);
        head.next.next.next.next.next = new Node(60);
      
        Console.WriteLine(getMiddle(head));
    }
}
```
````
**Output:**
```
40
```

**Time Complexity:** O (2 * n) = O(n) where n is the number of nodes in the linked list.
**Auxiliary Space:** O(1)
#### 2. Expected Approach
By Tortoise and Hare Algorithm -- O(n) time and O(1) space:

> [!note] Title
> We can use the [***Hare and Tortoise Algorithm***](https://www.geeksforgeeks.org/tag/tortoise-hare-approach/) to find the middle of the linked list. Traverse linked list using a slow pointer (***slow_ptr***) and a fast pointer (***fast_ptr*** ). Move the slow pointer to the next node(one node forward) and the fast pointer to the next of the next node(two nodes forward). When the fast pointer reaches the last node or NULL, then the slow pointer will reach the middle of the linked list.
>
In case of ***odd*** number of nodes in the linked list, ***slow_ptr*** will reach the middle node when ***fast_ptr*** will reach the last node and in case of ***even*** number of nodes in the linked list, ***slow_ptr*** will reach the middle node when ***fast_ptr*** will become NULL.

Below is the working of above approach:

![[images/Find-Middle-of-the-Linked-List-1_1.webp|center]]
![[images/Find-Middle-of-the-Linked-List-2_1.webp|center]]
![[images/Find-Middle-of-the-Linked-List-3_1.webp|center]]
````tabs

tab: C++
```cpp
// C++ program to illustrate how to find the middle element
// by using Floyd's Cycle Finding Algorithm
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
    Node(int x) {
        this->data = x;
        this->next = nullptr;
    }
};

// Function to get the middle of the linked list
int getMiddle(Node* head) {
  
    // Initialize the slow and fast pointer to the head of
    // the linked list
    Node* slow_ptr = head;
    Node* fast_ptr = head;

    while (fast_ptr != NULL && fast_ptr->next != NULL) {

        // Move the fast pointer by two nodes
        fast_ptr = fast_ptr->next->next;

        // Move the slow pointer by one node
        slow_ptr = slow_ptr->next;
    }

    // Return the slow pointer which is currenlty pointing
    // to the middle node of the linked list
    return slow_ptr->data;
}

int main() {

    // Create a hard-coded linked list:
    // 10 -> 20 -> 30 -> 40 -> 50 -> 60 
    Node* head = new Node(10);
    head->next = new Node(20);
    head->next->next = new Node(30);
    head->next->next->next = new Node(40);
    head->next->next->next->next = new Node(50);
    head->next->next->next->next->next = new Node(60);

    cout << getMiddle(head) << endl;

    return 0;
}
```
tab: C
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

// Function to get the middle of the linked list
int getMiddle(struct Node* head) {
  
    // Initialize the slow and fast pointer to the
    // head of the linked list
    struct Node* slow_ptr = head;
    struct Node* fast_ptr = head;

    // Traverse the linked list
    while (fast_ptr != NULL && fast_ptr->next != NULL) {
      
        // Move the fast pointer by two nodes
        fast_ptr = fast_ptr->next->next;

        // Move the slow pointer by one node
        slow_ptr = slow_ptr->next;
    }

    // Return the slow pointer which is currently pointing
    // to the middle node of the linked list
    return slow_ptr->data;
}

struct Node* createNode(int x) {
    struct Node* newNode =
      (struct Node*)malloc(sizeof(struct Node));
    newNode->data = x;
    newNode->next = NULL;
    return newNode;
}

int main() {
    // Create a hard-coded linked list:
    // 10 -> 20 -> 30 -> 40 -> 50 -> 60 
    struct Node* head = createNode(10);
    head->next = createNode(20);
    head->next->next = createNode(30);
    head->next->next->next = createNode(40);
    head->next->next->next->next = createNode(50);
    head->next->next->next->next->next = createNode(60);

    printf("%d\n", getMiddle(head));

    return 0;
}
```
tab: Java
```java
// Java program to illustrate how to find the middle element
// by using Floyd's Cycle Finding Algorithm

class Node {
    int data;
    Node next;

    Node(int x) {
        this.data = x;
        this.next = null;
    }
}

class GfG {

    // Function to get the middle of the linked list
    static int getMiddle(Node head) {

        // Initialize the slow and fast pointer to the head
        // of the linked list
        Node slow_ptr = head;
        Node fast_ptr = head;

        while (fast_ptr != null && fast_ptr.next != null) {

            // Move the fast pointer by two nodes
            fast_ptr = fast_ptr.next.next;

            // Move the slow pointer by one node
            slow_ptr = slow_ptr.next;
        }

        // Return the slow pointer which is currently
        // pointing to the middle node of the linked list
        return slow_ptr.data;
    }

    public static void main(String[] args) {

        // Create a hard-coded linked list:
        // 10 -> 20 -> 30 -> 40 -> 50 -> 60
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(50);
        head.next.next.next.next.next = new Node(60);

        System.out.println(getMiddle(head));
    }
}
```
tab: Python
```python
# Python program to illustrate how to find the middle element
# by using Floyd's Cycle Finding Algorithm

class Node:
    def __init__(self, x):
        self.data = x
        self.next = None

# Function to get the middle of the linked list
def getMiddle(head):

    # Initialize the slow and fast pointer to the
    # head of the linked list
    slow_ptr = head
    fast_ptr = head

    while fast_ptr is not None and fast_ptr.next is not None:

        # Move the fast pointer by two nodes
        fast_ptr = fast_ptr.next.next

        # Move the slow pointer by one node
        slow_ptr = slow_ptr.next

    # Return the slow pointer which is currently pointing to the
    # middle node of the linked list
    return slow_ptr.data

def main():

    # Create a hard-coded linked list:
    # 10 -> 20 -> 30 -> 40 -> 50 -> 60
    head = Node(10)
    head.next = Node(20)
    head.next.next = Node(30)
    head.next.next.next = Node(40)
    head.next.next.next.next = Node(50)
    head.next.next.next.next.next = Node(60)

    print(getMiddle(head))

if __name__ == "__main__":
    main()
```
tab: Javascript
```javascript
// Javascript program to illustrate how to find the middle
// element by using Floyd's Cycle Finding Algorithm

class Node {
    constructor(new_data) {
        this.data = new_data;
        this.next = null;
    }
}

// Function to get the middle of the linked list
function getMiddle(head) {

    // Initialize the slow and fast pointer to the head of
    // the linked list
    let slow_ptr = head;
    let fast_ptr = head;

    while (fast_ptr !== null && fast_ptr.next !== null) {

        // Move the fast pointer by two nodes
        fast_ptr = fast_ptr.next.next;

        // Move the slow pointer by one node
        slow_ptr = slow_ptr.next;
    }

    // Return the slow pointer which is currently pointing
    // to the middle node of the linked list
    return slow_ptr.data;
}

function main() {

    // Create a hard-coded linked list:
    // 10 -> 20 -> 30 -> 40 -> 50 -> 60
    const head = new Node(10);
    head.next = new Node(20);
    head.next.next = new Node(30);
    head.next.next.next = new Node(40);
    head.next.next.next.next = new Node(50);
    head.next.next.next.next.next = new Node(60);

    console.log(getMiddle(head));
}

main();
```
tab: C#
```csharp
// C# program to illustrate how to find the middle element
// by using Floyd's Cycle Finding Algorithm
using System;

class Node {
    public int data;
    public Node next;
    public Node(int x) {
        this.data = x;
        this.next = null;
    }
}

class GfG {

    // Function to get the middle of the linked list
    static int getMiddle(Node head) {

        // Initialize the slow and fast pointer to the head
        // of the linked list
        Node slow_ptr = head;
        Node fast_ptr = head;

        while (fast_ptr != null && fast_ptr.next != null) {

            // Move the fast pointer by two nodes
            fast_ptr = fast_ptr.next.next;

            // Move the slow pointer by one node
            slow_ptr = slow_ptr.next;
        }

        // Return the slow pointer which is currently
        // pointing to the middle node of the linked list
        return slow_ptr.data;
    }

      // Driver code
    static void Main() {

        // Create a hard-coded linked list:
        // 10 -> 20 -> 30 -> 40 -> 50 -> 60
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(50);
        head.next.next.next.next.next = new Node(60);

        Console.WriteLine(getMiddle(head));
    }
}
```
````
**Output**
```
Middle Value of Linked List is: 40
```
**Time Complexity:** O(n), where n is the number of nodes in the linked list.
**Auxiliary Space:** O(1)