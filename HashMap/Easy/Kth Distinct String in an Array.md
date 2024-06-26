# Intuition

To find the k-th distinct string in an array, first count the frequency of each string while maintaining their order of appearance using a LinkedHashMap. Then, iterate through the map to identify the k-th string that appears exactly once.

## Approach

1. Build a map which will contain the frequency of each **String**.
2. Iterate over the keys in the map in the order that they were inserted.
3. Check if an element is unique and increment the `i`.
4. Return the `k-th` element(String) when `i` == `k`.

## Complexity

- Time complexity:

```Java
for (i = 0; i < arr.length; i++) { 
    frequency.put(arr[i], frequency.getOrDefault(arr[i], 0) + 1); 
}
```

This loop iterates over the array arr once, performing a put operation for each element.
In a LinkedHashMap, the `put` and `getOrDefault` operations both have an average time complexity of `O(1)`.
Therefore, this part of the code runs in O(n) time, where n is the length of the array `arr`.

```Java
for (String key : frequency.keySet()) { ... }
```

This loop iterates over the keys of the `LinkedHashMap`, which in the worst case could be all elements of `arr` if all elements are **unique**.
Inside the loop, checking the frequency and incrementing the counter both take `O(1)` time.
Therefore, this part of the code also runs in `O(n)` time, where n is the number of elements in the array `arr`.

- Space complexity:
The `LinkedHashMap` stores a mapping from each unique string in the array arr to its frequency count. In the worst case, if all elements in arr are **unique**, the `LinkedHashMap` will store `N` entries.
Each entry consists of a key (the string) and a value (the integer frequency count). The space required for storing these entries is `O(n)`.
The integer variables `i`, and `counter`, each require O(1) space.

```Java
class Solution {
    public String kthDistinct(String[] arr, int k) {
        LinkedHashMap<String, Integer> frequency = new LinkedHashMap<>();
        int i;
        
        for(i = 0; i < arr.length; i = i + 1) {
            frequency.put(arr[i], frequency.getOrDefault(arr[i], 0 ) + 1);
        }

        i = 0;
        for(String key: frequency.keySet()) {
            if(frequency.get(key) == 1) {
                i = i + 1;
            }
            if(i == k){
                return key;
            }
        }

        return "";
    }
}
```
