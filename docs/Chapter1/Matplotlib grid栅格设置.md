# Matplotlib:grid栅格设置

# 栅格设置

打开栅格:`plt.grid(true)`

函数

```python
matplotlin.pyplot.grid(b, 
						which, 
						axis, 
						color, 
						linestyle, 
						linewidth， 
						**kwargs
					)

```

- `b`: 布尔值。就是是否显示网格线的意思。官网说如果b设置为None， 且kwargs长度为0，则切换网格状态。但是没弄明白什 么意思。如果b设置为None，但是又给了其它参数，则默认None值失效。
- `which` : 取值为`major`, `minor`， `both`。 默认为’major’。显示主刻度、副刻度、全部显示网格
- `axis`: 取值为`both`，`x`，`y`。就是想绘制哪个方向的网格线。
- `color` : 就是设置网格线的颜色。或者直接用 c 来代替 color 也可以。
- `linestyle` :也可以用ls来代替linestyle， 设置网格线的风格，是连续实线，虚线或者其它不同的线条。 | ‘-’ | ‘–’ | ‘-.’ | ‘:’ | ‘None’ | ’ ’ | ‘’]
- `linewidth` : 设置网格线的宽度
- `alpha`:设置透明度

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200324215218.png"/>

参数 `axis`

```python
fig,ax = plt.subplots(1,3)
ax[0].grid(axis="x")
ax[1].grid(axis="y")
ax[2].grid(axis="both")
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513103339.png"/>



