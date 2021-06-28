# Stack

```c++
/*stl  标准模板函数  stack 栈
 *栈先进先出（FIFO）
 * 栈的低地址存放栈顶元素
 */
#include <iostream>
#include <stack>
using namespace std;

int main()
{
//定义模板类对象
    stack<int> s;
//入栈
    s.push(5);
    s.push(9);
    s.push(6);
    s.push(4);
    cout << "top = " << s.top() << endl;  //查看栈顶元素
    cout << "size= " << s.size()<< endl;  //查看栈空间
    s.pop(); //出栈，栈的结构，使得出栈一次即删除栈顶源于
    cout << "top = " << s.top() << endl;
    cout << "size= " << s.size()<< endl;  
    cout << "empty : " << s.empty() << endl;//判断栈是否为空
}

```

