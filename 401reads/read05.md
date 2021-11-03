# linked List
## introduction 
> A Linked List is a sequence of Nodes that are connected/linked to each other. The most defining feature of a      Linked List is that each Node references the next Node in the link 
> There are two types of Linked List - Singly and Doubly. We will be implementing a Singly Linked List in this implementation.

- Linked List - A data structure that contains nodes that links/points to the next node in the list.
- Singly - Singly refers to the number of references the node has. A Singly linked list means that there is only one reference, and the reference points to the Next node in a linked list.
- Doubly - Doubly refers to there being two (double) references within the node. A Doubly linked list means that there is a reference to both the Next and Previous node.
- Node - Nodes are the individual items/links that live in a linked list. Each node contains the data for each link.
- Next - Each node contains a property called Next. This property contains the reference to the next node.
- Head - The Head is a reference of type Node to the first node in a linked list.
- Current - The Current is a reference of type Node to the node that is currently being looked at. When traversing, you create a new Current variable at the Head to guarantee you are starting from the beginning of the linked list

## Traversal
- Can't use foreach or for loop.
- The Next property is exceptionally important because it will lead us where the next node is
- The best way to approach a traversal is through the use of a while() loop.
- while loop will tell us when we get null (end of the list)
- urrent variable will tell us where exactly in the linked list 

## ALGORITHM

ALGORITHM Includes (value)
// INPUT <-- integer value
// OUTPUT <-- boolean

  Current <-- Head

  WHILE Current is not NULL
    IF Current.Value is equal to value
      return TRUE

    Current <-- Current.Next

  return FALSE

* In this algorithm:
 * Once we are in the while loop, we are checking if the value of the current node is equal to the value we are looking for
 * we will move Current to the next node that is being referenced and looping inside while
 * Once we hit the end, we know that we did not find the value and return true at any point, so the value is not in the LinkedList. We return false.

# Big O
## what is Big O
* Big O(oh) notation is used to describe the efficiency of an algorithm or function.
* This efficiency is evaluated based on 2 factors:

 1. Running Time (also known as time efficiency / complexity) The amount of time a function needs to complete.

 2. Memory Space (also known as space efficiency / complexity) The amount of memory resources a function uses to store data and instructions.
## Input Size
Input Size refers to the size of the parameter values, We will use the letter n to refer to the Input Size value

### In order to quantify the Running Time in our analysis:
 1. The time in milliseconds from the start of a function execution until it ends.
   * individual run times depending on how  powerful machines are.
 2. The number of operations that are executed.
 3. The number of “Basic Operations” that are executed.


### In order to quantify Memory Space, we can consider Four Sources of Memory Usage during function run-time:
 1. The amount of space needed to hold the code for the algorithm.
 2. The amount of space needed to hold the input data.
 3. The amount of space needed for the output data.
 4. The amount of space needed to hold working space during the calculation.


