```Java
class Solution {
    public int maxNumberOfBalloons(String text) {
        HashMap<Character, Integer> hashMap = new HashMap<>();
        String balloon = "balloon";

        for(Character c: text.toCharArray()){
            if(balloon.contains(c.toString())){
                hashMap.put(c, hashMap.getOrDefault(c, 0) + 1);
            }
        }

        for(Character c: balloon.toCharArray()){
            if(!hashMap.containsKey(c)){
                return 0;
            }
        }

        int minValue = Collections.min(hashMap.values());
        int min1 = hashMap.getOrDefault('l', 0) / 2;
        int min2 = hashMap.getOrDefault('o', 0) / 2;
        int minn = Math.min(min1, min2);
        minn = Math.min(minn, minValue);


        return minn;
    }
}
```
