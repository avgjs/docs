# Sound

Sound plugin is one of the core plugins of AVG.js, providing audio playback.

```javascript
import { core, plugins } from 'avg-core';

// run this code before core.render() to install the plugin
core.installPlugin(plugins.Audio);
```

## Using in Javascript


```javascript
// you can use it wherever you want,
// and more APIs is listed below.
core.plugins.audio.create(0, 'bgm/bgm.ogg', { loop: true });
core.plugins.audio.play(0);
```

### API

#### create(channel: number | string, src: string, options: object)

channel: Channel number or channel name, which can be a number or a string

src: Relative patt to assets folder

options:

| name | type | defualt | description |
| :--: | :--: | :--: | :-- |
| loop | boolean | false |  |
| preload | boolean | true | Load immediately or load when .play () is executed |
| autoplay | boolean | true |  |
| mute | boolean | false |  |
| rate | number | 1 | Playback rate |
| autounload | boolean | true | automatically unload audio |
| exclusive | boolean | true | If false, allows multiple audio to use the same channel |

#### destroy(channel)

Destroy a channel (stop playing and unload audio)

#### getByChannel(channel: number | string): Howl

Get an instance of a channel and return [Howler](https://github.com/goldfire/howler.js/) instance

#### play(channel: number | string)

Play the audio of a channel

#### pause(channel: number | string)

Pause / resume the audio of a channel

#### stop(channel: number | string)

Stop the audio of a channel

#### mute(channel: number | string, muted?: boolean)

Mute the audio of a channel

#### volume(channel: number | string, vol?: number)

Gets / sets the volume of a channel

#### fade(channel: number | string, from: number, to: number, duration: number)

Fade the audio volume of a channel from one value to another

#### fadeIn(channel: number | string, to: number, duration: number)

Fade the audio volume of a channel to a value

#### fadeOut(channel: number | string, duration: number)

Fade the audio volume of a channel to zero

#### rate(channel: number | string, rate?: number)

Gets / sets the playback rate of a channel

#### seek(channel: number | string, position?: number)

Gets / sets the playback position of a channel

#### loop(channel: number | string, loop?: boolean)

Gets / sets whether a channel is looped

#### stopAll()

Stop all channels of audio

#### channelExist(channel: number | string): boolean

Check if a channel has audio

#### channelVolume(channel): number

Get the audio volume of a channel

#### channelVolume(channel: number | string, vol: number)

Sets the audio volume of a channel, in the range 0-1

#### globalVolume(vol?: number): number

Gets / sets the global volume, and the final volume of each channel is equal to the product of the global volume and the channel volume

#### globalMute(muted?: boolean): boolean

Gets / sets global mute state


## Using in storyscript

You can use it like this in storyscript:

```storyscript
[sound bgm src='bgm/bgm.ogg' loop=true]
[sound bgm stop]

// or

[sound channel='bgm' src='bgm/bgm.ogg' loop=true]
[sound channel='bgm' stop]
```

Script content consists of three parts: command name (sound), channel (channel), parameters

Among them, the command name is fixed to `sound`;  
Channel is usually `channel=<number | string>` format, but for the sake of simplicity, we added `bgm` `se` `voice` three syntax sugar, respectively replacing `channel='bgm'` `channel='se'` `channel='voice'`.

The following lists all supported commands (in fact they only have a small difference from the APIs above):

```storyscript
// the value after `=` is the default value

[sound channel= src= volume=1 loop=false preload=true autoplay=true mute=false rate=1 autounload=true exclusive=true]

[sound channel= play/pause/stop/destroy]
[sound channel= mute/rate/volume/seek/loop value=]
[sound channel= fade from= to= duration=]
[sound channel= fadein to= duration=]
[sound channel= fadeout duration=]

// global
[sound mute/volume value=]
[sound stopall]
```

> **Why can not I get a value by command?**  
> This is related to the design ideas, we believe that storyscript should only bear the simple work. The "get" command and the subsequent processing will undoubtedly introduce more complex logic into storyscript, which we do not want to see. If you need to get some value and proccess it, you should use Javascript to do so and expose it as a new command for storyscript.

