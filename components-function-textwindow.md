# Textwindow

`<Textwindow>`是 AVG.js 的功能组件之一，为[故事脚本（Storyscript）](storyscript.md)提供文字打印相关命令。

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, Textwindow } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Textwindow/>
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](components-props.md)。

此外，还包括：

|    名称     |   类型    |    默认值/必须    | 描述
| :-------: | :-----: | :----------: | :--------------
|   text    | string  |      ''      | 要显示的文本内容
|   color   | number  |   0xffffff   | 文字颜色
|   size    | number  |      24      | 文字大小
|   speed   | number  |      24      | 文字打印速度（字/秒）
|   font    | string  | 'sans-serif' | 默认字体
| textRect  | number  |     null     | 文字显示区域，默认不限制(?)
|  bgFile   | string  |      ''      | 背景图片文件
| xintercal | number  |      0       | 字间距
| yintercal | number  |      3       | 行间距
|   bold    | boolean |    false     | 粗体
|  italic   | boolean |    false     | 斜体
| strike | boolean | false | 删除线 |
| under | boolean | false | 下划线 |
| shadow | boolean | false | 文字投影 |
| shadowcolor | number | 0x0 | 文字投影颜色 |
| stroke | boolean | false | 文字描边 |
| strokecolor | number | 0x0 | 文字描边颜色 |

在故事脚本中使用：

```storyscript
//  修改文本框属性（props）
[text set ...]   
//  显示/隐藏文本框，可使用 trans 设置渐变效果
[text show trans]
[text hide]
//  清空文本框文字内容
[text clear]
这是一行文字，后面的指令是等待换页[p]
这是又一行文字[r]
它直接换行了[p]
这行文字只等待点击[l]再点击才会换页[p]
```

> 渐变功能的详细用法参考[Transition](components-function-transition.md)
