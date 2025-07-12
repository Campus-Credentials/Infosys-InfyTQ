**Question 2: Coin Change II (Combinations)**

**Solution in Python**
```java
def coin_change_combinations(coins_str: str, amount: int) -> int:
    coins = list(map(int, coins_str.split()))

    # dp[i] will be the number of ways to make amount i
    dp = [0] * (amount + 1)
    dp[0] = 1 # There is one way to make amount 0 (by choosing no coins)

    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] += dp[i - coin]
            
    return dp[amount]

# Main execution block for taking input
if __name__ == "__main__":
    coins_str_val = input()
    amount_val = int(input())
    result = coin_change_combinations(coins_str_val, amount_val)
    print(result)
```
**Solution in Java**
```java
import java.util.Scanner;
import java.util.Arrays;

public class CoinChangeII {

    public static int coinChangeCombinations(int[] coins, int amount) {
        // dp[i] will be the number of ways to make amount i
        int[] dp = new int[amount + 1];
        dp[0] = 1; // There is one way to make amount 0 (by choosing no coins)

        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] += dp[i - coin];
            }
        }
        
        return dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String[] coinsStr = scanner.nextLine().split(" ");
        int[] coins = new int[coinsStr.length];
        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }
        
        int amount = Integer.parseInt(scanner.nextLine());
        
        int result = coinChangeCombinations(coins, amount);
        System.out.println(result);
        scanner.close();
    }
}

```
