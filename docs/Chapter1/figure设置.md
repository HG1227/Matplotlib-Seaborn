# figure设置

```python
matplotlib.pyplot.figure(num=None, figsize=None, 
                        dpi=None, facecolor=None, 
                        edgecolor=None, frameon=True, 
                        FigureClass=<class 'matplotlib.figure.Figure'>, 
                        clear=False, **kwargs)

```

创建一个新的画布( figure )。

**输入参数：**

- `num` ：整型或者字符串，可选参数，默认：None。
              如果不提供该参数，一个新的画布(figure)将被创建而且画布数量将会增加。
              如果提供该参数，带有id的画布是已经存在的，激活该画布并返回该画布的引用。
              如果这个画布不存在，创建并返回画布实例。
              如果 num 是字符串，窗口标题将被设置为该图的数字。
- `figsize` ：整型元组，可选参数 ，默认：None。
              每英寸的宽度和高度。如果不提供，默认值是figure.figsize。
- ` dpi` ：整型，可选参数，默认：None。每英寸像素点。如果不提供，默认是figure.dpi。
- `facecolor` ：背景色。如果不提供，默认值：figure.facecolor。
- `edgecolor` ：边界颜色。如果不提供，默认值：figure.edgecolor。
- `framemon` ：布尔类型，可选参数，默认值：True。如果是False，禁止绘制画图框。
- `FigureClass` ：源于matplotlib.figure.Figure的类。（可选）使用自定义图实例。
- `clear` ：布尔类型，可选参数，默认值：False。如果为True和figure已经存在时，这是清理掉改图。


**返回值：**

- `figure` ：**Figure**。返回的Figure实例也将被传递给后端的new_figure_manager，这允许将自定义的图类挂接到pylab接口中。



```python
import numpy as np
import matplotlib.pyplot as plt
#创建一个数组0-100，数据间隔是0.1
x=np.arange(0,100,0.1)
 
y=x**2
 
#调用subplots函数
#指定图像分辨率、大小和长宽比例
#创建一个800*600像素、100dpi(每英寸100点)分辨率的图形
#返回一个画布对象和一个轴数组
fig,axe=plt.subplots(figsize=(4,3),dpi=100)
 
#在axe上绘制一条抛物线，红色 点
axe.plot(x,y,"r:")
#设置y轴标记为X
axe.set_xlabel("X")
#设置x轴标记为Y
axe.set_ylabel("Y")
 
#设置图标题
axe.set_title("y=x**2")
 
#显示绘制的图片
plt.show()
```

<center>
    <img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20191221180005.png"/>
</center>

