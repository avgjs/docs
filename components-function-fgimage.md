# FGImage

`<FGImage>`是 AVG.js 的功能组件之一，为[故事脚本（Storyscript）](storyscript.md)提供立绘图片显示命令。

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, FGImage } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <FGImage width={1280} height={720}/>
      </Surface>
    );
  }
}
```

在故事脚本中使用：

```storyscript
[fg file="sakura_smile.png"]    //  瞬间切换图片，默认显示在中间
[fg left/right/center file="sakura_smile.png"]    // 瞬间切换图片，显示在左侧/右侧/中间
[fg left file="sakura_smile.png" trans]    // 渐变切换图片，显示在左侧

[fg clear left/right/center]    // 立刻清除左侧/右侧/中间的立绘
[fg clear left right trans]    // 渐变地同时清除左侧和右侧的立绘，left/right/center 可以任意组合
```

> 渐变功能的详细用法参考[Transition](components-function-transition.md)

!> 目前必须使用 `width` 和 `height` 指定画面区域，保持与画面尺寸相同即可。后续的版本中该参数将不再需要手工填写。