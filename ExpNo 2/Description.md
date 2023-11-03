ExpNo 2 : Implement Breadth First Search Traversal of a Graph
Aim:
To Implement Breadth First Search Traversal of a Graph using Python 3.

Theory:
Breadth-First Traversal (or Search) for a graph is like the Breadth-First Traversal of a tree. The only catch here is that, unlike trees, graphs may contain cycles so that we may come to the same node again. To avoid processing a node more than once, we divide the vertices into two categories:

Visited
Not Visited
A Boolean visited array is used to mark the visited vertices. For simplicity, it is assumed that all vertices are reachable from the starting vertex. BFS uses a queue data structure for traversal.

How does BFS work?
Starting from the root, all the nodes at a particular level are visited first, and then the next level nodes are traversed until all the nodes are visited. To do this, a queue is used. All the adjacent unvisited nodes of the current level are pushed into the queue, and the current-level nodes are marked visited and popped from the queue. Illustration: Let us understand the working of the algorithm with the help of the following example. Step1: Initially queue and visited arrays are empty.

image

Queue and visited arrays are empty initially. Step2: Push node 0 into queue and mark it visited.

image

Push node 0 into queue and mark it visited. Step 3: Remove node 0 from the front of queue and visit the unvisited neighbours and push them into queue.

image

Step 4: Remove node 1 from the front of queue and visit the unvisited neighbours and push them into queue.

image

Step 5: Remove node 2 from the front of queue and visit the unvisited neighbours and push them into queue.

image

Step 6: Remove node 3 from the front of queue and visit the unvisited neighbours and push them into queue. As we can see that every neighbours of node 3 is visited, so move to the next node that are in the front of the queue.

image

Steps 7: Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue. As we can see that every neighbours of node 4 are visited, so move to the next node that is in the front of the queue.

image

Remove node 4 from the front of queue and visit the unvisited neighbours and push them into queue. Now, Queue becomes empty, So, terminate these process of iteration.

Algorithm:
Construct a Graph with Nodes and Edges
Breadth First Uses Queue and iterates through the Queue for Traversal.
Insert a Start Node into the Queue.
Find its Successors Or neighbors and Check whether the node is visited or not.
If Not Visited, add it to the Queue. Else Continue.
Iterate steps 4 and 5 until all nodes get visited, and there are no more unvisited nodes.
Code:
Name: ANISH M J
Register Number:212221230005
from collections import deque
from collections import defaultdict
def bfs(graph,start,visited,path):
    queue = deque()
    path.append(start)
    queue.append(start)
    visited[start] = True
    while len(queue) != 0:
        tmpnode = queue.popleft()
        for neighbour in graph[tmpnode]:
            if visited[neighbour] == False:
                path.append(neighbour)
                queue.append(neighbour)
                visited[neighbour] = True
    return path

graph = defaultdict(list)
v,e = map(int,input().split())
for i in range(e):
    u,v = map(str,input().split())
    graph[u].append(v)
    graph[v].append(u)

start = '0'
path = []
visited = defaultdict(bool)
traversedpath = bfs(graph,start,visited,path)
print(traversedpath)
Output:
image

Result:
Thus,a Graph was constructed and implementation of Breadth First Search for the same graph was done successfully.
