# Ex21 Representation of Graph
## DATE:
## AIM:
To write a **Java program** to represent a given graph using an **Adjacency Matrix**, where the graph edges and the number of vertices are supplied by the user.

## Algorithm:
1.  Start.
2.  Read the value of **V** (number of vertices).
3.  Declare an adjacency matrix, **`adjMatrix[V][V]`**, of size $V \times V$.
4.  Initialize the entire matrix to **0**, signifying no edges initially.
5.  Define the **`addEdge(int[][] matrix, int u, int v)`** function to insert an edge:
    a. If the graph is **undirected**, set $matrix[u][v] = 1$ and $matrix[v][u] = 1$.
    b. *(If the graph were directed, only set $matrix[u][v] = 1$)*.
6.  Start a loop to read edges ($e_1, e_2$) from the user.
    a. Call `addEdge()` for the input vertices.
    b. Continue reading edges until a sentinel value (e.g., $e_1 = -1$ and $e_2 = -1$) is entered. [j] if an edge exists between vertex i and j]
7.  Define the **`printAdjMatrix(int[][] matrix)`** function to display the resulting matrix.
8.  End.

## Program:
/*
Program to display the adjacency matrix of the given graph
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/

import java.util.Scanner;

public class GraphRepresentation {

    // Global variable for number of vertices
    static int V;

    // Function to initialize the matrix to 0 (optional in Java as arrays are init to 0)
    static void init(int[][] arr) {
        // In Java, integer arrays are automatically initialized to 0. 
        // This function is kept for consistency with the C algorithm's intention.
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                arr[i][j] = 0;
            }
        }
    }

    // Function to add an edge (u -> v) to the adjacency matrix (Undirected Graph)
    static void addEdge(int[][] matrix, int u, int v) {
        if (u >= 0 && u < V && v >= 0 && v < V) {
            matrix[u][v] = 1;
            matrix[v][u] = 1; // For undirected graph
        }
    }

    // Function to print the adjacency matrix
    static void printAdjMatrix(int[][] matrix) {
        System.out.println("\nAdjacency Matrix:");
        // Print column headers
        System.out.print("  ");
        for (int i = 0; i < V; i++) {
            System.out.print(i + " ");
        }
        System.out.println();
        
        // Print matrix rows
        for (int i = 0; i < V; i++) {
            System.out.print(i + " "); // Row header
            for (int j = 0; j < V; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the number of vertices (V): ");
        V = scanner.nextInt();
        
        int[][] adjMatrix = new int[V][V];
        init(adjMatrix);
        
        System.out.println("Enter edges as pairs of vertices (u v), or -1 -1 to stop:");
        
        int e1, e2;
        
        // Loop to read edges
        while (true) {
            System.out.print("Edge (u v): ");
            e1 = scanner.nextInt();
            e2 = scanner.nextInt();
            
            if (e1 == -1 && e2 == -1) {
                break;
            }
            
            // Check for valid vertex range
            if (e1 >= 0 && e1 < V && e2 >= 0 && e2 < V) {
                addEdge(adjMatrix, e1, e2);
            } else {
                System.out.println("Invalid vertices. Must be between 0 and " + (V - 1));
            }
        }
        
        printAdjMatrix(adjMatrix);
        scanner.close();
    }
}

## Output:


![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to display the adjacency matrix of the given graph by supplying the edges and the number of vertices is implemented successfully.
