```Java
class Solution {
    public String tictactoe(int[][] moves) {
        int totalMoves = moves.length;
        int[] counts = new int[8];
      
        for (int moveIndex = totalMoves - 1; moveIndex >= 0; moveIndex -= 2) {
            int row = moves[moveIndex][0];
            int col = moves[moveIndex][1];
          
            counts[row]++;
            counts[col + 3]++;
          
            if (row == col) {
                counts[6]++;
            }
          
            if (row + col == 2) {
                counts[7]++;
            }
          
            if (counts[row] == 3 || counts[col + 3] == 3 || counts[6] == 3 || counts[7] == 3) {
                return moveIndex % 2 == 0 ? "A" : "B";
            }
        }
      
        return totalMoves == 9 ? "Draw" : "Pending";
    }
}
```
