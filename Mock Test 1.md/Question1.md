**Question 1:Substring with Unique Characters and Length Constraint**

**Solution in Python**
```java
def longest_unique_substring_with_min_len(s: str, k: int) -> str:
    n = len(s)
    if n == 0:
        return "-1"

    max_len = 0
    start_index = -1
    
    char_map = {}
    left = 0

    for right in range(n):
        char = s[right]
        if char in char_map and char_map[char] >= left:
            left = char_map[char] + 1
        
        char_map[char] = right

        current_len = right - left + 1
        
        if current_len > max_len:
            max_len = current_len
            start_index = left

    if max_len >= k:
        return s[start_index : start_index + max_len]
    else:
        return "-1"

# Main execution block for taking input
s_val = input() 
k_val = int(input()) 
result = longest_unique_substring_with_min_len(s_val, k_val)
print(result)

```
**Solution in Java**
```java
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner; 

public class LongestUniqueSubstring {

    public static String longestUniqueSubstringWithMinLen(String s, int k) {
        int n = s.length();
        if (n == 0) {
            return "-1";
        }

        int maxLen = 0;
        int startIndex = -1;
        
        Map<Character, Integer> charMap = new HashMap<>();
        int left = 0;

        for (int right = 0; right < n; right++) {
            char currentChar = s.charAt(right);
            
            if (charMap.containsKey(currentChar) && charMap.get(currentChar) >= left) {
                left = charMap.get(currentChar) + 1;
            }
            
            charMap.put(currentChar, right);

            int currentLen = right - left + 1;
            
            if (currentLen > maxLen) {
                maxLen = currentLen;
                startIndex = left;
            }
        }

        if (maxLen >= k) {
            return s.substring(startIndex, startIndex + maxLen);
        } else {
            return "-1";
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s_val = scanner.nextLine(); 
        int k_val = Integer.parseInt(scanner.nextLine()); 
        String result = longestUniqueSubstringWithMinLen(s_val, k_val);
        System.out.println(result);
        scanner.close();
    }
}

```
