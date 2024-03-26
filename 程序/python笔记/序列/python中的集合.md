在 Python 中，集合（set）是一种无序的集合数据类型，它包含不重复的元素。集合是 Python 内置的数据结构之一，它的主要特点是元素的唯一性和无序性。集合的操作包括添加元素、删除元素、检查元素是否存在、集合的并集、交集、差集等。
### 创建集合
创建集合的方法有很多种，最常见的是使用花括号 {} 或者 set () 函数。
```python
# 使用花括号创建集合
my_set = {1, 2, 3, 4}
# 使用set()函数创建集合
my_set = set([1, 2, 3, 4])
```
### 集合的基本操作
- **添加元素**：使用 add () 方法向集合中添加元素。
```python
my_set = {1, 2, 3}
my_set.add(4)
print(my_set) # 输出：{1, 2, 3, 4}
```
- **删除元素**：使用 remove () 方法删除集合中的元素。如果元素不存在，会抛出一个错误。使用 discard () 方法可以安全地删除元素，如果元素不存在，不会抛出错误。
```python
my_set = {1, 2, 3, 4}
my_set.remove(1)
print(my_set) # 输出：{2, 3, 4}
my_set.discard(5) # 不会抛出错误
```
- **检查元素是否存在**：使用 in 关键字检查元素是否存在于集合中。
```python
my_set = {1, 2, 3, 4}
print(2 in my_set) # 输出：True
```
### 集合的集合操作
- **并集**：使用 union () 方法或 | 运算符获取两个集合的并集。
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
union_set = set1.union(set2)
print(union_set) # 输出：{1, 2, 3, 4, 5}
```
- **交集**：使用 intersection () 方法或 & 运算符获取两个集合的交集。
```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}
intersection_set = set1.intersection(set2)
print(intersection_set) # 输出：{2, 3}
```
- **差集**：使用 difference () 方法或 - 运算符获取两个集合的差集。
```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}
difference_set = set1.difference(set2)
print(difference_set) # 输出：{1}
```
- **对称差集**：使用 symmetric_difference () 方法或 ^ 运算符获取两个集合的对称差集。
```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}
symmetric_difference_set = set1.symmetric_difference(set2)
print(symmetric_difference_set) # 输出：{1, 4}
```
集合是 Python 中非常强大的数据结构，它的无序性和唯一性使得它在处理不重复元素的集合时非常有用。
