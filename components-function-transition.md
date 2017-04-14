# Transition（渐变/转场）

## 使用渐变

对于已经包含了 Transition 的功能组件，可以在故事脚本中这样使用：

```storyscript
[bg file="background.jpg" pretrans]  // 冻结当前画面并执行命令
[bg file="background.jpg" trans]  // 执行命令并开始渐变动画，默认为 crossfade， 持续时间 1000ms

[bg file="background.jpg" trans method='universal' rule='rule/1.png'] // 使用其他渐变方案
```

目前支持的渐变方案及参数：

### crossfade

交叉淡入淡出

|    名称     |   类型    |    默认值/必须    | 描述
| :-------: | :-----: | :----------: | :--------------
|   duration    | number  |      1000      | 持续时间

### universal

动态遮片

|    名称     |   类型    |    默认值/必须    | 描述
| :-------: | :-----: | :----------: | :--------------
|   rule    | string  |      ''      | 遮片文件路径
|   duration    | number  |      1000      | 持续时间

### shutter

百叶窗

|    名称     |   类型    |    默认值/必须    | 描述
| :-------: | :-----: | :----------: | :--------------
|   direction    | string  |      'left'      | 方向
|   num    | number  |      16      | 窗叶数
|   duration    | number  |      1000      | 持续时间

### ripple

波纹

|    名称     |   类型    |    默认值/必须    | 描述
| :-------: | :-----: | :----------: | :--------------
|   origin    | array<number>  |      [0.5, 0.5]      | 起点
|   speed    | number  |      1      | 速度
|   count    | array<number>  |     [10, 10]     | 波峰数量
|   maxDrift    | number  |      24      | 最大漂移
|   duration    | number  |      1000      | 持续时间


## 为自定义组件添加渐变功能

待续
