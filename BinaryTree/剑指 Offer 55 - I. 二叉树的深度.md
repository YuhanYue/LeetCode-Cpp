#### [剑指 Offer 55 - I. 二叉树的深度](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)

**Description**

输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。



**Example**

给定二叉树 [3,9,20,null,null,15,7]

```C++
   3
   / \
  9  20
    /  \
   15   7
输出: 3
```



**Solution**

BFS按层序遍历。



**Code**

```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root == NULL)    return 0;
        queue<TreeNode* >q;
        q.push(root);
        int depth = 0;
        while(!q.empty()){
            int count = q.size();
            ++depth;
            while(count){
                TreeNode* temp = q.front();
                q.pop();
                if(temp->left) q.push(temp->left);
                if(temp->right) q.push(temp->right);
                --count;
            }
        }
        return depth;
    }   
};
```



