# Intuition

The problem is to determine whether there are three consecutive odd numbers in a given array. We can solve this by iterating through the array and checking every triplet of consecutive elements.

## Approach

1. **Edge Case Handling:** First, check if the array has fewer than three elements. If so, return `false` since it's impossible to have three consecutive elements.
2. **Check Consecutive Elements:** Iterate through the array, starting from the first element and going up to the third-to-last element. For each element, check if it and the next two elements are odd. If any such triplet is found, return `true`.
3. **Return Result:** If no such triplet is found, return `false`.

## Complexity

- Time complexity:
**Iteration:** The loop iterates through the array once, stopping at the third-to-last element. This gives a time complexity of `O(n)`, where `n` is the length of the array.

- Space complexity:
**Auxiliary Space:** The algorithm uses a constant amount of extra space for variables and does not require additional data structures proportional to the input size. Thus, the space complexity is `O(1)`.

## Code

```Java
class Solution {
    public boolean threeConsecutiveOdds(int[] arr) {
        int i;

        if(arr.length < 3) {
            return false;
        }

        if(arr[0] % 2 == 1 && arr[1] % 2 == 1 && arr[2] % 2 == 1) {
            return true;
        }

        for(i = 1; i < arr.length - 2; i = i + 1) {
            if(arr[i] % 2 == 1 && arr[i + 1] % 2 == 1  && arr[i + 1] % 2 == 1) {
                return true;
            }
        }

        return false;
    }
}
```
