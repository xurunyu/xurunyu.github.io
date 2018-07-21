---
titie: Java核心技术
---

## 抽象类能否包含实例方法？

__能__ 。
Java类库提供一个 AbstractCollection抽象类，它实现了Collection接口，可以用来扩展它以实现具体的集合类。
AbstractCollection 将基础方法 size iterator抽象化，而提供了具体的实例方法 contains
在继承这个抽象类的时候，需要将size iterator方法实现，而contains由超类AbstractCollection提供了，当然，如果有更搞笑的contains方法的话，也可以由子类自己实现。

## 泛型
泛型使得相同的代码被不同的类型的对象重复使用。比如一个集合类，可以存放任何类型的对象。
泛型在造轮子的时候更加有用。

![泛型](http://wx2.sinaimg.cn/large/445d0f8bgy1fthjr8772rj21kw0f5gth.jpg)

## 集合类
集合类实现了Collection接口。集合接口一个基本方法是返回集合的迭代器。
迭代器Iterator 通过 next() 方法遍历集合；remove() 方法可以删除取出的元素。remove与next所获得的元素索引密切相关，无法连续两次调用remove。

链表 数组 散列集 树集 队列 双向队列 优先级队列 映射表

队列
![队列](http://wx2.sinaimg.cn/large/445d0f8bgy1fthjepz50tj20v80fywgi.jpg)
