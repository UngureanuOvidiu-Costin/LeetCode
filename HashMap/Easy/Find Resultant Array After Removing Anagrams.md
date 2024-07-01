# Intuition

The problem is to remove consecutive anagrams from an array of words. An anagram of a word is another word formed by rearranging its letters. To identify anagrams, we can sort the characters of each word and compare the sorted versions. If the sorted version of the current word matches the sorted version of the previous word in the result list, they are anagrams and we skip adding the current word to the result list.

## Approach

1. **Helper Function to Sort Characters:** Create a helper function `sortWord` that takes a word, converts it to a character array, sorts it, and returns the sorted array as a string.
2. **Initialize Result List:** Start with a result list containing the first word.
3. **Iterate Through the Words:** For each word in the input list (starting from the second word):
    - Sort the current word.
    - Sort the last word added to the result list.
    - Compare the sorted versions. If they are different, add the current word to the result list.
4. **Return Result List:** The result list will contain the words with consecutive anagrams removed.

## Complexity

- Time complexity:
**Sorting Words:** Sorting each word takes `O(k * logk)`, where `k` is the length of the word. Assuming the average length of a word is constant, this is `O(1)`.
**Iterating Through Words:** Iterating through the words array takes `O(n)`, where `n` is the number of words.
**Total Complexity:** Since we sort each word, the overall time complexity is `O(n * k * logk)`. If the length of words is relatively small, this can be considered `O(n)`.

- Space complexity:
**Auxiliary Space:** The space needed for the result list and the auxiliary space used by the sortWord function. Sorting in Java uses `O(k)` auxiliary space.
**Total Complexity:** The space complexity is `O(n * k)` for the result list and the sorted character arrays.

## Code

```Java
class Solution {
    private String sortWord(String word) {
        char[] chars = word.toCharArray();
        Arrays.sort(chars);
        return new String(chars);
    }

    public List<String> removeAnagrams(String[] words) {
        List<String> result = new ArrayList<>();
        result.add(words[0]);

        for (int i = 1; i < words.length; i++) {
            String currentSorted = sortWord(words[i]);
            String lastSorted = sortWord(result.get(result.size() - 1));

            if (!currentSorted.equals(lastSorted)) {
                result.add(words[i]);
            }
        }

        return result;
    }
}
```
