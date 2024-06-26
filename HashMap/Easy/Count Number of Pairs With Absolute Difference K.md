# Solution

## Intuition

We can use a HashMap to check each element frequency as we need all possible pairs and duplicates are counted.

## Approach

1. Initialize a `counter` variable with `0`, it will contain the result.
2. Create a HashMap to store the frequency of each element.
3. Iterate over each element form `nums` and update it's frequency.
4. Iterate again over each element from `nums` and check if the frequency of `nums[i] + k` is present in the HashMap. If it is, update the `counter` with `nums[i] + k`'s frequency from the HashMap.
5. Return the `counter`.

## Complexity

- Time complexity: `O(N)`
Note `nums.length` with `N`.
First it takes `O(N)` to iterate over the array named `nums` and to update the HashMap.
Second it takes `O(N)` to iterate over the `nums` again to update the `counter`.
P.S.: `hashMap.put(nums[i], hashMap.getOrDefault(nums[i], 0) + 1);` takes O(1).
This also takes O(1):

```Java
if(hashMap.containsKey(temp)){
    counter = counter + hashMap.get(temp);
}
```

The total time complexity is the sum of: `O(N) + O(N) + O(1) + O(1) = 2 * O(N) = O(N)`

- Space complexity:
As the **constraints** specified, the interval of `nums[i]` is `1 <= nums[i] <= 100` so the HashMap will contain a maximum of `100` keys. Also the **constraints** mentioned that there will be a maximum of `200` values. This means that the hash map will contain a maximum of `100` keys, this remains unchanged. This results in `O(1)`.
The variable `i`, `counter`, `temp` also uses `O(1)`.
The result is O(1).

## Code

```Java
class Solution {
    public int countKDifference(int[] nums, int k) {
        HashMap<Integer, Integer> hashMap = new HashMap<Integer, Integer>();
        int i, counter = 0, temp;
        for(i = 0; i < nums.length; i = i + 1) {
            hashMap.put(nums[i], hashMap.getOrDefault(nums[i], 0) + 1);
        }

        for(i = 0; i < nums.length; i = i + 1) {
            temp = nums[i] + k;
            if(hashMap.containsKey(temp)){
                counter = counter + hashMap.get(temp);
            }
        }

        return counter;
    }
}
```
