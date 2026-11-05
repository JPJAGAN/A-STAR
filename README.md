<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name:JAGAN J P  </h3>
<h3>Register Number: 212224230099 </h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>

```````
// A* Search Algorithm
1.  Initialize the open list
2.  Initialize the closed list
    put the starting node on the open 
    list (you can leave its f at zero)

3.  while the open list is not empty
    a) find the node with the least f on 
       the open list, call it "q"

    b) pop q off the open list
  
    c) generate q's 8 successors and set their 
       parents to q
   
    d) for each successor
        i) if successor is the goal, stop search
        
        ii) else, compute both g and h for successor
          successor.g = q.g + distance between 
                              successor and q
          successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)
          
          successor.f = successor.g + successor.h

        iii) if a node with the same position as 
            successor is in the OPEN list which has a 
           lower f than successor, skip this successor

        iV) if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)
  
    e) push q on the closed list
    end (while loop)

``````
## PROGRAM: 
```
from collections import defaultdict

H_dist = {}

def aStarAlgo(start_node, stop_node):
    open_set = {start_node}
    closed_set = set()

    g = {start_node: 0}
    parents = {start_node: start_node}

    while open_set:
        n = min(open_set, key=lambda v: g[v] + heuristic(v))

        if n == stop_node:
            path = []
            while parents[n] != n:
                path.append(n)
                n = parents[n]
            path.append(start_node)
            path.reverse()
            print("Path found:", path)
            print("Cost:", g[stop_node])
            return path

        for m, weight in get_neighbors(n):
            new_cost = g[n] + weight

            if m not in g or new_cost < g[m]:
                g[m] = new_cost
                parents[m] = n
                open_set.add(m)
                closed_set.discard(m)

        open_set.remove(n)
        closed_set.add(n)

    print("Path does not exist!")
    return None

def get_neighbors(v):
    return Graph_nodes.get(v, [])

def heuristic(n):
    return H_dist[n]

graph = defaultdict(list)

n, e = map(int, input().split())

for _ in range(e):
    u, v, cost = input().split()
    cost = int(cost)

    graph[u].append((v, cost))
    graph[v].append((u, cost))

for _ in range(n):
    node, h = input().split()
    H_dist[node] = int(h)

Graph_nodes = graph

start = input().strip()
goal = input().strip()

aStarAlgo(start, goal)
```
## Sample Graph I
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/b1377c3f-011a-4c0f-a843-516842ae056a)

## Sample Graph II</h2>
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/acbb09cb-ed39-48e5-a59b-2f8d61b978a3)

## OUTPUT:

<img width="1277" height="892" alt="image" src="https://github.com/user-attachments/assets/3469093c-9e85-4d97-baf0-aa39839427b4" />

## RESULT:
Thus a graph was constructed and implemantation of A star Search for the same graph was done successfully.
