# Ex. No: 17A - Adjacency List Representation of a Graph
# AIM:
To write a Python program to demonstrate the adjacency list representation of the given graph.

# ALGORITHM:
Step 1: Start the program.

Step 2: Define a class AdjNode to create a node for each adjacent vertex:

Store the vertex number. Store the link to the next adjacent node. Step 3: Define a class Graph to create the graph using adjacency lists:

Initialize the number of vertices. Create a list (array) of size V, where each element is initially None. Step 4: Define a method add_edge(src, dest) to:

Add dest to the adjacency list of src. Add src to the adjacency list of dest (for undirected graphs). Step 5: Define a method print_graph() to:

Traverse the adjacency list of each vertex. Print the vertex and its adjacent nodes. Step 6: In the main program:

Create a Graph object with V vertices. Call add_edge() for all desired edges. Call print_graph() to display the adjacency list. Step 7: End the program.

# PYTHON PROGRAM
```
class AdjNode:
	def __init__(self, data):
		self.vertex = data
		self.next = None

class Graph:
	def __init__(self, vertices):
		self.V = vertices
		self.graph = [None] * self.V

	def add_edge(self, src, dest):

		node = AdjNode(dest)
		node.next = self.graph[src]
		self.graph[src] = node

		node = AdjNode(src)
		node.next = self.graph[dest]
		self.graph[dest] = node

	
	def print_graph(self):
	    for i in range(V):
	        print(f"Adjacency list of vertex {i}\n head ", end="")
	        temp=self.graph[i]
	        while temp:
	            print(f"-> {temp.vertex} ", end="")
	            temp=temp.next
	        print("\n")

if __name__ == "__main__":
	V = 5
	graph = Graph(V)
	graph.add_edge(0, 1)
	graph.add_edge(0, 4)
	graph.add_edge(1, 2)
	graph.add_edge(1, 3)
	graph.add_edge(1, 4)
	graph.add_edge(2, 3)
	graph.add_edge(3, 4)

	graph.print_graph()
```
# OUTPUT
<img width="717" height="420" alt="image" src="https://github.com/user-attachments/assets/060592e3-b3d3-4eab-a6ea-ea8acebf8c6d" />

# RESULT
Hence, The program is successfully executed and the adjacency list representation of the given graph is verified.

# Ex. No: 17B - BFS Traversal from a Given Source Vertex
# AIM:
To write a Python program to print BFS traversal from a given source vertex.

# ALGORITHM:
Step 1: Start the program.

Step 2: Create a graph using adjacency list representation.

Step 3: Add edges between vertices using the addEdge() method.

Step 4: Implement the BFS() function:

Initialize all vertices as not visited. Use a queue to track vertices for traversal. Mark the starting vertex as visited and enqueue it. Dequeue a vertex, process it, and enqueue all its adjacent unvisited vertices while marking them as visited. Step 5: Input the starting vertex and perform BFS traversal from it.

Step 6: Print the vertices in BFS order.

Step 7: End the program.

# PYTHON PROGRAM
```
from collections import defaultdict

class Graph:

	def __init__(self):

		self.graph = defaultdict(list)
	def addEdge(self,u,v):
		self.graph[u].append(v)

	def BFS(self, s):
		visited = [False] * (max(self.graph) + 1)
		queue = []

		queue.append(s)
		visited[s] = True
		while queue:
		    s=queue.pop(0)
		    print(s, end=' ')
		    for i in self.graph[s]:
		        if visited[i]==False:
		            queue.append(i)
		            visited[i]=True

n=int(input())
g = Graph()
g.addEdge(0, 1)
g.addEdge(0, 2)
g.addEdge(1, 2)
g.addEdge(2, 0)
g.addEdge(2, 3)
g.addEdge(3, 3)

print ("Following is Breadth First Traversal"
				" (starting from vertex {})".format(n))
g.BFS(n)
```
# OUTPUT
<img width="1174" height="213" alt="image" src="https://github.com/user-attachments/assets/f75fec9b-9731-460e-bdbf-0981edb0e531" />

# RESULT
Hence, The program is successfully executed and the Breadth First Search (BFS) traversal from the given source vertex is verified.

# Ex. No: 17C - DFS Traversal from a Given Source Vertex
# AIM:
To write a Python program to print DFS traversal from a given source vertex.

# ALGORITHM:
Step 1: Start the program.

Step 2: Create a graph using adjacency list representation.

Step 3: Add edges between vertices using the addEdge() method.

Step 4: Implement the DFSUtil() function to recursively visit and print each unvisited vertex:

Mark the current vertex as visited. Recursively call DFSUtil for each unvisited adjacent vertex. Step 5: In the DFS() function:

Initialize an empty set for visited vertices. Call DFSUtil() starting from the given vertex. Step 6: Input the starting vertex and perform DFS traversal.

