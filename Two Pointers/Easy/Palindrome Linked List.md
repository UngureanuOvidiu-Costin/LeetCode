```Python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:

        if head == None:
            return True
        if head != None and head.next == None:
            return True

        fast = head
        slow = head
        stack = []
    
        while fast != None and fast.next != None:
            stack.append(slow.val)
            fast = fast.next.next
            slow = slow.next
        

        if fast:
            slow = slow.next
        
        while stack:
            if slow.val != stack.pop():
                return False
            slow = slow.next
        
        return True
```
