**Question 1:Count Subarrays with Product Less Than K**

**Solution in Python**
```java
def num_subarray_product_less_than_k(nums_str: str, k: int) -> int:
    nums = list(map(int, nums_str.split()))
    
    if k <= 1:
        return 0

    product = 1
    left = 0
    count = 0

    for right in range(len(nums)):
        product *= nums[right]
        
        while product >= k:
            product //= nums[left]
            left += 1
        
        count += (right - left + 1)
        
    return count

# Main execution block for taking input
nums_str_val = input()
k_val = int(input())
result = num_subarray_product_less_than_k(nums_str_val, k_val)
print(result)

```
**Solution in Java**
```java
import java.util.Scanner;
import java.util.Arrays;

public class CountSubarraysProductLessThanK {

    public static int numSubarrayProductLessThanK(int[] nums, int k) {
        if (k <= 1) {
            return 0;
        }

        long product = 1;
        int left = 0;
        int count = 0;

        for (int right = 0; right < nums.length; right++) {
            product *= nums[right];
            
            while (product >= k) {
                product /= nums[left];
                left++;
            }
            
            count += (right - left + 1);
        }
        
        return count;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String[] numsStr = scanner.nextLine().split(" ");
        int[] nums = new int[numsStr.length];
        for (int i = 0; i < numsStr.length; i++) {
            nums[i] = Integer.parseInt(numsStr[i]);
        }
        
        int k = Integer.parseInt(scanner.nextLine());
        
        int result = numSubarrayProductLessThanK(nums, k);
        System.out.println(result);
        scanner.close();
    }
}

```
