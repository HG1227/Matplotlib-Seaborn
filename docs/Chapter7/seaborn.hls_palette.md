# seaborn.hls_palette

```py
seaborn.hls_palette(n_colors=6, h=0.01, l=0.6, s=0.65)
```

在 HLS 色调空间中获取一组均匀间隔的颜色。

h, s, 和 l 值应该在 0 和 1 之间。

参数：`n_colors`：int

> 调色板中的颜色数

`h`：float

> 第一个色调

`l`：float

> 亮度

`s`：float

> 饱和度


返回值：`palette`：seaborn 调色板

> 类似列表的颜色对象的 RGB 元组。



另外

在 HUSL 系统中使用等间距圆形色调创建一个调色板。

例子

使用默认参数创建一个有 10 种颜色的调色板：

```py
>>> import seaborn as sns; sns.set()
>>> sns.palplot(sns.hls_palette(10))

```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200512105929.jpg"/>

创建一个以不同色调值开头的 10 种颜色的调色板：

```py
>>> sns.palplot(sns.hls_palette(10, h=.5))

```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200512105949.jpg"/>

创建一个比默认颜色更暗的 10 种颜色的调色板：

```py
>>> sns.palplot(sns.hls_palette(10, l=.4))

```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200512110004.jpg"/>

创建 10 种颜色的调色板，其饱和度低于默认值：

```py
>>> sns.palplot(sns.hls_palette(10, s=.4))

```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200512110019.jpg"/>

