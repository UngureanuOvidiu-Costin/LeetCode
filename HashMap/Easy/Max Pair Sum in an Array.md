```Java
class Solution {
    public int maxSum(int[] nums) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        int result = Integer.MIN_VALUE, maxDigit;
        for(final int number: nums){
            maxDigit = findMaxDigit(number);
            if(hashMap.containsKey(maxDigit)){
                result = Math.max(result, number + hashMap.get(maxDigit));
            }
            hashMap.put(maxDigit, Math.max(number, hashMap.getOrDefault(maxDigit, 0)));
        }

        if(result != Integer.MIN_VALUE){
            return result;
        }

        return -1;
    }

    public int findMaxDigit(long number) {
        int maxDigit = 0;
        while (number > 0) {
            int digit = (int) (number % 10);
            maxDigit = Math.max(maxDigit, digit);
            number /= 10;
        }
        return maxDigit;
    }
}
```
