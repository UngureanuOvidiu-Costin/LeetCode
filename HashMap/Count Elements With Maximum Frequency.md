```Java
class Solution {
    public int maxFrequencyElements(int[] nums) {
        HashMap<Integer, Integer> occurence = new HashMap<>();
        int i;
        int max = 0;
        for(i = 0; i < nums.length; i = i + 1){
            occurence.put(nums[i], occurence.getOrDefault(nums[i], 0) + 1);
            if(max < occurence.get(nums[i])){
                max = occurence.get(nums[i]);
            }
        }

        int result = 0;
        for(Integer nr: occurence.keySet()){
            if(occurence.get(nr) == max){
                result = result + max;
            }
        }

        return result;
    }
}
```
