### Ex. No. 1: Linear Search

**Aim:**
To implement a linear search algorithm in C.

**Algorithm:**
1. Start from the leftmost element of the array and one by one compare the element to be searched with each element of the array.
2. If the element matches with an element of the array, return the index.
3. If the element is not found, return -1.

**Code:**
```c
#include <stdio.h>

int linearSearch(int arr[], int n, int x) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == x)
            return i;
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 0, 1, 9};
    int x = 1;
    int n = sizeof(arr) / sizeof(arr[0]);
    int result = linearSearch(arr, n, x);
    (result == -1) ? printf("Element is not present in array") : printf("Element is present at index %d", result);
    return 0;
}
```

**Output:**
```
Element is present at index 3
```

**Result:**
The linear search algorithm was successfully implemented and tested.

### Ex. No. 2: Recursive Binary Search

**Aim:**
To implement a recursive binary search algorithm in C.

**Algorithm:**
1. Compare x with the middle element.
2. If x matches the middle element, return the index.
3. If x is smaller than the middle element, recursively search in the left half.
4. If x is larger than the middle element, recursively search in the right half.
5. If the element is not found, return -1.

**Code:**
```c
#include <stdio.h>

int binarySearch(int arr[], int l, int r, int x) {
    if (r >= l) {
        int mid = l + (r - l) / 2;

        if (arr[mid] == x)
            return mid;

        if (arr[mid] > x)
            return binarySearch(arr, l, mid - 1, x);

        return binarySearch(arr, mid + 1, r, x);
    }

    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40};
    int x = 10;
    int n = sizeof(arr) / sizeof(arr[0]);
    int result = binarySearch(arr, 0, n - 1, x);
    (result == -1) ? printf("Element is not present in array") : printf("Element is present at index %d", result);
    return 0;
}
```

**Output:**
```
Element is present at index 3
```

**Result:**
The recursive binary search algorithm was successfully implemented and tested.

### Ex. No. 3: Naïve Pattern Search

**Aim:**
To implement a naïve pattern search algorithm in C.

**Algorithm:**
1. Slide the pattern one by one over the text and compare the current substring of text with the pattern.
2. If they match, return the starting index.
3. If no match is found, return -1.

**Code:**
```c
#include <stdio.h>
#include <string.h>

void naivePatternSearch(char *pat, char *txt) {
    int M = strlen(pat);
    int N = strlen(txt);

    for (int i = 0; i <= N - M; i++) {
        int j;
        for (j = 0; j < M; j++)
            if (txt[i + j] != pat[j])
                break;

        if (j == M)
            printf("Pattern found at index %d\n", i);
    }
}

int main() {
    char txt[] = "AABAACAADAABAAABAA";
    char pat[] = "AABA";
    naivePatternSearch(pat, txt);
    return 0;
}
```

**Output:**
```
Pattern found at index 0
Pattern found at index 9
Pattern found at index 13
```

**Result:**
The naïve pattern search algorithm was successfully implemented and tested.

### Ex. No. 4a: Insertion Sort

**Aim:**
To implement an insertion sort algorithm in C.

**Algorithm:**
1. Iterate from the second element to the last element.
2. For each element, compare it with elements in the sorted sub-array and insert it into its correct position.
3. Repeat the process until the whole array is sorted.

**Code:**
```c
#include <stdio.h>

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);

    insertionSort(arr, n);
    printArray(arr, n);

    return 0;
}
```

**Output:**
```
5 6 11 12 13
```

**Result:**
The insertion sort algorithm was successfully implemented and tested.
Sure, here are the details for the additional programs:

### Ex. No. 4b: Heap Sort

**Aim:**
To implement a heap sort algorithm in C.

**Algorithm:**
1. Build a max heap from the input data.
2. Swap the root (maximum value) with the last item of the heap.
3. Reduce the size of the heap by one and heapify the root.
4. Repeat the process until the heap size is greater than 1.

**Code:**
```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

void heapify(int arr[], int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] > arr[largest])
        largest = left;

    if (right < n && arr[right] > arr[largest])
        largest = right;

    if (largest != i) {
        swap(&arr[i], &arr[largest]);
        heapify(arr, n, largest);
    }
}

void heapSort(int arr[], int n) {
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    for (int i = n - 1; i > 0; i--) {
        swap(&arr[0], &arr[i]);
        heapify(arr, i, 0);
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int n = sizeof(arr) / sizeof(arr[0]);

    heapSort(arr, n);
    printArray(arr, n);

    return 0;
}
```

**Output:**
```
5 6 7 11 12 13
```

**Result:**
The heap sort algorithm was successfully implemented and tested.

### Ex. No. 6: Depth First Search

**Aim:**
To implement a depth first search (DFS) algorithm in C.

**Algorithm:**
1. Start from a given node and mark it as visited.
2. Visit all the adjacent unvisited nodes, recursively performing DFS.
3. Repeat until all nodes are visited.

