# seaborn.axes_style

```python
seaborn.axes_style(style=None,rc=None)
```

返回一个参数数组作为图表的自定义风格。

它会影响诸如**坐标轴的颜色**，是否默认启用网格，和其他自定义元素。

这个函数返回一个对象，该对象可以在 with 语句中使用以临时改变样式参数。

参数：style：字典,None,或者{darkgrid, whitegrid, dark, white, ticks}其中一个。

> 一个参数字典或者一个预配置集的名称。

rc：字典，可选的

> 给定参数映射以覆盖预先设定的（默认的）seaborn 样式参数字典

参见

给一个 seaborn 主题设定 matplotlib 参数，返回一个参数字典，以缩放图标元素并可以定义图表的调色板。

例子：

```python
>>> st = axes_style("whitegrid")
```

```python
>>> set_style("ticks", {"xtick.major.size": 8, "ytick.major.size": 8})
```

```python
>>> import matplotlib.pyplot as plt
>>> with axes_style("white"):
...     f, ax = plt.subplots()
...     ax.plot(x, y)
```

