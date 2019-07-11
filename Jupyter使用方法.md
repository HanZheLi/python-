# Jupyter使用方法及numpy、Series、dataFrame的入门

[TOC]



### 一、打开Jupyter的方法

在想要保存代码的文件夹内

```
shift+右键
```

打开powershell后，输入：

```
jupyter notebook
```

![1562835081132](.\图片\1562835081132.png)



### 二、numpy

操作如下截图：

![1562835652843](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562835652843.png)

![1562835693572](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562835693572.png)

![1562835743865](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562835743865.png)

![1562835771997](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562835771997.png)

![1562835795599](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562835795599.png)



### 三、Series

首先看看Series的思维导图

![1562836253416](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562836253416.png)

Series可以理解为是“竖立来”的列表（list）

在应用Series之前应该要导入两个包

```python
import numpy as np
import pandas as pd
```

我们可以通过两个问号+函数名打开帮助手册：

```python
??pd.Series
```

data表示的是数组，index指的是键：

```python
s1 = pd.Series(data=[1,2,3,4],index=['a','b','c','d'])#Series是竖起来的list
```

我们输出s1试试：

![1562836502055](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562836502055.png)

我们来看看其基础属性：

#### name

表示的是名称，例如我们可以设置`s1.index.name="NO."`，则![1562837106652](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837106652.png)

也可以设置data的name，与设置索引的name类似。

#### index&values

我们可以直接通过

```python
print(s1.index)
print(s1.valus)
```

来访问![1562836926541](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562836926541.png)

![1562837015562](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837015562.png)

#### 访问方式

要访问s1的某一行的values则直接通过：

```python
s1[i]
```

即可：![1562837172098](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837172098.png)

要访问某一键所对应的键值，则直接通过：

```python
s1['b']
```

![1562837217930](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837217930.png)

要同时访问多个键，可通过：

```python
s1[['a','b']]
```

![1562837256376](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837256376.png)

也可通过查看一些条件下的布尔值：

![1562837351346](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837351346.png)

可以通过切片的方式来访问多个键值对：

![1562837379644](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837379644.png)

可以通过布尔取值：

![1562837398296](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837398296.png)

##### loc和iloc方法

loc：表示根据索引取值，只能通过键来取

![1562837508156](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837508156.png)

iloc：默认用位置下标来访问（访问第二个和第0个键值对）

![1562837541443](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837541443.png)

#### 修改方式：

可以直接对某个键的键值进行修改：

![1562837620779](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837620779.png)

##### 删除：通过del命令

![1562837648160](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562837648160.png)

### 四、dataFrame

首先我们来看看dataFrame的部分思维导图：

![1562840877853](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562840877853.png)

我们先尝试使用pandas中的时间序列date_range函数来建立一个对象：

```python
dates = pd.date_range('20180401', periods=6)
```

* 注：date_range函数的原型是：

  ```python
  pandas.date_range(start=None, end=None, periods=None, freq='D', tz=None, normalize=False, name=None, closed=None, **kwargs)
  ```

  该函数主要用于生成一个固定频率的时间索引，在调用构造方法时，必须指定start、end、periods中的两个参数值，否则报错。

  

  输出它看看：

![1562840994747](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562840994747.png)

以刚刚初始化的对象作为参数初始化一个DataFrame对象：

```python
df = pd.DataFrame(np.random.randn(6,4), index=dates, columns=list('ABCD'))#6,4是维度，六行四列，A B C D是列名，dates作为行名
```

输出df：

![1562841434592](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841434592.png)

我们可以直接查看df的索引值：

![1562841490213](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841490213.png)

可以通过to_list函数将其转换为列表：

![1562841525712](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841525712.png)

或者直接进行类型转换：

![1562841541451](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841541451.png)



接下来获得数据以后我们可以开始画图了：

首先我们要加入画图工具包：

```python
import matplotlib.pyplot as plt#画图工具
%matplotlib inline#有了这句话就可以在浏览器当中嵌入这个图
```

然后输入

```python
df.plot()#画折线图
df.plot(kind='bar')#画柱状图
```

![1562841708173](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841708173.png)

![1562841654570](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841654570.png)



我们可以通过`info`函数来快捷查看多种信息：总行数、列数、每列元素类型和non-NaN的个数，总内存。

![1562841819291](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841819291.png)

可以通过describe函数来快速查看每一列的统计信息，默认排除所有NaN元素：

![1562841937084](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841937084.png)

可以通过`head`函数和`tail`函数，来从头至尾或者从尾至头查看信息：

![1562841945040](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841945040.png)

可以通过`sample`函数来随机选取n行数据查看：

![1562841991243](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562841991243.png)



对于访问某一列，我们可以直接通过键来访问：

![1562842066940](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842066940.png)

用`df.A`也可以得到同样的效果。

* 注：`df['2018-04-01']#会报错 因为访问是以列优先`



但我们可以用切片or布尔索引的方式来访问行：

![1562842159299](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842159299.png)

查看某一条件下的布尔值：

![1562842174938](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842174938.png)

通过布尔值取值：

![1562842190611](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842190611.png)



##### loc和iloc

可以直接访问某一行：

![1562842306933](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842306933.png)

可以通过loc函数来访问数组中的某一个元素：

![1562842256886](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842256886.png)

也可以同时访问某一行的多个元素：

![1562842277786](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842277786.png)

可以用`iloc`函数来同时访问具体某些行及某些列的元素：

![1562842359553](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842359553.png)



#### 保存入csv文件

通过`to_csv`函数可以直接写入一个csv文件：

![1562842501362](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842501362.png)

![1562842546161](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842546161.png)

我们也可以通过read_csv函数来从某个csv文件中读取内容，存入某个对象之中：

![1562842599592](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842599592.png)



可以通过sum函数、min函数来来计算某列或者某行的算数值：

![1562842796192](C:\Users\李瀚哲\AppData\Roaming\Typora\typora-user-images\1562842796192.png)



以上只是本人今日所学的十分基础的知识，日后会继续更新~
