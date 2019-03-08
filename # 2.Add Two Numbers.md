# 2.Add Two Numbers

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**

```text
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

**Code:**

```python
#  Definition for singly-linked list.
# 定义listNode
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # 将listNode转换成数字后，再相加，最后再将和转回listNode
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        # 将listNode转换成数字
        def getNumber(l):
            #初始化
            n_str = '';
            while l:
                n_str += str(l.val)
                l = l.next
            #返回n_str倒序读取并转换成int型
            return int(n_str[::-1])
            
        # 将int构建成listNode
        # reverse the digits of n and convert it to ListNode
        def buildListNode(n):
            # 将int型倒序转成string
            n_str_reversed = str(n)[::-1]
            # 构建ListNode,且head[0]=p[0]=0
            head = p = ListNode(0)
            for i in range(len(n_str_reversed)):
                # 按照顺序将n_str_reversed添加到链表p上
                p.next = ListNode(int(n_str_reversed[i]))
                # 链表链增加
                p = p.next
            # 因为head[0]=0 所以从head[1]开始
            return head.next
        
        n = getNumber(l1) + getNumber(l2)
        return buildListNode(n)
```

