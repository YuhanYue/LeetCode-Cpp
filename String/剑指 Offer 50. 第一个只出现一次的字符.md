#### [剑指 Offer 50. 第一个只出现一次的字符](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

**Description**

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。



**Example**

```C++
s = "abaccdeff"
返回 "b"

s = "" 
返回 " "

```



**Solution**

* 哈希表

  1. `unordered_map<char, int>` 下拉链表，按插入顺序，只要找到第一个出现次数为1的即可。

     

**REVIEW**

[C++中map、hash_map、unordered_map、unordered_set通俗辨析](https://blog.csdn.net/u013195320/article/details/23046305?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&dist_request_id=1328592.9151.16147531418168613&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)

[unordered_map](http://www.cplusplus.com/reference/unordered_map/unordered_map/)

```C++
unordered_map<Key,T>::iterator it;
(*it).first;             // the key value (of type Key)
(*it).second;            // the mapped value (of type T)
(*it);                   // the "element value" (of type pair<const Key,T>) 
it->first;               // same as (*it).first   (the key value)
it->second;              // same as (*it).second  (the mapped value) 

```



**Code**

```cpp
class Solution {
public:
    char firstUniqChar(string s) {
        if(s == "") return ' ';

        unordered_map<char,int> hash;//初始化？

        for(char ch: s) ++hash[ch];
        for(int i = 0; i < s.length(); i++){
            if(hash[s[i]] == 1) return s[i];
        }

        return ' ';
    }
};
```



