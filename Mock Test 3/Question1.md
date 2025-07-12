**Question 1:Number of Islands**

**Solution in Python**
```java
def num_islands(grid_data: list[str]) -> int:
    if not grid_data or not grid_data[0]:
        return 0

    grid = [list(row) for row in grid_data] # Convert strings to list of chars for mutability
    m = len(grid)
    n = len(grid[0])
    num_islands_count = 0

    def dfs(r, c):
        # Base cases: out of bounds or water
        if r < 0 or r >= m or c < 0 or c >= n or grid[r][c] == '0':
            return
        
        # Mark as visited (turn land into water)
        grid[r][c] = '0'

        # Explore neighbors
        dfs(r + 1, c)
        dfs(r - 1, c)
        dfs(r, c + 1)
        dfs(r, c - 1)

    for r in range(m):
        for c in range(n):
            if grid[r][c] == '1':
                num_islands_count += 1
                dfs(r, c) # Explore the entire island
                
    return num_islands_count

# Main execution block for taking input
if __name__ == "__main__":
    m, n = map(int, input().split())
    grid_rows = []
    for _ in range(m):
        grid_rows.append(input())
    
    result = num_islands(grid_rows)
    print(result)

```
**Solution in Java**
```java
import java.util.Scanner;

public class NumberOfIslands {

    public static int numIslands(char[][] grid) {
        if (grid == null || grid.length == 0 || grid[0].length == 0) {
            return 0;
        }

        int m = grid.length;
        int n = grid[0].length;
        int numIslandsCount = 0;

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                if (grid[r][c] == '1') {
                    numIslandsCount++;
                    dfs(grid, r, c, m, n); // Explore the entire island
                }
            }
        }
        
        return numIslandsCount;
    }

    private static void dfs(char[][] grid, int r, int c, int m, int n) {
        // Base cases: out of bounds or water
        if (r < 0 || r >= m || c < 0 || c >= n || grid[r][c] == '0') {
            return;
        }
        
        // Mark as visited (turn land into water)
        grid[r][c] = '0';

        // Explore neighbors
        dfs(grid, r + 1, c, m, n);
        dfs(grid, r - 1, c, m, n);
        dfs(grid, r, c + 1, m, n);
        dfs(grid, r, c - 1, m, n);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int m = scanner.nextInt();
        int n = scanner.nextInt();
        scanner.nextLine(); // Consume the newline character

        char[][] grid = new char[m][n];
        for (int i = 0; i < m; i++) {
            String row = scanner.nextLine();
            grid[i] = row.toCharArray();
        }
        
        int result = numIslands(grid);
        System.out.println(result);
        scanner.close();
    }
}

```
