# PythonStudy
# matplotlib绘图
#### 个人理解：matplotlib最先产生一个figure（画布）对象，以后所有的操作都是在figure上面进行的。有了figure之后就可以输出axes（坐标轴），可以有一个或者多个，数据就在axes上面绘制。然后可以设置axes的label，title等属性。

1. 导入基本库
```
import matplotlib.pyplot as plt
import numpy as np
```
简单的例子
```
fig, ax = plt.subplots() # 创建一个包含一个axes的figure
ax.plot([1, 2, 3, 4], [1, 4, 2, 3]) # 在axes上面绘图
```
实际上如果只需要一个axes，可以直接用下面方式作图
`plt.plot([1, 2, 3, 4], [1, 4, 2, 3])`. 与上面效果一样。

```
fig = plt.figure() # an empty figure with no Axes
fig, ax = plt.subplots() # a figure with a single Axes
fig, axs = plt.subplots(2, 2) # 创建2*2是axes的figure，以后做图就在axs上面操作，其中axs是一个元组，axes[0,0]则是在第一个位置绘图
```
注意一个**figure**可以包含多个**axes**，比如上面代码就包含4个axes。一个**axes**包含2到3个**axis**（2D和3D图像）， **axes**下面有方法`set_xlim([])`控制坐标轴范围，`set_title`， `set_xlabel`等来显示坐标轴标签与图名称。
```
x = np.linspace(0, 2, 100)
fig, ax = plt.subplots() 
ax.plot(x, x, label='linear') # Plot some data on the axes.
ax.plot(x, x**2, label='quadratic') # Plot more data on the axes...
ax.set_xlabel('x label') 
ax.set_ylabel('y label') # 添加xy标签
ax.set_title("Simple Plot") # 添加标题
ax.legend(loc='best') # 添加图例
```

#### matplotlib.pyplot is a collection of command style functions that make matplotlib work like MATLAB. 例如
```
plt.plot([1, 2, 3, 4], [1, 4, 9, 16], 'ro')
plt.axis([0, 6, 0, 20])
plt.show()
```
- 对于每一对`x-y`,都有第三个可选参数来控制线的形状与颜色，类似 `matlab`风格。
```
t = np.arange(0., 5., 0.2)
plt.plot(t, t, 'r--', t, t**2, 'bs', t, t**3, 'g^')
plt.show()
```
- 可以用字典键值对形式绘图
```
data = {'a': np.arange(50),
'c': np.random.randint(0, 50, 50),
'd': np.random.randn(50)}
data['b'] = data['a'] +
data['d'] = np.abs(data['d']) * 100
plt.scatter('a', 'b', c='c', s='d', data=data)#注意scatter函数用法
plt.xlabel('entry a')
plt.ylabel('entry b')
plt.show()
```
- 横坐标可以是字符串变量
```
values = [1, 10, 100]
plt.figure(figsize=(9, 3))
plt.bar(names, values)
plt.show()
```
#### Line对象的设置(linestyle,linewidth,...)
- 利用关键字参数： `plt.plot(x, y, linewidth=2.0)`
-  利用 `setp()`  
```
x = np.array([1,2,3,4,5])
y = x**2
y2 = x**3
line1,line2 = plt.plot(x,y,x,y2)
plt.setp(line1,'color','r')
plt.setp(line2,'color','g','linewidth',2.0)
plt.show()
```

####  plt绘图风格（`plt.style.available`）
- `plt.style.use('fivethirtyeight')`



#### `imshow()`函数
- `plt.imshow(lum_img, cmap="hot",clim=(0,0.5))`
- 或者 `imgplot = plt.imshow(lum_img)`
`  imgplot.set_cmap('nipy_spectral')`



