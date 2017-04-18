# BGImage

`<BGImage>`是 AVG.js 的功能组件之一，为[故事脚本（Storyscript）](zh/storyscript.md)提供背景图片显示命令。

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, BGImage } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <BGImage />
      </Surface>
    );
  }
}
```

在故事脚本中使用：

```storyscript
[bg file="bgimage/h01.png"]    //  瞬间切换图片
[bg file="bgimage/h01.png" trans]    // 使用渐变效果
```

> 渐变功能的详细用法参考[Transition](zh/components-function-transition.md)
