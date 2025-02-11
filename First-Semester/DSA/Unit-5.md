# Unit-5

## **Hashing**

Hashing is a technique used in data structures to map keys to values using a function called a **hash function**. It enables efficient data retrieval, insertion, and deletion.

### **1. Hash Table**

A **hash table** is a data structure that stores key-value pairs using a **hash function** to compute an index into an array of buckets or slots. This index determines where the value will be stored.

**Advantages of Hash Tables:**

- **Fast lookups**: \( O(1) \) on average.
- **Efficient insertions and deletions**: \( O(1) \) in the best case.
- **Flexible size**: Can dynamically resize in some implementations.

**Disadvantages:**

- **Collisions**: When multiple keys hash to the same index.
- **Memory consumption**: Extra space may be needed.

### **2. Hash Function**

A **hash function** is a function that converts an input (key) into a fixed-size number, usually an index in an array.

#### **Properties of a Good Hash Function**

- **Deterministic**: Same input should always produce the same output.
- **Uniform Distribution**: Should distribute keys evenly across the table.
- **Fast Computation**: Should be efficient to compute.
- **Minimize Collisions**: Reduce instances where different keys produce the same hash value.

#### **Common Hash Functions**

1. **Modulo Division**: `hash(key) = key % table_size`
2. **Multiplication Method**: `hash(key) = floor(table_size * (key * A % 1))` where `A` is a constant.
3. **Universal Hashing**: Uses randomization to minimize collisions.

### **3. Collision Resolution Techniques**

Collisions occur when multiple keys hash to the same index. There are two primary ways to handle them:

#### **A. Chaining (Separate Chaining)**

In **chaining**, each index in the hash table points to a linked list (or other data structure like a BST) that stores all the keys that hash to the same value.

**Advantages:**

- Handles collisions efficiently.
- Can store more elements than the table size.
- Simple implementation.

**Disadvantages:**

- Extra memory needed for pointers in linked lists.
- Performance degrades if chains become too long (linked list becomes a bottleneck).

#### **B. Open Addressing**

In **open addressing**, all keys are stored directly in the hash table, and if a collision occurs, a probing sequence is used to find the next available slot.

### **Types of Probing in Open Addressing:**

1. **Linear Probing**: If a collision occurs, check the next available slot (index = `(hash + i) % table_size`).
   - Simple but suffers from **primary clustering** (contiguous occupied slots).
2. **Quadratic Probing**: Uses a quadratic function to resolve collisions (index = `(hash + i²) % table_size`).

   - Reduces clustering but may not use all slots effectively.

3. **Double Hashing**: Uses a second hash function to determine the probing step (index = `(hash1 + i * hash2) % table_size`).
   - Minimizes clustering and provides a better distribution.

#### **Advantages of Open Addressing:**

- No extra memory required for pointers (better cache performance).
- Works well for fixed-size hash tables.

#### **Disadvantages:**

- Performance degrades as the table fills up.
- Deletion is complex (requires special handling like marking deleted slots).

### **Comparison: Chaining vs. Open Addressing**

| Feature           | Chaining                         | Open Addressing                    |
| ----------------- | -------------------------------- | ---------------------------------- |
| Space Efficiency  | Uses extra memory for pointers   | Uses table space only              |
| Performance       | Good when load factor is high    | Degrades as table fills up         |
| Deletion          | Simple (remove from linked list) | Complex (requires special markers) |
| Cache Performance | Worse (due to pointers)          | Better (locality of reference)     |

### **Conclusion**

- **Use chaining** when the table may grow dynamically or when deletions are frequent.
- **Use open addressing** when memory is limited, and you need better cache efficiency.

### Built-In Map

```cpp
#include <iostream>
#include <map>
using namespace std;

int main()
{
    map<int, int> mp;
    mp[1] = 1;
    mp[2] = 2;
    mp[3] = 3;
    mp[4] = 4;
    mp[5] = 5;
    mp[6] = 6;

    for (auto it : mp)
        cout << it.first << " " << it.second << endl;

    mp.erase(4);
    cout << "4 is erased" << endl;
    for (auto it : mp)
        cout << it.first << " " << it.second << endl;

    return 0;
}

```

---

## **Graphs: Terminology and Representation**

A **graph** is a data structure that consists of **vertices (nodes)** and **edges (connections between nodes)**. Graphs are widely used in computer science, from social networks to routing algorithms.

### **1. Graph Terminology**

#### **Basic Components**

- **Vertex (Node)**: A fundamental unit of a graph.
- **Edge (Link)**: A connection between two vertices.
- **Weight**: A value assigned to an edge (in weighted graphs).
- **Degree**: The number of edges connected to a vertex.

