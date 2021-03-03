#### [剑指 Offer 54. 二叉搜索树的第k大节点](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

**Description**

给定一棵二叉搜索树，请找出其中第k大的节点。



**Example**

```C++
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
```



**Solution**

二叉搜索树的中序遍历为 **递增序列** 。因此，中序遍历的倒序则为递减序列。

根据题意，第K大的数，就是排序好的数组的，倒数第K个数。二叉搜索树的特点之一，就是中序遍历(左->根->右)的顺序，单调递增的。
把整个二叉树还原成一个有序数组，再找倒数第k个数就可以了。



**Review**

[二叉树遍历](https://www.cnblogs.com/lanhaicode/p/10358736.html)



**Code**

```cpp
class Solution {
public:
    int kthLargest(TreeNode* root, int k) {
        int res = 0;
        dfs(root,res, k);
        return res;
    }

    void dfs(TreeNode* root,int& res, int &k){
        if(!root) return;
        dfs(root->right,res, k);
        --k;
        if(!k) res = root->val;
        dfs(root->left,res, k);
    }
};
```



