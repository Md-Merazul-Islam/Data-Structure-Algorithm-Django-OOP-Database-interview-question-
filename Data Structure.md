# Data Structure & Complexity Interview Questions:

## 1. What is time complexity?
Ans: Time complexity describes the efficiency of an algorithm, measuring how execution time grows with the input size. Common time complexities include:

Best case: O(1)
Average case: O(log n)
Worst case: O(N)
## 2. Why do we use time complexity?
Ans: Time complexity helps us understand how efficiently algorithms perform as input size increases. It allows us to compare algorithms, predict performance, and choose the best algorithm for a problem.

## 3. What is the time complexity of the following code?

        cpp
        Copy code
        for(int i = 0; i < n; i++) {
            cout << i << endl;
        }
        Ans: O(N)

## 4. What is the time complexity of this code?

        cpp
        Copy code
        for(int i = N; i > 1; i = i / 2) {
            cout << i << endl;
        }
        Ans: O(log N)

## 5. What is the time complexity of this code?

        cpp
        Copy code
        for(int i = 1; i < n; i = i * 2) {
            cout << i << endl;
        }
        Ans: O(log N)

## 6. What is the time complexity of this code?

        cpp
        Copy code
        for(int i = 1; i * i <= n; i++) {
            if(n % i == 0) {
                cout << i << " ";
                cout << n / i << " ";
            }
        }
        Ans: O(√n)

## 7. What is the time complexity of this code?

        cpp
        Copy code
        int i, j, k = 0;
        for(i = n / 2; i <= n; i++) {
            for(j = 2; j <= n; j *= 2) {
                k = k + n / 2;
            }
        }
        Ans: O(N log N)

## 8. What is space complexity?
Ans: Space complexity measures the amount of memory an algorithm uses relative to the input size. It helps understand how memory usage grows with input size. Typical space complexities:

O(1) - Constant space
O(n) - Linear space
O(n²) - Quadratic space
## 9. What is the time complexity of a linear search algorithm?
i) O(n)
ii) O(log N)
iii) O(n²)
iv) O(N log N)
Ans: i) O(n)

## 10. What is the time complexity of the bubble sort algorithm?
i) O(n)
ii) O(log N)
iii) O(n²)
iv) O(N log N)
Ans: iii) O(n²)

# Linked List Interview Questions:

## 1. What is a linked list?
Ans: A linked list is a linear data structure where each element (node) contains data and a pointer to the next node, forming a chain.

## 2. How many types of Linked Lists exist?
i) 2
ii) 3
iii) 4
iv) 5
Ans: iii) 4

## 3. What is a singly linked list?
Ans: A singly linked list has nodes that contain a data field and a next field, which points to the next node in the sequence.

## 4. How to insert a new node in a singly linked list at the beginning?

        cpp
        Copy code
        void insert_at_head(Node*& head, int v) {
            Node* newNode = new Node(v);
            newNode->next = head;
            head = newNode;
            cout << "Inserted at new head" << endl;
        }
        
## 5. How to insert a new node in a singly linked list at the end?

cpp
Copy code
void insert_at_tail(Node* head, int val) {
    Node* newNode = new Node(val);
    if(head == NULL) {
        head = newNode;
        return;
    }
    Node* tmp = head;
    while(tmp->next != NULL) {
        tmp = tmp->next;
    }
    tmp->next = newNode;
}
## 6. How to insert a new node in a singly linked list at any position?

cpp
Copy code
## void insert_at_any_position(Node* head, int pos, int val) {
    Node* newNode = new Node(val);
    Node* tmp = head;
    for(int i = 1; i <= pos - 1; i++) {
        tmp = tmp->next;
    }
    newNode->next = tmp->next;
    tmp->next = newNode;
}
## 7. How to delete a node from the head in a singly linked list?

cpp
Copy code
void delete_node_at_head(Node*& head) {
    Node* deleteNode = head;
    head = head->next;
    delete deleteNode;
}
## 8. How to delete a node from the tail in a singly linked list?

cpp
Copy code
void delete_node_at_tail(Node*& head) {
    if(head == NULL) {
        cout << "The list is empty!" << endl;
        return;
    }
    Node* tmp = head;
    while(tmp->next->next != NULL) {
        tmp = tmp->next;
    }
    Node* deleteNode = tmp->next;
    delete deleteNode;
    tmp->next = NULL;
}
## 9. How to delete a node from any position in a singly linked list?

cpp
Copy code
void delete_node_at_any_position(Node* head, int pos) {
    Node* tmp = head;
    for(int i = 1; i <= pos - 1; i++) {
        tmp = tmp->next;
    }
    Node* deleteNode = tmp->next;
    tmp->next = tmp->next->next;
    delete deleteNode;
}
## 10. What is a doubly linked list?
Ans: A doubly linked list contains nodes with data and two pointers: one pointing to the previous node and one to the next. This allows traversal in both directions.

