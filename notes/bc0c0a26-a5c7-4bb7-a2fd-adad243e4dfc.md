# 0019 · 删除链表的倒数第N个结点

题目链接：https://leetcode.cn/problems/remove-nth-node-from-end-of-list

难度：中等 | 语言：Java | 标签：链表、双指针

## 解题思路

这个方法也是找到删除节点的前一个节点，因为链表不能从后往前遍历，所以我们将链表压入栈，利用栈后进先出的特性，找到待删除节点的前一个节点。
重点：将链表压入栈不会改变原本链表的结构

## 代码

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0, head);
        Deque<ListNode> stack = new LinkedList<ListNode>();
        ListNode cur = dummy;
        while (cur != null) {
            stack.push(cur);
            cur = cur.next;
        }
        for (int i = 0; i < n; ++i) {
            stack.pop();
        }
        ListNode prev = stack.peek();
        prev.next = prev.next.next;
        ListNode ans = dummy.next;
        return ans;
    }
}
```

## 复杂度

时间复杂度O(L)，空间复杂度O(L)

## 踩过的坑



## 我的收获


