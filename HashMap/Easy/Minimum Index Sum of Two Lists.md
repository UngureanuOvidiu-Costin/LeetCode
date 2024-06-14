# LeetCode Problem Writeup

## Problem Title: [Minimum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/)

### Problem Description:

*Given two arrays of strings list1 and list2, find the common strings with the least index sum.
A common string is a string that appeared in both list1 and list2.
A common string with the least index sum is a common string such that if it appeared at list1[i] and list2[j] then i + j should be the minimum value among all the other common strings.
Return all the common strings with the least index sum. Return the answer in any order.*

### Approach:

1.Create two HashMaps, stringIndexes1 and stringIndexes2, to store indices of strings from list1 and list2.

2.Find common keys by filtering those present in both HashMaps.

3.Calculate a new HashMap, stringIndexes3, by adding corresponding indices for common keys.

4.Find the minimum value in stringIndexes3.

5.Filter the entries in stringIndexes3 to get keys with the minimum value.

6.Return the keys as a String array.

### Pseudocode:

```
function findRestaurant(list1, list2):
    stringIndexes1 = new HashMap()
    stringIndexes2 = new HashMap()
    stringIndexes3 = new HashMap()

    for i from 0 to length of list1 - 1:
        stringIndexes1.put(list1[i], i)

    for i from 0 to length of list2 - 1:
        stringIndexes2.put(list2[i], i)

    commonKeys = filter keys in stringIndexes1 where stringIndexes2 containsKey

    for each str in commonKeys:
        print(str)
        value1 = stringIndexes1.get(str)
        value2 = stringIndexes2.get(str)
        stringIndexes3.put(str, value1 + value2)

    minValue = minimum value in stringIndexes3
    print(minValue)

    keysWithMinValue = filter entries in stringIndexes3 where entry value is minValue
    resultArray = convert keysWithMinValue to String array

    perform garbage collection

    return resultArray

```

## Code Implementation:
```Java
class Solution {
    public String[] findRestaurant(String[] list1, String[] list2) {
        HashMap<String, Integer> stringIndexes1 = new HashMap<>();
        HashMap<String, Integer> stringIndexes2 = new HashMap<>();
        HashMap<String, Integer> stringIndexes3 = new HashMap<>();

        int i;
        for(i = 0; i < list1.length; i = i  + 1){
            stringIndexes1.put(list1[i], i);
        }

        for(i = 0; i < list2.length; i = i  + 1){
            stringIndexes2.put(list2[i], i);
        }

        List<String> commonKeys = stringIndexes1.keySet()
                                    .stream()
                                    .filter(stringIndexes2::containsKey)
                                    .collect(Collectors.toList());

        for (String str : commonKeys) {
            System.out.println(str);
            int value1 = stringIndexes1.get(str);
            int value2 = stringIndexes2.get(str);
            stringIndexes3.put(str, value1 + value2);
        }

        int minValue = Collections.min(stringIndexes3.values());
        System.out.println(minValue);
        List<String> keysWithMinValue = stringIndexes3.entrySet()
                .stream()
                .filter(entry -> entry.getValue() == minValue)
                .map(entry -> entry.getKey())
                .collect(Collectors.toList());

        String[] resultArray = keysWithMinValue.toArray(new String[0]);
        System.gc();
        return resultArray;
    }
}
```

## Complexity Analysis:
![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/3bd4f515-9694-4182-9e4a-4cb80c3d34ed)


### Time Complexity: 
Constructing stringIndexes1 and stringIndexes2: O(N) where N is the length of the longer list.

Filtering common keys: O(min(N, M)), where N and M are the lengths of list1 and list2.

Constructing stringIndexes3: O(min(N, M)).

Finding minimum value: O(min(N, M)).

Filtering keys with the minimum value: O(min(N, M)).

Constructing resultArray: O(min(N, M)).

Garbage collection: Time complexity not typically considered.

Overall time complexity: O(N + min(N, M)).
### Space Complexity: 
stringIndexes1, stringIndexes2, and stringIndexes3: O(min(N, M)).
commonKeys, keysWithMinValue, and resultArray: O(min(N, M)).
Overall space complexity: O(min(N, M)) because we use **Garbage Collector(but it's call is not very reliable)**