#### **Types of Graphs**

1. **Directed Graph (Digraph)**: Edges have a direction (e.g., A → B).
2. **Undirected Graph**: Edges have no direction (e.g., A — B).
3. **Weighted Graph**: Edges have weights/costs (e.g., road distances).
4. **Unweighted Graph**: All edges are considered equal.
5. **Cyclic Graph**: Contains cycles (a path that returns to a previous vertex).
6. **Acyclic Graph**: Has no cycles (e.g., trees).
7. **Connected Graph**: All vertices are reachable from any other vertex.
8. **Disconnected Graph**: Some vertices are not connected.

### **2. Graph Representation**

Graphs can be represented in multiple ways, depending on the application:

#### **A. Adjacency Matrix**

A **2D array** where:

- **Rows and columns** represent vertices.
- **A cell (i, j) stores 1 (or weight) if there is an edge from i to j, otherwise 0**.

**Example:**
For a graph with vertices A, B, C:

```
   A  B  C
A  0  1  1
B  1  0  1
C  1  1  0
```

##### **Pros**

✔️ Fast lookup \(O(1)\).  
✔️ Easy to implement.

##### **Cons**

❌ Uses \(O(V^2)\) space, even for sparse graphs.

```cpp
#include <iostream>
#include <queue>
using namespace std;

void printDFS(int **edges, int n, int sv, bool *visited)
{
    cout << sv << " ";
    visited[sv] = true;

    for (int i = 0; i < n; i++)
    {
        if (i == sv)
        {
            continue;
        }

        if (edges[sv][i] == 1)
        {
            if (visited[i])
            {
                continue;
            }
            printDFS(edges, n, i, visited);
        }
    }
}

void printBFS(int **edges, int n, int sv, bool *visited)
{
    queue<int> pending;
    pending.push(sv);
    visited[sv] = true;

    while (pending.size() != 0)
    {
        int temp = pending.front();
        cout << temp << " ";
        pending.pop();

        for (int i = 0; i < n; i++)
        {
            if (i == temp)
            {
                continue;
            }

            if (edges[temp][i] == 1)
            {
                if (visited[i])
                {
                    continue;
                }
                pending.push(i);
                visited[i] = true;
            }
        }
    }
}

void DFS(int **edges, int n, int sv)
{
    bool *visited = new bool[n];
    for (int i = 0; i < n; i++)
    {
        visited[i] = false;
    }

    for (int i = 0; i < n; i++)
    {
        if (!visited[i])
        {
            printDFS(edges, n, i, visited);
            cout << endl;
        }
    }

    delete[] visited;
}

void BFS(int **edges, int n, int sv)
{
    bool *visited = new bool[n];
    for (int i = 0; i < n; i++)
    {
        visited[i] = false;
    }

    for (int i = 0; i < n; i++)
    {
        if (!visited[i])
        {
            printBFS(edges, n, i, visited);
            cout << endl;
        }
    }
    delete[] visited;
}

int main()
{
    int n;
    int e;
    cin >> n >> e;

    int **edges = new int *[n];
    for (int i = 0; i < n; i++)
    {
        edges[i] = new int[n];
        for (int j = 0; j < n; j++)
        {
            edges[i][j] = 0;
        }
    }

    for (int i = 0; i < e; i++)
    {
        int first, second;
        cin >> first >> second;

        edges[first][second] = 1;
        edges[second][first] = 1;
    }

    int sv = 0;
    cout << "DFS" << endl;
    DFS(edges, n, sv);
    cout << "BFS" << endl;
    BFS(edges, n, sv);

    for (int i = 0; i < n; i++)
    {
        delete[] edges[i];
    }

    delete[] edges;

    return 0;
}
```

#### **B. Adjacency List**

A **list of lists (or dictionary)** where:

- Each vertex has a list of its connected vertices.

**Example:**

```
Graph = {
  'A': ['B', 'C'],
  'B': ['A', 'C'],
  'C': ['A', 'B']
}
```

##### **Pros**

✔️ Uses less space \(O(V + E)\).  
✔️ Efficient for sparse graphs.

##### **Cons**

❌ Lookup time is \(O(V)\) in worst case.

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void printDFS(vector<int> adj[], int n, int sv, bool *visited)
{
    cout << sv << " ";
    visited[sv] = true;

    vector<int> temp = adj[sv];
    for (int i = 0; i < temp.size(); i++)
    {
        if (!visited[temp[i]])
        {
            printDFS(adj, n, temp[i], visited);
        }
    }
}