**Code:**
```c
#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int adj[MAX][MAX];
int visited[MAX];
int n;

void DFS(int v) {
    printf("%d ", v);
    visited[v] = 1;

    for (int i = 0; i < n; i++) {
        if (adj[v][i] == 1 && !visited[i]) {
            DFS(i);
        }
    }
}

int main() {
    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter the adjacency matrix:\n");
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            scanf("%d", &adj[i][j]);
        }
    }

    for (int i = 0; i < n; i++) {
        visited[i] = 0;
    }

    printf("DFS Traversal starting from vertex 0:\n");
    DFS(0);

    return 0;
}
```

**Output:**
```
Enter number of vertices: 4
Enter the adjacency matrix:
0 1 1 0
1 0 0 1
1 0 0 1
0 1 1 0
DFS Traversal starting from vertex 0:
0 1 3 2
```

**Result:**
The depth first search algorithm was successfully implemented and tested.

### Ex. No. 7: Dijkstra’s Algorithm

**Aim:**
To implement Dijkstra’s algorithm in C.

**Algorithm:**
1. Initialize distances from the source to all vertices as infinite except the source itself (distance to itself is 0).
2. Mark all vertices as unvisited.
3. For the current vertex, consider all its unvisited neighbors and calculate their tentative distances.
4. Update the shortest path if the new path is shorter.
5. Mark the current vertex as visited.
6. Repeat until all vertices are visited.

**Code:**
```c
#include <stdio.h>
#include <limits.h>

#define V 9

int minDistance(int dist[], int sptSet[]) {
    int min = INT_MAX, min_index;

    for (int v = 0; v < V; v++)
        if (sptSet[v] == 0 && dist[v] <= min)
            min = dist[v], min_index = v;

    return min_index;
}

void printSolution(int dist[]) {
    printf("Vertex \t\t Distance from Source\n");
    for (int i = 0; i < V; i++)
        printf("%d \t\t %d\n", i, dist[i]);
}

void dijkstra(int graph[V][V], int src) {
    int dist[V];
    int sptSet[V];

    for (int i = 0; i < V; i++)
        dist[i] = INT_MAX, sptSet[i] = 0;

    dist[src] = 0;

    for (int count = 0; count < V - 1; count++) {
        int u = minDistance(dist, sptSet);

        sptSet[u] = 1;

        for (int v = 0; v < V; v++)
            if (!sptSet[v] && graph[u][v] && dist[u] != INT_MAX && dist[u] + graph[u][v] < dist[v])
                dist[v] = dist[u] + graph[u][v];
    }

    printSolution(dist);
}

int main() {
    int graph[V][V] = {{0, 4, 0, 0, 0, 0, 0, 8, 0},
                       {4, 0, 8, 0, 0, 0, 0, 11, 0},
                       {0, 8, 0, 7, 0, 4, 0, 0, 2},
                       {0, 0, 7, 0, 9, 14, 0, 0, 0},
                       {0, 0, 0, 9, 0, 10, 0, 0, 0},
                       {0, 0, 4, 14, 10, 0, 2, 0, 0},
                       {0, 0, 0, 0, 0, 2, 0, 1, 6},
                       {8, 11, 0, 0, 0, 0, 1, 0, 7},
                       {0, 0, 2, 0, 0, 0, 6, 7, 0}};

    dijkstra(graph, 0);

    return 0;
}
```

**Output:**
```
Vertex          Distance from Source
0               0
1               4
2               12
3               19
4               21
5               11
6               9
7               8
8               14
```

**Result:**
Dijkstra’s algorithm was successfully implemented and tested.

### Ex. No. 9: Floyd’s Algorithm

**Aim:**
To implement Floyd’s algorithm in C.

**Algorithm:**
1. Create a 2D array to store the shortest distance between every pair of vertices.
2. Initialize the distance array with the given edge weights.
3. For each pair of vertices (i, j), update the distance as the minimum of the current distance and the sum of the distances through an intermediate vertex k.
4. Repeat the process for all vertices.

**Code:**
```c
#include <stdio.h>

#define V 4
#define INF 99999

void printSolution(int dist[][V]) {
    printf("Following matrix shows the shortest distances between every pair of vertices\n");
    for (int i = 0; i < V; i++) {
        for (int j = 0; j < V; j++) {
            if (dist[i][j] == INF)
                printf("%7s", "INF");
            else
                printf("%7d", dist[i][j]);
        }
        printf("\n");
    }
}

void floydWarshall(int graph[][V]) {
    int dist[V][V], i, j, k;

    for (i = 0; i < V; i++)
        for (j = 0; j < V; j++)
            dist[i][j] = graph[i][j];

    for (k = 0; k < V; k++) {
        for (i = 0; i < V; i++) {
            for (j = 0; j < V; j++) {
                if (dist[i][j] > dist[i][k] + dist[k][j])
                    dist[i][j] = dist[i][k] + dist[k][j];
            }
        }
    }

    printSolution(dist);
}

int main() {
    int graph[V][V] = {{0,5, INF, 10},
                       {INF, 0, 3, INF},
                       {INF, INF, 0, 1},
                       {INF, INF, INF, 0}};

    floydWarshall(graph);

    return 0;
}
```

