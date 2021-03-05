#### [剑指 Offer 13. 机器人的运动范围](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/)

**Description**

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

**Example**

```C++
输入：m = 2, n = 3, k = 1
输出：3
  
  输入：m = 3, n = 1, k = 0
输出：1
```



**Solution**

DFS yyds！！

思路：

1. 计算BitSum
2. DFS边界：图的边界 + bitSum<k + 未被访问过

**Code**

```cpp
class Solution {
public:
    int movingCount(int m, int n, int k) {
         vector<vector<bool>> visited(m, vector<bool>(n, 0));
         return dfs(m,n,k,visited,0,0);
    }
    
    int dfs(int m, int n, int k, vector<vector<bool>> & visited,int i, int j){
        if(i >= m || j >= n || visited[i][j] || bitSum(i) + bitSum(j) > k) return 0;
        visited[i][j] = 1;
        int res = dfs(m,n,k,visited, i+1,j) + dfs(m,n,k,visited,i,j+1);
        return 1 + res;
        
    }

    int bitSum(int n){
         int sum = 0;
        while(n > 0) {
            sum += n % 10;
            n /= 10; 
        }
        return sum;
    }
};

```



