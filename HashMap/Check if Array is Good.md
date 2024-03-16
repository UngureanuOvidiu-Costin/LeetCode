```Java
class Solution {
    public boolean isGood(int[] nums) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        int i;
        int max = Integer.MIN_VALUE;
        for(i = 0; i < nums.length; i = i + 1){
            hashMap.put(nums[i], hashMap.getOrDefault(nums[i], 0) + 1);
            if(nums[i] > max){
                max = nums[i];
            }
        }

        boolean result = true;
        for(i = 1; i < max; i = i + 1){
            if(!hashMap.containsKey(i) || hashMap.get(i) != 1){
                result = false;
                break;
            }
        }

        return result && max == nums.length - 1;
    }
}
```
