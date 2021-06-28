#### [23. Merge k Sorted Lists](https://leetcode-cn.com/problems/merge-k-sorted-lists/)

 **Description**

You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.



 

**Example**

```
Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted list:
1->1->2->3->4->4->5->6

Input: lists = [[]]
Output: []
```





**Solution**

上午才做过合并两个有序连链表[21.merge two sorted lists](./21.Merfe Two Sorted Lists.md)，可以借鉴这个思路继续往下：

* 暴力

  从头开始循环，遍历一次list，从头到尾顺序合并每一个链表。

* 分治

  两两合并，dived and conquer

  ![img](https://pic.leetcode-cn.com/6f70a6649d2192cf32af68500915d84b476aa34ec899f98766c038fc9cc54662-image.png)

**Code**

```cpp

class Solution {
public:

    ListNode* merge2Lists(ListNode* a, ListNode* b){
        ListNode* pre = new ListNode;
        ListNode* head = pre;
        while(a && b){
            if(a->val <= b->val){
                pre->next = a;
                a = a->next;
            }else{
                pre->next = b;
                b = b->next;
            }
            pre = pre->next;
        }

        if(a || b) pre->next = a?a:b;
        return head->next;
    }

    ListNode* merge(vector<ListNode*>& lists, int l, int r){
        if(l==r) return lists[l];
        if(l>r) return nullptr;
        int mid = (l+r) >> 1;
        return merge2Lists(merge(lists,l, mid), merge(lists, mid+1, r));
    }

    ListNode* mergeKLists(vector<ListNode*>& lists) {
        // ListNode* res = nullptr;
        // for(int i = 0; i < lists.size(); i++){
        //     res = merge2Lists(res, lists[i]);
        // }
        // return res;
        return merge(lists, 0, lists.size()-1);
    }
};

```

