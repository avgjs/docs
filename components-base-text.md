# Text

`<Text>`是 AVG.js 的基础组件之一，用于显示一段文字。

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, Text } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Text text="越过长城，走向世界每个角落。\nAcross the Great Wall, we can reach every corner in the world."/>
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](components-props.md)。

此外，还包括：

| 名称 | 类型 | 默认值/必须 | 描述 |
| :--: | :--: | :--: | :-- |
| text | string | '' | 要显示的文本内容，使用 `\n` 换行 |
| style | object | - | 文字的样式，[类型和默认值参考这里](http://pixijs.download/release/docs/PIXI.TextStyle.html) |
