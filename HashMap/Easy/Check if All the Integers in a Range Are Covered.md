# Solution

```Java
class Solution {
    public boolean isCovered(int[][] ranges, int left, int right) {
        int i, check = 1;
        boolean[] covered = new boolean[51];

        for (i = 0; i < ranges.length; i++) {
            int start = ranges[i][0];
            int end = ranges[i][1];
            for (int j = start; j <= end; j++) {
                covered[j] = true;
            }
        }

        for(i = left; i <= right; i = i + 1) {
            if(covered[i] == false){
                return false;
            }
        }

        return true;
    }
}
```
