# AVG.js - 面向未来的文字冒险游戏框架

![](https://img.shields.io/badge/version-Setsumi-blue.svg?style=flat) ![](https://img.shields.io/npm/v/avg-core.svg?style=flat)

> 本项目处在 Alpha 阶段，暂不建议用于大型项目，但短篇使用 ok。  
> 欢迎建立 Issue 讨论任何相关的话题，但暂不接受非功能性 Pull Request（如：修正单词拼写）。

AVG.js 是一款开源 Web 游戏框架，以成为新一代的 AVG 类游戏制作框架为目标，兼顾与之相近的其他游戏类型，例如解谜、卡牌等。我们希望每个玩家都能够通过 Internet 随时随地享受游戏的乐趣，也希望每个游戏制作者都能够体验来自 Web 的思维为游戏开发带来的变革和便利。

若你想要获得关于 AVG.js 的最新消息，请关注我们的微博 [@BKEngine面包引擎](http://weibo.com/bakerymoe) （好吧，看起来很奇怪，但我们是一家…）。

同时，所有消息也会在我们的 [Gitter](https://gitter.im/AVG-js) 同步发布，主要的讨论交流也将在上面进行。

## 为什么选择 AVG.js

AVG.js 是一款功能丰富的游戏开发框架，能让你简单快速地搭建出你想要的游戏功能。通过筛选现成的或自行编写**组件**和**插件**，能够获得完全不同的游戏功能，如最简单基础的视觉小说，富于动画的卡牌收集，甚至充满复杂交互的解谜、战斗要素！

AVG.js 的图形部分基于最快的图像渲染库 [Pixi.js](https://github.com/pixijs/pixi.js)，支持总市场占有率 90% 以上的绝大多数浏览器（数据来自 [caniuse.com](caniuse.com)），在主流设备上运行流畅，同时在移动设备上能保持较低的发热量。

AVG.js 使用成熟的 [React](https://facebook.github.io/react/) 作为其组件化的基础，让开发者从繁琐而沉重的 UI 编写工作中解放出来是 AVG.js 设计目标之一。

与其他同类框架或引擎不同，依托 Pixi.js 和 React 活跃的社区和丰富的资源，AVG.js 从未孤军奋战，它的功能将源源不断从上游得到补充和增强。

此外，广受好评的 RPGMaker MV 同样基于 Pixi.js，这使得 AVG.js 能够完美地与其结合起来，为 RM 提供更强大的功能。

## 安装

确保已经正确安装 [Nodejs v6.5+](https://nodejs.org)

我们推荐您使用我们编写的命令行工具创建和发布您的游戏：

```shell
npm install -g avg-cli
avg create mygame
```

更详细的使用方法请参考[快速开始](zh/quick_start.md)

## Live Demo

[梦境下的约定试玩版](https://demo.avgjs.org) © 萌约游戏制作组

## 特性一览

- 资源预载
- 完整的补间动画、转场效果支持
- UI 状态化、数据驱动，自动管理内容更新
- 功能组件化，可自行组合复杂的可复用组件
- 细粒度场景管理器（由 React-router 提供）
- 自动发布工具（包含资源体积优化）
- 提供粒子系统、Live2D、Spine 等支持
- 增强功能可通过插件实现

## 参与开发

欢迎任何程度的参与！
无论你是发现了 Bug 或是想到了更好的点子，抑或只是想请求添加新的特性……你都可以发布 Issue 或到 Gitter 参与讨论！

不过在提交你的想法或代码之前，请阅读[贡献指引](https://github.com/pixijs/pixi.js/blob/master/CONTRIBUTING.md)。目前我们还没有自己的贡献指引，不过 Pixi.js 的指引可能已经足够说明所有的事情。

## 捐助和赞助

为了项目的继续进行，希望能够获得捐助/赞助。获得的资金将用于（按照先后顺序）：
- 购买维护项目运行所需的各种云服务或其他服务
- 为 Logo 设计支付费用
- 定制模板工程的 UI 界面和相关素材
- 支持中国国内非商业/同人游戏的发展
- 其他有必要的用途

若有意捐助/赞助，请联系 Icemic(#)bakery.moe

或直接向支付宝或 Paypal 捐助（请附上您的称呼，以便添加到捐助者名单）

<a href='https://ko-fi.com/A742BTX' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi4.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

<img height='142' style='border:0px;height:142px;' src='https://cloud.githubusercontent.com/assets/837432/19645521/a71da460-9a27-11e6-9605-aed9e251dd7a.png' border='0' alt='支付宝二维码' />

## License

若无单独说明  
本项目所有源代码以 [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0.html) 发布。  
本项目所有文档内容以 [CC-BY-NC-SA 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/) 发布






