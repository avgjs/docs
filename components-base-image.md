# Image

`<Image>` is one of the basic components of AVG.js, used to display a image.

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

All [standard properties](components-props.md) can be used.

?> The resource specified by `src` can not only be jpg/png/webp, but also be svg.
