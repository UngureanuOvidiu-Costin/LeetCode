```Java
class Solution {
    public String sortString(String s) {
        Map<Character, Integer> count = new HashMap<>();
        for (char c : s.toCharArray()) {
            count.put(c, count.getOrDefault(c, 0) + 1);
        }

        StringBuilder result = new StringBuilder();

        while (result.length() < s.length()) {
            for (char c = 'a'; c <= 'z'; c++) {
                if (count.containsKey(c) && count.get(c) > 0) {
                    result.append(c);
                    count.put(c, count.get(c) - 1);
                }
            }

            for (char c = 'z'; c >= 'a'; c--) {
                if (count.containsKey(c) && count.get(c) > 0) {
                    result.append(c);
                    count.put(c, count.get(c) - 1);
                }
            }
        }

        return result.toString();
    }
}
```
