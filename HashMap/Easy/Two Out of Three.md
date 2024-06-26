# Intuition

As we only need unique elements in these arrays and to perform an intersection over these unique elements.

## Approach

1. Initialize three `Set`s, one for each array and one for the result.
2. Populate each `Set` with values from corresponding array.
3. Perform an intersection between thses three `Set`s and store the intersection in the `Set` used to store the result.
4. Convert the `result Set` into an ArrayList and return it.

## Complexity

- Time complexity:
If we note `N` the number of elements in the each array, this being the maximum, we iterate over each array individually one time, ths takes `3 * O(N) = O(N)` because we have three arrays.
Next, we iterate over each Set, in worst-case each one contains only unique elements so this will take `3 * O(N) = O(N)`.
Computing the final `Set` which will contain thre result, takes about `O(N)`.
Computing the ArrayList also takes about `O(N)`.
The final result: `O(N)`.

- Space complexity:
If we have `N` elements at most in each array, we will temporarily use 3 * O(N) to store unique values using `Set`. `3 * O(N) = O(N)`
After that we will use another Set to store common values. In worst case, all values are common and we will use the same `O(N)`.
After that we will free the space of forst three `Set`s because they are not needed anymore.
We create a new ArrayList to return the result which also takes a maximum of `O(N)`.
Total amount of space allocated: `O(N)`.

```Java
class Solution {
    public List<Integer> twoOutOfThree(int[] nums1, int[] nums2, int[] nums3) {
        Set<Integer> hashMap1 = new HashSet<>();
        Set<Integer> hashMap2 = new HashSet<>();
        Set<Integer> hashMap3 = new HashSet<>();
        Set<Integer> resultSet = new HashSet<>();
        int i;
        
        for(i = 0 ; i < nums1.length; i = i + 1) {
            hashMap1.add(nums1[i]);
        }

        for(i = 0 ; i < nums2.length; i = i + 1) {
            hashMap2.add(nums2[i]);
        }

        for(i = 0 ; i < nums3.length; i = i + 1) {
            hashMap3.add(nums3[i]);
        }

        for(Integer key: hashMap1) {
            if(hashMap2.contains(key)) {
                resultSet.add(key);
                hashMap2.remove(key);
            }

            if(hashMap3.contains(key)) {
                resultSet.add(key);
                hashMap3.remove(key);
            }
        }

        for(Integer key: hashMap2) {
            if(hashMap1.contains(key)) {
                resultSet.add(key);
            }

            if(hashMap3.contains(key)) {
                resultSet.add(key);
                hashMap3.remove(key);
            }
        }

        hashMap1.clear();
        hashMap2.clear();
        hashMap3.clear();
        List<Integer> integerList = new ArrayList<>(resultSet);

        return integerList;
    }
}
```
