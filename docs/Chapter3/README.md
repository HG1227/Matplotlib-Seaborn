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




参数 ：`c` 颜色或颜色的数组或列表  

使用列表映射颜色，

```python
import numpy as np #数学处理库
import pandas as pd #用于处理.csv excel html 文本等文件
import matplotlib as mpl #画图像的库
import matplotlib.pyplot as plt #画二维图像的库
import seaborn as sns #颜色库

#2.无图例，分类型变量，即存在有两种数据，两列X对应一列y的情况
x = np.random.randn(10,2)#10行2列的数据集
y = np.array([0,0,1,1,0,1,0,1,0,0])#类别：假设目前有两种类型的数据分别是0和1

plt.figure(figsize=(8,4))

plt.scatter(x[:,0],
            x[:,1],
            s=50,
            c=y  # 使用数组标签映射颜色分类
           )
plt.savefig('./fig/散点图1.png')
```

<img src=".\img\散点图1.png" alt="散点图1" style="zoom:80%;" />

## 有图例的多类别散点图

有多图例的图，用循环的方式，进行绘制。

```python
import numpy as np #数学处理库
import pandas as pd #用于处理.csv excel html 文本等文件
import matplotlib as mpl #画图像的库
import matplotlib.pyplot as plt #画二维图像的库
import seaborn as sns #颜色库

#3.有图例，分类型变量，即存在有两种数据，两列X对应一列y的情况
x = np.random.randn(10,2)#10行2列的数据集
y = np.array([0,0,1,1,0,1,0,1,0,0])#类别：假设目前有两种类型的数据分别是0和1

plt.figure(figsize=(8,4))

#要想生成两个图例，就要循环，分别循环颜色和标签

colors = ["red","black"]
labels=["Zero","One"]

for i in range(x.shape[1]):
    plt.scatter(x[y==i,0],x[y==i,1],c=colors[i],label=labels[i])

#在标签中存在几种类别，我们就循环几次，一次画一个点
plt.legend()
plt.savefig('./fig/散点图2.png')
```

<img src=".\img\散点图2.png" alt="散点图2" style="zoom:80%;" />

## 随机颜色散点图

```python
datasets=pd.read_csv("./midwest_filter.csv")#由原博主提供的在线数据集直接导入

watch_cat=datasets['category']
#print(watch_cat)#查看原始标签

categories=np.unique(datasets['category'])#去掉重复项
#print(categories)#查看去重后类别
#print(len(categories))#查看有几个类别

#准备颜色
'''colorx=plt.cm.tab10(5.2)#从tab10色带中取出一个颜色

x1=np.random.randn(10)
x2=x1+x1**2-10
plt.scatter(x1,x2,s=50,c=np.array(colorx).reshape(1,-1))

plt.show()'''

#开始绘制复杂散点图
#我们需要循环和类别数目一样的次数，目前有14各类别
#我们用循环的i来生成小数，这样就可以生成不同的颜色
plt.figure(figsize=(16,10))#定义画布

for i in range (len(categories)):
	plt.scatter(datasets.loc[datasets["category"]==categories[i],"area"]
                ,datasets.loc[datasets["category"]==categories[i],"poptotal"]
                ,s=20,c=np.array(plt.cm.tab10(i/len(categories))).reshape(1,-1) #每次生成一个颜色
                ,label=categories[i])

plt.legend()
plt.savefig('./fig/cm2.png')
```

<img src=".\img\cm2.png" alt="cm2" style="zoom:80%;" />