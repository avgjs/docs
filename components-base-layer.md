# Layer

`<Layer>`is one of the basic components of AVG.js, used to represent a *layer* which has width and height.

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

All [standard properties](components-props.md) can be used.

In addition, it also includes:

| Name | Type | Default/Needed | Description |
| :--: | :--: | :--: | :-- |
| width | number | screen width | width of layer, default to screen width |
| height | number | screen height | height of layer, default to screen height |
| fillColor | number | 0x0 | background color |
| fillAlpha | number | 0 | background alpha |
| clip | boolean | false | whether cut out the content beyond width/height |

!> Rendering performance will drop when clip is set to true, so keep it false if unnecessary.

