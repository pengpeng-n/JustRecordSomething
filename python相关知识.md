python语言相关记录：

### 一. 字典删除元素的几种方式：

1.clear()删除字典中的所有元素：

```python
dict = {'name': 'aaa', 'val': 10000}
dict.clear();  # 清空词典所有条目
```

2.pop()删除字典给定键 key 所对应的值，返回值为被删除的值

```python
site= {'name': 'aaa', 'val': 10000}
pop_obj = site.pop('name') # 删除要删除的键值对，如{'name':'aaa'}
print pop_obj   # 输出 ：aaa
```

3.del 全局方法，能删单一的元素也能清空字典，清空只需一项操作

```python
site= {'name': 'aaa', 'val': 10000}
del site['name'] # 删除键是'name'的条目 
del site  # 清空字典所有条目
```

4.popitem()随机返回并删除字典中的一对键和值

```python
site= {'name': 'aaa', 'val': 10000}
pop_obj=site.popitem() # 随机返回并删除一个键值对
print pop_obj   # 输出结果可能是{'val','1000'}
```

### 二. 列表插入元素的几种方式：

1.append()函数：接受一个参数（待插入的元素），将该参数视为一个列表元素在原列表的末尾插入，如果该参数是一个列表，那么就将这个列表作为一个列表元素插入到列表中。

```python
a = [1, 2]
b = [3, 4]
a.append(b)  # a = [1, 2, [3, 4]]
```

2.extend()函数：接受一个参数将其在原列表的末尾插入，待插入的元素视为一个列表，将该列表的每个元素依次插入到原列表中。

```python
a = [1, 2]
b = [3, 4]
a.extend(b)  # a = [1, 2, 3, 4]
```

3.insert()函数：接受两个参数。L.insert(index, object)，在列表L的index前，按对象插入object。（类似于append，只是可以指定插入位置）

```
a = [1, 2]
b = [3, 4]
a.insert(1, b)  # a = [1, [3, 4], 2]
```

### 三. python中的字符串常用函数

1.判断字符串的类型：

str.isdigit():判断是否是数字；str.isalpha():判断是否是字母；str.isalnum():判断是否是字母或者数字

str.lower(), str.upper()：分别将字符串中的大写字母变成小写字母，或者将字符串中的小写字母变成大写字母。

2.filter(function, iterable)函数，用来过滤字符串。python2中返回列表，python3中返回迭代器。

```python
s = "1A3.d8a.*)mlSk"
s = [*filter(str.isalnum, s.lower())] # 将s中所有大写字母变成小写字母，再过滤得到其中的字母和数字，*用来解压，取出返回的迭代器中的每个元素，组成一个新列表。
```

```python
def is_odd(n):
    return n % 2 == 1
newlist = list(filter(is_odd, [1, 2, 3, 4, 5, 6]))#取出所有奇数
```

