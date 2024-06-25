# Solution

```Java
class Solution {
    public int countGoodSubstrings(String s) {
        int i;
        List<String> uniqueSubstrings = new ArrayList<>();
        String temp;
        char a, b, c;
        for (i = 0; i < s.length() - 2; i++) {
            a = s.charAt(i);
            b = s.charAt(i + 1);
            c = s.charAt(i + 2);

            if (a != b && a != c && b != c) {
                uniqueSubstrings.add("" + a + b + c);
            }
        }

        return uniqueSubstrings.size();
    }
}

```
