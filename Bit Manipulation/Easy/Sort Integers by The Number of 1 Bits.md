# Intuition
In order to solve the problem, we can implement a custom sorting algorithm where we count the number of set bits of two numbers and then return the smaller one.

# Approach
1. Convert the array of primitive type to an array of type `Integer`
2. Use `Comparator` to implement a custom sorting comparation:
2.1. Save the number of set bits for both numbers into temp variables.
2.2. If the temp variables are different, return `true` if first one is smaller or false otherwise. (For ascending order)
2.3. If the temp variables are the same, return `true` if first one is smaller or false for the same reasoning.
3. Convert the array of type `Integer` to primitive and return.

# Complexity
- Time complexity:
    - Sorting takes $O(n*log(n))$ 
    - Counting the number of bits takes $O(1)$ because we have a fixed number of bits
    - Final: $O(n * log(n))$

- Space complexity:
    - In order to store the temporary array, it takes $O(n)$ as it is a copy of the initial array.

# Code
```java []
class Solution {
    public int[] sortByBits(int[] arr) {

        Integer[] boxed = Arrays.stream(arr)
                                .boxed()
                                .toArray(Integer[]::new);

        Arrays.sort(boxed, new Comparator<Integer>() {
            @Override
            public int compare(Integer x1, Integer x2){
                int x1BitCount = Integer.bitCount(x1);
                int x2BitCount = Integer.bitCount(x2);
            
                if(x1BitCount != x2BitCount){
                    return Integer.compare(x1BitCount, x2BitCount);
                }

                return Integer.compare(x1, x2);
            }
        });

        return Arrays.stream(boxed)
                     .mapToInt(Integer::intValue)
                     .toArray();
    }
}
```
