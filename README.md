# AVG.js - A Future-oriented Adventure Game Framework

![](https://img.shields.io/badge/version-Setsumi-blue.svg?style=flat) ![](https://img.shields.io/npm/v/avg-core.svg?style=flat)

> The project is in Alpha stage, not recommended for large projects, but may be enough for a shorter one.
> Welcome to discuss any related topics, but non-functional Pull Request will not be accepted for the time being. (e.g. fix a wrong spelling in code, but except for fixes or updates for documents.)

AVG.js is an open source web-game framework, aiming to be a new generation of AVG development framework. Also, we take some similar types of games into account, such as puzzles, renai simulation, kancolle-like, TCG/CCG etc. We hope that every player will be able to enjoy a game anytime and anywhere through the Internet, hope that each game maker can experience a easier game development.

All the news will be released in our [Gitter](https://gitter.im/AVG-js), where you can also discuss more topics with us!

## Why choose AVG.js

AVG.js is a feature-rich game development framework that allows you build your game quickly and easily. By using different off-the-shelf or customized **components** and **plugins**, you can make different types of games, such as the simplest visual novels, card collection with animations, and even puzzle or action games with a lot of interactions.

AVG.js is based on the fastest graphic rendering library [Pixi.js](https://github.com/pixijs/pixi.js), support more than 90% modern browsers with smoothly fps and low heat on mobile devices.

AVG.js uses [React](https://facebook.github.io/react/) as the basis of its componentization, frees game makers from heavy UI development.

It's always convenient for every one to use extensions of pixi.js and react in AVG.js, e.g. use react-router as scene manager or use pixi-spine as a custom component.

In addition, the highly acclaimed RPGMaker MV is also based on Pixi.js, so AVG.js can be combined with it for more exciting gameplay.

## Installation

Make sure [Nodejs v6.5+](https://nodejs.org) has been installed correctly.

We recommend that you create and publish your game using our command-line tools:

```shell
npm install -g avg-cli
avg create mygame
```

For more details, refer to [Quickstart](quick_start.md)

## Live Demo (Chinese language)

[梦境下的约定试玩版](https://demo.avgjs.org) © 萌约游戏制作组

## Features

- Resource preloading
- Tween & Transition
- Stateful UI, Data-driven
- Componentization
- Fine-grained SceneManager (Using react-router)
- Automatic publishing tool (Include resource size optimization)
- Particle System, Live2D, Spine
- Plugins

## Participate in development

Any contribution is welcomed!
No matter you find a bug, think of a better idea, or just want to ask for new features... Issue it or participate discussion in Gitter!

But before you submit your ideas or code, please read [Contribution guidelines](https://github.com/pixijs/pixi.js/blob/master/CONTRIBUTING.md). At present we do not have our own contribution guidelines, but Pixi.js guidelines may have been sufficient to explain all the things.

## Donation and sponsorship

We hope to receive donation/sponsorship for the continuation of the project. The funds obtained will be used (in order):
- Purchase a variety of cloud services or other services required to maintain the project
- Pay for Logo design
- Customize the UI of the template project and related material
- Support Chinese non-commercial/indie/doujin game development
- Other necessary uses

If you wish to donate/sponsor, please contact Icemic(#)bakery.moe

Or donate to Alipay or Paypal (Please attach your name)

<a href='https://ko-fi.com/A742BTX' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi4.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

<img height='142' style='border:0px;height:142px;' src='https://cloud.githubusercontent.com/assets/837432/19645521/a71da460-9a27-11e6-9605-aed9e251dd7a.png' border='0' alt='Alipay QRCode' />

## License

If not otherwise stated  
All the source code of this project is distributed under [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).  
All the documentation of this project is distributed under [CC-BY-NC-SA 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/).






