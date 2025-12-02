# Ex24 Topological Sort
## DATE:
## AIM:
To write a **Java program** to implement **Kahn's algorithm** for **Topological Sorting** to determine whether a topological ordering for the given **Directed Graph** is possible, which verifies the absence of cycles.

## Algorithm:
1.  Start.
2.  Define a **`Graph`** class using an **Adjacency List** and an array `indegree` to store the in-degree of each vertex.
3.  Implement the **`calculateInDegree()`** method: Traverse the adjacency list and increment the `indegree` count for every destination vertex of an edge.
4.  Define the **`topologicalSort()`** method (Kahn's Algorithm):
    a. Initialize a **Queue** and add all vertices with an `indegree` of **0** (source nodes).
    b. Initialize a `count` of visited vertices to 0 and an `ArrayList` to store the topological order.
    c. While the queue is **not empty**: 
        i. **Dequeue** a vertex $u$.
        ii. Add $u$ to the topological order list and increment `count`.
        iii. For every neighbor $v$ of $u$:
            - Decrement the `indegree` of $v$ by 1.
            - If $indegree[v]$ becomes **0**, **enqueue** $v$.
5.  **Check for cycles**: After the loop, if the final `count` is **less than the total number of vertices ($V$)**, the graph contains a cycle, and no complete topological ordering is possible.
6.  Display the result: either the topological order or the cycle warning.
7.  End.

## Program:
/*
Program to determine whether the topological ordering for the following graph is possible or not
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

import java.util.LinkedList;
import java.util.Queue;
import java.util.ArrayList;
import java.util.Arrays;

public class TopologicalSort {
    private int V; // Number of vertices
    private LinkedList<Integer> adj[]; // Adjacency Lists
    
    public TopologicalSort(int v) {
        V = v;
        adj = new LinkedList[v];
        for (int i = 0; i < v; ++i)
            adj[i] = new LinkedList<>();
    }

    // Function to add a directed edge u -> v
    public void addEdge(int u, int v) {
        adj[u].add(v);
    }

    // Function to perform Topological Sort using Kahn's Algorithm
    public void topologicalSort() {
        int indegree[] = new int[V];
        
        // 1. Calculate indegree for all vertices
        for (int u = 0; u < V; u++) {
            for (int v : adj[u]) {
                indegree[v]++;
            }
        }

        // 2. Initialize Queue and add all vertices with in-degree 0
        Queue<Integer> q = new LinkedList<>();
        for (int i = 0; i < V; i++) {
            if (indegree[i] == 0)
                q.add(i);
        }

        // 3. Process vertices
        int count = 0;
        ArrayList<Integer> topologicalOrder = new ArrayList<>();

        while (!q.isEmpty()) {
            int u = q.poll(); // Dequeue a vertex with in-degree 0
            topologicalOrder.add(u);
            count++;

            // For all neighbors v of u
            for (int v : adj[u]) {
                // Decrement in-degree of v
                indegree[v]--;

                // If in-degree becomes 0, enqueue it
                if (indegree[v] == 0)
                    q.add(v);
            }
        }

        // 4. Check for cycles
        if (count < V) {
            System.out.println("No topological ordering possible, graph contains cycle");
        } else {
            System.out.println("Topological ordering is possible. Vertices in topological order are:");
            System.out.println(topologicalOrder);
        }
    }

    public static void main(String args[]) {
        // Construct the sample graph from the image (assuming vertices 0 to 4)
        TopologicalSort graph = new TopologicalSort(5);
        
        // Edges from the graph image:
        // 0 -> 1, 0 -> 2
        // 1 -> 3
        // 2 -> 3, 2 -> 4
        graph.addEdge(0, 1);
        graph.addEdge(0, 2);
        graph.addEdge(1, 3);
        graph.addEdge(2, 3);
        graph.addEdge(2, 4);

        System.out.println("--- Topological Sort (Kahn's Algorithm) ---");
        graph.topologicalSort();
    }
}

## Output:

![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to determine whether the topological ordering for the given graph is possible or not, using Kahn's algorithm, is implemented successfully.
