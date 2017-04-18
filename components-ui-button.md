# Button

`<Button>` is one of the interface components of AVG.js, which is used to display a button.

```javascript
import { React, Component, core, components, ui } from 'avg-core';
const { Surface } = components;
const { Button } = ui;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Button src="button.png" onClick={() => alert('clicked!')}>
      </Surface>
    );
  }
}
```

All [standard properties](components-props.md) can be used.

In addition, it also includes:

| Name | Type | Default/Needed | Description |
| :--: | :--: | :--: | :-- |
| lite | boolean | true | lite means to divided the image into two parts (idle/over), otherwise into three parts (idle/over/clicked) |

?> The resource specified by `src` can not only be jpg/png/webp, but also be svg.
