```Java
class Solution {
    public int sumOfUnique(int[] nums) {
        HashMap<Integer, Integer> frequency = new HashMap<>();
        int i;
        int sum = 0;
        for(i = 0; i < nums.length; i = i + 1){
            frequency.put(nums[i], frequency.getOrDefault(nums[i], 0) + 1);
        }
        
        for(Integer number: frequency.keySet()){
            if(frequency.get(number) == 1){
                sum = sum + number;
            }
        }
        
        return sum;
    }
}
```
