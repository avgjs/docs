
# Standard Properties

| Name | Type | Default/Needed | Description |
| :--: | :--: | :--: | :-- |
| src | string | - | url of resource |
| alpha | number | 1 | transparency |
| visible | boolean | true | events will not trigger when invisible |
| cacheAsBitmap | boolean | false | which can improve performance, but you have to refresh it manually. Recommends to keep false |
| buttonMode | boolean | false | whether change pointer to hand style when mouse over. It will be set to true when `onClick` is listened, but it can be override by user's property setting. |
| x | number | 0 | x coordinate |
| y | number | 0 | y coordinate |
| position | array<number> | [x, y] | Same with above, but in array format |
| width | number | texture width | width |
| height | number | texture width | height |
| pivot | array<number> | [0, 0] | center of rotate |
| anchor | array<number> | [0, 0] | center of coordinate |
| rotation | number | 0 | radian, rotate clockwise |
| scale | array<number> | [0, 0] | scale ratio |
| skew | array<number> | [0, 0] | skew ratio |
| tint | number | 0x0 | tint color |
