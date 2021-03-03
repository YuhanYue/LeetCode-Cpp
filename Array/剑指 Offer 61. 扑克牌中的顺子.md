#### [[剑指 Offer 61. 扑克牌中的顺子](https://leetcode-cn.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/)](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)



**Description**

从扑克牌中随机抽5张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。



**Example**

```C++
输入: [1,2,3,4,5]
输出: True
  
输入: [0,0,1,2,5]
输出: True
```



**Solution**

判定顺子的两个条件：

* max - min < 5;
* 不能有重复



**Code**

```cpp
class Solution {
public:
    bool isStraight(vector<int>& nums) {
        unordered_map<int, int> repeat;
        int minNum = 14;
        int maxNum = -1;
        for(int i = 0; i < nums.size(); i++){
            if(nums[i] == 0) continue;
            ++repeat[nums[i]];
            if(repeat[nums[i]] > 1) return false;
            minNum = min(minNum, nums[i]);
            maxNum = max(maxNum, nums[i]);
        }

        return maxNum - minNum < 5? 1: 0;
    }
};
```



