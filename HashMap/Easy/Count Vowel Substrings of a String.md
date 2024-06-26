# Intuition

We will make use of the `Set`(HashSet) to check if we've met all the vowels in the substring.
Overall, we have to loop through all the substring and check if the substring contains only vowels and also contains all of the vowels inside.

## Approach

1. Initialize a `Set` to store unique vowels.
2. Iterate thriugh all possible vowels substrings and use `break` when needed. Iterate from the beginning to the end of the string.
3. Inner loop will go from `j = i` to `j < word.length()` to iterate over each possible substring.
4. We obtain a substring that starts at `i` and ends at `j`. Each time we find a vowel, add it to the `Set`. If it's not a vowel, break.
5. If `Set.size() == 5`, means that it contains all the vowels so we increase the `counter`.
6. Don't forget to clear the current `Set` if the character is not a vowel or after the inner loop.
7. Return the `counter`.

## Complexity

- Time complexity:
The outer loop runs from `i = 0` to `i < word.length()`. This means it runs `N` times, where `N` is the length of the input string `word`.
For each iteration of the outer loop, the inner loop runs from `j = i` to `j < word.length()`. In the worst case, this can run up to `N` times for the first iteration, `N-1` times for the second iteration, and so on.
The total number of iterations of the inner loop across all iterations of the outer loop can be described by the sum of the first `N` natural numbers: `N + N - 1 + N - 2 + ... = N(N+1)/2`
Combining the complexities together: `O(N^2)`

- Space complexity:
The space used by the `uniqueVowels` set can contain a maximum of 5 vowels, leads to `O(1)`.
The integer variables `i`, `j`, and `counter` use `O(1)` space.
Overall: `O(1)`

```Java
class Solution {
    public int countVowelSubstrings(String word) {
        int i, j, counter = 0;
        // A Set used to verify that the substring contains all the vowels
        Set<Character> uniqueVowels = new HashSet<>();
        // Iterate over each character
        for(i = 0; i < word.length(); i = i + 1) {
            // Iterate over each substring
            for(j = i; j < word.length(); j = j + 1) {
                // Check if the current character is a vowel
                if(!isVowel(word.charAt(j))) {
                    // Clear the Set
                    uniqueVowels.clear();
                    // There is no more need to iterate, we keep going
                    break;
                }

                // Add the vowel to the set
                uniqueVowels.add(word.charAt(j));
                // This means that the current substring is a Vowel Substring
                if(uniqueVowels.size() == 5) {
                    // So we must increase the counter
                    counter = counter + 1;
                }
            }
            // If the string contains only vowels we must reset the Set
            uniqueVowels.clear();
        }
        // Return the result
        return counter;
    }

    boolean isVowel(char c){
        if(c == 'a' || c == 'e' || c == 'u' || c == 'i' || c == 'o') {
            return true;
        }
        return false;
    }
}
```
