```Java
class Solution {
    public int mostFrequentEven(int[] nums) {
        HashMap<Integer, Integer> frequency = new HashMap<>();
        int maxFrequency = 0, number = -1;
        int i;

        for(i = 0; i < nums.length; i = i + 1){
            if(nums[i] % 2 == 0) {
                frequency.put(nums[i], frequency.getOrDefault(nums[i], 0) + 1);
                if (frequency.get(nums[i]) > maxFrequency) {
                    maxFrequency = frequency.get(nums[i]);
                    number = nums[i];
                }
                
                if(frequency.get(nums[i]) == maxFrequency && nums[i] < number){
                    number = nums[i];
                }
            }
        }

        return maxFrequency == 0 ? -1 : number;
    }
}
```
