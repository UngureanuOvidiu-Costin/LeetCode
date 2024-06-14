# LeetCode Problem Writeup

## Problem Title: [Unique Morse Code Words](https://leetcode.com/problems/unique-morse-code-words/description/)

### Problem Description:
International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows:

'a' maps to `".-"`,
'b' maps to `"-..."`,
'c' maps to `"-.-."`, and so on.
For convenience, the full table for the `26` letters of the English alphabet is given below:

  *[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]* <br>
Given an array of strings words where each word can be written as a concatenation of the Morse code of each letter.

For example, "cab" can be written as `"-.-..--..."`, which is the concatenation of `"-.-."`, `".-"`, and `"-..."`. We will call such a concatenation the *transformation* of a word.
Return the number of different *transformations* among all words we have.

### Approach:
1. Create a mapping of each character to its corresponding Morse code.
2. Iterate through each word in the input array.
3. For each word, iterate through its characters, transform each character to its Morse code using the mapping, and concatenate these codes.
4. Store the concatenated Morse code in a set to ensure uniqueness.
5. Finally, return the size of the set, which represents the number of unique Morse code transformations.


### Pseudocode:
```Python
uniqueMorseRepresentations(words):
    Initialize a hashmap morseMap to store mappings from characters to Morse code
    Initialize a set counter to store unique Morse code transformations
    
    // Mapping characters to Morse code
    morse = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
    for each character c from 'a' to 'z':
        morseMap.put(c, morse[c - 'a'])
    
    // Iterating through each word
    for each word in words:
        Initialize a string temp to store the Morse code transformation of the current word
        
        // Transforming each character to Morse code and concatenating
        for each character ch in lowercase of word:
            temp = temp + morseMap.get(ch)
        
        Add temp to the counter set
        
    return the size of the counter set

```

## Solution:

```Java
class Solution {
    public int uniqueMorseRepresentations(String[] words) {
        String[] morse = {".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."};
        HashMap<Character, String> morseMap = new HashMap<>();
        for (char c = 'a'; c <= 'z'; c++) {
            morseMap.put(c, morse[c - 'a']);
        }

        Set<String> counter = new HashSet<>();
        String temp = "";
        for(String word: words){
            for(Character c: word.toLowerCase().toCharArray()){
                temp = temp + morseMap.get(c);
            }
            counter.add(temp);
            temp = "";
        }
        return counter.size();
    }
}
```

## Complexity Analysis:
### Time Complexity: O(n)
- Creating the mapping of characters to Morse code: This step takes constant time as it involves initializing a hashmap with mappings for all 26 characters of the alphabet, resulting in O(1) time complexity.
- Since there are `n` characters in total across all words, this step takes O(n) time complexity.
- Since there are `m` words and each word's *transformation* is added to the set, this step also takes O(m) time complexity.
- Overall, the time complexity is dominated by the iteration through the characters of all words, resulting in O(n) time complexity.
### Space Complexity: O(m)
- The space required for storing the mapping of characters to Morse code is constant as it only involves storing mappings for all 26 characters of the alphabet, resulting in O(1) space complexity
- Storing unique Morse code transformations in a set: The space required for storing unique transformations depends on the number of unique transformations.
  <br>In the worst case, all words result in unique transformations, leading to O(m) space complexity for the HashSet.
- The space required for auxiliary variables like temp is also constant, resulting in O(1) space complexity.
- **Overall**: O(m)
