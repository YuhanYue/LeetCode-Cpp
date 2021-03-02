#### [剑指 Offer 32 - II. 从上到下打印二叉树 II](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)



**Description**

从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。



**Example**

给定二叉树：

```C++
    3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：

```
[
  [3],
  [9,20],
  [15,7]
]
```



**Solution**

比普通的BFS多一步实现层次遍历的输出，即为每层创建一个一维数组，再加入到二维数组中。



**Review**

队列操作 `queue.pop()`、`queue.push()`、`queue.size()`、`queue.front()`。



**Code**

```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(root == NULL) return res;
        
        queue<TreeNode*> q;
        q.push(root);

        while(!q.empty()){
            int size = q.size();
            vector<int> temp;//为每层建的数组
            for(int i = 0; i < size; i++){
                TreeNode* curr = q.front();
                q.pop();
                temp.push_back(curr->val);
                
                if(curr->left) q.push(curr->left);
                if(curr->right) q.push(curr->right);
            }
            res.push_back(temp);
        }

        return res;
    }
};

```



