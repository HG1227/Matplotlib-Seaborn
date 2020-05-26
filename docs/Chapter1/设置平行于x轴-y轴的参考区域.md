# 设置平行于x轴/y轴的参考区域

```python
axhspan() / axvspan()

ax ~ axis 
h ~ horizontal，水平的 
v ~ vertical，垂直的 
span ~ 跨度，区间，范围
这两个函数分别用于设置平行于x轴/y轴的参考区域。

```

```
import matplotlib.pyplot as plt
import numpy as np

# 生成数据
x = np.linspace(0, 10, 100)
y = np.sin(x)

# 使用scatter绘图
plt.plot(x, y, ls='-.', lw=2, c='c', label='sin(x)')
plt.legend()

# xmin/xmax/ymin/ymax用于设置区间范围
# facecolor用于设置区域颜色
# alpha用于设置透明度
plt.axhspan(ymin=-0.25, ymax=0.25, facecolor='purple', alpha=0.3)
plt.axvspan(xmin=4, xmax=6, facecolor='g', alpha=0.3)

plt.show()

```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200324214021.png"/>



```
import matplotlib.pyplot as plt

fig, ax = plt.subplots()
ax.plot(range(20))
ax.axvspan(8, 14, ymin=0.1, ymax=0.9, alpha=0.5, color='red')

plt.show()
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200324214136.png"/>