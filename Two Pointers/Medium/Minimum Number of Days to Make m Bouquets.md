```Java
class Solution {
    public int minDays(int[] bloomDay, int m, int k) {
        if (((long)m * k) > bloomDay.length) {
            return -1;
        }

        int left = Arrays.stream(bloomDay).min().getAsInt();
        int right = Arrays.stream(bloomDay).max().getAsInt();
        int mid;
        while(left < right){
            mid = left + (right - left) / 2;
            if(getBouquetCount(bloomDay, k, mid) >= m){
                right = mid;
            }else{
                left = mid + 1;
            }
        }

        return left;
    }

    private int getBouquetCount(int[] bloomDay, int k, int waitingDays) {
        int bouquetCount = 0;
        int requiredFlowers = k;
        for (final int day : bloomDay)
            if (day > waitingDays) {
                requiredFlowers = k;
            } else if (--requiredFlowers == 0) {
                ++bouquetCount;
                requiredFlowers = k;
            }
        return bouquetCount;
    }
}
```