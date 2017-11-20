---
Python learning notes
---

# 初始Python

### Python好处

便捷，快速，功能强大

### 安装Python

官网下载安装文件安装Python 3

使用安装包自带的IDLE进行编写代码

### 数据结构 列表 - 数组

```python
movies = ["The Holy Grail","The Life of brain"]
```

Python不需要声明变量类型

列表通过下标访问数据

```python
print(movies[0])
```

列表是一个集合对象，所以提供特有的方法

```python
len(movies) 
movies.appen("The Meaning of Life")
movies.pop()
movies.extend(["Another 1","Another 2"])
movies.remove("Another 1")
movies.insert(0,"Another 3")
```

列表可以放置混合类型的数据

### 迭代 - 循环

```python
for movie in movies:
	print(movie)
```

语法:

​	for 目标标识符 in 列表 :

​		列表处理代码

```python
count = 0
while count < len(movies):
	print(movies[count])
    count = count+1
```

while循环和for循环作用一样

### 条件表达式

```python
if isinstance(movies,list):
    print(movies)
else:
    print("not list")

```

### 注意项

#### 字符串

单引号和双引号都可以创建字符串，只要前后一致即可

在一个字符串中包含双引号

```python
str = "includ quote \" "
str = 'includ quote " '
```

#### 命名规则

名字以一个字母或下划线开头，后面可以包含任一字母、数字、/、下划线

区分大小写

#### BIF

built in function, python 3中大约有70个BIF

在IDLE shell中输入:

```python
dir(__builtins__)
```

可以查看所有BIF的列表

输入:

```python
help(isinstance)
```

可以查看isinstance()的功能描述





