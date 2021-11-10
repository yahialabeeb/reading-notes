# Stacks and Queues
## Stack
### What is a Stack
* A stack is a data structure that consists of Nodes. Each Node references the next Node in the stack, but does not reference its previous.

### Common terminology for a stack is

1. Push - Nodes or items that are put into the stack are pushed
* O(1) operation

* Assigning it as the new top, with its next property equal to the original top.

2. Pop - Nodes or items that are removed from the stack are popped. 

* Removing a Node from the top.
* O(1) operation
3. op - This is the top of the stack.
4. Peek - When you peek you will view the value of the top Node in the stack. 
* Getting the value of top Node in stack
5. IsEmpty - returns true when stack is empty otherwise returns false.

## Stacks follow concepts:
1. FILO
* First In Last Out => This means that the first item added in the stack will be the last item popped out of the stack.
2. LIFO
* Last In First Out => This means that the last item added to the stack will be the first item popped out of the stack.

## What is a Queue?

1. Enqueue - Nodes or items that are added to the queue.
* O(1) operation
2. Dequeue - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
3. Front - This is the front/first Node of the queue.
4. Rear - This is the rear/last Node of the queue.
5. Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
6. IsEmpty - returns true when queue is empty otherwise returns false

## Queues follow these concepts:
1. FIFO
* First In First Out => This means that the first item in the queue will be the first item out of the queue.

2. LILO
* Last In Last Out => This means that the last item in the queue will be the last item out of the queue.
