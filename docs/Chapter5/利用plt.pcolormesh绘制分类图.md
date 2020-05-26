# 利用plt.pcolormesh绘制分类图


用pcolormesh()能画的, 用scatter()也能画, 但是经过测试, 发现用scatter()画的速度比pcolormesh()要慢不少 - -
```
plt.pcolormesh(X,Y,Z,cmap=cm)
```

`X，Y`：指的是二维网格面每一个点的横纵坐标
`Z:(X,Y)` :坐标处的颜色值
`cmap`:着色方案



`pcolormesh` 的作用是: 用不规则的矩形网格创建伪彩色图。

```python
'''
多元分类：逻辑回归分类器 并绘制pcolormesh伪彩图
sklearn.linear_model.LogisticRegression(
        solver='liblinear',
        C=正则强度)
'''
# pcolormesh(x, y, c=d, cmap='jet') cmap:渐变色映射
 
plt.pcolormesh(...):
 
    a = np.array([1, 2, 3])
    b = np.array([-1, -2, -3, -4])
 
    a.shape, b.shape
    Out[55]: ((3,), (4,))
 
    c = np.meshgrid(a, b); 
    # c       					   # c is a 'list', not 'numpy.array'
    Out[57]:                       # c[0]：沿行(axis=0)广播, 每一行元素跟上一行相同
    [array([[1, 2, 3],             # c[1]：沿列(axis=1)广播, 每一列元素跟上一列相同
            [1, 2, 3],             # (c[0],c[1])组成的坐标点(x,y)将覆盖并形成(1<=x<=3,-4<=y<=-1)区间组成的2*3的矩形
            [1, 2, 3],
            [1, 2, 3]]), 
    array([[-1, -1, -1],
            [-2, -2, -2],
            [-3, -3, -3],
            [-4, -4, -4]])]
 
    c[0].shape, c[1].shape
    Out[61]: ((4, 3), (4, 3))
 
    plt.pcolormesh(c[0], c[1], c=...)             
# c[0]表示点横坐标，c[1]表示纵坐标
# 对样本(c[0], c[1])周围（包括样本所在坐标）的四个坐标点进行着色，C代表着色方案
        # 点(c[0], c[1])所有坐标点如下：
        '''
            ^
            |---1------2------3---->
            |
           -1  (1,-1) (2,-1) (3,-1)
            |
           -2  (1,-2) (2,-2) (3,-2)
            |
           -3  (1,-3) (2,-3) (3,-3)
            |
           -4  (1,-4) (2,-4) (3,-4)
            |
            '''
```

```python
'''
多元分类：逻辑回归分类器
sklearn.linear_model.LogisticRegression(
        solver='liblinear',
        C=正则强度)
'''
 
import numpy as np
import matplotlib.pyplot as plt
import sklearn.linear_model as lm
 
# train_set
x = np.array([
        [4, 7],
        [3.5, 8],
        [3.1, 6.2],
        [0.5, 1],
        [1, 2],
        [1.2, 1.9],
        [4, 2],
        [5.7, 1.5],
        [5.4, 2.2]])                                             # 散点[x,y]
y = np.array([0, 0, 0, 1, 1, 1, 2, 2, 2])                        # 多元分类 3类
 
# 逻辑回归分类器
model = lm.LogisticRegression(solver='liblinear', C=50)          # C
model.fit(x, y)
 
plt.figure('Logistic Classification', facecolor='lightgray')
plt.title('Logistic Classification', fontsize=14)
plt.xlabel('x', fontsize=14)
plt.ylabel('y', fontsize=14)
plt.tick_params(labelsize=10)
 
'''
pcolormesh参数设置：
'''
l, r, h = x[:, 0].min() - 1, x[:, 0].max() + 1, 0.005            # 左边界，右边界，水平方向点间距
b, t, v = x[:, 1].min() - 1, x[:, 1].max() + 1, 0.005            # 下边界，上边界，垂直方向点间距
 
#print(np.arange(l, r, h).shape, np.arange(b, t, v).shape)       # (1440,) (1800,),shape不同，不能直接作为输入,转为
grid_x = np.meshgrid(np.arange(l, r, h), np.arange(b, t, v))     # (m-array,n-array)--> list(mat(m,n), mat(m,n))
 
print(grid_x[0])                                                 # x[i, j]  (1800, 1440) <class 'numpy.ndarray'> 
print(grid_x[1])                                                 # y[i, j]  (1800, 1440) <class 'numpy.ndarray'> 
#print(grid_x[1].shape)                                          # (1800, 1440) <class 'numpy.ndarray'>
flat_x = np.c_[grid_x[0].ravel(), grid_x[1].ravel()]             # 保证输入散点的坐标点横纵坐标个数一样
flat_y = model.predict(flat_x)                                   # 输入栅格点阵坐标，模型预测输出的分类
grid_y = flat_y.reshape(grid_x[0].shape)                         # 分类标签：用做pcolormesh栅格着色的依据
print(grid_y)
#[[1 1 1 ... 2 2 2]             # 0, 1, 2 分别代表三种不同颜色
# [1 1 1 ... 2 2 2]
# [1 1 1 ... 2 2 2]
# ...
# [0 0 0 ... 0 0 0]
# [0 0 0 ... 0 0 0]
# [0 0 0 ... 0 0 0]]
 
 
# pcolormesh: 伪彩图 pcolormesh(X, Y, C) 
# X,Y均为2-D array,如果为1-D 会自动广播，X和Y构成网格点阵
# X,Y对应位置元素x[i,j]和y[i,j]组成一个坐标点(x[i,j],y[i,j])，对样本周围（包括样本所在坐标）的四
#个坐标点进行着色，C代表着色方案
plt.pcolormesh(grid_x[0], grid_x[1], grid_y, cmap='gray')       # gray_r 与gray的色带相反
 
plt.scatter(x[:, 0], x[:, 1], c=y, cmap='brg', s=60)            # 颜色映射
```

<img src="https://raw.githubusercontent.com/HG1227/image/master/img_tuchuang/20200508111334.png"/>





参考：

<a href="https://blog.csdn.net/qq_39355550/article/details/82735366?utm_medium=distribute.pc_relevant.none-task-blog-baidujs-1" blank="">plt.pcolormesh绘制分类图</a> 

<a href="https://blog.csdn.net/zsdust/article/details/79726118?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2" blank="">利用plt.pcolormesh绘制分类图</a> 