
# 通用属性

| 名称 | 类型 | 默认值 | 描述 |
| :--: | :--: | :--: | :-- |
| src | string | - | 资源的url，仅对 Image 有效 |
| alpha | number | 1 | 透明度 |
| visible | boolean | true | 是否可见，不可见时事件也不会触发 |
| cacheAsBitmap | boolean | false | 缓存为图片，能提高性能，但内容更改后需要手动刷新，建议维持默认 |
| buttonMode | boolean | false | 鼠标移过时是否显示手型指针，当设置了 onClick 监听时自动为 true，可覆盖该默认行为 |
| x | number | 0 | x 坐标 |
| y | number | 0 | y 坐标 |
| position | array<number> | [x, y] | 和上面两个一样，但是数组形式 |
| width | number | texture width | 宽度 |
| height | number | texture width | 高度 |
| pivot | array<number> | [0, 0] | 轴点，旋转的中心 |
| anchor | array<number> | [0, 0] | 锚点，坐标的中心 |
| rotation | number | 0 | 旋转角度，单位为弧度，为正时顺时针旋转 |
| scale | array<number> | [0, 0] | 缩放 |
| skew | array<number> | [0, 0] | 扭曲 |
| tint | number | 0x0 | 着色 |