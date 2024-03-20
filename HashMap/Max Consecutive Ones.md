```Java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int nr = 0, max = 0;
        int i;

        for(i = 0; i < nums.length; i = i + 1) {
            if(nums[i] == 1){
                nr++;
            }else {
                nr = 0;
            }
            
            if(nr > max){
                max = nr;
            }
        }

        return max;
    }
}
```
