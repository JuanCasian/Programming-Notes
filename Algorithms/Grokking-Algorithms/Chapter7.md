- [Weighted Graphs](#weighted-graphs)
- [Dijkstra's Algorithm](#dijkstras-algorithm)
    - [Implementation](#implementation)

## Weighted Graphs
- Graphs in which the edges have values
    - Ex: Maps of places where the edges have the distance between each other, so if you want to go from one place to another you want to find not the path with least nodes, but the one shortest

## Dijkstra's Algorithm
- Algorithm used with weighted graphs to find the minimized path
    - Ex: get somewhere in the quickest route
- This algorithm only works with directed acyclic graphs
    - no graphs with cycles
- You can **NOT** use this algorithm with negative weighted edges
    - For negatively weighted graphs use Bellman-Ford algorithm
- This algorithm searches the fastest path to all nodes in the graph from a beginning so you can get them at the end

**Note: A cyclic graph is a graph that creates a loop between nodes**

1. Find the cheapest node
2. Find how much does it cost to get to its neighbors
3. Find the next cheapest node that you have not checked before and repeat step 2
4. Keep doing it until you visit all nodes

### Implementation
- You use hashtables to save the nodes so you can travel through them easily
- You need to keep track of the next variables per node:
    - Parents
    - Costs
    - Cost of the edge

```
def get_lowest_cost_node(hashT):
    lowest_cost = float("inf")
    lowest_cost_node = None
    for node_key in hashT.keys():
        cost = hashT[node_key].current_cost
        if (cost < lowest_cost and hashT[node_key].checked is False):
            lowest_cost = hashT[node_key].current_cost
            lowest_cost_node = hashT[node_key]
    return lowest_cost_node

def get_shortest_path(hashT, start, end):
    node = start
    node.current_cost = 0
    while node is not None:
        cost = node.current_cost
        neighbors = node.neighbors
        for n in neighbors.keys():
            new_cost = cost + neighbors[n]
            if (hashT[n].current_cost > new_cost):
                hashT[n].current_cost = new_cost
                hashT[n].parent = node
        node.checked = True
        node = get_lowest_cost_node(hashT)
    path = []
    while (end):
        path = [end.label] + path
        end = end.parent
    return path
```
