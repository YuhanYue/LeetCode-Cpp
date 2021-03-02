#### [剑指 Offer 28. 对称的二叉树](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)



**Description**

请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。



**Example**

```
   1
   / \
  2   2
 / \ / \
3  4 4  3
```



**Solution**  
重点在于成对比较，使用栈或队列都可，也不需要纠结左右指针是否正确。 少用递归！


**Code**

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        if(root == NULL) return true;

        stack<TreeNode*> stk;
        stk.push(root->left);
        stk.push(root->right);
        
        while(!stk.empty()){
            TreeNode* rightNode = stk.top();
            stk.pop();
            TreeNode* leftNode = stk.top();
            stk.pop();

            //比较是否相等
            if(!leftNode && !rightNode) continue;
            if( !leftNode || !rightNode || leftNode->val!= rightNode->val) return false;
        
            stk.push(leftNode->left);
            stk.push(rightNode->right);
            stk.push(leftNode->right);
            stk.push(rightNode->left);
            
            
        }

        return true;
    }
};
```



