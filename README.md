# treapy

平衡树“树堆”的Python实现。

```python
from treapy import treap
a=treap({'key_B':'value_B','key_A':'value_A'})
a['key_C']='value_C'
for i in a:
    print(i)
print(list(a.item()))
```

元素会保持按照键有序。

```python
key_A
key_B
key_C
[('key_A', 'value_A'), ('key_B', 'value_B'), ('key_C', 'value_C')]
```

重载了比较函数的对象可用于键。

```python
class pair:
    def __init__(self,first,second):
        self.first=first
        self.second=second
    def __lt__(self,other):
        if(self.first==other.first):
            return self.second<other.second
        return self.first<other.first
    def __eq__(self,other):
        return self.first==other.first and self.second==other.second
    def __repr__(self):
        return "pair(%s,%s)"%(self.first,self.second)
a=treap()
a[pair(2,3)]='value2,3'
a[pair(1,3)]='value1,3'
a[pair(1,2)]='value1,2'
for i,j in a.item():
    print(i,':',j)
```

```python
pair(1,2) : value1,2
pair(1,3) : value1,3
pair(2,3) : value2,3
```

快速按从小到大排名获取元素（以0起始）

```python
a=treap()
for i in '0123456789':
    a[i]='value_'+i
print(list(a))
print(a.rank(4))
```

 ```python
['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
('4', 'value_4')
 ```

