# Ex22 Breadth First Graph
## DATE:
## AIM:
To write a **Java program** to implement the **Breadth-First Search (BFS)** algorithm for a graph, and demonstrate the traversal order using a **Queue** data structure.

## Algorithm:
1.  Start.
2.  Define a **`Graph`** class using an **Adjacency List** representation (e.g., an array of ArrayLists).
3.  Define the **`BFS(int startNode)`** method:
    a. Initialize a boolean array, **`visited[]`**, for all vertices to `false`.
    b. Create a **Queue** (e.g., `java.util.LinkedList` implementing `Queue`).
    c. Mark the `startNode` as visited and **enqueue** it.
    d. While the queue is **not empty**: 
        i. **Dequeue** a vertex $u$.
        ii. Print or record $u$ (this is the traversal sequence).
        iii. For every unvisited neighbor $v$ of $u$:
            - Mark $v$ as **visited**.
            - **Enqueue** $v$.
4.  Define a **`printQueue()`** utility method (or print the queue contents within the BFS loop) to show the state of the queue at various points.
5.  In the `main` method, create a sample graph, and call the `BFS()` method starting from a specified vertex.
6.  End.

## Program:
/*
Program to traverse graph using BFS
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

import java.util.LinkedList;
import java.util.Queue;
import java.util.ArrayList;

public class BreadthFirstGraph {
    private int V; // Number of vertices
    private LinkedList<Integer> adj[]; // Adjacency Lists

    public BreadthFirstGraph(int v) {
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

    // Utility function to print the current state of the queue
    void printQueue(Queue<Integer> q) {
        if (q.isEmpty()) {
            System.out.println("Queue is empty");
        } else {
            System.out.print("Queue contains: " + q + "\n");
        }
    }

    // BFS traversal
    void BFS(int s) {
        // Mark all the vertices as not visited
        boolean visited[] = new boolean[V];

        // Create a queue for BFS
        Queue<Integer> queue = new LinkedList<Integer>();

        // Mark the current node as visited and enqueue it
        visited[s] = true;
        queue.add(s);

        System.out.println("--- BFS Traversal Process ---");
        System.out.println("Starting Node: " + s);
        System.out.print("Traversal Sequence: ");

        while (queue.size() != 0) {
            // Dequeue a vertex from queue and print it
            int u = queue.poll();
            System.out.print(u + " ");
            
            // Utility call to show queue state (optional, for demonstration)
            // printQueue(queue); 

            // Get all adjacent vertices of the dequeued vertex u.
            // If an adjacent vertex has not been visited, mark it visited and enqueue it.
            for (int v : adj[u]) {
                if (!visited[v]) {
                    visited[v] = true;
                    queue.add(v);
                }
            }
        }
        System.out.println();
    }

    public static void main(String args[]) {
        // Sample graph construction (4 vertices)
        BreadthFirstGraph g = new BreadthFirstGraph(4);
        g.addEdge(0, 1);
        g.addEdge(0, 2);
        g.addEdge(1, 2);
        g.addEdge(2, 0);
        g.addEdge(2, 3);
        g.addEdge(3, 3);

        System.out.println("--- Graph Structure (Adjacency List) ---");
        System.out.println("0 -> " + g.adj[0]);
        System.out.println("1 -> " + g.adj[1]);
        System.out.println("2 -> " + g.adj[2]);
        System.out.println("3 -> " + g.adj[3]);
        System.out.println("----------------------------------------");

        // Start BFS from vertex 2
        g.BFS(2);
    }
}

## Output:
![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to traverse the given graph in the breadth-first manner using the BFS algorithm and a Queue data structure is implemented successfully.
