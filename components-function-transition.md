# Transition (Gradient Effect)

## Usage

For functional components that already contain Transition, you can use it in Storyscript like this:

```storyscript
[bg file="background.jpg" pretrans]  // Freeze the current component and execute the command
[bg file="background.jpg" trans]  // Execute the command and start the gradient animation, default effect is `crossfade`, the duration is 1000ms

[bg file="background.jpg" trans method='universal' rule='rule/1.png'] // Use other transition effect
```

Currently supported gradients and parameters:

### crossfade

|    Name     |   Type    |    Default/Needed    | Description
| :-------: | :-----: | :----------: | :--------------
|   duration    | number  |      1000      | duration

### universal

(aka dynamic mask)

|    Name     |   Type    |    Default/Needed    | Description
| :-------: | :-----: | :----------: | :--------------
|   rule    | string  |      ''      | mask file
|   duration    | number  |      1000      | duration

### shutter

|    Name     |   Type    |    Default/Needed    | Description
| :-------: | :-----: | :----------: | :--------------
|   direction    | string  |      'left'      | direction
|   num    | number  |      16      | number of blinds
|   duration    | number  |      1000      | duration

### ripple

|    Name     |   Type    |    Default/Needed    | Description
| :-------: | :-----: | :----------: | :--------------
|   origin    | array<number>  |      [0.5, 0.5]      | origin point
|   speed    | number  |      1      | speed of ripple
|   count    | array<number>  |     [10, 10]     | number of crests
|   maxDrift    | number  |      24      | max drift
|   duration    | number  |      1000      | duration


## Add gradient effect to custom components

To be continued...
