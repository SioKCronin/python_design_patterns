# BFS

## Connected component

A connected component of an undirected graph is a subgraph such that any two nodes in the subgraph are connected to 
each by a path. Interestingly, **strongly** connected component is a subgraph of a directed graph where every node is
reachable from both directions.  

```
def bfs_connected_component(graph, start):
    explored = []
    queue = [start]

    while queue:
        node = queue.pop(0)
        if node not in explored:
            explored.append(node)
            neighbors = graph[node]

            for neighbor in neighbors:
                queue.append(neighbor)
    return explored
```

## Shortest path

```
def bfs_shortest_path(graph, start, goal):
    queue = [[start]]

    while queue:
        path = queue.pop(0)
        node = path[-1]
        if node == goal:
            return path
        for neighbor in graph[node]:
            new_path = list(path)
            new_path.append(neighbor)
            queue.append(new_path)
            
    return "No path connecting"
```