## 11. How many fields does a doubly linked list have?
i) One
ii) Two
iii) Three
iv) Four
Ans: iii) Three

## 12. How to insert a new node at the head of a doubly linked list?

cpp
Copy code
void insert_at_head(Node*& head, Node*& tail, int val) {
    Node* newNode = new Node(val);
    if(head == NULL) {
        head = newNode;
        tail = newNode;
        return;
    }
    newNode->next = head;
    head->prev = newNode;
    head = newNode;
}
## 13. How to insert a new node at the tail of a doubly linked list?

cpp
Copy code
void insert_at_tail(Node*& head, Node*& tail, int val) {
    Node* newNode = new Node(val);
    if(head == NULL) {
        head = newNode;
        tail = newNode;
        return;
    }
    newNode->prev = tail;
    tail->next = newNode;
    tail = newNode;
}
## 14. How to insert a new node at any position in a doubly linked list?

cpp
Copy code
void insert_at_any_position(Node*& head, Node*& tail, int pos, int val) {
    Node* newNode = new Node(val);
    Node* tmp = head;
    for(int i = 1; i <= pos - 1; i++) {
        tmp = tmp->next;
    }
    newNode->next = tmp->next;
    tmp->next->prev = newNode;
    tmp->next = newNode;
    newNode->prev = tmp;
}
## 15. How to delete a node at the head of a doubly linked list?

cpp
Copy code
void delete_at_head(Node*& head, Node*& tail) {
    Node* deleteNode = head;
    if(head == tail) {
        head = NULL;
        tail = NULL;
    } else {
        head = head->next;
        head->prev = NULL;
    }
    delete deleteNode;
}
## 16. How to delete a node at the tail of a doubly linked list?

cpp
Copy code
void delete_at_tail(Node*& head, Node*& tail) {
    Node* deleteNode = tail;
    if(head == tail) {
        head = NULL;
        tail = NULL;
    } else {
        tail = tail->prev;
        tail->next = NULL;
    }
    delete deleteNode;
}
## 17. What is the time complexity for inserting a new node at the head of a singly linked list?
i) O(n)
ii) O(1)
iii) O(log n)
iv) O(n log n)
Ans: ii) O(1)

## 18. What happens when you try to access the next node of the last node in a singly linked list?
i) Returns the head node
ii) Returns null (None in Python)
iii) Causes an error
iv) Creates a new node automatically
Ans: ii) Returns null (None)

## 19. What is the primary disadvantage of a singly linked list over a doubly linked list?
Ans: Singly linked lists can only be traversed in one direction, limiting reverse traversal and making operations like deletion from the tail less efficient.

# Stack & Queue Interview Questions:

## 1. What is a stack?
Ans: A stack is a data structure that follows the Last In, First Out (LIFO) principle, where the last element added is the first one to be removed.

## 2. What is a queue?
Ans: A queue is a data structure that follows the First In, First Out (FIFO) principle, where the first element added is the first one to be removed.

## 3. What is the time complexity of pushing an element onto a stack?
i) O(n)
ii) O(1)
iii) O(log n)
iv) O(n log n)
Ans: ii) O(1)

## 4. What is the time complexity of popping an element from a stack?
i) O(n)
ii) O(1)
iii) O(log n)
iv) O(n log n)
Ans: ii) O(1)

## 5. What is a stack overflow?
Ans: A stack overflow occurs when you try to push an element onto a full stack, exceeding its memory capacity.

## 6. What happens when you try to pop an element from an empty stack?
A) Stack Overflow
B) Stack Underflow
C) It returns null
D) It inserts a new element
Ans: B) Stack Underflow

## 7. What is the time complexity of inserting an element into a queue (enqueue)?
i) O(1)
ii) O(n)
iii) O(log n)
iv) O(n log n)
Ans: i) O(1)

## 8. What is the time complexity of removing an element from a queue (dequeue)?
i) O(1)
ii) O(n)
iii) O(log n)
iv) O(n log n)
Ans: i) O(1)

## 9. What happens if we try to remove an element from an empty queue?
A) Queue Overflow
B) Queue Underflow
C) It returns null
D) It inserts a new element
Ans: B) Queue Underflow

## 10. In which scenarios is a stack most useful?
A) When we need to access elements in any order
B) When we need to access the most recently added element first
C) When we need to access the least recently added element first
D) When memory usage must be minimal
Ans: B) When we need to access the most recently added element first

## 11. In which scenarios is a queue most useful?
A) When the last added element should be processed first
B) When the first added element should be processed first
C) When memory usage must be minimal
D) When we need random access to elements
Ans: B) When the first added element should be processed first

