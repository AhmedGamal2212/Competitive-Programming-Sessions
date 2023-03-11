# Graph Theory

Graph theory is a very important topic in competitive programming. It is the study of graphs, which are mathematical structures used to model pairwise relations between objects. In computer science, graphs are used to represent networks of communication, data organization, computational devices, the flow of computation, among others. Graphs have a wide variety of applications in computer science, and understanding them is crucial for success in competitive programming.

## Basic Graph Terminology

Before diving into graph theory algorithms and implementations, it's important to understand the basic graph terminology. This terminology provides the foundation for working with graphs.

- **Vertex (Node):** A data object that represents a point in the graph. It is usually represented by a circle. Vertices are the building blocks of graphs.
- **Edge:** A connection between two vertices. It is usually represented by a line. Edges are the links that connect vertices in a graph.
- **Directed Graph:** A graph where edges have a direction. The edges are represented by arrows pointing from one vertex to another. Directed graphs are used in many applications, such as representing the flow of data or traffic.
- **Undirected Graph:** A graph where edges do not have a direction. The edges are represented by lines connecting two vertices. Undirected graphs are simpler than directed graphs, but they are still quite useful.
- **Weighted Graph:** A graph where edges have a weight or cost associated with them. Weighted graphs are used to model many real-world problems, such as the shortest path between two points in a network.
- **Degree:** The number of edges that are connected to a vertex. The degree of a vertex is an important characteristic of a graph.

## Graph Implementation

There are several ways to implement a graph in competitive programming. One common way is to use an adjacency matrix. An adjacency matrix is a two-dimensional array where each row and column represents a vertex, and the entries represent the edges between them. If the graph is weighted, the entries can represent the weights of the edges. Using an adjacency matrix to represent a graph has some advantages, such as constant-time edge lookup and easy graph traversal.

```cpp
const int MAXN = 1000; // Maximum number of vertices
int adjMatrix[MAXN][MAXN];

void addEdge(int u, int v, int w) {
    adjMatrix[u][v] = w;
    // For an undirected graph, add the following line
    // adjMatrix[v][u] = w;
}

```

Another way to implement a graph is to use an adjacency list. An adjacency list is an array of linked lists, where each element represents a vertex, and the linked list contains the vertices that are connected to it. If the graph is weighted, the linked list can contain pairs of vertices and their corresponding weights. Using an adjacency list to represent a graph has some advantages, such as efficient memory usage and easy addition and removal of edges.

```cpp
const int MAXN = 1000; // Maximum number of vertices
vector<pair<int, int>> adjList[MAXN];

void addEdge(int u, int v, int w) {
    adjList[u].push_back({v, w});
    // For an undirected graph, add the following line
    // adjList[v].push_back({u, w});
}

```

## Is that everything? 
- There's much more to learn about graph theory, and that's precisely what we're here to do together. Explore the sessions, reading and watching materials, and practice problems to fill in the gaps in your understanding of the topic, and acquire new skills and creative solutions to implement your ideas.


## Graph Theory Topics Covered So Far

- [Introduction to Graph Theory](https://github.com/AhmedGamal2212/Competitive-Programming-Sessions/tree/master/Graph%20Theory/Introduction)