# Matplotlib text注释

```python
matplotlib.pyplot.text(x, y, 
                       s, 
                       fontdict=None, 
                       withdash=False, 
                       **kwargs)
```

参数

- `x`, `y`：表示坐标； 

- `s`：字符串文本； 

- `fontdict`：字典，可选, 文字属性； 

- `family`: 字体优先级列表 ‘serif’, ‘sans-serif’, ‘cursive’, ‘fantasy’, ‘monospace’

- `style`: 字体风格 ‘normal’, ‘italic’ , ‘oblique’.

- `weight`: 字体粗细，0-1000之间数字或者 ‘ultralight’, ‘light’, ‘normal’, ‘regular’, ‘book’, ‘medium’, ‘roman’, ‘semibold’, ‘demibold’, ‘demi’, ‘bold’, ‘heavy’, ‘extra bold’, ‘black’中的一个

- `size`: 字体大小，‘xx-small’, ‘x-small’, ‘small’, ‘medium’, ‘large’, ‘x-large’, ‘xx-large’ 或者一个整数

- `backgroundcolor` : 背景色
- `fontsize` 字体大小
- `kw`： `fontsize=12`, 
  `horizontalalignment=‘center’`、
  `ha=’cener’ `
  `verticalalignment=’center’`、
  `va=’center’`
- ` bbox` 给字体添加框，如` bbox=dict(facecolor='red', alpha=0.5) `等，各种风格
- `alpha` 设置框体的透明度， 
- `facecolor` 设置框体的颜色 
- `rotation` 表示标签的旋转角度，以逆时针计算，取整

```python
x = np.arange(-10, 11, 1)  #形成一个数组，第三个参数表示步长，#start,end,step
y = x ** 2

plt.plot(x, y)

# 第一个参数是x轴坐标
# 第二个参数是y轴坐标
# 第三个参数是要显式的内容
# alpha 设置字体的透明度
# family 设置字体
# size 设置字体的大小
# style 设置字体的风格
# wight 字体的粗细
# bbox 给字体添加框，alpha 设置框体的透明度， facecolor 设置框体的颜色
plt.text(x=-3, y=80, s="function: $y = x * x$", size = 15, alpha = 0.8)
plt.text(x=-3, y=40, s="function: $y = x * x$", size = 15,\
         family = "fantasy", color = "r", style = "italic", weight = "light",\
         bbox = dict(facecolor = "r", alpha = 0.2))
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513145421.png"/>



添加数据标签

```python
def showResult(xList, yList, title, xLabel, yLabel):
    plt.plot(xList, yList, 'g*-')
    plt.title(title)
    plt.xlabel(xLabel)
    plt.ylabel(yLabel)
    for x, y in zip(xList, yList):
        plt.text(x, y+0.3, str(y), ha='center', va='bottom', fontsize=10.5)
    plt.savefig('111.jpg')
    plt.show()

x_arr = [1, 2, 3, 4, 5, 6]
y_arr = [1, 4, 9, 16, 25, 36]
showResult(x_arr, y_arr, 'title', 'x', 'y')
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513145630.jpg"/>



其中

```python
for x, y in zip(xList, yList):
	plt.text(x, y+0.3, '%.0f'%y, ha='center', va='bottom', fontsize=10.5)


```

逐个获取需要标注的点的横纵坐标 x与 y，然后在位置 (x, y+0.3) 处以 10.5 的字体显示出 y 的值，‘center’ 和 ‘bottom’ 分别指水平和垂直方向上的对齐方式。