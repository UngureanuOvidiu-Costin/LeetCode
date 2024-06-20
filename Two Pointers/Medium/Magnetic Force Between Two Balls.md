# Solution

```Java
class Solution {
    public int maxDistance(int[] position, int m) {
        Arrays.sort(position);
        
        int left = 1;
        int right = position[position.length - 1];
        int mid;
        while (left < right) {
            mid = (left + right + 2) >>> 1;

            if(isFeasible(position, mid, m)){
                left = mid;
            }else{
                right = mid - 1;
            }
        }

        return left;
    }

    private boolean isFeasible(int[] position, int distance, int maxDistance) {
        int previousPosition = position[0];
        int count = 1;
        int i;

        for(i = 1; i < position.length; i = i + 1) {
            if(position[i] - previousPosition >= distance){
                count = count + 1;
                previousPosition = position[i];
            }            
        }

        return count >= maxDistance;
    }
}
```
