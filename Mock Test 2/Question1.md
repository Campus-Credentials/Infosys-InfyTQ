**Question 1:Minimum Jumps to Reach End**

**Solution in Python**
```java
def min_jumps(arr_str: str) -> int:
    arr = list(map(int, arr_str.split()))
    n = len(arr)

    if n <= 1:
        return 0

    if arr[0] == 0:
        return -1

    jumps = 0
    current_end = 0
    farthest = 0

    for i in range(n):
        if i > farthest:
            return -1

        farthest = max(farthest, i + arr[i])

        if i == current_end:
            jumps += 1
            current_end = farthest

            if current_end >= n - 1:
                return jumps
    
    return -1 # Should only be reached if end is unreachable, which current_end < n - 1 implies

# Main execution block for taking input
arr_str_val = input()
result = min_jumps(arr_str_val)
print(result)

```
**Solution in Java**
```java
import java.util.Scanner;
import java.util.Arrays;

public class MinJumps {

    public static int minJumps(int[] arr) {
        int n = arr.length;

        if (n <= 1) {
            return 0;
        }

        if (arr[0] == 0) {
            return -1;
        }

        int jumps = 0;
        int currentEnd = 0;
        int farthest = 0;

        for (int i = 0; i < n; i++) {
            if (i > farthest) {
                return -1;
            }

            farthest = Math.max(farthest, i + arr[i]);

            if (i == currentEnd) {
                jumps++;
                currentEnd = farthest;

                if (currentEnd >= n - 1) {
                    return jumps;
                }
            }
        }
        
        return -1;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String[] arrStr = scanner.nextLine().split(" ");
        int[] arr = new int[arrStr.length];
        for (int i = 0; i < arrStr.length; i++) {
            arr[i] = Integer.parseInt(arrStr[i]);
        }
        
        int result = minJumps(arr);
        System.out.println(result);
        scanner.close();
    }
}

```
