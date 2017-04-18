# Tween（补间动画）

在 AVG.js 中，补间动画功能是以组件方式提供的。

## 介绍

### 引入

```js
import { React, Component, components, core } from 'avg-core';
const { Tween } = components;
```

### 在组件中使用：

```js
<Image src='title/bg.png'>
  <Tween schemes={schemes} ref={tween => this.tween = tween}>
    <Textbutton
      text='开始游戏' style={style} anchor={[0.5, 0.5]} x={400} y={310} key={'title1'}
      onClick={() => this.context.router.push('/story')} 
      onTap={() => this.context.router.push('/story')}
    />
    <Textbutton text='读取存档' style={style} anchor={[0.5, 0.5]} x={400} y={390} key={'title2'} />
    <Textbutton text='其他信息' style={style} anchor={[0.5, 0.5]} x={400} y={470} key={'title3'} />
  </Tween>
</Image>
```

具体步骤：

1. 用 Tween 组件包裹要进行补间动作的子组件*
2. 为子组件添加唯一的 key
3. 根据 key 创建对应的 schemes，每个 scheme 即一个动画方案
   Scheme 格式为 Object，可以通过 JSON 从外部引入，也可以使用工具类 `Tween.builder()` 创建。  
   例如，

  ```js
  const schemes = Tween.builder()
    .scheme('default')
      .sequence(1, true)
        .moveTo('title1', { y: 100 }, 2000)
        .moveTo('title2', { x: 100, y: 180 }, 2000)
        .parallel(1, true)
          .callback('title1', () => console.log('emit!'))
          .moveTo('title1', { x: 600, y: 100 }, 3000)
          .moveTo('title2', { x: 600, y: 180 }, 2000, Tween.Easing.Quadratic.InOut, 1, true)
        .end()
        .moveTo('title2', { x: 600, y: 480 }, 2000, Tween.Easing.Quadratic.In, 2, false)
      .end()
    .end()
    .scheme('another')
    .end()
    .getSchemes();
  ```
  以上创建了两个动画方案，分别名为 `default` 和 `another`，其中`another`方案为空。
