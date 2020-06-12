# Matplotlib：线型、标记

﻿在Python中用matplotlib画图的时候，为了区分曲线的类型，给曲线上面加一些标识或者颜色。以下是颜色和标识的汇总。

##### 颜色（`color`简写为 `c`）：

- 蓝色： 'b' (blue)
- 绿色： 'g' (green)
- 红色： 'r' (red)
- 蓝绿色(墨绿色)： 'c' (cyan)
- 红紫色(洋红)： 'm' (magenta)
- 黄色： 'y' (yellow)
- 黑色： 'k' (black)
- 白色： 'w' (white)
- 灰度表示： e.g. 0.75 ([0,1]内任意浮点数)
- RGB表示法： e.g. '#2F4F4F' 或 (0.18, 0.31, 0.31)
- 任意合法的html中的颜色表示： e.g. 'red', 'darkslategray'

##### 线型（`linestyle` 简写为 `ls`）：

- 实线： '-'
- 虚线： '--'
- 虚点线： '-.'
- 点线： ':'
- 点： '.' 

##### 点型（标记marker）：

- 像素： ','
- 圆形： 'o'
- 上三角： '^'
- 下三角： 'v'
- 左三角： '<'
- 右三角： '>'
- 方形： 's'
- 加号： '+' 
- 叉形： 'x'
- 棱形： 'D'
- 细棱形： 'd'
- 三脚架朝下： '1'（就是丫）
- 三脚架朝上： '2'
- 三脚架朝左： '3'
- 三脚架朝右： '4'
- 六角形： 'h'
- 旋转六角形： 'H'
- 五角形： 'p'
- 垂直线： '|'
- 水平线： '_'
- gnuplot 中的steps： 'steps' （只能用于kwarg中）

##### 标记大小（`markersize `简写为` ms`）： 

- markersize： 实数 

##### 标记边缘宽度（`markeredgewidth `简写为 `mew`）：

- markeredgewidth：实数

##### 标记边缘颜色（markeredgecolor `简写为 `mec`）：

- markeredgecolor：颜色选项中的任意值

##### 标记表面颜色（markerfacecolor 简写为 mfc）：

markerfacecolor：颜色选项中的任意值

##### 透明度（alpha）：

- alpha： [0,1]之间的浮点数

##### 线宽（linewidth）：

- linewidth： 实数

