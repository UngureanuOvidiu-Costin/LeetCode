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
    public ListNode mergeInBetween(ListNode list1, int a, int b, ListNode list2) {
        ListNode firstNodeToStop = list1;
        ListNode lastNodeToStop = list1;
        int firstStop;
        for(firstStop = 0; firstStop < a - 1; firstStop++){
            firstNodeToStop = firstNodeToStop.next;
            lastNodeToStop = lastNodeToStop.next;
        }

        for(;firstStop < b+1; firstStop = firstStop + 1){
            lastNodeToStop = lastNodeToStop.next;
        }
        
        firstNodeToStop.next = list2;
        while (list2.next != null){
            list2 = list2.next;
        }

        list2.next = lastNodeToStop;

        return list1;
    }
}
```