Step 7: Print the vertices in DFS order.

Step 8: End the program.

# PYTHON PROGRAM
from collections import defaultdict
```
class Graph:
	def __init__(self):

		self.graph = defaultdict(list)

	def addEdge(self, u, v):
		self.graph[u].append(v)

	def DFSUtil(self, v, visited):

		visited.add(v)
		print(v, end=' ')
		for neighbour in self.graph[v]:
		    if neighbour not in visited:
		        self.DFSUtil(neighbour, visited)

	def DFS(self, v):
		visited = set()
		self.DFSUtil(v, visited)

n=int(input())
g = Graph()
g.addEdge(0, 1)
g.addEdge(0, 2)
g.addEdge(1, 2)
g.addEdge(2, 0)
g.addEdge(2, 3)
g.addEdge(3, 3)

print("Following is DFS from (starting from vertex {})".format(n))
g.DFS(n)
```
# OUTPUT
<img width="1003" height="215" alt="image" src="https://github.com/user-attachments/assets/fa49a036-bd88-4bce-9aa2-0cc52685692b" />

# RESULT
Hence, The program is successfully executed and the Depth First Search (DFS) traversal from the given source vertex is verified.

# Ex. No: 17D - Generate a Graph for a Given Fixed Degree Sequence
# AIM:
To write a Python program to generate a graph for a given fixed degree sequence.

# ALGORITHM:
Step 1: Start the program.

Step 2: Check if the sum of the degree sequence is even.

(A necessary condition for the sequence to be graphical.)

If not even, print an error message and exit the program. Step 3: Use the Havel-Hakimi algorithm to determine whether a simple graph can be constructed from the sequence, and to generate the graph.

Step 4: If the graph is successfully created, visualize it using a graph drawing function (e.g., networkx.draw()).

Step 5: End the program.

# PYTHON PROGRAM
```
def printMat(degseq, n):

	mat = [[0] * n for i in range(n)]

	for i in range(n):
		for j in range(i + 1, n):

			if (degseq[i]>0 and degseq[j] > 0):
				degseq[i] -= 1
				degseq[j] -= 1
				mat[i][j] = 1
				mat[j][i] = 1

	print("      ", end ="")
	for i in range(n):
		print(" ", "(", i, ")", end ="")
	print()
	print()
	for i in range(n):
		print("  ", "(", i, ")", end = " ")
		for j in range(n):
			print("  ", mat[i][j], end = " ")
		print()

degseq=[]
for i in range(0, 5):
    ele = int(input())
  
    degseq.append(ele)
#degseq =[v0,v1,v2,v3,v4]

n = len(degseq)
printMat(degseq, n)
```
# OUTPUT
<img width="863" height="264" alt="image" src="https://github.com/user-attachments/assets/d6e746ab-6581-4cef-926b-91d93f9781c2" />

# RESULT
Hence, The program is successfully executed and a simple graph has been generated for the given fixed degree sequence.

# Ex. No: 17E - Topological Sorting of a DAG
# AIM:
To write a Python program to print topological sorting of a Directed Acyclic Graph (DAG).

# ALGORITHM:
Step 1: Create a graph and add edges to represent relationships between nodes.

Step 2: Use a visited set to keep track of visited nodes and a stack (or list) to record the order of nodes after processing.

Step 3: Perform DFS for each unvisited node:

Explore all its neighbors. Recursively apply DFS to each unvisited adjacent node. After all neighbors are visited, push the current node onto the stack. Step 4: After DFS is complete for all nodes, the stack will contain nodes in reverse order of their completion time.

Step 5: Print the stack in reverse to get the topological order.

# PYTHON PROGRAM
```
def addEdge(u, v):
	global adj
	adj[u].append(v)

def DFS(v):
	global visited, departure, time
	visited[v] = 1
	for i in adj[v]:
		if visited[i] == 0:
			DFS(i)
	departure[time] = v
	time += 1

def topologicalSort():
    for i in range(V):
        if visited[i]==0:
            DFS(i)
    for i in range(V-1, -1, -1):
        print(departure[i], end=" ")

if __name__ == '__main__':

	V,time, adj, visited, departure = 6, 0, [[] for i in range(7)], [0 for i in range(7)],[-1 for i in range(7)]
	addEdge(5, 2)
	addEdge(5, 0)
	addEdge(4, 0)
	addEdge(4, 1)
	addEdge(2, 3)
	addEdge(3, 1)

	print("Topological Sort of the given graph is")
	topologicalSort()
```
# OUTPUT
<img width="764" height="149" alt="image" src="https://github.com/user-attachments/assets/a10fd279-b7e6-4cc8-bd64-8ce03951b39a" />

# RESULT
Hence, The program is successfully executed and the topological sorting of the given Directed Acyclic Graph (DAG) is verified.

