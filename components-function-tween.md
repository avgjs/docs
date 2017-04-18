# Tween

In AVG.js, the tweened animation function is provided as a component.

## Introduction

### Import

```js
import { React, Component, components, core } from 'avg-core';
const { Tween } = components;
```

### Usage in components

```js
<Image src='title/bg.png'>
  <Tween schemes={schemes} ref={tween => this.tween = tween}>
    <Textbutton
      text='Start' style={style} anchor={[0.5, 0.5]} x={400} y={310} key={'title1'}
      onClick={() => this.context.router.push('/story')} 
      onTap={() => this.context.router.push('/story')}
    />
    <Textbutton text='Load' style={style} anchor={[0.5, 0.5]} x={400} y={390} key={'title2'} />
    <Textbutton text='Info' style={style} anchor={[0.5, 0.5]} x={400} y={470} key={'title3'} />
  </Tween>
</Image>
```
Specific steps:

1. Wrap the subcomponent to be tweened with the Tween component
2. Add a unique key to the subcomponent
3. According to key to create the corresponding schemes
    Scheme format is Object, which can be imported externally via JSON or can be created using the util class `Tween.builder()`.
    E.g,

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
  The above created two animation schemes, named `default` and` another`, `another` is an empty scheme.
​  The `default` scheme defines a more complex animation program, including multiple sprites and serial/parallel execution，the details of each command [can be found later in the specific explanation](#Command Details)
4. Pass schemes to Tween component as a property

> Tween components are only valid for direct subcomponents

### Animation Playing

If the `default` scheme exists, it will play automatically after the component is mounted.

To play other animation schemes, you can call the component method:

1. Get the component instance by ref, such as `ref={tween => this.tween = tween}`
2. In proper position, execute `this.tween.runTween('scheme name')`

Complete example:

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
            text='Start' style={style} anchor={[0.5, 0.5]} x={400} y={310} key={'title1'}
            onClick={() => this.context.router.push('/story')} 
            onTap={() => this.context.router.push('/story')}
          />
          <Textbutton text='Load' style={style} anchor={[0.5, 0.5]} x={400} y={390} key={'title2'} />
          <Textbutton text='Info' style={style} anchor={[0.5, 0.5]} x={400} y={470} key={'title3'} />
        </Tween>
      </Image>
    );
  }
}
```

## Command Details

### Properties of subcomponents

As you can see from the above example, we set a lot of properties for each `<Textbutton>`, which is automatically used as the initial value of the animation. In the playing of animation, you can also change them freely.

It is advisable to specify an initial value for all properties that will be used in the animation scheme to avoid the illegal value of `NaN` due to the process of `null`.

### Tween API

#### .runTween(name)

Run a pre-defined animation scheme (passed in the `schemes` property of Tween component).

#### .runScheme(scheme[, name])

Passing a new animation scheme and running it, you can specify a name for it by the second argument `name`.

#### .stopTween(name)

Stop a running animation scheme by name.

### Tween.builder() API

| Parameter      | Description                            |
| -------- | ----------------------------- |
| target   | The component to perform the action, aka the key of the component  |
| params   | parameters of the action, maybe an Object or other type |
| duration | Duration                        |
| easing   | Easing function, refers to [Easing Functions] (#Easing Functions)    |
| repeat   | repeat time, default to 0             |
| yoyo     | repeat animation like yoyo            |

#### .schema(name)

Define a new animation scheme.

#### .sequence(repeat = 0, yoyo = false)

Create a serial execution queue, each action will be executed in order.

#### .parallel(repeat = 0, yoyo = false)

Create a parallel execution queue, each action will be executed at the same time. When the last action is ended, the queue is ended.

#### .end()

End an animation scheme definition or serial/parallel queue.

#### .getSchemes()

Get the defined animation schemes object that can be passed as a property to the Tween component.

#### .moveTo/moveBy(target, { x, y }, duration = 0, easing = linear, repeat = 0, yoyo = false)

Move the node to a absolute coordinate or by a relative offset.

At least one of the two parameters `x, y` must be filled.

#### .fadeTo/fadeBy(target, value, duration = 0, easing = linear, repeat = 0, yoyo = false)

Fade the node's alpha to a absolute value or by a relative value.

#### .rotateTo/rotateBy(target, value, duration = 0, easing = linear, repeat = 0, yoyo = false)

Rotate the node to a absolute value or by a relative value in radians.

#### .scaleTo/scaleBy(target, { x,y }, duration = 0, easing = linear, repeat = 0, yoyo = false)

Scale the node to a absolute value or by a relative value.

#### .shake(target, { offsetX, offsetY }, duration = 0, easing = linear, repeat = 0, yoyo = false)

Shake effect

#### .quake(target, { offsetX, offsetY, speed = 10 }, duration = 0, easing = linear, repeat = 0, yoyo = false)

Quake effect
The difference between shake and quake is that the offset of the vibration is random and offset of quake is used as maximum value.

#### .setProperty(target, { …params })

Set the properties of the node directly, such as `visible`, etc., Except for ` target` and `params`, DO NOT set the following parameters, otherwise it may cause an exception.

#### .callback(target, callback, duration, easing = linear, repeat = 0, yoyo = false)

When the animation is played to that position, a function callback is triggered and the node object specified by `target` is the context.

If it is in a `sequence` or `parallel` which is `repeat > 0`, it will be triggered on each repeat.

callback defination: `(progress, lastProgress, target, finish) => { /* do something... */; finish() }`。

If `duration` is specified greater than 0, you do not need to execute` finish () `manually, otherwise you must execute` finish () `manually.


### Easing Functions

Tween.Easing presets a variety of commonly used easing functions, including Linear, Quadratic, Cubic, Quartic, Quintic, Sinusoidal, Exponential, Circular, Elastic, Back and Bounce. At the same time each type is divided into In, Out and InOut three sub-categories (except Linear Linear, which only has a None type). [The curve for each function can be found here](http://easings.net).

You can use it like `Tween.Easing.Linear.None` or `Tween.Easing.Cubic.In`.

Or you can pass your own easing function:

```js
function myEasing(t) {
  return Math.sin(Math.PI / 2 * t);
}

.moveTo('key', { x: 100 }, 1000, myEasing);
```
