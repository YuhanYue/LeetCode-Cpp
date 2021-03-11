# unordered_set

### 增删查:

`unordered_set::insert`
`unordered_set::find`
`unordered_set::erase`



### 用法

##### 基本操作

```C++
//initial 
unordered_set<int> c1;

//插入函数 emplace()
c1.emplace(1);

//插入函数 insert()
c1.insert(1);

//删除 erase()
c1.erase(1);//1.迭代器 value 区域

//value出现的次数 count() 返回匹配给定主键的元素的个数
c1.count(1);
```

##### 容量操作

```C++
//判断是否为空
c1.empty();
    
//获取元素个数 size()
c1.size();
    
//获取最大存储量 max_size()
c1.max_size();
```

<img src="/Users/yuhan/Library/Application Support/typora-user-images/Screen Shot 2021-03-11 at 3.10.49 PM.png" alt="Screen Shot 2021-03-11 at 3.10.49 PM" style="zoom:50%;" />