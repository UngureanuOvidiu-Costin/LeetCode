# Intuition
The sequence is built recursively.  
We start with `S1 = "0"` and each next string is constructed using the rule:
`Si = Si-1 + "1" + reverse(invert(Si-1)`

Where:
- `invert` flips every bit (`0 → 1`, `1 → 0`)
- `reverse` reverses the resulting string.

Because the constraints for `n` are small (the length of `Sn` is at most \(2^n - 1\)), we can directly build the string step by step until we reach `Sn`, then return the `k`-th character.


# Approach
1. Start with the base string `s = "0"`.
2. For each level from `2` to `n`:
   - Save the previous string `prev`.
   - Create an inverted version of `prev` by flipping each bit.
   - Reverse the inverted string.
   - Construct the new string as:
     ```
     s = prev + "1" + reversed_inverted_prev
     ```
3. After building `Sn`, return the character at index `k - 1`.

# Complexity
- Time complexity:  
  \(O(2^n)\) — because the length of the final string grows to \(2^n - 1\), and we process it during construction.

- Space complexity:  
  \(O(2^n)\) — we store the entire string `Sn`.

# Code
```java []
class Solution {
    public char findKthBit(int n, int k) {
        String s = "0";

        for (int i = 2; i <= n; i++) {
            String prev = s;
            StringBuilder inverted = new StringBuilder();

            for (char c : prev.toCharArray()) {
                inverted.append(c == '0' ? '1' : '0');
            }

            inverted.reverse();
            s = prev + "1" + inverted.toString();
        }

        return s.charAt(k - 1);
    }
}
```