void DFS(vector<int> adj[], int n)
{
    bool *visited = new bool[n];
    for (int i = 0; i < n; i++)
    {
        visited[i] = false;
    }

    for (int i = 0; i < n; i++)
    {
        if (!visited[i])
        {
            printDFS(adj, n, i, visited);
            cout << endl;
        }
    }
}

void printBFS(vector<int> adj[], int n, int sv, bool *visited)
{
    queue<int> pending;
    pending.push(sv);
    visited[sv] = true;

    while (pending.size() != 0)
    {
        int front = pending.front();
        pending.pop();
        vector<int> temp = adj[front];
        cout << front << " ";
        for (int i = 0; i < temp.size(); i++)
        {
            if (!visited[temp[i]])
            {
                pending.push(temp[i]);
                visited[temp[i]] = true;
            }
        }
    }
}

void BFS(vector<int> adj[], int n)
{
    bool *visited = new bool[n];
    for (int i = 0; i < n; i++)
    {
        visited[i] = false;
    }

    for (int i = 0; i < n; i++)
    {
        if (!visited[i])
        {
            printBFS(adj, n, i, visited);
            cout << endl;
        }
    }
}

int main()
{
    int n, e;
    cin >> n >> e;

    vector<int> adj[n];

    for (int i = 0; i < e; i++)
    {
        int f, s;
        cin >> f >> s;

        // Undirected Graph
        adj[f].push_back(s);
        adj[s].push_back(f);

        // Directed Graph
        // adj[f].push_back(s);
    }

    cout << "DFS" << endl;
    DFS(adj, n);

    cout << "BFS" << endl;
    BFS(adj, n);

    return 0;
}
```

#### **C. Edge List**

A **list of edges**, each containing two vertices (and optionally a weight).

**Example:**

```
Edges = [
  ('A', 'B', 1),
  ('A', 'C', 1),
  ('B', 'C', 1)
]
```

##### **Pros**

✔️ Simple to understand.  
✔️ Efficient for edge-centric operations.

##### **Cons**

❌ Slow for adjacency queries.

### **Which Representation to Use?**

| Representation       | Space Complexity | Best For      |
| -------------------- | ---------------- | ------------- |
| **Adjacency Matrix** | \(O(V^2)\)       | Dense Graphs  |
| **Adjacency List**   | \(O(V + E)\)     | Sparse Graphs |
| **Edge List**        | \(O(E)\)         | Edge Queries  |

---

## **Graphs, Multi-Graphs**

A **graph** is a collection of **vertices (nodes)** and **edges (connections between nodes)**. There are different types of graphs based on the structure and properties of edges.

### **Simple Graph**

A **simple graph** is an **undirected graph** where:  
✅ No multiple edges between two vertices.  
✅ No self-loops (edges connecting a vertex to itself).

#### **Example**

```
    A — B
    |   |
    C — D
```

- Vertices: `{A, B, C, D}`
- Edges: `{(A, B), (A, C), (B, D), (C, D)}`

---

### **Multi-Graph**

A **multi-graph** allows:  
✅ **Multiple edges** between two vertices (parallel edges).  
✅ **Self-loops** (an edge connecting a vertex to itself).

#### **Example**

```
    A === B
    |   /
    C — D
```

- Parallel edges: `A === B` (two edges between A and B).
- Self-loop: `C → C` (if present).

#### **Use Cases of Multi-Graphs:**

- **Transportation networks** (multiple roads between cities).
- **Social networks** (multiple types of relationships).

## **Directed Graph (Digraph)**

A **directed graph** (or **digraph**) has **edges with a direction**. Each edge is represented as an **ordered pair (u, v)**, meaning **u → v** (edge goes from u to v).

### **Example of a Directed Graph**

```
    A → B → D
      ↘
        C → D
```

- Vertices: `{A, B, C, D}`
- Directed Edges: `{(A, B), (A, C), (B, D), (C, D)}`

### **Properties of Directed Graphs:**

- **Indegree** of a vertex: Number of incoming edges.
- **Outdegree** of a vertex: Number of outgoing edges.
- **Strongly Connected**: A graph is **strongly connected** if every vertex is reachable from any other vertex.
- **Weakly Connected**: A graph is **weakly connected** if replacing all edges with undirected edges makes it connected.

#### **Examples of Directed Graph Usage:**

- **Web pages** (links between pages).
- **Task scheduling** (dependency graphs).
- **Road maps** (one-way streets).

---

## **Sequential Representation of Graphs & Adjacency Matrix**

Graphs can be represented using various techniques. Two common representations are **sequential representation** and **adjacency matrix representation**.

### **1. Sequential Representation of Graphs**

In sequential representation, we use **arrays (or lists)** to store graph information.

#### **Types of Sequential Representations**

1. **Adjacency Matrix Representation**
2. **Edge List Representation**
3. **Adjacency List Representation** (not strictly sequential but commonly used)

### **2. Adjacency Matrix Representation**

An **adjacency matrix** is a **2D array (matrix)** where:

- **Rows and columns represent vertices.**
- **A cell (i, j) stores 1 (or weight) if there is an edge from vertex i to j, otherwise 0.**

### **Adjacency Matrix for an Undirected Graph**

#### **Example Graph:**

```
    A — B
    |   |
    C — D