​  在 `default` 方案中，定义了较为复杂的动画方案，包含多个精灵对象和串行、并行两种执行方式，每个命令的详细方案[可在后面找到具体的解释](#命令详解)
4. 将 schemes 作为属性传递给 Tween 组件

**注：补间组件只对直接子组件有效*

### 动画播放

若 `default` 动画方案存在，那么它会在组件载入后自动播放。

若要播放其他动画方案，可通过调用组件方法获得：

1. 通过 ref 获得组件实例，如 `ref={tween => this.tween = tween}`
2. 在合适的位置执行 `this.tween.runTween('scheme name')`

完整范例：

```js
export default class Title extends Component {
  static contextTypes = {
    router: React.PropTypes.any,
  }
  render() {

    const schemes = Tween.builder()
      .scheme('default')
        .sequence(1, true)
          .moveTo('title1', { y: 100 }, 2000)
          .moveTo('title2', { x: 100, y: 180 }, 2000)
          .parallel(1, true)
            .callback('title1', () => console.log('emit!'))
            .moveTo('title1', { x: 600, y: 100 }, 3000)
            .moveTo('title2', { x: 600, y: 180 }, 2000, Tween.Easing.Quadratic.InOut, 1, true)
          .end()
          .moveTo('title2', { x: 600, y: 480 }, 2000, Tween.Easing.Quadratic.In, 2, false)
        .end()
      .end()
      .scheme('another')
      .end()
      .getSchemes();

    return (
      <Image src='title/bg.png'>
        <Tween schemes={schemes} ref={tween => this.tween = tween}>
          <Textbutton
            text='开始游戏' style={style} anchor={[0.5, 0.5]} x={400} y={310} key={'title1'}
            onClick={() => this.context.router.push('/story')} 
            onTap={() => this.context.router.push('/story')}
          />
          <Textbutton text='读取存档' style={style} anchor={[0.5, 0.5]} x={400} y={390} key={'title2'} />
          <Textbutton text='其他信息' style={style} anchor={[0.5, 0.5]} x={400} y={470} key={'title3'} />
        </Tween>
      </Image>
    );
  }
}
```

## 命令详解

### 关于 Tween 的子组件的属性（props）

从上面的示例可以看到，我们为每个 `<Textbutton>` 都传递了很多属性值，这些属性将自动作为动画的初始值使用。在动画播放的过程中，你也可以自由更改他们的值。

建议为所有将在动画方案中使用的属性指定初始值，以避免部分数值因默认为 `null` 而使得动画执行时计算出非法的 `NaN` 。

### Tween API

#### .runTween(name)

运行定义好的动画方案，该方案必须已经在 Tween 组件的 schemes 属性中定义。

#### .runScheme(scheme[, name])

传递一个新的动画方案并运行，可以通过第二个参数 `name` 为其指定一个名字。

#### .stopTween(name)

停止对应名称的动画方案运行。

### Tween.builder() API

参数解释：

| 参数名      | 解释                            |
| -------- | ----------------------------- |
| target   | 动画目标，即要执行该动画的组件 key           |
| params   | 动画参数，依不同命令不同，可以是 Object 也可以是值 |
| duration | 动画持续时间                        |
| easing   | 渐变函数，参考[渐变函数定义](#渐变函数定义)      |
| repeat   | 重复播放动画次数，0 为不重复               |
| yoyo     | 是否以往复方式播放动画                   |

#### .schema(name)

定义一个新的动画方案。

#### .sequence(repeat = 0, yoyo = false)

创建一个串行执行队列，内部的每个动画指令都将按顺序执行。

#### .parallel(repeat = 0, yoyo = false)

创建一个并行执行队列，内部的每个动画指令都将同时执行，待最后一个动画执行后结束并行队列。

#### .end()

结束一个动画方案定义或串行/并行队列。

#### .getSchemes()

获得定义的动画方案数据，可作为 prop 传递给 Tween 组件。

#### .moveTo/moveBy(target, { x, y }, duration = 0, easing = linear, repeat = 0, yoyo = false)

将节点移动到绝对坐标（To）或移动一段相对偏移（By）。

x, y 两参数至少填写一个

#### .fadeTo/fadeBy(target, value, duration = 0, easing = linear, repeat = 0, yoyo = false)

将节点透明度渐变到绝对值（To）或渐变一段相对值（By）。

#### .rotateTo/rotateBy(target, value, duration = 0, easing = linear, repeat = 0, yoyo = false)

将节点旋转到绝对值（To）或旋转一段相对值（By），单位为弧度。

#### .scaleTo/scaleBy(target, { x,y }, duration = 0, easing = linear, repeat = 0, yoyo = false)

将节点缩放到绝对比例（To）或缩放一段相对比例（By）。

#### .shake(target, { offsetX, offsetY }, duration = 0, easing = linear, repeat = 0, yoyo = false)

摇晃效果

#### .quake(target, { offsetX, offsetY, speed = 10 }, duration = 0, easing = linear, repeat = 0, yoyo = false)

震动效果，与摇晃的区别在于震动的偏移是随机的，参数中指定的是最大偏移量。

speed 参数表示每秒震动的次数

#### .setProperty(target, { …params })

设置节点的属性，如 `visible` 等，除 `target` 和 `params` 两参数外，请勿设置后面的参数，否则可能会引起异常。

#### .callback(target, callback, duration, easing = linear, repeat = 0, yoyo = false)

当动画播放到该位置时触发一个函数回调，以 `target` 指定的节点对象为上下文。

若其属于一个 `repeat > 0` 的 `sequence` 或 `parallel`，则在每次重复时都会触发。

callback 格式：`(progress, lastProgress, target, finish) => { /* do something... */; finish() }`。

若指定了大于 0 的 `duration`，则无需手动执行 `finish()`，否则必须手动执行 `finish()`。


### 渐变函数定义

在 Tween.Easing 预置了各种常用的渐变函数，包括 Linear, Quadratic, Cubic, Quartic, Quintic, Sinusoidal, Exponential, Circular, Elastic, Back 和 Bounce 等类型，同时每个类型又分为 In, Out 和 InOut 三种子分类（线性的 Linear 除外，只要 None 一种类型）。[每种函数的动作曲线可以参考这里](http://easings.net/zh-cn)

你可以使用诸如 `Tween.Easing.Linear.None` 或 `Tween.Easing.Cubic.In` 方式使用。

或者你可以传递你自己定义的渐变函数，例如

```js
function myEasing(t) {
  return Math.sin(Math.PI / 2 * t);
}

.moveTo('key', { x: 100 }, 1000, myEasing);
```


