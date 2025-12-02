# Ex23 Depth First Graph
## DATE:
## AIM:
To write a **Java program** to implement the **Depth-First Search (DFS)** algorithm for a graph, and demonstrate the traversal order using the **Adjacency List** representation.

## Algorithm:
1.  Start.
2.  Define a **`Graph`** class using an **Adjacency List** representation (an array/list of `ArrayLists` to store neighbors).
3.  Define the **`DFS(int startNode)`** method:
    a. Initialize a boolean array, **`visited[]`**, for all vertices to `false`.
    b. Call the recursive helper function **`DFSUtil(int vertex, boolean[] visited)`** starting with the `startNode`. 
4.  Define the recursive **`DFSUtil(int vertex, boolean[] visited)`** method:
    a. Mark the current `vertex` as **visited** and print or record it (this is the traversal sequence).
    b. For every neighbor $v$ of the current `vertex`:
        i. If $v$ is **not visited**, recursively call `DFSUtil(v, visited)`.
5.  In the `main` method, create a sample graph, and call the `DFS()` method starting from a specified vertex.
6.  End.

## Program:
/*
Program to traverse the graph below in the depth first fashion
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

import java.util.LinkedList;
import java.util.ArrayList;

public class DepthFirstGraph {
    private int V; // Number of vertices
    private LinkedList<Integer> adj[]; // Adjacency Lists

    public DepthFirstGraph(int v) {
        V = v;
        adj = new LinkedList[v];
        for (int i = 0; i < v; ++i)
            adj[i] = new LinkedList();
    }

    // Function to add an edge into the graph (undirected)
    void addEdge(int v, int w) {
        adj[v].add(w);
        adj[w].add(v); // For undirected graph
    }

    // Recursive helper function for DFS
    void DFSUtil(int vertex, boolean visited[]) {
        // Mark the current node as visited and print it
        visited[vertex] = true;
        System.out.print(vertex + " ");

        // Recur for all the neighbors of this vertex
        for (int neighbor : adj[vertex]) {
            if (!visited[neighbor]) {
                DFSUtil(neighbor, visited);
            }
        }
    }

    // Main DFS function
    void DFS(int s) {
        // Mark all the vertices as not visited
        boolean visited[] = new boolean[V];
        System.out.println("--- DFS Traversal Process ---");
        System.out.println("Starting Node: " + s);
        System.out.print("Traversal Sequence: ");
        
        // Call the recursive helper function
        DFSUtil(s, visited);
        System.out.println();
    }

    public static void main(String args[]) {
        // Sample graph construction (4 vertices: 0, 1, 2, 3)
        DepthFirstGraph g = new DepthFirstGraph(4);
        g.addEdge(0, 1);
        g.addEdge(0, 2);
        g.addEdge(1, 2);
        g.addEdge(2, 0);
        g.addEdge(2, 3);
        g.addEdge(3, 3); // Self-loop

        System.out.println("--- Graph Structure (Adjacency List) ---");
        System.out.println("0 -> " + g.adj[0]);
        System.out.println("1 -> " + g.adj[1]);
        System.out.println("2 -> " + g.adj[2]);
        System.out.println("3 -> " + g.adj[3]);
        System.out.println("----------------------------------------");

        // Start DFS from vertex 2
        g.DFS(2);
    }
}

## Output:


![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to traverse the given graph in the depth-first manner using the DFS algorithm and the Adjacency List representation is implemented successfully.
