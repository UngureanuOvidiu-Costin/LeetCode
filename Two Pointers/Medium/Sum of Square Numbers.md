```Java
class Solution {
    public boolean judgeSquareSum(int c) {
        int a = (int)Math.sqrt(c);
        if( c == a * a){
            return true;
        }

        for(a = 1; a <= c / a; a = a + 1){
            double b = (int) Math.sqrt(c - a * a);
            if(b == (int)b && (int)b * (int)b + a * a == c){
                return true;
            }
        }
        return false;
    }
};
```