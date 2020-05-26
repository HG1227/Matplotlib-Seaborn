# Matplotlib：刻度线的开启和关闭

﻿在matplotlib中，刻度线叫`tick`，刻度值叫`tick_label`

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190924160130807.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hIRzIwMTcxMjI2,size_16,color_FFFFFF,t_70)



注意这幅图片中就包含了关于刻度线的一些信息。比方，不仅有主刻度线(`Major tick`)，还有次刻度线(`Minor tick`)。并且我们看到刻度线都是朝着图的外侧。图中，上边的和右边的坐标轴(`Spine`)并没有刻度线。

## 是否显示次刻度线

在pylab中内置了两个函数`minorticks_on()`和`minorticks_off() `用来确定是否显示次刻度线。
如下代码实现在左侧图中显示次刻度线，在右侧不显示次刻度线。在默认的情况下，不显示次刻度线。

```python
plt.subplot(121)
plt.minorticks_on()
plt.subplot(122)
plt.minorticks_off()
plt.show()
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513104927.png"/>



## 刻度线的朝向

一般而言，我们希望刻度线朝外分布，这样避免影响图中的曲线和说明。但是有时候刻度线朝内分布，可以让图之间更加紧凑。在pylab中，利用`tick_params`控制刻度线的朝向，是朝图里，图外，还是都有。下面代码产生的图从左往右，分别显示朝里，朝外，两边都有的情况。

```python
plt.subplot(131)
plt.tick_params(direction='in')

plt.subplot(132)
plt.tick_params(direction="out")

plt.subplot(133)
plt.tick_params(direction='inout')

plt.show()
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190924161248776.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hIRzIwMTcxMjI2,size_16,color_FFFFFF,t_70)

## 选择修改主刻度线还是次刻度线

通过上面的例子可以看出，修改刻度线的主要函数就是tick_params。那么每次调用这个函数，是修改主刻度线、次刻度线，还是都改呢？这个由参数`which`控制。比方下面这段代码，分别让主刻度线朝里、次刻度线朝里、主次均朝里。最后一个图说明默认情况下，主次刻度线均朝外。

```python
plt.subplot(141)
plt.minorticks_on()
plt.tick_params(which='magor',direction='in')

plt.subplot(142)
plt.minorticks_on()
plt.tick_params(which='minor',direction='in')

plt.subplot(143)
plt.minorticks_on()
plt.tick_params(which='both',direction='in')

plt.subplot(144)
plt.minorticks_on()
plt.text(0.5,0.5,'default')

plt.show()
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019092416223528.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hIRzIwMTcxMjI2,size_16,color_FFFFFF,t_70)

## 修改刻度线的长度和宽度

如上图，如果觉得刻度线太短，太细，不太显眼，我们可以修改其长短、粗细。依然使用函数`tick_params`，通过参数`width`和`length`控制。下面代码让左图的主刻度线粗一些，右图的次刻度线长一些。

```python
plt.subplot(121)
plt.minorticks_on()
plt.tick_params(which='major',width=4)

plt.subplot(122)
plt.minorticks_on()
plt.tick_params(which='minor',length=10)

plt.show()
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190924162616183.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hIRzIwMTcxMjI2,size_16,color_FFFFFF,t_70)

## 在哪些轴上显示刻度线

我们来看怎么控制刻度线出现在哪些轴上。这里用参数`left`，`right`,`bottom,`top`来控制，下面代码画出的图片，依次显示上下左右轴上的刻度线。(自己实验的，默认左边和下边是开启的 )

```python
plt.subplot(1,4,1)
plt.tick_params(top=True,bottom=False,left=False,right=False)

plt.subplot(1,4,2)
plt.tick_params(top=False,bottom=True,left=False,right=False)

plt.subplot(1,4,3)
plt.tick_params(top=False,bottom=False,left=True,right=False)

plt.subplot(1,4,4)
plt.tick_params(top=False,bottom=False,left=False,right=True)

plt.show()
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2019092419034139.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hIRzIwMTcxMjI2,size_16,color_FFFFFF,t_70)

## 在哪些轴上显示刻度值

注意上面的图，刻度线分别出现在我们控制的坐标轴上，但是刻度值在默认情况下还是出现在左下两个轴上。这里仅说明如何让刻度值出现在相应刻度线的位置。比方，我们仅让上面的轴显示刻度线，也仅在该轴上显示刻度值，利用`labelbottom`, `labeltop`, `labelleft`, `labelright`四个参数控制，代码和图如下所示。

```python
plt.tick_params(top=True,bottom=False,left=False,right=False)
plt.tick_params(labeltop=True,labelleft=False,labelright=False,labelbottom=False)
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190924165140303.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hIRzIwMTcxMjI2,size_16,color_FFFFFF,t_70)

