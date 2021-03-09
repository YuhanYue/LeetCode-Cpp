#### [剑指 Offer 30. 包含min函数的栈](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)

**Description**

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。



**Example**

```C++
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.

```



**Solution**

辅助栈

<img src="/Users/yuhan/Library/Application Support/typora-user-images/Screen Shot 2021-03-09 at 4.09.00 PM.png" alt="Screen Shot 2021-03-09 at 4.09.00 PM" style="zoom:50%;" />



**Code**

```cpp
class MinStack {
private:
    stack<int> A;
    stack<int> B;

public:
    /** initialize your data structure here. */
    MinStack() {
        
    }
    
    void push(int x) {
        A.push(x);
        if(B.empty() || B.top() > x){
            B.push(x);
        } else {
            B.push(B.top());
        }

    }
    
    void pop() {
            A.pop();
            B.pop();
    }
    
    int top() {
        return A.top();
    }
    
    int min() {
        return B.top();
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->min();
 */
```



