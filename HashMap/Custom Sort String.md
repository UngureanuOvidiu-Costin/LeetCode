# LeetCode Problem Writeup

## Problem Title: [Custom Sort String](https://leetcode.com/problems/custom-sort-string/description/)

### Problem Description:

*You are given two strings order and s. All the characters of order are unique and were sorted in some custom order previously.*

*Permute the characters of s so that they match the order that order was sorted. More specifically, if a character x occurs before a character y in order, then x should occur before y in the permuted string.*

*Return any permutation of s that satisfies this property.*

### Approach:

*The solution iterates through both the order string and the input string s. It uses a HashMap to count the occurrences of each character in s. Then, it iterates through the order string and appends characters from s based on the order in the order string. Finally, it appends any remaining characters from s that were not in the order string.*

### Pseudocode:
```Python
function customSortString(order, s):
    hashMap2 = new HashMap<Character, Integer>()
    reconstructedString = new StringBuilder()

    for each character c in s:
        if c is not in hashMap2:
            hashMap2[c] = 1
        else:
            hashMap2[c] += 1

    for each character key in order:
        if key exists in hashMap2:
            if hashMap2[key] == 1:
                append key to reconstructedString
            else:
                repeat hashMap2[key] times:
                    append key to reconstructedString
            remove key from hashMap2

    for each keyCh in hashMap2:
        repeat hashMap2[keyCh] times:
            append keyCh to reconstructedString

    return reconstructedString as String

```

## Code Implementation:
```Java
class Solution {
    public String customSortString(String order, String s) {
        HashMap<Character, Integer> hashMap2 = new HashMap<Character, Integer>();
        int i, j;
        char c;
        StringBuilder reconstructedString = new StringBuilder();
        char key;
        
        for(i = 0; i < s.length(); i = i + 1){
            c = s.charAt(i);
            if(!hashMap2.containsKey(c)){
                hashMap2.put(c, 1);
            }else{
                hashMap2.put(c, hashMap2.get(c) + 1);
            }
        }

        for(i = 0; i < order.length(); i++){
            key = order.charAt(i);
            if(hashMap2.containsKey(key)){

                if(hashMap2.get(key) == 1){
                    reconstructedString.append(key);
                }else{
                    for(j = 0; j < hashMap2.get(key); j = j + 1){
                        reconstructedString.append(key);
                    }
                }
                hashMap2.remove(key);
            }
        }


        for(Character keyCh: hashMap2.keySet()){
            for(j = 0; j < hashMap2.get(keyCh); j = j + 1){
                reconstructedString.append(keyCh);
            }
        }

        return reconstructedString.toString();
    }
}
```

## Complexity Analysis:

### Time Complexity:
Let n be the length of the string s and m be the length of the string order.
- Populating the HashMap: O(n)
- Iterating through order: O(m)
- Appending characters to the result string: O(n)
- Overall time complexity: O(n + m)
 ![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/3e114344-c020-454e-9b3e-9713799d5c71)

  
### Space Complexity:
- HashMap to store character counts: O(n)
- StringBuilder to store the result string: O(n)
- O(1) for temp chars and string index
- Overall space complexity: O(n)
 ![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/8598ec8e-4862-487c-9dbe-742e4fe3b7b8)
