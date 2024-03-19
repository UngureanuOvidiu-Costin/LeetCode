```Java
class Solution {
    public boolean buddyStrings(String s, String goal) {
        if (s.length() != goal.length()) {
            return false;
        }


        if (s.equals(goal)) {
            HashSet<Character> set = new HashSet<>();
            for (char c : s.toCharArray()) {
                if (set.contains(c)) {
                    return true;
                }
                set.add(c);
            }
            return false;
        }

        int firstDiff = -1, secondDiff = -1;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) != goal.charAt(i)) {
                if (firstDiff == -1) {
                    firstDiff = i;
                } else if (secondDiff == -1) {
                    secondDiff = i;
                } else {
                    return false;
                }
            }
        }

        return (secondDiff != -1 && s.charAt(firstDiff) == goal.charAt(secondDiff) &&
                s.charAt(secondDiff) == goal.charAt(firstDiff));
    }
}
```
