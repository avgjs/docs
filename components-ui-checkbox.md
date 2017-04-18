# Checkbox

`<Checkbox>` is one of the interface components of AVG.js, which is used to display a check box or ratio box.

```javascript
import { React, Component, core, components, ui } from 'avg-core';
const { Surface } = components;
const { Checkbox } = ui;

class Game extends Component {
  handleFullscreenChange(value) {
    alert(value);
  }
  render() {
    return (
      <Surface>
        <Checkbox src='option/screen_full.png' position={[700, 250]} name={'fullscreen'} value={true} defaultChecked={false} onChange={this.handleFullscreenChange.bind(this)}/>
        <Checkbox src='option/screen_window.png' position={[900, 250]} name={'fullscreen'} value={false} defaultChecked={true} />
      </Surface>
    );
  }
}
```

All [standard properties](components-props.md) can be used.

In addition, it also includes:

| Name | Type | Default/Needed | Description |
| :--: | :--: | :--: | :-- |
| defaultChecked | boolean | false | default state |
| value | any | undefined | value passed to callback function |
| onChange | function | - | callback when state changed |
| name | string | undefined | group name, if it is not set the component will be a check box, or it will be ratio box |

?> The resource specified by `src` can not only be jpg/png/webp, but also be svg.

!> When `name` is specified, you should set `onChange` property on just one of the components in the same group.
