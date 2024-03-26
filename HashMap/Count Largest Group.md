```Java
class Solution {
    public int countLargestGroup(int n) {
        HashMap<Integer, Integer> digitsSums = new HashMap<>();
        int i, tempSum;
        for(i = 1; i <= n; i = i + 1){
            tempSum = getDigitSum(i);
            digitsSums.put(tempSum, digitsSums.getOrDefault(tempSum, 0) + 1);
        }

        int max = Integer.MIN_VALUE;
        for(int count: digitsSums.values()){
            max = Math.max(max, count);
        }

        int count = 0;
        for(int groupSize: digitsSums.values()){
            if(groupSize == max){
                count = count + 1;
            }
        }

        return count;
    }

    private int getDigitSum(int num) {
        int sum = 0;
        while (num > 0) {
            sum += num % 10;
            num /= 10;
        }
        return sum;
    }
}
```
