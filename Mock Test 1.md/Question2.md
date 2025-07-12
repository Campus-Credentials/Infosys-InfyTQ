**Question 2:Minimize Operations to Make Array Elements Equal**

**Solution in Python**
```java
import math

def min_cost_equalize_array_func(arr_str: str, c1: int, c2: int) -> int:
    arr = list(map(int, arr_str.split()))
    n = len(arr)
    if n == 0:
        return 0
    if n == 1:
        return 0

    arr.sort()

    min_total_cost = float('inf')

    for target_x in arr:
        current_cost = 0
        for num in arr:
            if num < target_x:
                current_cost += (target_x - num) * c1
            elif num > target_x:
                current_cost += (num - target_x) * c2
        min_total_cost = min(min_total_cost, current_cost)
    
    return min_total_cost

# Main execution block for taking input
arr_str_val = input() 
c1_val = int(input()) 
c2_val = int(input()) 
result = min_cost_equalize_array_func(arr_str_val, c1_val, c2_val)
print(result)

```
**Solution in Java**
```java
import java.util.Arrays;
import java.util.Scanner; 

public class MinCostEqualizeArray {

    public static long minCostEqualizeArray(int[] arr, int c1, int c2) {
        int n = arr.length;
        if (n == 0) {
            return 0;
        }
        if (n == 1) {
            return 0;
        }

        Arrays.sort(arr);

        long minTotalCost = Long.MAX_VALUE;

        for (int targetX : arr) {
            long currentCost = 0;
            for (int num : arr) {
                if (num < targetX) {
                    currentCost += (long) (targetX - num) * c1;
                } else if (num > targetX) {
                    currentCost += (long) (num - targetX) * c2;
                }
            }
            minTotalCost = Math.min(minTotalCost, currentCost);
        }
        
        return minTotalCost;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String[] arr_str = scanner.nextLine().split(" "); 
        int[] arr_val = new int[arr_str.length];
        for (int i = 0; i < arr_str.length; i++) {
            arr_val[i] = Integer.parseInt(arr_str[i]);
        }
        int c1_val = Integer.parseInt(scanner.nextLine()); 
        int c2_val = Integer.parseInt(scanner.nextLine()); 
        long result = minCostEqualizeArray(arr_val, c1_val, c2_val);
        System.out.println(result);
        scanner.close();
    }
}

```
