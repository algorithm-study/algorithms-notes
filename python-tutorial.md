#Python Quick Tutorial
本文介绍Python用于解决算法问题的基础

##赋值
Python给变量赋值的时候不需要指定变量类型
```python
x = 1 # 整数
x = 4.483958 # 浮点数
x = 'hello, world' # 字符串，单引号可以用双引号替换
x = [1, 2, 3] # 数组 (List)
x = {'a': 1, 'b', 2} # 哈希表
```

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

## 常用数据结构

### 数组 (List)
数组在Python里一般用List来表示
```python
a = [] # 空数组
a = [1, 2, 3]  # 有三个整数的数组
```

### 哈希表 (字典/Hash Table/Dictionary)
哈希表在Python中就是dictionary，用来存储key-value pair
```python
a = {} # 空dictionary

a[*key*] = *value* # 给a的key赋值value
b = a[*key*] # 让b等于a中key的value
```