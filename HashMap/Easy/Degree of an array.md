```Java
class Solution {
    public int findShortestSubArray(int[] nums) {

        if(nums.length == 1){
            return 1;
        }

        HashMap<Integer, Integer> left = new HashMap<>();
        HashMap<Integer, Integer> right = new HashMap<>();
        HashMap<Integer, Integer> count = new HashMap<>();
        int i, max = 0;

        for(i = 0; i < nums.length; i = i + 1){
            if(!count.containsKey(nums[i])){
                count.put(nums[i], 1);
                left.put(nums[i], i);
            }else {
                count.put(nums[i], count.get(nums[i]) + 1);
                
            }
            right.put(nums[i], i);
        }

        int result = nums.length;
        int degree = Collections.max(count.values());
        for(int x: count.keySet()){
            if(count.get(x) == degree){
                result = Math.min(result, right.get(x) - left.get(x) + 1);
            }
        }
        
        return result;
    }
}
```
