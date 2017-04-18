# Checkbox

`<Checkbox>`是 AVG.js 的界面组件之一，用于显示一个单选框或复选框。

```javascript
import { React, Component, core, components, ui } from 'avg-core';
const { Surface } = components;
const { Checkbox } = ui;

class Game extends Component {
  handleFullscreenChange(value) {
    alert(value);
  }
  render() {
    return (
      <Surface>
        <Checkbox src='option/screen_full.png' position={[700, 250]} name={'fullscreen'} value={true} defaultChecked={false} onChange={this.handleFullscreenChange.bind(this)}/>
        <Checkbox src='option/screen_window.png' position={[900, 250]} name={'fullscreen'} value={false} defaultChecked={true} />
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](zh/components-props.md)。

此外，还包括：

| 名称 | 类型 | 默认值/必须 | 描述 |
| :--: | :--: | :--: | :-- |
| defaultChecked | boolean | false | 默认是否选中 |
| value | any | undefined | 回调函数中的值 |
| onChange | function | - | 选中状态发生改变时触发的回调 |
| name | string | undefined | 所属的选框组名，若不设置则为多选框，设置后将于相同名称的其他单选框联动 |

?> src 指定的资源不仅可以是 jpg png webp 等图片格式，也可以是矢量格式 svg

!> 当指定了 name 时，只需对相同 name 的单选框中的其中一个设置 onChange 监听即可
