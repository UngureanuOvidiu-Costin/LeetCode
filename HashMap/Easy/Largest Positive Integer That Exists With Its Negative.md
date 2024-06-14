```Java
class Solution {
    public int findMaxK(int[] nums) {
        HashMap<Integer, Integer> frequency = new HashMap<>();
        int i;
        for(i = 0 ; i < nums.length; i = i + 1){
            frequency.put(nums[i], frequency.getOrDefault(nums[i], 0) + 1);
        }

        int max = 0;
        for(Integer nr: frequency.keySet()){
            if(frequency.containsKey(-nr)){
                if(Math.abs(nr) > max){
                    max = Math.abs(nr);
                }
            }
        }

        if(max != 0){
            return max;
        }
        return -1;
    }
}
```
