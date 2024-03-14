```Java
class Solution {
    public int[] findMissingAndRepeatedValues(int[][] grid) {
        int size = grid.length;
        int i, j;
        int sum = 0;
        HashMap<Integer, Integer> frequency = new HashMap<>();
        int duplicate = 0;
        for (i = 0; i < grid.length; i = i + 1) {
            for(j = 0; j < grid.length; j = j + 1){
                frequency.put(grid[i][j], frequency.getOrDefault(grid[i][j], 0) + 1);
                sum = sum + grid[i][j];
                if(frequency.get(grid[i][j]) == 2){
                    duplicate = grid[i][j];
                    sum = sum - grid[i][j];
                }
            }
        }

        int totalSum = (1 + grid.length* grid.length) * grid.length*grid.length / 2;
        int[] result = {duplicate, totalSum-sum};
        return result;
    }
}
```
