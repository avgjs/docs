# Button

`<Button>`是 AVG.js 的界面组件之一，用于显示一个按钮。

```javascript
import { React, Component, core, components, ui } from 'avg-core';
const { Surface } = components;
const { Button } = ui;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Button src="button.png" onClick={() => alert('clicked!')}>
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](zh/components-props.md)。

此外，还包括：

| 名称 | 类型 | 默认值/必须 | 描述 |
| :--: | :--: | :--: | :-- |
| lite | boolean | true | 素材的切分方式，简易切分指将图片分成2部分（通常/移过，移动端为通常/点击），否则分为三部分（通常/移过/点击） |

?> src 指定的资源不仅可以是 jpg png webp 等图片格式，也可以是矢量格式 svg
