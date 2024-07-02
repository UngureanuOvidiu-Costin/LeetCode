# Solution

```Java
class Solution {
    public int minOperations(List<Integer> nums, int k) {
        Set<Integer> kNums = new HashSet<>();
        int i, counter = 0;
        
        for(i = nums.size() - 1; i >= 0; i = i - 1) {
            if(nums.get(i) <= k){
                kNums.add(nums.get(i));

                if(kNums.size() == k){
                    return counter+1;
                }
            }
            counter++;
        }

        return counter+1;
    }
}
```
