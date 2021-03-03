#### [剑指 Offer 53 - I. 在排序数组中查找数字 I](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)



**Description**

统计一个数字在排序数组中出现的次数。



**Example**

```C++
输入: nums = [5,7,7,8,8,10], target = 8
输出: 2
  
输入: nums = [5,7,7,8,8,10], target = 6
输出: 0
```



**Solution**

zjd说：这题搞花里胡哨的就是傻逼



**Code**

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int n;
        int i = 0;
        for(i = 0; i < nums.size(); i++){
            if(nums[i] == target){
                n = i;
                break;
            }
        }

        if(i == nums.size()) return 0;

        int count = 1;
        for(int i = n+1; i < nums.size(); i++){
            if(nums[i] == target) count++;

        }

        return count;
    }
};
```



