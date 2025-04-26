Given a positive integer n, generate an n x n matrix filled with elements from 1 to n2 in spiral order.

https://leetcode.com/problems/spiral-matrix-ii/description/

java
```java
class Solution {
    public int[][] generateMatrix(int n) {
        int loop = 0;
        int[][] result = new int[n][n];
        int start = 0;
        int count = 1;
        int i, j;
        while (loop++ < n / 2) {
            for (j = start; j < n - loop; j++) {
                result[start][j] = count;
                count++;
            }

            for (i = start; i < n - loop; i++) {
                result[i][j] = count;
                count++;
            }

            for (; j >= loop; j--) {
                result[i][j] = count;
                count++;
            }

            for (; i >= loop; i--) {
                result[i][j] = count;
                count++;
            }
            start++;
        }

        if (n % 2 == 1) {
            result[start][start] = count;
        }

        return result;
    }
}
```

c#
```csharp
public class Solution {
    public int[][] GenerateMatrix(int n) {
        int loop = 0;
        int[][] result = new int[n][];
        
        // Initialize the jagged array in C#
        for (int k = 0; k < n; k++) {
            result[k] = new int[n];
        }
        
        int start = 0;
        int count = 1;
        int i, j;
        
        while (loop++ < n / 2) {
            for (j = start; j < n - loop; j++) {
                result[start][j] = count;
                count++;
            }
            for (i = start; i < n - loop; i++) {
                result[i][j] = count;
                count++;
            }
            for (; j >= loop; j--) {
                result[i][j] = count;
                count++;
            }
            for (; i >= loop; i--) {
                result[i][j] = count;
                count++;
            }
            start++;
        }
        
        if (n % 2 == 1) {
            result[start][start] = count;
        }
        
        return result;
    }
}
```

- Initialization: Creates an n x n result matrix. Initializes loop to 0 (layer counter), start to 0 (starting index for each layer), and count to 1 (the number to fill into the matrix).

- Iterative Layer Filling: The while (loop++ < n / 2) loop processes the layers. n / 2 calculates the number of full layers to process.(For every two steps inwards (one from the top/bottom and one from the left/right), you complete a full layer. Therefore, we only need to iterate up to approximately half the dimension of the matrix.) The loop++ increments the loop counter after its value is used in the comparison. so it has to be inside the condition.

- Four inner for loops fill the top row (left to right), right column (top to bottom), bottom row (right to left), and left column (bottom to top) of the current layer. start is incremented to move to the next inner layer.

- Handling Odd n: If n is odd, the center element is filled after the loop.

- Time Complexity: O(n2). The code iterates through all n2 elements of the matrix exactly once to fill them. The four inner loops combined iterate a total of n2 times.

- Space Complexity: O(n2). The code uses a 2D array (the result matrix) of size n×n to store the generated matrix. The space used scales with the square of the input size.