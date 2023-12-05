# LeetCode Problem Writeup

## Problem Title: [Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/)

### Problem Description:

*Given the root of a binary search tree and an integer k, return true if there exist two elements in the BST such that their sum is equal to k, or false otherwise.*

### Approach:

**1.Traversal:**
Traverse the binary tree, either recursively or iteratively using a stack.
During traversal, visit each node.
**2.Hash Set for Complements:**
Maintain a HashSet to store unique values encountered during traversal.
For each visited node, check if its complement (k - current.val) is present in the HashSet.
If found, a pair is found, and the function can return true.
**3.Updating HashSet:**
Add the current node's value to the HashSet to ensure uniqueness.
Continue the traversal to the right subtree.
**4.Return False if No Pair Found:**
If the traversal completes without finding a pair, return false.*

### Pseudocode:

```plaintext
function findPairWithSum(root, k):
    // Initialize an empty HashSet to store unique values
    set = createEmptyHashSet()

    // Initialize a stack for tree traversal
    stack = createEmptyStack()

    // Start traversal with the root node
    current = root

    // Continue traversal until the stack is empty or current is null
    while current is not null or stack is not empty:
        // Traverse as far left as possible
        while current is not null:
            // Push the current node onto the stack
            stack.push(current)
            // Move to the left child
            current = current.left

        // Pop a node from the stack
        current = stack.pop()

        // Check if the complement exists in the set
        if set.contains(k - current.value):
            // A pair is found, return true
            return true

        // Add the current value to the set
        set.add(current.value)

        // Move to the right subtree
        current = current.right

    // If no pair is found during traversal, return false
    return false
```

## Code Implementation:

**1st Solution**
```class Solution {
    public boolean findTarget(TreeNode root, int k) {
        HashMap<Integer, Integer> hash = new HashMap<>();
        Stack<TreeNode> stack = new Stack<>();

        TreeNode current = root;

        while (current != null || !stack.isEmpty()) {
            while (current != null) {
                stack.push(current);
                current = current.left;
            }

            current = stack.pop();
            
            if (hash.containsKey(current.val)) {
                hash.put(current.val, hash.get(current.val) + 1);
            } else {
                hash.put(current.val, 1);
            }

            if (hash.containsKey(k - current.val) && (k - current.val != current.val || hash.get(k - current.val) > 1)) {
                // Verify if a good pair exists and if there is a pair of type k/2 + k/2(duplicates)
                return true;
            }

            current = current.right;
        }

        return false;
    }
}
```
**2nd Solution**
```
class Solution {
    public boolean findTarget(TreeNode root, int k) {
        HashSet<Integer> set = new HashSet<>();
        return findPair(root, k, set);
    }

    private boolean findPair(TreeNode node, int k, HashSet<Integer> set) {
        if (node == null) {
            return false;
        }

        if (set.contains(k - node.val)) {
            return true;
        }

        set.add(node.val);

        return findPair(node.left, k, set) || findPair(node.right, k, set);
    }
}
```

## Complexity Analysis:
**1st Solution**
![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/83d6dbd6-d863-47e3-b7b2-2604e7e0b5e3)

**2nd Solution**
![image](https://github.com/UngureanuOvidiu-Costin/LeetCode/assets/102877918/65acc88f-26dd-4241-b6d1-81afa5b99d5b)


### Time complexity Analysis:
Traversal: The time complexity of the traversal step is O(n), where n is the number of nodes in the binary tree. This is because each node is visited once.
HashSet Operations: The operations on the HashSet (adding and checking for presence) are generally O(1) on average. In the worst case, when there are hash collisions, the complexity becomes O(n), but this is unlikely to happen frequently.
The overall time complexity is O(n), dominated by the tree traversal.

### Space Complexity Analysis:
HashSet Space: The space complexity of the HashSet is O(n) in the worst case. In the average case, it might be less than O(n), depending on the distribution of values in the tree.
Stack Space: The space complexity of the stack used for traversal is O(h), where h is the height of the tree. In the worst case (skewed tree), the height h could be equal to n, making it O(n). In a balanced tree, the height is log(n), resulting in O(log(n)) space complexity.
The overall space complexity is O(n) in the worst case and O(log(n)) in the average case.
