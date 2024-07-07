# Intuition

The problem requires calculating the total number of water bottles one can drink given that empty bottles can be exchanged for full ones. This can be solved by repeatedly exchanging empty bottles for full ones until no more exchanges are possible.

## Approach

1. **Initialization**: Start with the initial number of full water bottles as the result.

2. **Loop**: Continue exchanging empty bottles for full ones until the number of bottles is less than the number needed for an exchange (`numExchange`):
   - For each iteration, add the number of new bottles obtained through exchange to the result.
   - Update the number of bottles to the sum of the new bottles obtained and the remainder of the division of bottles by `numExchange`.

3. **Return**: The result will be the total number of bottles consumed.

## Complexity

- **Time complexity**: O(log n), where `n` is the initial number of bottles. This is because with each exchange, the number of bottles decreases logarithmically.

- **Space complexity**: O(1), since we are using a constant amount of extra space.

## Code

```Java
class Solution {
    public int numWaterBottles(int numBottles, int numExchange) {
        int result = numBottles;
        while(numBottles / numExchange > 0){
            result = result + numBottles / numExchange;
            numBottles = numBottles / numExchange + numBottles % numExchange;
        }

        return result;
    }
}
```
