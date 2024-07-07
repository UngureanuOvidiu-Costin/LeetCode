# Solution

```Java
class Solution {
    public void moveZeroes(int[] nums) {
        int k = 0;
        int i;

        for(i = 0; i < nums.length; i = i + 1) {
            if(nums[i] != 0) {
                nums[k] = nums[i];
                k = k + 1;
            }
        }

        for(i = k; i < nums.length; i = i + 1) {
            nums[i] = 0;
        }
    }
}
```
