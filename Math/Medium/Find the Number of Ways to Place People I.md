```Java
class Solution {
    public int numberOfPairs(int[][] points) {
        int i, j, aY, bY, result = 0;
        boolean check;

        Arrays.sort(points, (a, b) -> {
            if (a[0] != b[0]) return Integer.compare(a[0], b[0]);
            return Integer.compare(b[1], a[1]);
        });

        for(i = 0; i < points.length - 1; i = i + 1) {
            aY = points[i][1];
            int maxY = Integer.MIN_VALUE;

            for(j = i + 1; j < points.length; j = j + 1) {
                bY = points[j][1];

                if(aY >= bY && bY > maxY){
                    maxY = bY;
                    result++;
                }
            }
        }

        return result;
    }
}
```
