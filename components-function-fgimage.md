# FGImage

`<FGImage>`is one of functional components of AVG.js, provides character image display command for [Storyscript](storyscript.md).

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

Usage in Storyscript：

```storyscript
[fg file="sakura_smile.png"]    //  Instantly change the image, display on the center of the screen by default
[fg left/right/center file="sakura_smile.png"]    // Instantly change the image, display on the left/right/center
[fg left file="sakura_smile.png" trans]    // Gradient to change the image, display on the left

[fg clear left/right/center]    // Instantly clear the left/right/center image
[fg clear left right trans]    // Gradient to clear the images on the left and right at the same time
```

> Detailed usage of the fade function refers to [Transition](components-function-transition.md)

!> You must now use `width` and` height` to specify the screen area, usually keep it the same with the screen size. In next version, these properties will no longer be required.
