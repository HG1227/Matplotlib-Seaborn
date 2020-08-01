# 散点图

## `matplotlib.pyplot.scatter`

```python
matplotlib.pyplot.scatter(x, y, 
                          s=None, 
                          c=None, 
                          marker=None, 
                          cmap=None, 
                          norm=None, 
                          vmin=None, 
                          vmax=None, 
                          alpha=None, 
                          linewidths=None, 
                          verts=<deprecated parameter>, 
                          edgecolors=None, *, 
                          plotnonfinite=False, 
                          data=None, **kwargs)
```

参数：

- `x, y` The data positions. shape (n, )

- `s` shape (n, ), 以点 ** 2为单位的标记大小。默认值为rcParams['lines.marker大小']**2。

- `c` 颜色或颜色的数组或列表

- `marker` MarkerStyle，默认值：rcParams[“散点标记“]（默认值：'o'）

- `cmap`  [`Colormap`](https://www.osgeo.cn/matplotlib/api/_as_gen/matplotlib.colors.Colormap.html#matplotlib.colors.Colormap) ，可选，默认值：无颜色映射，可选，默认值：无

- `alpha` : 标量，可选，默认值：无 

  alpha混合值，介于0（透明）和1（不透明）之间。

- `linewidths` : 标量或类似数组，可选，默认值：无    标记边缘的线条宽度。

- `edgecolors` : 标记的边缘颜色

- 

