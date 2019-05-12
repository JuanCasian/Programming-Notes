- [Graphs](#graphs)
    - [What is it?](#what-is-it)
- [Implementing a graph in python](#implementing-a-graph-in-python)
- [Breadth-first search](#breadth-first-search)
    - [Implementation](#implementation)
    - [Time complexity](#time-complexity)
- [Queues](#queues)

## Graphs

### What is it?
- Is a data structure that models a set of connections.
- Graphs are made of:
    - nodes ()
    - edges ->
- Nodes conected together are called neighbors

## Implementing a graph in python
- You create a hashtable in each node to show the connection between each node
```
graph = {}
graph[“you”] = [“alice”, “bob”, “claire”] //Entry of graph with you
graph[“bob”] = [“anuj”, “peggy”]
graph[“alice”] = [“peggy”]
graph[“claire”] = [“thom”, “jonny”]
graph[“anuj”] = []
graph[“peggy”] = []
graph[“thom”] = []
graph[“jonny”] = []
```
- This code shows the implementation of a directed graph because only you are neighbor of the other, but the other is not a neighbor of you
- Undirected graphs are both wayas and don't have arrows

## Breadth-first search
- Search algorithm for graphs
- Answers 2 main type of questions:
    - Is there a path from node A to node B?
    - What is the shortest path form node A to node B?
- Checks first the closest connections to the source and then starts going to outer levels, but always finishing with the previous degree of closeness before going to the next one.
- Uses a **queue** to do this

### Implementation
- You use a parent variable to check from which node you came from
- You want to put a variable as checked so that you don't check the same twice
- The checked variable is what allows a unidirectional graph to be searched with this algorithm becuse it will keep you from doing an infinite loop
1. Keep a queue ocntainning the people to check
2. pop a node off the queue
3. check if the node was **not** checked before
4. check if that node has the answer
    1. If so return the answer
    2. If not mark the node as checked and add the neighbors of the node to the queue
5. Loop
6. If the queue is empty then the answer is not present in the graph

```
from collections import deque

class Node:
    def __init__(self, value, neighbors):
         self.val = value
         self.neighbors = neighbors
         self.parent = None
         self.checked = False

    def print_neighbors(self):
        for node in self.neighbors:
            print('Node Value: {}, node object: {}'.format(node.val, node))



def bread_first_search(start_node, val):
    search_queue = deque()
    search_queue.append(start_node)
    while (search_queue):
        current_node = search_queue.popleft()
        if (current_node.val == val):
            return current_node
        elif (current_node.checked == False):
            for node in current_node.neighbors:
                if (node.parent == None):
                    node.parent = current_node
                search_queue.append(node)
        current_node.checked = True
    return False

```
### Time complexity
$$O(V + E)$$
$$ V = Vertices(Nodes); E = Edges$$


## Queues
- List of things
- FIFO - First in First out