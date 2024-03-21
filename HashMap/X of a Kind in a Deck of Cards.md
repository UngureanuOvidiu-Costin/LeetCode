```Java
class Solution {
    public boolean hasGroupsSizeX(int[] deck) {
        HashMap<Integer, Integer> hashMapDeck = new HashMap<>();
        int i;
        for(i = 0; i < deck.length; i = i + 1){
            hashMapDeck.put(deck[i], hashMapDeck.getOrDefault(deck[i], 0) + 1);
        }

        Integer[] frequency = hashMapDeck.values().toArray(new Integer[0]);
        int gcd = 0;
        int temp;
        for (int freq : frequency) {
            while (freq != 0) {
                temp = freq;
                freq = gcd % freq;
                gcd = temp;
            }
        }

        return gcd > 1;
    }
}

```
