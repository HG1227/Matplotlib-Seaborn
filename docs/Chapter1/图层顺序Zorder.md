# 图层顺序Zorder

Zorder演示

艺术家的绘画顺序是由他们的 `zorder` 属性，它是一个浮点数。具有更高 `zorder` 画在上面。您可以通过设置 `zorder` . 默认值取决于艺术家的类型：

<img src=".\img\image-20200801174813185.png" alt="image-20200801174813185" style="zoom:80%;" />

对plotting方法的任何调用都可以显式地为该特定项的zorder设置值。

```python
import matplotlib.pyplot as plt
import numpy as np

r = np.linspace(0.3, 1, 30)
theta = np.linspace(0, 4*np.pi, 30)
x = r * np.sin(theta)
y = r * np.cos(theta)
```

以下示例包含 [`Line2D`](https://www.osgeo.cn/matplotlib/api/_as_gen/matplotlib.lines.Line2D.html#matplotlib.lines.Line2D) 创建的 [`plot()`](https://www.osgeo.cn/matplotlib/api/_as_gen/matplotlib.axes.Axes.plot.html#matplotlib.axes.Axes.plot) 点（a） [`PatchCollection`](https://www.osgeo.cn/matplotlib/api/collections_api.html#matplotlib.collections.PatchCollection) )创建者 [`scatter()`](https://www.osgeo.cn/matplotlib/api/_as_gen/matplotlib.axes.Axes.scatter.html#matplotlib.axes.Axes.scatter) . 因此，在默认情况下，点位于线的下方（第一个子图）。在第二个子图中 `zorder` 点的顶端被明确地设置为移动。

```python
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(6, 3.2))

ax1.plot(x, y, 'C3', lw=3)
ax1.scatter(x, y, s=120)
ax1.set_title('Lines on top of dots')

ax2.plot(x, y, 'C3', lw=3)
ax2.scatter(x, y, s=120, zorder=2.5)  # move dots on top of line
ax2.set_title('Dots on top of lines')

plt.tight_layout()
```

<img src=".\img\sphx_glr_zorder_demo_001.png" alt="sphx_glr_zorder_demo_001" style="zoom:80%;" />

许多创建可见对象的函数都接受 `zorder` 参数。

```python
x = np.linspace(0, 7.5, 100)
plt.rcParams['lines.linewidth'] = 5
plt.figure()
plt.plot(x, np.sin(x), label='zorder=2', zorder=2)  # bottom
plt.plot(x, np.sin(x+0.5), label='zorder=3',  zorder=3)
plt.axhline(0, label='zorder=2.5', color='lightgrey', zorder=2.5)
plt.title('Custom order of elements')
l = plt.legend(loc='upper right')
l.set_zorder(2.5)  # legend between blue and orange line
plt.show()
```

<img src=".\img\sphx_glr_zorder_demo_002.png" alt="sphx_glr_zorder_demo_002" style="zoom:80%;" />