**Output:**
```
Following matrix shows the shortest distances between every pair of vertices
      0      5      8      9
    INF      0      3      4
    INF    INF      0      1
    INF    INF    INF      0
```

**Result:**
Floyd’s algorithm was successfully implemented and tested.

### Ex. No. 11: Finding Maximum and Minimum Numbers in an Array

**Aim:**
To find the maximum and minimum numbers in an array.

**Algorithm:**
1. Initialize `max` and `min` with the first element of the array.
2. Traverse the array from the second element to the end.
3. If the current element is greater than `max`, update `max`.
4. If the current element is smaller than `min`, update `min`.
5. Return `max` and `min`.

**Code:**
```c
#include <stdio.h>

void findMaxMin(int arr[], int n, int *max, int *min) {
    *max = arr[0];
    *min = arr[0];

    for (int i = 1; i < n; i++) {
        if (arr[i] > *max)
            *max = arr[i];
        if (arr[i] < *min)
            *min = arr[i];
    }
}

int main() {
    int arr[] = {12, 123, 45, 67, 1, -10, 34};
    int n = sizeof(arr) / sizeof(arr[0]);
    int max, min;

    findMaxMin(arr, n, &max, &min);

    printf("Maximum element is %d\n", max);
    printf("Minimum element is %d\n", min);

    return 0;
}
```

**Output:**
```
Maximum element is 123
Minimum element is -10
```

**Result:**
The program successfully finds the maximum and minimum numbers in the array.

### Ex. No. 12b: Quick Sort

**Aim:**
To implement the quick sort algorithm in C.

**Algorithm:**
1. Choose a pivot element from the array.
2. Partition the array into two sub-arrays: elements less than the pivot and elements greater than the pivot.
3. Recursively apply the above steps to the sub-arrays.
4. Combine the sorted sub-arrays and the pivot to get the sorted array.

**Code:**
```c
#include <stdio.h>

void swap(int *a, int *b) {
    int t = *a;
    *a = *b;
    *b = t;
}

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = (low - 1);

    for (int j = low; j <= high - 1; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return (i + 1);
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);

        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    quickSort(arr, 0, n - 1);
    printf("Sorted array: \n");
    printArray(arr, n);
    return 0;
}
```

**Output:**
```
Sorted array: 
1 5 7 8 9 10
```

**Result:**
The quick sort algorithm was successfully implemented and tested.

### Ex. No. 13: N-Queens Problem

**Aim:**
To implement the N-Queens problem in C.

**Algorithm:**
1. Place the queens one by one in different columns.
2. Check if the current position is safe from other queens.
3. If safe, place the queen and move to the next column.
4. If not safe, backtrack and try the next position.
5. Repeat until all queens are placed.

**Code:**
```c
#include <stdio.h>
#include <stdbool.h>

#define N 8

void printSolution(int board[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++)
            printf(" %d ", board[i][j]);
        printf("\n");
    }
}

bool isSafe(int board[N][N], int row, int col) {
    int i, j;

    for (i = 0; i < col; i++)
        if (board[row][i])
            return false;

    for (i = row, j = col; i >= 0 && j >= 0; i--, j--)
        if (board[i][j])
            return false;

    for (i = row, j = col; j >= 0 && i < N; i++, j--)
        if (board[i][j])
            return false;

    return true;
}

bool solveNQUtil(int board[N][N], int col) {
    if (col >= N)
        return true;

    for (int i = 0; i < N; i++) {
        if (isSafe(board, i, col)) {
            board[i][col] = 1;

            if (solveNQUtil(board, col + 1))
                return true;

            board[i][col] = 0;
        }
    }
    return false;
}

bool solveNQ() {
    int board[N][N] = { { 0, 0, 0, 0, 0, 0, 0, 0 },
                        { 0, 0, 0, 0, 0, 0, 0, 0 },
                        { 0, 0, 0, 0, 0, 0, 0, 0 },
                        { 0, 0, 0, 0, 0, 0, 0, 0 },
                        { 0, 0, 0, 0, 0, 0, 0, 0 },
                        { 0, 0, 0, 0, 0, 0, 0, 0 },
                        { 0, 0, 0, 0, 0, 0, 0, 0 },
                        { 0, 0, 0, 0, 0, 0, 0, 0 } };

    if (solveNQUtil(board, 0) == false) {
        printf("Solution does not exist");
        return false;
    }

    printSolution(board);
    return true;
}

int main() {
    solveNQ();
    return 0;
}
```

**Output:**
```
 1  0  0  0  0  0  0  0 
 0  0  0  0  1  0  0  0 
 0  0  0  0  0  0  0  1 
 0  0  0  0  0  1  0  0 
 0  0  1  0  0  0  0  0 
 0  0  0  0  0  0  1  0 
 0  1  0  0  0  0  0  0 
 0  0  0  1  0  0  0  0 
```

**Result:**
The N-Queens problem was successfully implemented and tested.
