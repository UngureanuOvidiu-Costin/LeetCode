```Java
class Solution {
    public int repeatedNTimes(int[] nums) {
        HashMap<Integer, Integer> frequency = new HashMap<>();

        int i;
        for(i = 0; i < nums.length; i = i + 1){
            frequency.put(nums[i], frequency.getOrDefault(nums[i], 0) + 1);
            if(frequency.get(nums[i]) > 1){
                return nums[i];
            }
        }
        return -1;
    }
}

```
