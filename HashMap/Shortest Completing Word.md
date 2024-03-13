# LeetCode Problem Writeup

## Problem Title: [Shortest Completing Word](https://leetcode.com/problems/shortest-completing-word/description/)

### Problem Description:
Given a string `licensePlate` and an array of strings `words`, find the shortest completing word in `words`.

A *completing* word is a word that *contains all the letters* in `licensePlate`. Ignore numbers and spaces in `licensePlate`, and treat letters as case insensitive. If a letter appears more than once in `licensePlate`, then it must appear in the word the same number of times or more.

For example, if `licensePlate` = "aBc 12c", then it contains letters 'a', 'b' (ignoring case), and 'c' twice. Possible completing `words` are "abccdef", "caaacab", and "cbca".

Return the shortest completing word in `words`. It is guaranteed an answer exists. If there are multiple shortest completing `words`, return the first one that occurs in `words`.

### Intuition:
  *The problem requires finding the shortest completing word from an array of words, where a completing word contains all the letters from a given license plate. We need to ignore numbers and spaces in the license plate, and treat letters as case insensitive.*

### Approach:
1. Create a hashmap to count the frequency of characters in the license plate. Iterate through the license plate string, convert it to lowercase, and count the frequency of letters.
2. Iterate through each word in the array of `words`.
3. For each word, create a hashmap to count the frequency of characters.
4. Check if the word contains all the characters and their frequencies required to complete the license plate.
5. If it does, update the solution with the shortest completing word found so far.
6. Return the shortest completing word.

### Pseudocode:

```Python
shortestCompletingWord(licensePlate, words):
    // Create a hashmap to count the frequency of characters in the license plate
    license = HashMap<Character, Integer>()
    
    // Count characters in licensePlate
    for each character c in licensePlate.toLowerCase():
        if c is a letter:
            if c does not exist in license:
                add c to license with frequency 1
            else:
                increment the frequency of c in license by 1
    
    // Initialize variables for solution
    solution = null
    min_length = INFINITY
    
    // Iterate through each word in words
    for each word in words:
        // Create a hashmap to count the frequency of characters in the current word
        tempHashMap = HashMap<Character, Integer>()
        
        // Count characters in current word
        for each character c in word.toLowerCase():
            if c does not exist in tempHashMap:
                add c to tempHashMap with frequency 1
            else:
                increment the frequency of c in tempHashMap by 1
        
        // Check if the current word is completing
        completing = true
        for each character c in license:
            if c does not exist in tempHashMap or frequency of c in tempHashMap < frequency of c in license:
                set completing to false
                break
        
        // If the current word is completing and shorter than current solution, update solution
        if completing and length of word < min_length:
            set solution to word
            set min_length to length of word
    
    // Return the shortest completing word
    return solution

```

## Solution:
```Java
class Solution {
    public String shortestCompletingWord(String licensePlate, String[] words) {
        HashMap<Character, Integer> license = new HashMap<>();
        int i;

        for (char c : licensePlate.toLowerCase().toCharArray()) {
            if (Character.isLetter(c)) {
                license.put(c, license.getOrDefault(c, 0) + 1);
            }
        }
        
        String solution = null;
        int min = Integer.MAX_VALUE;
        for (String word : words) {
            HashMap<Character, Integer> tempHashMap = new HashMap<>();
            for (char c : word.toLowerCase().toCharArray()) {
                tempHashMap.put(c, tempHashMap.getOrDefault(c, 0) + 1);
            }

            boolean check = true;
            for (char c : license.keySet()) {
                if (!tempHashMap.containsKey(c) || tempHashMap.get(c) < license.get(c)) {
                    check = false;
                    break;
                }
            }

            if(check && word.length() < min){
                solution = word;
                min = word.length();
            }
        }

        return solution;
    }
}
```

## Complexity Analysis:

### Time Complexity: Let n be the length of the longest word and m be the length of the license plate.
  - Constructing the hashmap for the license plate takes O(m) time.
  - For each word, constructing the hashmap takes O(n) time.
  - We iterate through each character of the license plate and each word once, so the overall time complexity is O(m + n*k), where k is the number of `words`.
### Space Complexity:
  - We use extra space for the hashmap to store the frequencies of characters in the license plate, which takes O(m), and each word, which takes O(1) because we dont keep it.
  - The overall space complexity is O(m).
