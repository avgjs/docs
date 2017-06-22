# 声音

声音插件是 AVG.js 的核心插件之一，提供音频播放功能。

```javascript
import { core, plugins } from 'avg-core';

// run this code before core.render() to install the plugin
core.installPlugin(plugins.Audio);
```

## 在 Javascript 中使用


```javascript
// you can use it wherever you want,
// and more APIs is listed below.
core.plugins.audio.create(0, 'bgm/bgm.ogg', { loop: true });
core.plugins.audio.play(0);
```

### API

#### create(channel: number | string, src: string, options: object)

channel: 通道号或通道名，可以是数字或字符串

src: 相对于 Assets 文件夹的路径

options:

| 名称 | 类型 | 默认值/必须 | 描述 |
| :--: | :--: | :--: | :-- |
| loop | boolean | false | 是否循环播放 |
| preload | boolean | true | 是否自动加载（立即加载或在.play()执行时加载） |
| autoplay | boolean | true | 是否自动播放 |
| mute | boolean | false | 是否静音 |
| rate | number | 1 | 播放速率 |
| autounload | boolean | true | 是否自动卸载音频 |
| exclusive | boolean | true | 唯一性，若为false则允许多个音频使用相同的channel |

#### destroy(channel)

销毁某个通道（停止播放并卸载音频）

#### getByChannel(channel: number | string): Howl

获得某个通道的实例，返回 [Howler](https://github.com/goldfire/howler.js/) 实例

#### play(channel: number | string)

播放某个通道的音频

#### pause(channel: number | string)

暂停/恢复某个通道的音频

#### stop(channel: number | string)

停止某个通道的音频

#### mute(channel: number | string, muted?: boolean)

静音某个通道的音频

#### volume(channel: number | string, vol?: number)

获取/设置某个通道的音量

#### fade(channel: number | string, from: number, to: number, duration: number)

使某个通道的音频音量从某一值渐变到另一值

#### fadeIn(channel: number | string, to: number, duration: number)

使某个通道的音频淡入

#### fadeOut(channel: number | string, duration: number)

使某个通道的音频淡出

#### rate(channel: number | string, rate?: number)

获取/设置某个通道的播放速率

#### seek(channel: number | string, position?: number)

获取/设置某个通道的播放位置

#### loop(channel: number | string, loop?: boolean)

获取/设置某个通道是否循环播放

#### stopAll()

停止全部通道的音频

#### channelExist(channel: number | string): boolean

判断某个通道是否有音频

#### channelVolume(channel): number

获取某个通道的音量

#### channelVolume(channel: number | string, vol: number)

为某个通道设置音量，取值范围 0-1

#### globalVolume(vol?: number): number

获取/设置全局音量，每个通道的最终音量等于全局音量与通道音量的乘积

#### globalMute(muted?: boolean): boolean

获取/设置全局静音状态


## 在故事脚本中使用

可以在故事脚本中这样使用：

```storyscript
[sound bgm src='bgm/bgm.ogg' loop=true]
[sound bgm stop]

// or

[sound channel='bgm' src='bgm/bgm.ogg' loop=true]
[sound channel='bgm' stop]
```

可见，脚本内容由三部分组成：命令名（sound），通道（channel），参数

其中，命令名是固定不变的；  
通道一般为`channel=<number | string>`的格式，但为了简便，我们添加了 `bgm` `se` `voice` 三个语法糖，分别可以代替 `channel='bgm'` `channel='se'` `channel='voice'` 使用。

下面列举全部支持的命令（事实上他们与上面的 APIs 只有很小的区别）：

```storyscript
// the value after `=` is the default value

[sound channel= src= volume=1 loop=false preload=true autoplay=true mute=false rate=1 autounload=true exclusive=true]

[sound channel= play/pause/stop/destroy]
[sound channel= mute/rate/volume/seek/loop value=]
[sound channel= fade from= to= duration=]
[sound channel= fadein to= duration=]
[sound channel= fadeout duration=]

// global
[sound mute/volume value=]
[sound stopall]
```

> **为什么不包含「获取」性质的命令？**  
> 这与设计思路有关，我们认为故事脚本只应承担简单的工作，而「获取」命令及之后的处理无疑是将更复杂的逻辑引入了故事脚本，这是我们不希望看到的。如果需要获取一些值并进行处理，你应当使用 Javascript 进行，并将其暴露为新的命令供调用。

