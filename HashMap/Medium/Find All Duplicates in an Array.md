```Java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        Set<Integer> result = new HashSet<>();
        int i;
        int n = nums.length;
        for(i = 0; i < nums.length; i = i + 1) {
            int temp = nums[i];
            if(temp < 0){
                temp = temp * -1;
            }

            if (nums[temp % n] > 0) {
                nums[temp % n] = nums[temp % n] * -1;
            }else {
                result.add(temp);
            }
        }
        return new ArrayList<>(result);
    }
}
```