```

#### **Adjacency Matrix Representation:**

|     | A   | B   | C   | D   |
| --- | --- | --- | --- | --- |
| A   | 0   | 1   | 1   | 0   |
| B   | 1   | 0   | 0   | 1   |
| C   | 1   | 0   | 0   | 1   |
| D   | 0   | 1   | 1   | 0   |

- **0 means no edge**, **1 means edge exists**
- Symmetric for **undirected graphs**

### **Adjacency Matrix for a Directed Graph**

#### **Example Directed Graph:**

```
    A → B
    ↓   ↓
    C → D
```

#### **Adjacency Matrix Representation:**

|     | A   | B   | C   | D   |
| --- | --- | --- | --- | --- |
| A   | 0   | 1   | 1   | 0   |
| B   | 0   | 0   | 0   | 1   |
| C   | 0   | 0   | 0   | 1   |
| D   | 0   | 0   | 0   | 0   |

- **Asymmetric for directed graphs**
- **A → B (1 at A,B), but not B → A (0 at B,A)**

### **Advantages of Adjacency Matrix**

✅ **Fast lookup \(O(1)\)** for edge existence  
✅ **Simple representation**  
✅ **Works well for dense graphs**

### **Disadvantages of Adjacency Matrix**

❌ **Uses \(O(V^2)\) space**, inefficient for sparse graphs  
❌ **Inefficient for adding/deleting edges**

---

## **Graph Traversals**

Graph traversal is the process of visiting all the vertices of a graph in a systematic manner. There are two main traversal techniques:

1. **Breadth-First Search (BFS)** → Uses a **queue (FIFO)**
2. **Depth-First Search (DFS)** → Uses a **stack (LIFO) or recursion**

### **1. Breadth-First Search (BFS)**

**BFS** explores all neighbors of a node before moving to their neighbors.

- Uses a **queue** for traversal.
- Suitable for **shortest path in an unweighted graph**.

#### **C++ Implementation of BFS**

```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

// Function to perform BFS traversal
void BFS(vector<vector<int>> &adj, int start) {
    int n = adj.size();
    vector<bool> visited(n, false);
    queue<int> q;

    visited[start] = true;
    q.push(start);

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";

        // Explore neighbors
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

int main() {
    int V = 5;  // Number of vertices
    vector<vector<int>> adj(V);

    // Creating an undirected graph
    adj[0] = {1, 2};
    adj[1] = {0, 3, 4};
    adj[2] = {0, 4};
    adj[3] = {1};
    adj[4] = {1, 2};

    cout << "BFS Traversal: ";
    BFS(adj, 0); // Start BFS from node 0

    return 0;
}
```

#### **Output**

```
BFS Traversal: 0 1 2 3 4
```

### **2. Depth-First Search (DFS)**

**DFS** explores as far as possible along a branch before backtracking.

- Uses a **stack** (explicit or recursion).
- Suitable for **pathfinding, topological sorting, and cycle detection**.

#### **C++ Implementation of DFS**

```cpp
#include <iostream>
#include <vector>

using namespace std;

// Function to perform DFS traversal
void DFSUtil(vector<vector<int>> &adj, vector<bool> &visited, int node) {
    visited[node] = true;
    cout << node << " ";

    // Explore neighbors
    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            DFSUtil(adj, visited, neighbor);
        }
    }
}

void DFS(vector<vector<int>> &adj, int start) {
    int n = adj.size();
    vector<bool> visited(n, false);
    DFSUtil(adj, visited, start);
}

