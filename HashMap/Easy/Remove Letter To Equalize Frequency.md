```Java
class Solution {
    public boolean equalFrequency(String s) {
        int[] v = new int[26];
        Arrays.fill(v, 0);
        
        for (int i = 0; i < s.length(); i++) {
            v[s.charAt(i) - 'a']++;
        }
        
        for (int i = 0; i < s.length(); i++) {
            int currElement = s.charAt(i) - 'a';
            v[currElement]--;
            int f = 0;
            boolean temp = true;
            for (int j = 0; j < 26; j++) {
                if (v[j] != 0) {
                    if (f == 0) {
                        f = v[j];
                    }
                    if (f != v[j]) {
                        temp = false;
                    }
                }
            }
            if (temp) {
                return true;
            }
            v[currElement]++;
        }
        return false;
    }
}
```
