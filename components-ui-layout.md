# Layout

`<Layout>` is one of the interface components of AVG.js, which provides simple horizental/vertical layout.

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

All [standard properties](components-props.md) can be used.

In addition, it also includes:

| Name | Type | Default/Needed | Description |
| :--: | :--: | :--: | :-- |
| clip | boolean | false | whether cut out the content beyond layer |
| padding | array<number> | [0, 0, 0, 0] | - |
| direction | string | 'vertical' | arrange direction, value is `vertical` or `horizental` |
| baseline | number | 0 | baseline alignment position, 0~1, means *the <baseline> position of each subcomponent is aligned as a line* |
| interval | number | 0 | the interval between subcomponents |
| maxWidth | number | Infinity | - |
| maxHeight | number | Infinity | - |
| overflowX | string | 'scroll' | `scroll` or `hidden` |
| overflowY | string | 'scroll' | `scroll` or `hidden` |
| scrollerOffsetX | number | 0 | offset x of scroller |
| scrollerOffsetY | number | 0 | offset y of scroller |
| onScroll | function | - | callback when scrolling |
| vertical | number | - | force the position of vertical scroller |
| horizental | number | - | force the position of horizental scroller |
| scrollStyle | object | - | scroll's style |

!> vertical/horizontal must be used with onScroll, aka the controlled component

> scrollStyle example
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