int main() {
    int V = 5;  // Number of vertices
    vector<vector<int>> adj(V);

    // Creating an undirected graph
    adj[0] = {1, 2};
    adj[1] = {0, 3, 4};
    adj[2] = {0, 4};
    adj[3] = {1};
    adj[4] = {1, 2};

    cout << "DFS Traversal: ";
    DFS(adj, 0); // Start DFS from node 0

    return 0;
}
```

#### **Output**

```
DFS Traversal: 0 1 3 4 2
```

### **Comparison of BFS & DFS**

| Feature          | BFS                              | DFS                            |
| ---------------- | -------------------------------- | ------------------------------ |
| Uses             | Queue (FIFO)                     | Stack/Recursion (LIFO)         |
| Best for         | Shortest path (unweighted graph) | Pathfinding, cycle detection   |
| Space Complexity | \(O(V)\) (for queue)             | \(O(V)\) (for recursion stack) |
| Time Complexity  | \(O(V + E)\)                     | \(O(V + E)\)                   |

### **Conclusion**

- Use **BFS** for shortest paths & level-wise traversal.
- Use **DFS** for exploring paths, cycle detection, and topological sorting.

---

## **Connected Components (Connected Components)**

A **connected component** of a graph is a **maximal set of vertices** such that there is a **path between any two vertices** in the component.

### **Types of Graphs & Connectivity**

- **Connected Graph**: Has only **one** connected component.
- **Disconnected Graph**: Has **multiple** connected components.

### **Example**

```
    Component 1:  A - B - C
    Component 2:  D - E
```

- `{A, B, C}` forms **one** connected component.
- `{D, E}` forms **another** connected component.

### **Algorithm to Find Connected Components (Using DFS)**

1. Initialize **visited** array.
2. Traverse all vertices using DFS/BFS.
3. Every time a new unvisited vertex is found, it's a **new component**.
4. Count and print components.

### **C++ Code for Connected Components using DFS**

```cpp
#include <iostream>
#include <vector>

using namespace std;

void DFS(vector<vector<int>> &adj, vector<bool> &visited, int node) {
    visited[node] = true;
    cout << node << " ";

    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            DFS(adj, visited, neighbor);
        }
    }
}

void findConnectedComponents(vector<vector<int>> &adj, int V) {
    vector<bool> visited(V, false);
    int count = 0;

    for (int i = 0; i < V; i++) {
        if (!visited[i]) {
            count++;
            cout << "Component " << count << ": ";
            DFS(adj, visited, i);
            cout << endl;
        }
    }
}

int main() {
    int V = 6;
    vector<vector<int>> adj(V);

    // Creating a disconnected graph
    adj[0] = {1, 2};
    adj[1] = {0, 2};
    adj[2] = {0, 1};
    adj[3] = {4};  // Second component
    adj[4] = {3};
    adj[5] = {};   // Third component (single node)

    cout << "Connected Components in the Graph:\n";
    findConnectedComponents(adj, V);

    return 0;
}
```

### **Output**

```
Component 1: 0 1 2
Component 2: 3 4
Component 3: 5
```

---

## **Spanning Tree**

A **spanning tree** of a graph is a **subgraph** that:  
✅ Includes **all vertices** of the original graph.  
✅ Is a **tree** (connected and acyclic).  
✅ Has **V-1 edges** for a graph with **V vertices**.

### **Example Graph**

```
Original Graph:
    A --- B
    |  \  |
    C --- D

Spanning Tree (One of Many Possible):
    A --- B
    |
    C --- D
```

- **All vertices are included.**
- **No cycles.**
- **Has (V-1) edges.**

🔹 **A graph may have multiple spanning trees.**

---

## **Minimum Spanning Tree (MST)**

A **minimum spanning tree (MST)** is a spanning tree **with the minimum total edge weight**.

### **Popular Algorithms to Find MST**

1. **Prim’s Algorithm** → Greedy, starts with a single node.
2. **Kruskal’s Algorithm** → Greedy, sorts edges by weight.

### **C++ Code for MST (Using Kruskal’s Algorithm)**

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

struct Edge {
    int u, v, weight;
    bool operator<(Edge const &other) {
        return weight < other.weight;
    }
};

struct DisjointSet {
    vector<int> parent, rank;

    DisjointSet(int n) {
        parent.resize(n);
        rank.resize(n, 0);
        for (int i = 0; i < n; i++)
            parent[i] = i;
    }

    int find(int v) {
        if (parent[v] == v) return v;
        return parent[v] = find(parent[v]);  // Path compression
    }

    void union_sets(int a, int b) {
        a = find(a);
        b = find(b);
        if (a != b) {
            if (rank[a] < rank[b])
                swap(a, b);
            parent[b] = a;
            if (rank[a] == rank[b])
                rank[a]++;
        }
    }
};

int KruskalMST(int V, vector<Edge> &edges) {
    sort(edges.begin(), edges.end());  // Sort edges by weight
    DisjointSet ds(V);

    int minCost = 0;
    vector<Edge> mst;

    for (Edge e : edges) {
        if (ds.find(e.u) != ds.find(e.v)) {
            ds.union_sets(e.u, e.v);
            mst.push_back(e);
            minCost += e.weight;
        }
    }

    cout << "Minimum Spanning Tree Edges:\n";
    for (Edge e : mst)
        cout << e.u << " - " << e.v << " (" << e.weight << ")\n";

    return minCost;
}

int main() {
    int V = 4;
    vector<Edge> edges = {
        {0, 1, 10}, {0, 2, 6}, {0, 3, 5}, {1, 3, 15}, {2, 3, 4}
    };

    int minCost = KruskalMST(V, edges);
    cout << "Minimum Cost of MST: " << minCost << endl;

    return 0;
}
```

