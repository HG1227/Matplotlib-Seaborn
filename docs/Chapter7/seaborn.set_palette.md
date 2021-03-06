# seaborn.set_palette

```py
seaborn.set_palette(palette, n_colors=None, desat=None, color_codes=False)
```

通过 searborn 调色板设置 matplotlib 色彩循环

参数：`palette`：seaborn color paltte &#124; matplotlib colormap &#124; hls &#124; husl

> 调色板参数。 应该可以被 [`color_palette()`](seaborn.color_palette.html#seaborn.color_palette "seaborn.color_palette") 函数处理。

`n_colors`：int

> 色彩循环中的颜色数量。默认数量与`palette`模式有关, 查看[`color_palette()`](seaborn.color_palette.html#seaborn.color_palette "seaborn.color_palette")文档了解更多内容。

`desat`：float

> 每种颜色去饱和的比例。

`color_codes`：bool

> 如果为`True`，并且`palette`是 seaborn 调色板, 则将颜色代码简写 (例如“b”, “g”, “r”等等)映射到当前调色板上。



另外

在`with`语句中临时设置调色板或色彩循环。设置参数以调整绘图元素的默认参数。

例子

```py
>>> set_palette("Reds")

```

```py
>>> set_palette("Set1", 8, .75)

```