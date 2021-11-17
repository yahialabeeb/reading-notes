# Trees
* Binary Trees, Binary Search Trees, and K-ary Trees.
## Common Terminology
1. Node - A Tree node is a component which may contain it’s own values, and references to other nodes
2. Root - The root is the node at the beginning of the tree
3. K - A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
4. Left - A reference to one child node, in a binary tree
5. Right - A reference to the other child node, in a binary tree
6. Edge - The edge in a tree is the link between a parent and child node
7. Leaf - A leaf is a node that does not have any children
8. Height - The height of a tree is the number of edges from the root to the furthest leaf

## Traversals
### Depth First
1. Pre-order: root >> left >> right
* Pre-order means that the root has to be looked at first.
``` pseudo 
ALGORITHM preOrder(root)
// INPUT <-- root node
// OUTPUT <-- pre-order output of tree node's values

    OUTPUT <-- root.value

    if root.left is not Null
        preOrder(root.left)

    if root.right is not NULL
        preOrder(root.right)
```
1. In-order: left >> root >> right
``` psuedo 
// INPUT <-- root node
// OUTPUT <-- in-order output of tree node's values

    if root.left is not NULL
        inOrder(root.left)

    OUTPUT <-- root.value

    if root.right is not NULL
        inOrder(root.right)
```

1. Post-order: left >> right >> root
``` pseudo 
ALGORITHM postOrder(root)
// INPUT <-- root node
// OUTPUT <-- post-order output of tree node's values

    if root.left is not NULL
        postOrder(root.left)

    if root.right is not NULL
        postOrder(root.right)

    OUTPUT <-- root.value
```

* The most common way to traverse through a tree is to use recursion.

ALGORITHM preOrder(root)
// INPUT <-- root node
// OUTPUT <-- pre-order output of tree node's values

    OUTPUT <-- root.value

    if root.left is not Null
        preOrder(root.left)

    if root.right is not NULL
        preOrder(root.right)
### Breadth First
* Traditionally, breadth first traversal uses a queue (instead of the call stack via recursion) to traverse the width/breadth of the tree. Let’s break down the process.
``` pseudo 
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console

  Queue breadth <-- new Queue()
  breadth.enqueue(root)

  while breadth.peek()
    node front = breadth.dequeue()
    OUTPUT <-- front.value

    if front.left is not NULL
      breadth.enqueue(front.left)

    if front.right is not NULL
      breadth.enqueue(front.right)
```
## Binary Tree Vs K-ary Trees

* Trees can have any number of children per node, but Binary Trees restrict the number of children to two (hence our left and right children).

## K-ary Trees
* If Nodes are able have more than 2 child nodes, we call the tree that contains them a K-ary Tree. In this type of tree we use K to refer to the maximum number of children that each Node is able to have.

```  
ALGORITHM breadthFirst(root)
// INPUT  <-- root node
// OUTPUT <-- front node of queue to console

  Queue breadth <-- new Queue()
  breadth.enqueue(root)

  while breadth.peek()
    node front = breadth.dequeue()
    OUTPUT <-- front.value

    for child in front.children
        breadth.enqueue(child)
```
### Adding a node
* It doesn’t matter where a new node gets placed.

* One strategy for adding a new node to a binary tree is to fill all “child” spots from the top down.
* During the traversal, we find the first node that does not have all it’s children filled, and insert the new node as a child. We fill the child slots from left to right.

* In the event you would like to have a node placed in a specific location, you need to reference both the new node to create, and the parent node upon which the child is attached to.

### Big O
* The Big O time complexity for inserting a new node is O(n). 
* Searching for a specific node will also be O(n). 
* The Big O space complexity for a node insertion using breadth first insertion will be O(w), where w is the largest width of the tree.

* A “perfect” binary tree is one where every non-leaf node has exactly two children.

## Binary Search Trees
* A Binary Search Tree (BST) is a type of tree that does have some structure attached to it
### Searching a BST
* Searching a BST can be done quickly, because all you do is compare the node you are searching for against the root of the tree or sub-tree.
## Big O
* The Big O time complexity of a Binary Search Tree’s insertion and search operations is O(height). 
* In the worst case, we will have to search all the way down to a leaf, which will require searching through as many nodes as the tree is tall. 
* In a balanced (or “perfect”) tree, the height of the tree is log(n). In an unbalanced tree, the worst case height of the tree is n.

* **The Big O space complexity of a BST search would be O(1). During a search, we are not allocating any additional space.**