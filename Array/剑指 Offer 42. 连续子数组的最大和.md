#### [剑指 Offer 42. 连续子数组的最大和](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

**Description**

输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。



**Example**

```C++
输入: nums = [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```



**Solution**

1. 贪心

   采取贪心策略，只要当前子段的和最大，就记录到res中，如果sum的结果小于0，必须将sum = 0，然后重新开始计算新的子段和，因为加上负数只会更小。

   ⚠️ 刚开始把两个if写反导致[-1]时过不了。要先更新res，再将sum置零。

2. DP 不会 下次再看



**Code**

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int res = INT_MIN;
        int sum = 0;

        for(int num: nums){
            sum += num;
            if(sum > res) res = sum;
            if(sum < 0) sum = 0;
           
        }
        return res;
    }
};
```



