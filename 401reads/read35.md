# Graphs
A graph is a **non-linear** data structure that can be looked at as a collection of vertices (nodes) potentially connected by line segments named edges.

## common terminology:

1. Vertex - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
2. Edge - An edge is a connection between two nodes.
3. Neighbor - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
4. Degree - The degree of a vertex is the number of edges connected to that vertex.
## Directed vs Undirected
### Undirected Graphs
* An Undirected Graph is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.

### Directed Graphs (Digraph)
* Digraph has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.


## Complete vs Connected vs Disconnected

The three different types of graph are completed, connected, and disconnected.

### Complete Graphs
A complete graph is when all nodes are connected to all other nodes.

### Connected
A connected graph is graph that has all of vertices/nodes have at least one edge.

### Disconnected
A disconnected graph is a graph where some vertices may not have edges.


## Acyclic vs Cyclic

### Acyclic Graph
An acyclic graph is a directed graph without cycles.

A cycle is when a node can be traversed through and potentially end up back at itself.

A directed acyclic graph is also called a DAG. This can also be represented as what we know as a tree.

### Cyclic Graphs
A Cyclic graph is a graph that has cycles.

A cycle is defined as a path of a positive length that starts and ends at the same vertex.

## Graph Representation
We represent graphs through:

1. Adjacency Matrix
2. Adjacency List

#### We will represent the following graph as both an Adjacency Matrix and an Adjacency List:

![UndirectedGraph](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/UndirectedGraph.PNG)

### 1. Adjacency Matrix
An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix

Each Row and column represents each vertex of the data structure. The elements of both the column and the row must add up to 1 if there is an edge that connects the two, or zero if there isn’t a connection.

This is what an adjacency matrix looks like:

![AdjMatrix](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjMatrix.PNG)

A few things to note from the above:

1. you can see that Vertex A connects to both Vertex D and Vertex C. To show this, we place a 1 in the position of (a,c) and (a,d).
2. We follow this same pattern for the other vertex’s and where they are connected.
3. If there is not an edge/connection between the vertex’s, we represent this by placing a 0 in the appropriate point of the matrix.

#### Note a sparse graph is when there are very few connections. a dense graph is when there are many connections

### 2. Adjacency List
* **An adjacency list is the most common way to represent graphs.**

* An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.

* Adjacency lists make it easy to view if one vertices connects to another.

* This is what an Adjacency List looks like:

![Adjacency List](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/AdjList.PNG)

### how we will implement this in code:


1. We can visually see that we are working with a collection of some sort. The visual is depicting a Linked List, but you could easily make it an array of arrays if you’d like.
2. Each index or node (depending on the data structure you choose to represent the adjacency list) will be a vertex within the graph.
3. Every time you add an edge, you will find the appropriate vertices in the data structure and add it to the appropriate location.

### Weighted Graphs
A weighted graph is a graph with numbers assigned to its edges. These numbers are called weights. 

## Traversals

## Breadth First
In a breadth first traversal, you are starting at a specific vertex/node. This node must be specified when calling the BreadthFirst() method.
To prevent an infinite loop, we need to have some way to keep track of whether a vertex has been “visited” before. Upon each visit, we’ll add the previously-unvisited vertex to a visited set, so we know not to visit it again as traversal continues.

### The algorithm breadth first traversal looks like:

1. Enqueue the declared start node into the Queue.
2. Create a loop that will run while the node still has nodes present.
3. Dequeue the first node from the queue
4. if the Dequeue‘d node has unvisited child nodes, add the unvisited children to visited set and insert them into the queue.

* This is the code for a breadth first traversal:
```pseudo 
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)   

    return nodes;

``` 
Here is a breakdown of what is going on:

#### note

1. If there are any disconnected nodes (such as islands) with the graph data structure, they will not be traversed.
2. Breadth-first only outputs the nodes that are connected in some relation to the root that you pass in.

### Depth First
In a depth first traversal, we approach it a bit different than the way we do when working with a depth first traversal of a tree. Similar to how the breadth-first uses a queue, we are going to use a Stack for our depth-first traversal.

* The algorithm for a depth first traversal is as follows:

1. Push the root node into the stack
2. Start a while loop while the stack is not empty
3. Peek at the top node in the stack
4. If the top node has unvisited children, mark the top node as visited, and then Push any unvisited children back into the stack.
5. If the top node does not have any unvisited children, Pop that node off the stack
6. repeat until the stack is empty.
## Real World Uses of Graphs

1. GPS and Mapping
1. Driving Directions
1. Social Networks
1. Airline Traffic
1. Netflix uses graphs for suggestions of products

