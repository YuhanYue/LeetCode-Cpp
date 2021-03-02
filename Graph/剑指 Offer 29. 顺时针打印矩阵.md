#### [剑指 Offer 29. 顺时针打印矩阵](https://leetcode-cn.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)



**Description**

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。



**Example**

```C++
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
```



**Solution**

模拟图，上下左右四个边界，四种方向，每次收缩边界。



**Code**

```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> res;
        if(matrix.empty()) return res;

        //设定边界
        int left = 0;
        int right  = matrix[0].size() - 1;
        int up = 0;
        int down = matrix.size() - 1;
 
        while(true){
            //left->right
            for(int i = left; i <= right; i++){
                res.push_back(matrix[up][i]);
            }
            if(++up > down) break;

            //up->down
            for(int i = up; i <= down; i++){
                res.push_back(matrix[i][right]);
            }
            if(--right < left) break;
            
            //right->left
            for(int i = right; i>= left; i--){
                res.push_back(matrix[down][i]);
            }
            if(--down < up) break;

            //down->up
            for(int i = down; i >= up; i--){
                res.push_back(matrix[i][left]);
            }
            if(++left > right) break;
        }
        return res;
        
    }
};
```



