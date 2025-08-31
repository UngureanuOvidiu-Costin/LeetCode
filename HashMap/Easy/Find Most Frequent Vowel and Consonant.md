# Intuition
We need to find the most frequent vowel and the most frequent consonant in the given string, then return the sum of their frequencies.  
The key idea is to **count how many times each letter appears**, and then separate vowels from consonants.

# Approach
1. Convert the string into lowercase and split it into characters.  
2. Use a hash map (`$frequency`) to count how many times each letter appears.  
3. Iterate through the frequency map. If the character is a vowel (`a, e, i, o, u`), update the maximum vowel frequency. Otherwise, update the maximum consonant frequency.  
4. Return the sum of the maximum vowel and consonant frequencies.

# Complexity
- **Time complexity:**
  - Counting frequencies takes $O(n)$, where $n$ is the length of the string.
  - Checking frequencies again takes $O(k)$, where $k \leq 26$.
  - Overall: $O(n)$.  
- **Space complexity:** We store at most 26 letters in the frequency map, so the extra space used is $O(1)$ (constant).  

# Code
```php
class Solution {

    /**
     * @param String $s
     * @return Integer
     */
    function maxFreqSum($s) {
        $maxVowels = 0;
        $maxConsonants = 0;
        $vowels = ['a', 'e', 'i', 'o', 'u'];
        $frequency = [];

        // Count frequency of each character
        foreach (str_split(strtolower($s)) as $ch) {
            $frequency[$ch] = ($frequency[$ch] ?? 0) + 1;
        }

        // Find maximum vowel and consonant frequencies
        foreach ($frequency as $character => $count) {
            if (in_array($character, $vowels)) {
                $maxVowels = max($maxVowels, $count);
            } else {
                $maxConsonants = max($maxConsonants, $count);
            }
        }

        return $maxVowels + $maxConsonants;
    }
}
