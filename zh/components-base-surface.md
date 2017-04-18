# Surface

`<Surface>` 组件是 AVG.js 引入 Web 页面时的最底层组件，它实质上是用 React 封装的 `<canvas>` 标签。

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
      </Surface>
    );
  }
}
render(<Game />, document.getElementById('app'));

(async () => {
  await core.init(1280, 720, {
    fitWindow: true,
    assetsPath: 'assets',
    tryWebp: false
  });

  core.render(<Game />, document.getElementById('app'));

  core.start();
})();
```

上面的代码展示了 AVG.js 的最基本使用方法（画面无内容，黑屏）

在`<Surface>`的内部，可以自由添加其他的组件来构建游戏系统。