### **Output**

```
Minimum Spanning Tree Edges:
2 - 3 (4)
0 - 3 (5)
0 - 1 (10)
Minimum Cost of MST: 19
```

### **C++ Code for MST (Using Prim's Algorithm)**

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <climits>

using namespace std;

// Structure to represent an edge in the adjacency list
struct Edge {
    int vertex, weight;
    bool operator>(const Edge &other) const {
        return weight > other.weight; // Min-heap based on weight
    }
};

// Prim's Algorithm Function
void PrimMST(vector<vector<Edge>> &adj, int V) {
    vector<int> key(V, INT_MAX);  // Stores minimum edge weight
    vector<int> parent(V, -1);    // Stores MST
    vector<bool> inMST(V, false); // Track included vertices
    priority_queue<Edge, vector<Edge>, greater<Edge>> pq; // Min-heap

    key[0] = 0; // Start from vertex 0
    pq.push({0, 0});

    for (int count = 0; count < V; count++) {
        if (pq.empty()) break;

        // Extract min-weight vertex
        int u = pq.top().vertex;
        pq.pop();

        inMST[u] = true; // Include vertex in MST

        // Explore neighbors
        for (Edge &e : adj[u]) {
            int v = e.vertex;
            int weight = e.weight;

            // If v is not in MST and weight is less than the current key
            if (!inMST[v] && weight < key[v]) {
                key[v] = weight;
                pq.push({v, key[v]});
                parent[v] = u; // Update parent
            }
        }
    }

    // Print MST edges
    cout << "Minimum Spanning Tree Edges:\n";
    for (int i = 1; i < V; i++) {
        cout << parent[i] << " - " << i << " (Weight: " << key[i] << ")\n";
    }
}

int main() {
    int V = 5;
    vector<vector<Edge>> adj(V);

    // Adding edges (Undirected Graph)
    adj[0].push_back({1, 2});
    adj[0].push_back({3, 6});
    adj[1].push_back({0, 2});
    adj[1].push_back({2, 3});
    adj[1].push_back({3, 8});
    adj[1].push_back({4, 5});
    adj[2].push_back({1, 3});
    adj[2].push_back({4, 7});
    adj[3].push_back({0, 6});
    adj[3].push_back({1, 8});
    adj[4].push_back({1, 5});
    adj[4].push_back({2, 7});

    // Run Prim’s Algorithm
    PrimMST(adj, V);

    return 0;
}
```

### **Output**

```
Minimum Spanning Tree Edges:
0 - 1 (Weight: 2)
1 - 2 (Weight: 3)
1 - 4 (Weight: 5)
0 - 3 (Weight: 6)
```

### **Comparison: Kruskal’s vs. Prim’s Algorithm**

| Feature        | Kruskal’s Algorithm       | Prim’s Algorithm                              |
| -------------- | ------------------------- | --------------------------------------------- |
| Approach       | Greedy (sort edges)       | Greedy (grow MST from a vertex)               |
| Best for       | Sparse graphs             | Dense graphs                                  |
| Complexity     | \(O(E \log E)\)           | \(O(V^2)\) (or \(O(E + V \log V)\) with heap) |
| Data Structure | Disjoint Set (Union-Find) | Priority Queue (Heap)                         |

### **Conclusion**

- **Connected Components**: Identify different groups in a graph.
- **Spanning Tree**: A subgraph connecting all vertices with no cycles.
- **Minimum Spanning Tree (MST)**: The lowest-cost spanning tree.
- **Kruskal’s Algorithm**: Efficient for sparse graphs.
- **Prim’s Algorithm**: Efficient for dense graphs.

---

## **Single Source Shortest Path**

Finds the shortest path from a **single source** node to **all other nodes** in a graph.

### **Dijkstra’s Algorithm (Single Source)**

✅ Works with **positive edge weights**  
✅ Uses a **priority queue (Min-Heap)** for efficiency  
✅ Time Complexity: **\(O((V + E) \log V)\)** (with priority queue)

### **C++ Code for Single Source Dijkstra Algorithm**

```cpp
#include <iostream>
#include <queue>
using namespace std;

