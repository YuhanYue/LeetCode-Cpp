#### [剑指 Offer 52. 两个链表的第一个公共节点](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

**Description**

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。



**Example**



输入两个链表，找出它们的第一个公共节点。

如下面的两个链表： 

<img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_1.png" alt="img" style="zoom:50%;" />



```C++
输入： intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出： Reference of the node with value = 8
输入解释： 相交节点的值为 8 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点.
```



**Solution**

双指针：

<img src="https://pic.leetcode-cn.com/1614527163-BKaiqs-Picture1.png" alt="Picture1.png" style="zoom:33%;" />



考虑构建两个节点指针 A , B 分别指向两链表头节点 headA , headB ，做如下操作：

* 指针 A 先遍历完链表 headA ，再开始遍历链表 headB ，当走到 node 时，共走步数为：
  a + (b - c)

* 指针 B 先遍历完链表 headB ，再开始遍历链表 headA ，当走到 node 时，共走步数为：
  b + (a - c)

​      此时指针 A , B 重合，并有两种情况：

​												a + (b - c) = b + (a - c)


1. 若两链表 有 公共尾部 (即 c > 0c>0 ) ：指针 A , B 同时指向「第一个公共节点」node 。、
2. 若两链表 无 公共尾部 (即 c = 0c=0 ) ：指针 A , B 同时指向 null 。





**Code**

```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *A = headA;
        ListNode *B = headB;

        while(A != B){
            if(A == NULL) A = headB;
            else A = A->next;

            if(B == NULL) B = headA;
            else B = B->next;
        }

        return A;
    }
};
```



