# Ex25 Adjacency List Representation
## DATE:
## AIM:
To write a **Java program** to represent a given graph using the **Adjacency List** data structure and display the resulting list.

## Algorithm:
1.  Start.
2.  Define a **`Graph`** class with an integer **V** (number of vertices) and an array of `LinkedLists` (or `ArrayLists`) named **`adj`** to represent the adjacency list.
3.  Read the number of vertices ($V$) and the number of edges ($E$).
4.  Define the **`addEdge(int u, int v)`** function:
    a. For an **undirected graph**, add $v$ to $adj[u]$'s list and add $u$ to $adj[v]$'s list.
5.  Read $E$ pairs of vertices (edges) and call `addEdge()` for each pair to construct the graph. 
6.  Define the **`printGraph()`** function:
    a. Loop through each vertex $i$ from $0$ to $V-1$.
    b. Print the vertex $i$, followed by an arrow, and then iterate through $adj[i]$'s list, printing all neighboring vertices.
7.  End.

## Program:
/*
Program to represent the given graph using the adjacency list
Developed by: Dharani dharan K
RegisterNumber: Dharani dharan K
*/

import java.util.LinkedList;
import java.util.ArrayList;
import java.util.Scanner;

public class AdjacencyListRepresentation {
    private int V; // Number of vertices
    private LinkedList<Integer> adj[]; // Array of Lists for Adjacency List

    public AdjacencyListRepresentation(int v) {
        V = v;
        adj = new LinkedList[v];
        for (int i = 0; i < v; ++i)
            adj[i] = new LinkedList<>();
    }

    // Function to add an edge to the graph (Undirected)
    void addEdge(int u, int v) {
        if (u >= 0 && u < V && v >= 0 && v < V) {
            adj[u].add(v);
            adj[v].add(u); // Since the graph is typically undirected unless specified
        }
    }

    // Function to print the adjacency list representation
    void printGraph() {
        System.out.println("\nAdjacency List Representation:");
        for (int i = 0; i < V; ++i) {
            System.out.print("Vertex " + i + " is connected to: ");
            for (int neighbor : adj[i]) {
                System.out.print(neighbor + " -> ");
            }
            System.out.println("NULL");
        }
    }

    public static void main(String args[]) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the number of vertices (V): ");
        int V = scanner.nextInt();
        
        System.out.print("Enter the number of edges (E): ");
        int E = scanner.nextInt();

        AdjacencyListRepresentation graph = new AdjacencyListRepresentation(V);
        
        System.out.println("Enter edges as pairs of vertices (u v):");
        
        // Input edges
        for (int i = 0; i < E; i++) {
            System.out.print("Edge " + (i + 1) + " (u v): ");
            int u = scanner.nextInt();
            int v = scanner.nextInt();
            
            if (u >= 0 && u < V && v >= 0 && v < V) {
                graph.addEdge(u, v);
            } else {
                System.out.println("Invalid vertices. Skipping edge.");
            }
        }
        
        graph.printGraph();
        scanner.close();
    }
}

## Output:


![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to represent the given graph using the Adjacency List is implemented successfully.
