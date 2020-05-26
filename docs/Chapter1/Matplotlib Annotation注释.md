# Matplotlib：Annotation注释

#### 添加注释和箭头 `plt.annotate()`

```python
添加注释  annotate()
    参数 ：(1) s  : 注释文本
          (2) xy : 箭头坐标
          (3) xytext: 文本坐标
          (4) 字体设置等参数
          (5) 设置箭头，arrowprops 
                arrowprops : 是一个dict (字典)
           第一种方式：{'width':宽度,'headwidth':箭头宽,facecolor,'headlength':箭头长,
                         'shrink':两端收缩总长度分数}   
        		  facecolor：箭头颜色
                  shrink:箭头的长度（两坐标距离的比例，0~1）
                   width:箭头的宽度
                例如：arrowprops={'width':5,'headwidth':10,'headlength':10,'shrink':0.1}
           第二种方式：'arrowstyle':样式 
                例如：
              有关arrowstyle的样式：'-' 、'->'、'<-'、'-['、'|-|'、'-|>'、'<|-'、'<->'
                                   'fancy','simple','wedge'  

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190930094144180.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0hIRzIwMTcxMjI2,size_16,color_FFFFFF,t_70)

```python
x = np.random.randint(0,30,size=10)
x[5] = 30  # 把索引为5的位置改为30
plt.figure(figsize=(12,6))
plt.plot(x)
plt.ylim([-2,35]) # 设置y轴的刻度
plt.annotate(s='this point is important',xy=(5,30),xytext=(6,31),fontsize=16,
             arrowprops={'arrowstyle':'->'})
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200513151310.jpg"/>

