#### [剑指 Offer 32 - III. 从上到下打印二叉树 III](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

**Description**

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。



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
  [20,9],
  [15,7]
]
```



**Solution**

II - 比普通的BFS多一步实现层次遍历的输出，即为每层创建一个一维数组，再加入到二维数组中。

III - 加一个数组的reverse即可。剑指offer就这？？？⚠️😊



**Review**

`reverse(arr.begin(), arr.end())`

**Code**

```cpp

class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> res;
        if(root == NULL) return res;

        queue<TreeNode*> q;
        q.push(root);
        int count = 1;

        while(!q.empty()){
            int size = q.size();
            vector<int> temp;
            for(int i = 0; i < size; i++){
                TreeNode* curr = q.front();
                q.pop();
                temp.push_back(curr->val);

                if(curr->left) q.push(curr->left);
                if(curr->right) q.push(curr->right);   
            }
            if(count % 2 == 0){//偶数层
                reverse(temp.begin(), temp.end());
                }
            res.push_back(temp);
            ++count;
        }
        return res;
    }
};

```



