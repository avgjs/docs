# Image

`<Image>`是 AVG.js 的基础组件之一，用于显示一个图片。

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, Image } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Image src='assets/h06.png' x={0} y={0}/>
      </Surface>
    );
  }
}
```

可使用全部的[标准属性](components-props.md)。

?> src 指定的资源不仅可以是 jpg png webp 等图片格式，也可以是矢量格式 svg
