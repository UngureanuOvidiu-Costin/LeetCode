```Java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeZeroSumSublists(ListNode head) {
        ListNode front = new ListNode();
        front.val = 0;
        ListNode current = new ListNode();
        front.next = head;
        current = head;
        int prefixSum = 0;
        HashMap<Integer, ListNode> prefixSumList = new HashMap<>();
        prefixSumList.put(0, front);

        while (current != null){
            prefixSum = prefixSum + current.val;
            prefixSumList.put(prefixSum, current);
            current = current.next;
        }

        prefixSum = 0;
        current = front;


        while (current != null) {
            prefixSum += current.val;
            current.next = prefixSumList.get(prefixSum).next;
            current = current.next;
        }
        return front.next;
    }
}
```
