# Solution

```Java
class Solution {
    public int findTheWinner(int n, int k) {
        if (n == 1) {
            return 1;
        }

        int winner = (findTheWinner(n - 1, k) + k) % n;
        return winner == 0 ? n : winner;
    }
}
```
