# Matplotlib：axes脊柱(坐标轴)

## 设置坐标轴范围

`plt.xlim()`、`plt.ylim `()

另外也可以使用`plt.axis([xmin, xmax, ymin, ymax])`确定坐标值的范围

面向对象的方法

`ax.set_xlim()`
`ax.set_ylim ()`

设置坐标轴的范围可以通过`axis()`,` xlim()`和`ylim()`三个来设置，`axis()`用来同时设置x轴和y轴，后面的两个都是针对于特定的坐标轴而言。

```python
matplotlib.pyplot.xlim(*args, **kwargs)
```



有两种参数输入方式

- `plt.xlim(num1, num2)`
- `plt.xlim(xmin=num1,xmax=num2)`



```python
matplotlib.pyplot.axis(*v, **kwargs)
```

**参数详解：**

1. **xmin, xmax, ymin, ymax** : float, optional

```python
pyplot.axis([1,2,2,4])
```



## 设置坐标轴名称

`plt.xlabel()`、`plt.ylabel()` 设置坐标轴名称

面向对象的方法

`ax.set_xlabel()`
`ax.set_ylabel()`

## 设置坐标轴刻度标签

`plt.xticks`、`plt.yticks`设置坐标轴刻度

面向对象的方法

`ax.set_xticklabel()`
`ax.set_yticklabel()` 

```python
matplotlib.pyplot.xticks(ticks=None, 
                         labels=None, 
                         *kwargs)
```

参数

- **ticks**array-like, optional

  The list of xtick locations. Passing an empty list removes all xticks.

- **labels**array-like, optional

  The labels to place at the given *ticks* locations. This argument can only be passed if *ticks* is passed as well.

