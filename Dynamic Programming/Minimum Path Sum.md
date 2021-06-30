#### [64. Minimum Path Sum](https://leetcode-cn.com/problems/minimum-path-sum/)

**Description**

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.



**Example**

![img](https://assets.leetcode.com/uploads/2020/11/05/minpath.jpg)

```E
Example 1:

Input: grid = [[1,3,1],[1,5,1],[4,2,1]]
Output: 7
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
Example 2:

Input: grid = [[1,2,3],[4,5,6]]
Output: 12

```




**Solution**

f[i] [j] = min(f[i-1] [j], f[i] [j-1]) + grid[i] [j];

注意下开头的限定条件



**Code**

```cpp
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int i,j;
        int rows = grid.size(), cols = grid[0].size();
        vector<vector<int>> dp(rows, vector<int>(cols));

        dp[0][0] = grid[0][0];

        for(i = 1; i < rows; i++){
            dp[i][0] = dp[i-1][0] + grid[i][0];
        }
        for(j = 1; j < cols; j++){
            dp[0][j] = dp[0][j-1] + grid[0][j];
        }

        for(i = 1; i < grid.size(); i++){
            for(j = 1; j < grid[0].size(); j++){
                dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j];
            }
        }

        return dp[rows-1][cols-1];
    }
};

```



