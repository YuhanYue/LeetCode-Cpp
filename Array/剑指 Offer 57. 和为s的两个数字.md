#### [剑指 Offer 57. 和为s的两个数字](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

**Description**

输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。



**Example**

```C++
输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
  
输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
```



**Solution**

❗️微软面试 双指针 智障题

看了下题解还有hash表解决？[hash](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/solution/mian-shi-ti-57-he-wei-s-de-liang-ge-shu-zi-shuang-/)



**Code**

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size()-1;

        while(left < right){
            if(nums[left] + nums[right] == target) return vector<int> {nums[left],nums[right]};
            if(nums[left] + nums[right] < target) left++;
            else right--;
        }
        return vector<int> {};

    }
};
```



