# Layout

`<Layout>`是 AVG.js 的界面组件之一，提供简单的水平/垂直布局功能。

```javascript
import { React, Component, core, components, ui } from 'avg-core';
const { Surface, Image } = components;
const { Layout } = ui;

class Game extends Component {
  handleFullscreenChange(value) {
    alert(value);
  }
  render() {
    return (
      <Surface>
        <Layout modal={true}>
          <Image src='img.png' key={1}/>
          <Image src='img.png' key={2}/>
          <Image src='img.png' key={3}/>
          <Image src='img.png' key={4}/>
        </Layout>
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](components-props.md)。

此外，还包括：

| 名称 | 类型 | 默认值/必须 | 描述 |
| :--: | :--: | :--: | :-- |
| clip | boolean | false | 是否剪裁 |
| padding | array<number> | [0, 0, 0, 0] | 内边距 |
| direction | string | 'vertical' | 排列方向，可选：vertical/horizental |
| baseline | number | 0 | 基线对齐位置，取值0-1，指“每个子组件的x位置对齐为一线” |
| interval | number | 0 | 每个子组件的间隔 |
| maxWidth | number | Infinity | 最大宽度 |
| maxHeight | number | Infinity | 最大高度 |
| overflowX | string | 'scroll' | 横向溢出时的处理方式，可选：scroll/hidden |
| overflowY | string | 'scroll' | 纵向溢出时的处理方式，可选：scroll/hidden |
| scrollerOffsetX | number | 0 | 滚动条位置X偏移 |
| scrollerOffsetY | number | 0 | 滚动条位置Y偏移 |
| onScroll | function | - | 滚动发生时的回调 |
| vertical | number | - | 垂直滚动条位置 |
| horizental | number | - | 水平滚动条位置 |
| scrollStyle | object | - | 滚动条样式 |

!> vertical/horizental 必须与 onScroll 配合使用，即受控组件

> scrollStyle 示例
```json
{
  backgroundColor: 0x777777,
  backgroundAlpha: 0.5,
  backgroundWidth: 18,
  buttonColor: 0x777777,
  buttonAlpha: 0.7,
  buttonWidth: 14,
}
```
