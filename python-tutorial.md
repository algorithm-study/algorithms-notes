#Python Quick Tutorial
本文介绍Python用于解决算法问题的基础

---

##赋值
Python给变量赋值的时候不需要指定变量类型
```python
x = 1 # 整数
x = 4.483958 # 浮点数
x = 'hello, world' # 字符串，单引号可以用双引号替换
x = [1, 2, 3] # 数组 (List)
x = {'a': 1, 'b', 2} # 哈希表
```

---

##if else
基本结构:
```python
if *condition*:
  一些语句
elif *condition*:
  另外一些语句
# 可以有0~正无穷个 elif
else:
  最后一些语句
```

---

## 循环
一般会用到for和while循环
```python
for *variable* in *List*:
  一些语句

while *condition*:
  一些语句
```

for 一般用于遍历数组，又可以分为两种用法:
1. 遍历数组每个元素
```python
a = ['a', 'b', 'c']
for item in a:
  # 在循环过程中, item分别等于 'a', 'b', 和'c'
```

2. 遍历数组下标
a = ['a', 'b', 'c']
for i in range(len(a)):
  # 在循环过程中, item分别等于 0, 1, 2

range()是一个函数，用于返回一个包含一个范围的数值的数组
比如range(5)返回[0, 1, 2, 3, 4]

---

## 列表推导式

列表推导式(List Comprehensions)提供了一种简洁优雅地创建列表的方法。
举例，为了生成从0到9的所有数的平方，直觉是用for循环来做：
```python
squares = []
for x in range(10):
    squares.append(x**2)
```
可以看到，这么简单的一个功能就要写三行代码，非常繁琐，下面使用列表推导式：
```python
squares = [x**2 for x in range(10)]
```

> [python docs] (https://docs.python.org/2/tutorial/datastructures.html)

---

## Lambda 函数
Lambda 函数是一种短小精悍的**匿名函数**，经常与 `map()`, `filter()`, `reduce()` 等函数联合使用。

**语法**:  ```lambda argument_list: expression```

下面的lambda 函数返回其接收的两个参数的和
```python
>>> f = lambda x, y : x + y
>>> f(1,1)
2
```

---

## map, filter, reduce 函数
1. map
 `map()` 函数接收两个参数，其第一个参数是一个函数，第二个参数是一个可迭代的序列。它返回一个**新的序列**，序列中的值等于分别将 `func` 作用于 `seq` 中的每一个元素得到的值。
 **语法**: ```new_seq = map(func, seq)```
 ```python
 num = [1, 2, 3, 4, 5]
 new_num = map(lambda x : x**2, num)
 >>> num
 [1, 2, 3, 4, 5]
 >>> new_num  # 返回的新列表，其每个值分别为原列表中对应元素的平方
 [1, 4, 9, 16, 25]
 ```
 
2. filter()
 `filter()` 函数接收两个参数，语法与 `map()` 函数相同。其作用是将`func` 作用于 `seq` 中的每一个元素，如果结果为 `True` ，将它添加到返回的**新序列**中，否则直接忽略。
  ```python
 num = [1, 2, 3, 4, 5]
 new_num = filter(lambda x : x % 2 == 0, num)
 >>> num
 [1, 2, 3, 4, 5]
 >>> new_num  # 返回的新列表，其每个值分别对应着元列表中的偶数
 [2, 4]
 ```
 
3. reduce()
 `reduce()` 函数接收两个参数，语法与 `map()` 函数相同，但其功能略微复杂。
 假设 seq = [ s1, s2, s3, ... , sn ], `reduce()` 的工作方式介绍如下：
 * 首先它弹出列表的前两个元素，并调用 `func()`, 然后将结果从首部添加进seq，此时的 `seq` 为 
  [ func(s1, s2), s3, ... , sn ]。
 * 接着重复上一步骤，直至`seq` 中只剩下一个元素为止，将其作为 `reduce()` 的返回值返回。
```python
 num = [1, 2, 3, 4, 5]
 new_num = reduce(lambda x, y : x + y, num)
 >>> num
 [1, 2, 3, 4, 5]
 >>> new_num  # 返回num中所有数之和
 15
```

> [python-course] (http://www.python-course.eu/lambda.php)

---

## 常用数据结构

### 数组 (List)
数组在Python里一般用List来表示
```python
a = [] # 空数组
a = [1, 2, 3]  # 有三个整数的数组
```

---

### 堆栈(Stack)
堆栈的特性是先入后出，可以使用List的 `append()` 以及 `pop()` 函数（默认弹出最后一个元素）来实现堆栈。
```python
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack
[3, 4, 5]
>>> stack.pop()
5
>>> stack.pop()
4
>>> stack
[3]

```

---

### 队列(Queue)
队列的特性是先入先出，虽然同样可以使用List 的 `pop(0)` 来实现队列从首部取元素的功能，但是此操作的时间复杂度为 `O(n)`，效率不高。
Python内置的 `collections.deque` 类提供了快速从首部和尾部弹出元素的方法，可以使用它来实现队列。
```python
>>> from collections import deque
>>> queue = deque([3, 4, 5])
>>> queue.append(6)
>>> queue.popleft()
3
>>> queue.popleft()
4
>>> queue
deque([5, 6])
```

---

### 集合(Set)
集合在Python中是一种无序的数据结构，它的特性即是不允许存在重复的元素，常见的用途为**判断存在性**(效率很高）以及**剔除重复元素**。

```python
>>> a = set([1, 2, 3, 4, 5, 5])
>>> b = set([3, 4, 5, 6, 7, 7])
>>> a                                  # unique letters in a
set([1, 2, 3, 4, 5])
>>> a - b                              # values in a but not in b
set([1, 2])
>>> a | b                              # values in either a or b
set([1, 2, 3, 4, 5, 6, 7])
>>> a & b                              # values in both a and b
set([3, 4, 5])
>>> a ^ b                              # values in a or b but not both
set([1, 2, 6, 7])
```

---

### 哈希表 (字典/Hash Table/Dictionary)
哈希表在Python中就是dictionary，用来存储key-value pair
```python
a = {} # 空dictionary

a[*key*] = *value* # 给a的key赋值value
b = a[*key*] # 让b等于a中key的value
```
