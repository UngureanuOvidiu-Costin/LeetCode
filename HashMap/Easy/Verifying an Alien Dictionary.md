```Java
class Solution {
    public boolean isAlienSorted(String[] words, String order) {

        HashMap<Character, Integer> positions = new HashMap<>();

        int i, j;
        for(i = 0; i < order.length(); i = i + 1){
            positions.put(order.charAt(i), i);
        }

        String current = words[0];
        int len;
        for(i = 1; i < words.length; i = i + 1){
            len = Math.min(current.length(), words[i].length());
            for(j = 0; j < len; j = j + 1){
                if(!Objects.equals(positions.get(current.charAt(j)), positions.get(words[i].charAt(j)))){
                    break;
                }
            }

            if (j < current.length() && j < words[i].length() &&
                    positions.get(current.charAt(j)) > positions.get(words[i].charAt(j))) {
                return false;
            }

            if (j == words[i].length() && j < current.length()) {
                return false;
            }
            current = words[i];
        }
        return true;
    }
}
```
