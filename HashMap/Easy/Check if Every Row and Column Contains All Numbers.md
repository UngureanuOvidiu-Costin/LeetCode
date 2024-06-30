# Solution

```Java
class Solution {
    public boolean checkValid(int[][] matrix) {
        int size = matrix.length;
        int i, j;

        for (i = 0;  i < size; ++ i) {
            boolean[] check = new boolean[size];
            for (j = 0; j < size; ++j) {

                int numberIndex = matrix[ i][j] - 1;
                if (check[numberIndex]) {
                    return false;
                }
                check[numberIndex] = true;
            }
        }


        for (j = 0; j < size; ++j) {
            boolean[] check = new boolean[size];
            for (i = 0;  i < size; ++ i) {
                int numberIndex = matrix[ i][j] - 1;
                if (check[numberIndex]) {
                    return false;
                }
                
                check[numberIndex] = true;
            }
        }
        
        return true;
    }
}
```
