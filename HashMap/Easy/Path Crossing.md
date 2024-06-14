```Java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public boolean isPathCrossing(String path) {
        Set<String> visitedCoords = new HashSet<>();

        int i;
        char c;
        int x = 0, y = 0;
        String currentCoords = "";
        visitedCoords.add("0,0");
        for(i = 0; i < path.length(); i = i + 1){
            switch (path.charAt(i)){
                case 'N':
                    y = y + 1;
                    break;
                case 'S':
                    y = y - 1;
                    break;
                case 'E':
                    x = x + 1;
                    break;
                case 'W':
                    x = x - 1;
                    break;
                default:
                    break;
            }
            currentCoords = x + "," + y;
            if(visitedCoords.contains(currentCoords)){
                return true;
            }
            visitedCoords.add(currentCoords);
        }
        
        return false;
    }
}
```
