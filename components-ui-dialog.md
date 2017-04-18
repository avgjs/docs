# Dialog

`<Dialog>` is one of the interface components of AVG.js, which is used to display a empty dialog.

```javascript
import { React, Component, core, components, ui } from 'avg-core';
const { Surface, Image } = components;
const { Dialog } = ui;

class Game extends Component {
  handleFullscreenChange(value) {
    alert(value);
  }
  render() {
    return (
      <Surface>
        <Dialog modal={true}>
          <Image src='img.png' />
        </Dialog>
      </Surface>
    );
  }
}
```

All [standard properties](components-props.md) can be used.

In addition, it also includes:

| Name | Type | Default/Needed | Description |
| :--: | :--: | :--: | :-- |
| clip | boolean | false | whether cut out the content beyond dialog |
| modal | boolean | false | whether it is a modal |
| dragable | boolean | false | whether it is dragable |
| dragArea | array | [0, 0, Infinity, Infinity] | the area respond to drag action |
