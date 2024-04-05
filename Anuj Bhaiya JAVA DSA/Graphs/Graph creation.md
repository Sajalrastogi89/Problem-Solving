# Intuition
The program aims to take input for representing a graph either using an adjacency matrix or an adjacency list, based on user choice, and then print the graph representation accordingly.

# Approach
1. Take input for the total number of vertices and edges.
2. Prompt the user to choose between using an adjacency matrix or an adjacency list.
3. Initialize either an adjacency matrix or an adjacency list based on the user's choice.
4. Take input for edges (source and destination) and add them to the graph accordingly.
5. Print the graph representation based on the chosen method.

# Complexity
- Time complexity: 
    - For input: O(vertices + edges)
    - For printing the graph: O(vertices^2) for adjacency matrix, O(vertices + edges) for adjacency list
    Overall, the time complexity depends on the chosen method.
- Space complexity: 
    - For adjacency matrix: O(vertices^2)
    - For adjacency list: O(vertices + edges)

# Code
```java
package org.example.codes;

import java.util.ArrayList;
import java.util.Scanner;

public class Graphs {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter total vertices:");
        int vertices = scanner.nextInt();
        System.out.println("Enter total edges:");
        int edges = scanner.nextInt();
        System.out.println("Enter:\n1 for Adjacency Matrix \n2 for Adjacency List");
        int method = scanner.nextInt();
        while (method != 1 && method != 2) {
            System.out.println("Invalid choice. Please re-enter:");
            method = scanner.nextInt();
        }

        if (method == 1) {
            int[][] adjacencyMatrix = initializeAdjacencyMatrix(vertices);
            takeInputForMatrix(vertices, edges, scanner, adjacencyMatrix);
            printMatrix(adjacencyMatrix);
        } else {
            ArrayList<ArrayList<Integer>> adjacencyList = initializeAdjacencyList(vertices);
            takeInputForList(vertices, edges, scanner, adjacencyList);
            printList(adjacencyList);
        }
    }

    // Method to initialize adjacency matrix with zeros
    private static int[][] initializeAdjacencyMatrix(int vertices) {
        return new int[vertices + 1][vertices + 1];
    }

    // Method to initialize adjacency list
    private static ArrayList<ArrayList<Integer>> initializeAdjacencyList(int vertices) {
        ArrayList<ArrayList<Integer>> adjacencyList = new ArrayList<>();
        for (int i = 0; i <= vertices; i++) {
            adjacencyList.add(new ArrayList<>());
        }
        return adjacencyList;
    }

    // Method to take input for adjacency matrix
    private static void takeInputForMatrix(int vertices, int edges, Scanner scanner, int[][] adjacencyMatrix) {
        for (int i = 1; i <= vertices; i++) {
            System.out.println("Enter source vertex:");
            int source = scanner.nextInt();
            while (true) {
                System.out.println("Enter destination vertex or -1 to move to next source:");
                int dest = scanner.nextInt();
                if (dest == -1)
                    break;
                addEdgeToMatrix(source, dest, adjacencyMatrix);
            }
        }
    }

    // Method to take input for adjacency list
    private static void takeInputForList(int vertices, int edges, Scanner scanner, ArrayList<ArrayList<Integer>> adjacencyList) {
        for (int i = 1; i <= vertices; i++) {
            System.out.println("Enter source vertex:");
            int source = scanner.nextInt();
            while (true) {
                System.out.println("Enter destination vertex or -1 to move to next source:");
                int dest = scanner.nextInt();
                if (dest == -1)
                    break;
                addEdgeToList(source, dest, adjacencyList);
            }
        }
    }

    // Method to add edge to adjacency matrix
    private static void addEdgeToMatrix(int source, int dest, int[][] adjacencyMatrix) {
        adjacencyMatrix[source][dest] = 1;
    }

    // Method to add edge to adjacency list
    private static void addEdgeToList(int source, int dest, ArrayList<ArrayList<Integer>> adjacencyList) {
        adjacencyList.get(source).add(dest);
    }

    // Method to print adjacency matrix
    private static void printMatrix(int[][] adjacencyMatrix) {
        for (int i = 1; i < adjacencyMatrix.length; i++) {
            for (int j = 1; j < adjacencyMatrix[i].length; j++) {
                System.out.print(adjacencyMatrix[i][j] + " ");
            }
            System.out.println();
        }
    }

    // Method to print adjacency list
    private static void printList(ArrayList<ArrayList<Integer>> adjacencyList) {
        for (int i = 1; i < adjacencyList.size(); i++) {
            for (int j = 0; j < adjacencyList.get(i).size(); j++) {
                System.out.print(adjacencyList.get(i).get(j) + " ");
            }
            System.out.println();
        }
    }
}
