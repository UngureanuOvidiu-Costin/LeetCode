# Solution

```Java
class Solution {
    public int[] findEvenNumbers(int[] digits) {
        List<Integer> result = new ArrayList<>();

        HashMap<Integer, Integer> digitsMap = new HashMap<>();
        for (int digit : digits) {
            digitsMap.put(digit, digitsMap.getOrDefault(digit, 0) + 1);
        }

        for (int i = 100; i <= 998; i += 2) {
            int firstDigit = i / 100;
            int secondDigit = (i / 10) % 10;
            int thirdDigit = i % 10;

            HashMap<Integer, Integer> tempMap = new HashMap<>();
            tempMap.put(firstDigit, tempMap.getOrDefault(firstDigit, 0) + 1);
            tempMap.put(secondDigit, tempMap.getOrDefault(secondDigit, 0) + 1);
            tempMap.put(thirdDigit, tempMap.getOrDefault(thirdDigit, 0) + 1);

            boolean isValid = true;
            for (int key : tempMap.keySet()) {
                if (tempMap.get(key) > digitsMap.getOrDefault(key, 0)) {
                    isValid = false;
                    break;
                }
            }

            if (isValid) {
                result.add(i);
            }
        }

        return result.stream().mapToInt(Integer::intValue).toArray();
    }
}
```
