# Solution

```Java
class Solution {
    public int mostFrequent(int[] nums, int key) {
        HashMap<Integer, Integer> frequencyMap = new HashMap<>();
        int i;
        int maxFrequency = 0;
        int max = -1;

        for(i = 0; i < nums.length - 1; i = i + 1) {
            if(nums[i] == key) {
                frequencyMap.put(nums[i + 1], frequencyMap.getOrDefault(nums[i + 1], 0) + 1);
            }
        }

        for(Integer tempKey: frequencyMap.keySet()) {
            if(frequencyMap.get(tempKey) > maxFrequency) {
                max = tempKey;
                maxFrequency = frequencyMap.get(tempKey);
            }
        }

        return max;
    }
}
```
