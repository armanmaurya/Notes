In this article, the Linked List implementation of the [Queue Data Structure](../Queue%20Data%20Structure.md) is discussed and implemented. Print '-1' if the queue is empty.
**Approach:** To solve the problem follow the below idea:

> [!note] Title
> We maintain two pointers, **front** and **rear**. The front points to the first item of the queue and rear points to the last item.
>- **enQueue():** This operation adds a new node after the rear and moves the rear to the next node.
>- **deQueue():** This operations removes the front node and moves the front to the next node.

Follow the below steps to solve the problem:
- Create a class **QNode** with data members integer data and **QNode*** next
	- A parameterized constructor that takes an integer $x$ value as a parameter and sets data equal to $x$ and next as **NULL**. 
- Create a class Queue with data members QNode front and rear.
- Enqueue Operation with parameter x:
	- Initialize QNode* temp with data = $x$
	- If the rear is set to NULL then set the front and rear to temp and return (Base Case).
	- Else set rear next to temp and then move rear to temp.
- Dequeue Operation:
	- If the front is set to NULL return (Base Case).
	- Initialize QNode temp with front and set front to its next.
	- If the front is equal to NULL then set the rear to NULL
	- Delete temp form memory.
Below is the implementation of the above approach:
````tabs

tab: C++
```cpp
// C++ program to implement the queue data structure using
// linked list
#include <bits/stdc++.h>
using namespace std;

// Node class representing a single node in the linked list
class Node {
public:
    int data;
    Node* next;
    Node(int new_data)
    {
        this->data = new_data;
        this->next = nullptr;
    }
};

// Class to implement queue operations using a linked list
class Queue {

    // Pointer to the front and the rear of the linked list
    Node *front, *rear;

public:
    // Constructor to initialize the front and rear
    Queue() { front = rear = nullptr; }

    // Function to check if hte queu is empty
    bool isEmpty()
    {
        // If the front and rear are null, then the queue is
        // empty, otherwise it's not
        if (front == nullptr) {
            return true;
        }
        return false;
    }

    // Function to add an element to the queue
    void enqueue(int new_data) {

        // Create a new linked list node
        Node* new_node = new Node(new_data);

        // If queue is empty, the new node is both the front
        // and rear
        if (this->isEmpty()) {
            front = rear = new_node;
            return;
        }

        // Add the new node at the end of the queue and
        // change rear
        rear->next = new_node;
        rear = new_node;
    }

    // Function to remove an element from the queue
    void dequeue() {

        // If queue is empty, return
        if (this->isEmpty()) {
            cout << "Queue Underflow\n";
            return;
        }

        // Store previous front and move front one node
        // ahead
        Node* temp = front;
        front = front->next;

        // If front becomes nullptr, then change rear also
        // to nullptr
        if (front == nullptr)
            rear = nullptr;

        // Deallocate memory of the old front node
        delete temp;
    }

    // Function to get the front element of the queue
    int getFront() {
      
      // Checking if the queue is empty
        if (this->isEmpty()) {
            cout << "Queue is empty\n";
            return INT_MIN;
        }
        return front->data;
    }

    // Function to get the rear element of the queue
    int getRear() {

      // Checking if the queue is empty
        if (this->isEmpty()) {
            cout << "Queue is empty\n";
            return INT_MIN;
        }
      
        return rear->data;
    }
};

// Driver code to test the queue implementation
int main()
{
    Queue q;

    // Enqueue elements into the queue
    q.enqueue(10);
    q.enqueue(20);

    // Display the front and rear elements of the queue
    cout << "Queue Front: " << q.getFront() << endl;
    cout << "Queue Rear: " << q.getRear() << endl;

    // Dequeue elements from the queue
    q.dequeue();
    q.dequeue();

    // Enqueue more elements into the queue
    q.enqueue(30);
    q.enqueue(40);
    q.enqueue(50);

    // Dequeue an element from the queue
    q.dequeue();

    // Display the front and rear elements of the queue
    cout << "Queue Front: " << q.getFront() << endl;
    cout << "Queue Rear: " << q.getRear() << endl << endl;

    return 0;
}
```
tab: C
```c
// C program to implement the queue data structure using
// linked list
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>

// Node structure representing a single node in the linked
// list
typedef struct Node {
    int data;
    struct Node* next;
} Node;

// Function to create a new node
Node* createNode(int new_data)
{
    Node* new_node = (Node*)malloc(sizeof(Node));
    new_node->data = new_data;
    new_node->next = NULL;
    return new_node;
}

// Structure to implement queue operations using a linked
// list
typedef struct Queue {

    // Pointer to the front and the rear of the linked list
    Node *front, *rear;
} Queue;

// Function to create a queue
Queue* createQueue()
{
    Queue* q = (Queue*)malloc(sizeof(Queue));
    q->front = q->rear = NULL;
    return q;
}

// Function to check if the queue is empty
int isEmpty(Queue* q)
{

    // If the front and rear are null, then the queue is
    // empty, otherwise it's not
    if (q->front == NULL && q->rear == NULL) {
        return 1;
    }
    return 0;
}

// Function to add an element to the queue
void enqueue(Queue* q, int new_data)
{

    // Create a new linked list node
    Node* new_node = createNode(new_data);

    // If queue is empty, the new node is both the front
    // and rear
    if (q->rear == NULL) {
        q->front = q->rear = new_node;
        return;
    }

    // Add the new node at the end of the queue and
    // change rear
    q->rear->next = new_node;
    q->rear = new_node;
}

// Function to remove an element from the queue
void dequeue(Queue* q)
{

    // If queue is empty, return
    if (isEmpty(q)) {
        printf("Queue Underflow\n");
        return;
    }

    // Store previous front and move front one node
    // ahead
    Node* temp = q->front;
    q->front = q->front->next;

    // If front becomes null, then change rear also
    // to null
    if (q->front == NULL)
        q->rear = NULL;

    // Deallocate memory of the old front node
    free(temp);
}

// Function to get the front element of the queue
int getFront(Queue* q)
{

    // Checking if the queue is empty
    if (isEmpty(q)) {
        printf("Queue is empty\n");
        return INT_MIN;
    }
    return q->front->data;
}

// Function to get the rear element of the queue
int getRear(Queue* q)
{

    // Checking if the queue is empty
    if (isEmpty(q)) {
        printf("Queue is empty\n");
        return INT_MIN;
    }
    return q->rear->data;
}

// Driver code
int main()
{
    Queue* q = createQueue();

    // Enqueue elements into the queue
    enqueue(q, 10);
    enqueue(q, 20);
    
      printf("Queue Front: %d\n", getFront(q));
    printf("Queue Rear: %d\n", getRear(q));

    // Dequeue elements from the queue
    dequeue(q);
    dequeue(q);


    // Enqueue more elements into the queue
    enqueue(q, 30);
    enqueue(q, 40);
    enqueue(q, 50);

    // Dequeue an element from the queue
    dequeue(q);

    printf("Queue Front: %d\n", getFront(q));
    printf("Queue Rear: %d\n", getRear(q));

    return 0;
}
```
tab: Java
```java
// Java program to implement the queue data structure using
// linked list

// Node class representing a single node in the linked list
class Node {
    int data;
    Node next;

    Node(int new_data) {
        this.data = new_data;
        this.next = null;
    }
}

// Class to implement queue operations using a linked list
class Queue {
  
    // Pointer to the front and the rear of the linked list
    Node front, rear;

    // Constructor to initialize the front and rear
    Queue() { front = rear = null; }

    // Function to check if the queue is empty
    boolean isEmpty() {
      
        // If the front and rear are null, then the queue is
        // empty, otherwise it's not
        return front == null && rear == null;
    }

    // Function to add an element to the queue
    void enqueue(int new_data) {
      
        // Create a new linked list node
        Node new_node = new Node(new_data);

        // If queue is empty, the new node is both the front
        // and rear
        if (rear == null) {
            front = rear = new_node;
            return;
        }

        // Add the new node at the end of the queue and
        // change rear
        rear.next = new_node;
        rear = new_node;
    }

    // Function to remove an element from the queue
    void dequeue() {
      
        // If queue is empty, return
        if (isEmpty()) {
            System.out.println("Queue Underflow");
            return;
        }

        // Store previous front and move front one node
        // ahead
        Node temp = front;
        front = front.next;

        // If front becomes null, then change rear also
        // to null
        if (front == null) {
            rear = null;
        }
    }

    // Function to get the front element of the queue
    int getFront() {
      
        // Checking if the queue is empty
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return Integer.MIN_VALUE;
        }
        return front.data;
    }

    // Function to get the rear element of the queue
    int getRear() {
      
        // Checking if the queue is empty
        if (isEmpty()) {
            System.out.println("Queue is empty");
            return Integer.MIN_VALUE;
        }
        return rear.data;
    }
}

// Driver code to test the queue implementation
public class Main {
    public static void main(String[] args) {
        Queue q = new Queue();

        // Enqueue elements into the queue
        q.enqueue(10);
        q.enqueue(20);
      
          System.out.println("Queue Front: " + q.getFront());
        System.out.println("Queue Rear: " + q.getRear());

        // Dequeue elements from the queue
        q.dequeue();
        q.dequeue();

        // Enqueue more elements into the queue
        q.enqueue(30);
        q.enqueue(40);
        q.enqueue(50);

        // Dequeue an element from the queue
        q.dequeue();

        System.out.println("Queue Front: " + q.getFront());
        System.out.println("Queue Rear: " + q.getRear());
    }
}
```
tab: Python
```python
# Python program to implement the queue data structure using
# linked list

# Node class representing a single node in the linked list
class Node:
    def __init__(self, new_data):
        self.data = new_data
        self.next = None

# Class to implement queue operations using a linked list
class Queue:
    def __init__(self):
      
        # Pointer to the front and the rear of the linked list
        self.front = None
        self.rear = None

    # Function to check if the queue is empty
    def is_empty(self):
      
        # If the front and rear are null, then the queue is
        # empty, otherwise it's not
        return self.front is None and self.rear is None

    # Function to add an element to the queue
    def enqueue(self, new_data):
      
        # Create a new linked list node
        new_node = Node(new_data)

        # If queue is empty, the new node is both the front
        # and rear
        if self.rear is None:
            self.front = self.rear = new_node
            return

        # Add the new node at the end of the queue and
        # change rear
        self.rear.next = new_node
        self.rear = new_node

    # Function to remove an element from the queue
    def dequeue(self):
      
        # If queue is empty, return
        if self.is_empty():
            print("Queue Underflow")
            return

        # Store previous front and move front one node
        # ahead
        temp = self.front
        self.front = self.front.next

        # If front becomes null, then change rear also
        # to null
        if self.front is None:
            self.rear = None

    # Function to get the front element of the queue
    def get_front(self):
      
        # Checking if the queue is empty
        if self.is_empty():
            print("Queue is empty")
            return float('-inf')
        return self.front.data

    # Function to get the rear element of the queue
    def get_rear(self):
      
        # Checking if the queue is empty
        if self.is_empty():
            print("Queue is empty")
            return float('-inf')
        return self.rear.data


# Driver code
if __name__ == "__main__":
    q = Queue()

    # Enqueue elements into the queue
    q.enqueue(10)
    q.enqueue(20)

    # Display the front and rear elements of the queue
    print("Queue Front:", q.get_front())
    print("Queue Rear:", q.get_rear())

    # Dequeue elements from the queue
    q.dequeue()
    q.dequeue()

    # Enqueue more elements into the queue
    q.enqueue(30)
    q.enqueue(40)
    q.enqueue(50)

    # Dequeue an element from the queue
    q.dequeue()

    # Display the front and rear elements of the queue
    print("Queue Front:", q.get_front())
    print("Queue Rear:", q.get_rear())
```
tab: Javascript
```javascript
// Javascript program to implement the queue data structure
// using linked list

// Node class representing a single node in the linked list
class Node {
    constructor(new_data)
    {
        this.data = new_data;
        this.next = null;
    }
}

// Class to implement queue operations using a linked list
class Queue {
    constructor()
    {
        // Pointer to the front and the rear of the linked
        // list
        this.front = null;
        this.rear = null;
    }

    // Function to check if the queue is empty
    isEmpty()
    {
        // If the front and rear are null, then the queue is
        // empty, otherwise it's not
        return this.front === null && this.rear === null;
    }

    // Function to add an element to the queue
    enqueue(new_data)
    {
        // Create a new linked list node
        const new_node = new Node(new_data);

        // If queue is empty, the new node is both the front
        // and rear
        if (this.rear === null) {
            this.front = this.rear = new_node;
            return;
        }

        // Add the new node at the end of the queue and
        // change rear
        this.rear.next = new_node;
        this.rear = new_node;
    }

    // Function to remove an element from the queue
    dequeue()
    {
        // If queue is empty, return
        if (this.isEmpty()) {
            console.log("Queue Underflow");
            return;
        }

        // Store previous front and move front one node
        // ahead
        const temp = this.front;
        this.front = this.front.next;

        // If front becomes null, then change rear also
        // to null
        if (this.front === null) {
            this.rear = null;
        }
    }

    // Function to get the front element of the queue
    getFront()
    {
        // Checking if the queue is empty
        if (this.isEmpty()) {
            console.log("Queue is empty");
            return Number.MIN_VALUE;
        }
        return this.front.data;
    }

    // Function to get the rear element of the queue
    getRear()
    {
        // Checking if the queue is empty
        if (this.isEmpty()) {
            console.log("Queue is empty");
            return Number.MIN_VALUE;
        }
        return this.rear.data;
    }
}

// Driver code
const q = new Queue();

// Enqueue elements into the queue
q.enqueue(10);
q.enqueue(20);

// Display the front and rear elements of the queue
console.log("Queue Front:", q.getFront());
console.log("Queue Rear:", q.getRear());

// Dequeue elements from the queue
q.dequeue();
q.dequeue();

// Enqueue more elements into the queue
q.enqueue(30);
q.enqueue(40);
q.enqueue(50);

// Dequeue an element from the queue
q.dequeue();

// Display the front and rear elements of the queue
console.log("Queue Front:", q.getFront());
console.log("Queue Rear:", q.getRear());
```
tab: C#
```csharp
// C# program to implement the queue data structure using
// linked list
using System;

// Node class representing a single node in the linked list
class Node {
    public int data;
    public Node next;

    public Node(int new_data) {
        this.data = new_data;
        this.next = null;
    }
}

// Class to implement queue operations using a linked list
class Queue {
  
    // Pointer to the front and the rear of the linked list
    Node front, rear;

    // Constructor to initialize the front and rear
    public Queue() {
        front = rear = null;
    }

    // Function to check if the queue is empty
    public bool isEmpty() {
      
        // If the front and rear are null, then the queue is
        // empty, otherwise it's not
        return front == null && rear == null;
    }

    // Function to add an element to the queue
    public void enqueue(int new_data) {
      
        // Create a new linked list node
        Node new_node = new Node(new_data);

        // If queue is empty, the new node is both the front
        // and rear
        if (rear == null) {
            front = rear = new_node;
            return;
        }

        // Add the new node at the end of the queue and
        // change rear
        rear.next = new_node;
        rear = new_node;
    }

    // Function to remove an element from the queue
    public void dequeue() {
      
        // If queue is empty, return
        if (isEmpty()) {
            Console.WriteLine("Queue Underflow");
            return;
        }

        // Move front one node
        // ahead
        front = front.next;
        /* No need to manually Deallocate the front */

        // If front becomes null, then change rear also
        // to null
        if (front == null) {
            rear = null;
        }
    }

    // Function to get the front element of the queue
    public int getFront() {
      
        // Checking if the queue is empty
        if (isEmpty()) {
            Console.WriteLine("Queue is empty");
            return int.MinValue;
        }
        return front.data;
    }

    // Function to get the rear element of the queue
    public int getRear() {
        // Checking if the queue is empty
        if (isEmpty()) {
            Console.WriteLine("Queue is empty");
            return int.MinValue;
        }
        return rear.data;
    }
}

// Driver code to test the queue implementation
class Program {
    static void Main(string[] args) {
        Queue q = new Queue();

        // Enqueue elements into the queue
        q.enqueue(10);
        q.enqueue(20);

        Console.WriteLine("Queue Front: " + q.getFront());
        Console.WriteLine("Queue Rear: " + q.getRear());

        // Dequeue elements from the queue
        q.dequeue();
        q.dequeue();

        // Enqueue more elements into the queue
        q.enqueue(30);
        q.enqueue(40);
        q.enqueue(50);

        // Dequeue an element from the queue
        q.dequeue();

        Console.WriteLine("Queue Front: " + q.getFront());
        Console.WriteLine("Queue Rear: " + q.getRear());
    }
}
```
````
**Output**
```
Queue Front: 10
Queue Rear: 20
Queue Front: 40
Queue Rear: 50
```
**Time Complexity:** O(1). The time complexity of both operations enqueue() and dequeue() is O(1) as it only changes a few pointers in both operations.
**Auxiliary Space:** O(1), The auxiliary Space of both operations enqueue() and dequeue() is O(1) as constant extra space is required\.