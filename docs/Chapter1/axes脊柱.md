# axes脊柱(坐标系)设置

`ax = plt.gca() ` # 获取当前的axes

属性列表

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200324215435.png"/>



**去掉脊柱(坐标系)**

```
ax.spines[‘top’].set_visible(False) #去掉上边框

ax.spines[‘bottom’].set_visible(False) #去掉下边框

ax.spines[‘left’].set_visible(False) #去掉左边框

ax.spines[‘right’].set_visible(False) #去掉右边框


```

**移动脊柱**

```
ax.spines[‘right’].set_color(‘none’)
ax.spines[‘top’].set_color(‘none’)

ax.xaxis.set_ticks_position(‘bottom’)  ##刻度的显示位置(轴的下面/上面)
ax.spines[‘bottom’].set_position((‘data’,0))

ax.yaxis.set_ticks_position(‘left’)
ax.spines[‘left’].set_position((‘data’,0))

```

```
plt.tick_params(axis="x",labelrotation=-60)

ax=plt.gca()
ax.spines['top'].set_visible(False) #去掉上边框
ax.spines['right'].set_visible(False) #去掉上边框
ax.xaxis.set_ticks_position('bottom')
ax.spines['bottom'].set_position(('data',0.5))


```



**设置边框线颜色**

`ax = plt.gca()` # 获取当前的axes

```python
ax.spines['right'].set_color('blue')
ax.spines['top'].set_color('none')

```

**设置边框线宽**

```python
ax1.spines['left'].set_linewidth(5)

```

**设置边框线型**

```python
ax.spines['left'].set_linestyle('--')

```

**设置反方向x轴(y轴同理)**

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

示例：

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
#ax.xaxis.set_ticks_position('bottom')
#ax.yaxis.set_ticks_position('right')


# 7.设置反方向(y轴同理)
ax.invert_xaxis()  # x轴反向

# 展示
plt.show()


```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200324221750.png"/>



<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200324221811.png"/>

将坐标轴移到中间，即笛卡尔坐标轴。路径：将图形上，右边隐藏，将下，左边移动到中间，需要用到`gca函数`获取Axes对象，接着通过这个对象指定每条边的位置，使用`set_color`设置成none。