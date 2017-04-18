# Text

`<Text>`is one of the basic components of AVG.js, used to display a text.

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, Text } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Text text="越过长城，走向世界每个角落。\nAcross the Great Wall, we can reach every corner in the world."/>
      </Surface>
    );
  }
}
```

All [standard properties](components-props.md) can be used.

In addition, it also includes:

| Name | Type | Default/Needed | Description |
| :--: | :--: | :--: | :-- |
| text | string | '' | text content, use `\n` to wrap |
| style | object | - | style of text, [type and default values are here](http://pixijs.download/release/docs/PIXI.TextStyle.html) |
