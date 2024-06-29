# Solution

```Java
class Solution {
    public int[] maxSubsequence(int[] nums, int k) {

        List<int[]> pairs = new ArrayList<>();
        for (int i = 0; i < nums.length; i++) {
            pairs.add(new int[]{nums[i], i});
        }
        
        pairs.sort((a, b) -> b[0] - a[0]);
        
        List<int[]> selected = pairs.subList(0, k);
        
        selected.sort(Comparator.comparingInt(a -> a[1]));
        
        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = selected.get(i)[0];
        }
        
        return result;
    }
}
```