// Dijkstra Algorithm is used to find minimum distance between two vertices(source to destination)
// Here I am finding minimum distance for all vertices from source

void DijkstraAlgo(int **edges, int n, int source)
{
    bool *visited = new bool[n];
    for (int i = 0; i < n; i++)
    {
        visited[i] = false;
    }

    int *distance = new int[n];
    for (int i = 0; i < n; i++)
    {
        distance[i] = INT16_MAX;
    }

    distance[source] = 0;

    int count = 0;
    while (count < n - 1)
    {
        // Step 1 -> Find minimum weight along the un-visited vertices
        int minDistance = INT16_MAX;
        int minDistanceIndex;
        for (int i = 0; i < n; i++)
        {
            if (!visited[i] && distance[i] < minDistance)
            {
                minDistance = distance[i];
                minDistanceIndex = i;
            }
        }

        for (int i = 0; i < n; i++)
        {
            if (edges[minDistanceIndex][i] != 0 && !visited[i])
            {
                if (edges[minDistanceIndex][i] + distance[minDistanceIndex] < distance[i])
                {
                    distance[i] = edges[minDistanceIndex][i] + distance[minDistanceIndex];
                }
            }
        }
        visited[minDistanceIndex] = true;
        count++;
    }

    //  Output
    for (int i = 0; i < n; i++)
    {
        cout << "From " << source << " To " << i << " " << distance[i] << endl;
    }

    delete[] visited;
    delete[] distance;
}

// Input -> 6 11 5 0 1 2 0 2 1 0 3 3 1 2 4 1 3 7 2 3 6 2 4 9 2 5 8 3 5 10 3 4 11 4 5
// Input -> 5 7 4 0 1 8 0 2 2 1 2 9 2 4 5 3 4 3 2 3 6 1 3
// Input -> 5 7 4 0 1 8 0 2 2 1 2 9 2 4 4 3 4 5 2 3 5 1 3

int main()
{
    // n : Number of vertices
    // e : Number of edges
    int n, e;
    cin >> n >> e;

    // Adjancy matrix which holds all edges
    int **edges = new int *[n];
    for (int i = 0; i < n; i++)
    {
        edges[i] = new int[n];
        for (int j = 0; j < n; j++)
        {
            edges[i][j] = 0;
        }
    }

    for (int i = 0; i < e; i++)
    {
        // f : first vertices of edge
        // s : second vertices of edge
        int s, d, w;
        cin >> w >> s >> d;
        edges[s][d] = w;
        edges[d][s] = w;
    }

    DijkstraAlgo(edges, n, 0);

    for (int i = 0; i < n; i++)
    {
        delete[] edges[i];
    }

    delete[] edges;
    return 0;
}
```

### **Output**

```
Vertex  Distance from Source (0)
0       0
1       8
2       9
3       7
4       5
```

---

## **All Pairs Shortest Path**

Finds the shortest path **between every pair** of vertices.

### **Dijkstra’s Algorithm (All-Pairs)**

✅ Runs **Dijkstra’s algorithm for every vertex as a source**  
✅ Time Complexity: **\(O(V (E + V \log V))\)**

### **C++ Code for All-Pairs Dijkstra Algorithm**

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <climits>

using namespace std;

struct Edge {
    int vertex, weight;
    bool operator>(const Edge &other) const {
        return weight > other.weight; // Min-Heap
    }
};

vector<int> Dijkstra(vector<vector<Edge>> &adj, int V, int src) {
    vector<int> dist(V, INT_MAX);
    priority_queue<Edge, vector<Edge>, greater<Edge>> pq;

    dist[src] = 0;
    pq.push({src, 0});

    while (!pq.empty()) {
        int u = pq.top().vertex;
        int currentDist = pq.top().weight;
        pq.pop();

        if (currentDist > dist[u]) continue;

        for (Edge &e : adj[u]) {
            int v = e.vertex;
            int weight = e.weight;

            if (dist[u] + weight < dist[v]) {
                dist[v] = dist[u] + weight;
                pq.push({v, dist[v]});
            }
        }
    }

    return dist;
}

void AllPairsDijkstra(vector<vector<Edge>> &adj, int V) {
    cout << "All Pairs Shortest Paths:\n";

    for (int src = 0; src < V; src++) {
        vector<int> dist = Dijkstra(adj, V, src);
        cout << "From Vertex " << src << ":\n";
        for (int i = 0; i < V; i++)
            cout << "  To " << i << ": " << (dist[i] == INT_MAX ? -1 : dist[i]) << "\n";
        cout << endl;
    }
}

int main() {
    int V = 4;
    vector<vector<Edge>> adj(V);

    // Adding weighted edges
    adj[0].push_back({1, 3});
    adj[0].push_back({2, 7});
    adj[1].push_back({0, 3});
    adj[1].push_back({2, 1});
    adj[1].push_back({3, 5});
    adj[2].push_back({0, 7});
    adj[2].push_back({1, 1});
    adj[2].push_back({3, 2});
    adj[3].push_back({1, 5});
    adj[3].push_back({2, 2});

    AllPairsDijkstra(adj, V);

    return 0;
}
```

