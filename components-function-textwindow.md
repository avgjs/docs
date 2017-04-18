# Textwindow

`<Textwindow>`is one of functional components of AVG.js, provides text print command for [Storyscript](storyscript.md).

```javascript
import { React, Component, core, components } from 'avg-core';
const { Surface, Textwindow } = components;

class Game extends Component {
  render() {
    return (
      <Surface>
        <Textwindow/>
      </Surface>
    );
  }
}
```

All [standard properties](components-props.md) can be used.

In addition, it also includes:

| Name | Type | Default/Needed | Description |
| :-------: | :-----: | :----------: | :-------------- |
|   text    | string  |      ''      | text content |
|   color   | number  |   0xffffff   | text color |
|   size    | number  |      24      | text size |
|   speed   | number  |      24      | printing speed (characters/second) |
|   font    | string  | 'sans-serif' | default font |
| textRect  | number  |     null     | display area, default to unlimited |
|  bgFile   | string  |      ''      | background image |
| xinterval | number  |      0       | word spacing |
| yinterval | number  |      3       | line spacing |
|   bold    | boolean |    false     | if is bold |
|  italic   | boolean |    false     | if is italic |
| strike | boolean | false | strikethrough |
| under | boolean | false | underline |
| shadow | boolean | false | text shadow |
| shadowcolor | number | 0x0 | text shadow color |
| stroke | boolean | false | text stroke |
| strokecolor | number | 0x0 | text stroke color |

Usage in Storyscript:

```storyscript
//  Modify the text box properties
[text set ...]   
//  Show/hide text box, you can use `trans` to set the gradient effect
[text show trans]
[text hide]
//  Empty the text of the text box
[text clear]
This is a line of text, it will wait for changing the page[p]
This is another line of text[r]
It directly to the next line[p]
This line of text waits for a click[l]And then click to change the page[p]
```

> Detailed usage of the fade function refers to [Transition](components-function-transition.md)
