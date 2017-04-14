# Layer

`<Layer>`是 AVG.js 的基础组件之一，用于表示一个固定宽高的「层」。

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, Layer, Image } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Layer width={400} height={600}>
          <Image file='assets/h06.png' />
        </Layer>
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](components-props.md)。

此外，还包括：

| 名称 | 类型 | 默认值/必须 | 描述 |
| :--: | :--: | :--: | :-- |
| width | number | surface width | 层的宽度，默认为画面宽度 |
| height | number | surface width | 层的高度，默认为画面高度 |
| fillColor | number | 0x0 | 背景颜色 |
| fillAlpha | number | 0 | 背景透明度 |
| clip | boolean | false | 是否根据高宽剪裁掉超出的内容 |

!> clip 设置成 true 后会降低界面刷新的性能，如无必要请保持为 false

