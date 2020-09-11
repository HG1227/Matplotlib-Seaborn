# matplotlib.cm选择颜色映射

`matplotlib.cm.cmap(float)`   

输入0-1 的浮点数，从 cmap中随机生成一个颜色

返回值为元组：

```python
plt.cm.tab10(5.2)
#(0.09019607843137255, 0.7450980392156863, 0.8117647058823529, 1.0)
#R,G,B,alpha
```

当所绘制只有一个 item  的时候需要将其转换成二维数组

```python
colorx=plt.cm.tab10(5.2)#从tab10色带中取出一个颜色

x1=np.random.randn(10)
x2=x1+x1**2-10
plt.scatter(x1,x2,s=50,c=np.array(colorx).reshape(1,-1))
```

<img src=".\img\cm.png" alt="cm" style="zoom:80%;" />



cmap : 可以连续的或者分段的颜色库。

渐变色：

<img src=".\img\image-20200904091120962.png" alt="image-20200904091120962" style="zoom:80%;" />

连续色：

<img src=".\img\image-20200904091215686.png" alt="image-20200904091215686" style="zoom:80%;" />



<img src=".\img\image-20200904091246023.png" alt="image-20200904091246023" style="zoom:80%;" />

```python
datasets=pd.read_csv("./midwest_filter.csv")#由原博主提供的在线数据集直接导入
#查看数据
watch_data1=datasets.head()
#print(watch_data1)
watch_data2=datasets.columns
#print(watch_data2)
#准备标签
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
                ,s=20 #点的大小
                ,c=np.array(plt.cm.tab10(i/len(categories))).reshape(1,-1) #每次生成一个颜色
                ,label=categories[i])

plt.legend()
plt.show()

```

![cm2](F:\GithubWorkspace\GBooks\matplotlib\Chapter1\img\cm2.png)

参考：https://www.osgeo.cn/matplotlib/tutorials/colors/colormaps.html