### **Output**

```
All Pairs Shortest Paths:
From Vertex 0:
  To 0: 0
  To 1: 3
  To 2: 4
  To 3: 6

From Vertex 1:
  To 0: 3
  To 1: 0
  To 2: 1
  To 3: 3

From Vertex 2:
  To 0: 4
  To 1: 1
  To 2: 0
  To 3: 2

From Vertex 3:
  To 0: 6
  To 1: 3
  To 2: 2
  To 3: 0
```

### **Alternative: Floyd-Warshall Algorithm (All-Pairs)**

✅ Uses **Dynamic Programming**  
✅ Works for **both positive and negative weights** (but no negative cycles)  
✅ Time Complexity: **\(O(V^3)\)**  
✅ **Better than Dijkstra for dense graphs.**

### **Comparison of Shortest Path Algorithms**

| Algorithm                      | Type                | Works With                       | Complexity              |
| ------------------------------ | ------------------- | -------------------------------- | ----------------------- |
| **Dijkstra (Single Source)**   | Greedy              | Positive Weights                 | \(O((V + E) \log V)\)   |
| **Dijkstra (All-Pairs)**       | Greedy              | Positive Weights                 | \(O(V (E + V \log V))\) |
| **Floyd-Warshall (All-Pairs)** | Dynamic Programming | All Weights (No Negative Cycles) | \(O(V^3)\)              |

### **Conclusion**

- **Use Dijkstra (Single Source) when finding paths from one node to all others.**
- **Use All-Pairs Dijkstra for graphs with positive weights and fewer vertices.**
- **Use Floyd-Warshall for dense graphs with all-pairs shortest paths.**

---

## Topological Sort

🔹 **Topological sorting** is a **linear ordering** of vertices in a **Directed Acyclic Graph (DAG)** such that **for every directed edge \( u \to v \), vertex \( u \) comes before vertex \( v \) in the ordering**.

#### **Key Points**

✅ **Works only on DAGs (Directed Acyclic Graphs)**  
✅ **Used in scheduling problems, task dependencies, and compiler design**  
✅ **Has multiple valid orderings**  
✅ **Can be implemented using DFS or Kahn’s Algorithm (BFS-based)**

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <stack>
using namespace std;

void DFS(vector<int> adj[], int n, int sv, bool *visited, stack<int> &st)
{
    // cout << sv << " ";
    visited[sv] = true;

    vector<int> temp = adj[sv];
    for (int i = 0; i < temp.size(); i++)
    {
        if (!visited[temp[i]])
        {
            DFS(adj, n, temp[i], visited, st);
        }
    }

    st.push(sv);
}

vector<int> topologicalSort(vector<int> adj[], int n)
{
    bool *visited = new bool[n];
    for (int i = 0; i < n; i++)
    {
        visited[i] = false;
    }
    stack<int> st;
    // DFS(adj, n, 0, visited, st);
    for (int i = 0; i < n; i++)
    {
        if (!visited[i])
        {
            DFS(adj, n, i, visited, st);
            // cout << endl;
        }
    }

    vector<int> ans;
    while (st.size() != 0)
    {
        ans.push_back(st.top());
        st.pop();
    }

    return ans;
}

int main()
{
    int n, e;
    cin >> n >> e;

    vector<int> adj[n];

    for (int i = 0; i < e; i++)
    {
        int f, s;
        cin >> f >> s;

        // Topological Sort is only defined for Directed Acylic Graph (DAG)
        // Directed Graph
        adj[f].push_back(s);
    }

    cout << "DFS" << endl;
    vector<int> ans = topologicalSort(adj, n);
    for (int i = 0; i < ans.size(); i++)
    {
        cout << ans[i] << " ";
    }

    return 0;
}
```

---

## **`Gagan Saini`**
