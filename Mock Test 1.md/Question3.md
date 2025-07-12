**Question 3:Longest Palindromic Subsequence with Deletions**

**Solution in Python**
```java
def longest_palindromic_subsequence(s: str) -> int:
    n = len(s)
    if n == 0:
        return 0
    
    dp = [[0] * n for _ in range(n)]

    for i in range(n):
        dp[i][i] = 1

    for length in range(2, n + 1):
        for i in range(n - length + 1):
            j = i + length - 1
            if s[i] == s[j]:
                dp[i][j] = 2 + (dp[i+1][j-1] if i + 1 <= j - 1 else 0)
            else:
                dp[i][j] = max(dp[i+1][j], dp[i][j-1])
                
    return dp[0][n-1]

# Main execution block for taking input
s_val = input() 
result = longest_palindromic_subsequence(s_val)
print(result)

```
**Solution in Java**
```java
import java.util.Scanner; 

public class LongestPalindromicSubsequence {

    public static int longestPalindromicSubsequence(String s) {
        int n = s.length();
        if (n == 0) {
            return 0;
        }

        int[][] dp = new int[n][n];

        for (int i = 0; i < n; i++) {
            dp[i][i] = 1;
        }

        for (int length = 2; length <= n; length++) {
            for (int i = 0; i <= n - length; i++) {
                int j = i + length - 1;
                if (s.charAt(i) == s.charAt(j)) {
                    dp[i][j] = 2 + ( (i + 1 <= j - 1) ? dp[i+1][j-1] : 0 );
                } else {
                    dp[i][j] = Math.max(dp[i+1][j], dp[i][j-1]);
                }
            }
        }
                
        return dp[0][n-1];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s_val = scanner.nextLine(); 
        int result = longestPalindromicSubsequence(s_val);
        System.out.println(result);
        scanner.close();
    }
}

```