- **kwargs**

  [`Text`](https://matplotlib.org/api/text_api.html#matplotlib.text.Text) properties can be used to control the appearance of the labels.

  常用的文本属性有 `fontsize` `color` `rotation` 等

**显示数字标签**

```
plt.plot()
plt.xticks( np.arange(5) )
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513134901.png"/>

**显示x轴的刻标以及对应的标签**

```python
plt.plot()
plt.xticks( np.arange(5), ['Tom', 'Dick', 'Harry', 'Sally', 'Sue'] )
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513115243.png"/>

```python
x = np.linspace(-3, 3, 50)
y1 = 2*x + 1
y2 = x**2

plt.figure()
plt.plot(x, y2)
plt.plot(x, y1, color='red', linewidth=1.0, linestyle='--')

plt.xlim((-1, 2))
plt.ylim((-2, 3))
plt.xlabel('I am x')
plt.ylabel('I am y')

new_ticks = np.linspace(-1, 2, 5)
plt.xticks(new_ticks)
plt.yticks([-2, -1.8, -1, 1.22, 3],
           [r'$really\ bad$', r'$bad$', r'$normal$', r'$good$', r'$really\ good$'])
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513135434.png"/>

## 设置axes脊柱(坐标系)

属性列表

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513135637.png"/>

### 去掉脊柱(坐标系)

```python
ax.spines[‘top’].set_visible(False) #去掉上边框

ax.spines[‘bottom’].set_visible(False) #去掉下边框

ax.spines[‘left’].set_visible(False) #去掉左边框

ax.spines[‘right’].set_visible(False) #去掉右边框

```

```
plt.tick_params(axis="x",labelrotation=-60)
ax=plt.gca() #获取对象
ax.spines['top'].set_visible(False) #去掉上边框
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513135918.png"/>

### 移动脊柱

```python
ax.spines[‘right’].set_color(‘none’)

ax.spines[‘top’].set_color(‘none’)

ax.xaxis.set_ticks_position(‘bottom’) # 刻度的显示位置

ax.spines[‘bottom’].set_position((‘data’,0))

ax.yaxis.set_ticks_position(‘left’)

ax.spines[‘left’].set_position((‘data’,0))

```

```python
plt.tick_params(axis="x",labelrotation=-60)
ax=plt.gca()
ax.spines['top'].set_visible(False) #去掉上边框
ax.spines['right'].set_visible(False) #去掉上边框

# 设置 bottom 的位置在 left 0.8处
ax.spines['bottom'].set_position(('data',0.8))
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513140340.png"/>

```python
plt.tick_params(axis="x",labelrotation=-60)
ax=plt.gca()
ax.spines['top'].set_visible(False) #去掉上边框
ax.spines['right'].set_visible(False) #去掉上边框
# 设置ticks 显示在top 处
ax.xaxis.set_ticks_position('top')
ax.spines['bottom'].set_position(('data',0.8))
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513140649.png"/>

### 设置边框线颜色

```python
ax = plt.gca() # 获取当前的axes

ax.spines['right'].set_color('blue')

ax.spines['top'].set_color('none')
```



### 设置边框线宽

```python
ax1.spines['left'].set_linewidth(5)
```



### 设置边框线型

```python
ax.spines['left'].set_linestyle('--')
```

### 设置反方向x轴(y轴同理)

```python
ax.invert_xaxis()  # x轴反向
```

```python
plt.tick_params(axis="x",labelrotation=-60)
ax=plt.gca()
ax.spines['top'].set_visible(False) #去掉上边框
ax.spines['right'].set_visible(False) #去掉上边框
ax.xaxis.set_ticks_position('bottom')
ax.spines['bottom'].set_position(('data',0.5))
ax.invert_xaxis()  # x轴反向

```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513141101.png"/>

```
gca():获取当前坐标轴信息
.spines:设置边框
.set_color:设置边框颜色：默认白色
.spines:设置边框
.xaxis.set_ticks_position:设置x坐标刻度数字或名称的位置
.yaxis.set_ticks_position:设置y坐标刻度数字或名称的位置
.set_position:设置边框位置
```



## 案例

```python
# 导入模块
import matplotlib.pyplot as plt
import numpy as np

# 数据
x = np.linspace(-10, 10, 100)
y = x**2

# 绘图
plt.plot(x, y)

ax = plt.gca()
# ===设置脊(边框)===
# 1.隐藏上与右的边框
ax.spines['top'].set_visible(False)
ax.spines['right'].set_color(None)

# 2.设置颜色
ax.spines['left'].set_color('b')
ax.spines['bottom'].set_color('r')

# 3.设置线宽
ax.spines['left'].set_linewidth(5)
ax.spines['bottom'].set_linewidth(3)

# 4.设置线形
ax.spines['left'].set_linestyle('--')
ax.spines['left'].set_linestyle('-.')

# 5.设置交点位置（0， 35）
ax.spines['left'].set_position(('data', 0))
ax.spines['bottom'].set_position(('data', 35))

# 6.设置数据显示的位置
#ax.xaxis.set_ticks_position('bottom')
#ax.yaxis.set_ticks_position('right')


# 7.设置反方向(y轴同理)
ax.invert_xaxis()  # x轴反向
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513141401.png"/>

```
# 导入模块
import matplotlib.pyplot as plt
import numpy as np

# 数据
x = np.linspace(-10, 10, 100)
y = x**2

# 绘图
plt.plot(x, y)

ax = plt.gca()
# ===设置脊(边框)===
# 1.隐藏上与右的边框
ax.spines['top'].set_visible(False)
ax.spines['right'].set_color(None)

# 2.设置颜色
ax.spines['left'].set_color('b')
ax.spines['bottom'].set_color('r')

# 3.设置线宽
ax.spines['left'].set_linewidth(5)
ax.spines['bottom'].set_linewidth(3)

# 4.设置线形
ax.spines['left'].set_linestyle('--')
ax.spines['left'].set_linestyle('-.')

# 5.设置交点位置（0， 35）
ax.spines['left'].set_position(('data', 0))
ax.spines['bottom'].set_position(('data', 35))

# 6.设置数据显示的位置
ax.xaxis.set_ticks_position('bottom')
ax.yaxis.set_ticks_position('right')


# 7.设置反方向(y轴同理)
ax.invert_xaxis()  # x轴反向
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513141600.png"/>

将坐标轴移到中间，即笛卡尔坐标轴。路径：将图形上，右边隐藏，将下，左边移动到中间，需要用到gac函数获取Axes对象，接着通过这个对象指定每条边的位置，使用set_color设置成none。实现代码如下：

```python
x = np.arange(-2*np.pi,2*np.pi,0.01)#定义横轴范围
y = np.sin(3*x)/x#函数
y2 = np.sin(2*x)/x
y3 = np.sin(x)/x
plt.plot(x,y)#绘制,matplotlib默认展示不同的颜色
plt.plot(x,y2,'--')
plt.plot(x,y3)
plt.xticks([-2*np.pi,-np.pi,0,np.pi,2*np.pi],[r'$-2\pi$',r'$\pi$','$0$','$\pi$','$2\pi$'])#显示横坐标刻度值，不加第二个参数，将显示的是数值而不是字母
plt.yticks([-1,0,1,2,3],[r'$-1$','$0$','$+1$','$+2$','$+3$'])
plt.legend(['y','y2','y3'])
plt.title('M10')
ax = plt.gca()#使用gca函数获取axes对象
ax.spines['right'].set_color('none')#右侧边隐藏
ax.spines['top'].set_color('none')
ax.xaxis.set_ticks_position('bottom')#将底边设为横坐标
ax.spines['bottom'].set_position(('data',0))#将坐标置于坐标0处
ax.yaxis.set_ticks_position('left')#左边设置为纵坐标
ax.spines['left'].set_position(('data',0))
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513141851.png"/>