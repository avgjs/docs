# BGImage

`<BGImage>` is one of functional components of AVG.js, provides background image display command for [Storyscript](storyscript.md).

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

Usage in Storyscript：

```storyscript
[bg file="bgimage/h01.png"]    //  Instantly change the image
[bg file="bgimage/h01.png" trans]    // Gradient to change the image
```

> Detailed usage of the fade function refers to [Transition](components-function-transition.md)
