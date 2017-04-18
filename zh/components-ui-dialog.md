# Dialog

`<Dialog>`是 AVG.js 的界面组件之一，用于显示一个空对话框。

```javascript
import { React, Component, core, components, ui } from 'avg-core';
const { Surface, Image } = components;
const { Dialog } = ui;

class Game extends Component {
  handleFullscreenChange(value) {
    alert(value);
  }
  render() {
    return (
      <Surface>
        <Dialog modal={true}>
          <Image src='img.png' />
        </Dialog>
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](zh/components-props.md)。

此外，还包括：

| 名称 | 类型 | 默认值/必须 | 描述 |
| :--: | :--: | :--: | :-- |
| clip | boolean | false | 是否剪裁 |
| modal | boolean | false | 是否为模态 |
| dragable | boolean | false | 是否可拖动 |
| dragArea | array | [0, 0, Infinity, Infinity] | 响应拖动的对话框区域 |
