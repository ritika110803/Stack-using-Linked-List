C Program: Stack Implementation Using Linked List

This project demonstrates how to implement a *Stack Data Structure using a Linked List* in C.

Unlike the array implementation, this version allows *dynamic memory allocation*, meaning the stack can grow until system memory is exhausted.

---

Description

The program:

* Defines a stack using a struct Node
* Implements:

  * *Push operation*
  * *Pop operation*
  * *Display operation*
* Handles:

  * *Stack Overflow* (when memory is unavailable)
  * *Stack Underflow* (when stack is empty)
* Uses dynamic memory allocation (malloc) and deallocation (free)

This example is ideal for students learning *Stacks and Linked Lists in Data Structures*.

---

Source Code

c

#include <stdio.h>

#include <stdlib.h>

// Define stack node

struct Node {
    int data;
    struct Node* next;
};

struct Node* top = NULL;

// Push operation

void push(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));

    if (newNode == NULL) {
        
        printf("Stack Overflow! Memory not available\n");
        return;
    }

    newNode->data = value;
    newNode->next = top;
    top = newNode;

    printf("%d pushed into stack\n", value);
}

// Pop operation

void pop() {
    if (top == NULL) {
       
        printf("Stack Underflow! Stack is empty\n");
        return;
    }

    struct Node* temp = top;
    printf("%d popped from stack\n", top->data);
    top = top->next;
    free(temp);
}

// Display stack

void display() {
    if (top == NULL) {
        
        printf("Stack is empty\n");
        return;
    }

    struct Node* temp = top;
    printf("Stack elements are:\n");
    while (temp != NULL) {
        printf("%d\n", temp->data);
        temp = temp->next;
    }
}

int main() {
    
    push(10);
    push(20);
    push(30);

    display();

    pop();
    display();

    return 0;
}


---

How to Compile and Run

Using GCC

1. Save the file as stack_linkedlist.c
2. Open terminal or command prompt
3. Compile the program:


gcc stack_linkedlist.c -o stack_linkedlist


4. Run the executable:


./stack_linkedlist


(On Windows, use stack_linkedlist.exe)

---

Sample Output


10 pushed into stack
20 pushed into stack
30 pushed into stack
Stack elements are:
30
20
10
30 popped from stack
Stack elements are:
20
10


---

Concepts Covered

* Stack Data Structure
* Linked List implementation
* Dynamic memory allocation (malloc)
* Memory deallocation (free)
* LIFO (Last In, First Out) principle
* Pointer manipulation

---

How Stack Works (Linked List Version)

* Each new element is inserted at the *top*
* top pointer always points to the most recent element
* On *push*:

  * New node → points to old top
  * Top → updated to new node
* On *pop*:

  * Top node is removed
  * Memory is freed
  * Top moves to next node

This implementation removes the fixed-size limitation of array-based stacks.

---

Time Complexity

* *Push:* O(1)
* *Pop:* O(1)
* *Display:* O(n)

---

Advantages Over Array Implementation

* No fixed size limit
* Better memory utilization
* Grows dynamically

---

⚠️ Recommended Improvements

* Add *peek()* operation
* Make it *menu-driven*
* Free all remaining nodes before program termination
* Add user input functionality

---
