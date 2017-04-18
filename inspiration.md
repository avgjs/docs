# Inspiration

## Separation of game system and script

We often encounters two problems when using traditional VN game engines (like Kirikiri2):

- Scripting system is very backward for programmers. Using it to write a game system is extremely cumbersome, you always had to update the interface content on your own. The code is often not reusable, you may have to rewrite all the code when UI design changes.
- For non-programmers, the script is too difficult to learn. You have to let the programmer to enter the story, but communication between programmer and director always has troubles.

Both are due to a problem: the traditional engine, system programming and story entry are relying on the same set of command-style script system.

Command-based scripting system itself is very easy to understand, it is suitable for people who do not have programming knowledge to learn. But it is not suitable for the expression of complex logic, especially the game system. In order to compensate for this shortcoming, these script systems often introduce more complex commands and jumps. Finally, it is not only NOT improve the capability of system programming, but also increase the complexity which makes it more difficult for many non-programmers to learn.

AVG.js' primary idea is the separation of game system and script. The game system is suitable to use a real programming languages (e.g. Javascript or Python), rather than command-styled scripting languages. Meanwhile, the scripting language can be greatly simplified.

AVG.js has made a significant simplification of the script, making it a simple language that can only be used to express storytelling. I believe that the game maker can learn it quickly by learning it for a short time, or even just copy the form without understanding the grammar. We call it [Storyscript](storyscript.md).

In addition, this module is also replaceable, you can write a more suitable one for yourselves, such as direct reading csv file as a script.

So what about the game system?

## Writing game system easier with React

Load&Save, config, CG mode are basic systems of a AVG, which is more important, it is often not just a simple visual novel, but also contains puzzles, mini games and even fighting system.

Facing to complex system logic, we manually create each element, update each ralated element when handling some interactions, and delete each element when quit it, in the past. Accidentally lost something, accidentally a bug which is difficult to troubleshoot. 

Is there a easier way? Of course.

The reason why the above problems occur is that they are command-style programming, ie *tell the program what I need it to do*, which naturally needs to be described in great detail. The corresponding one is declarative programming, where you only need to describe *what I want* and give the required data to it. When you change the data, the user interface will update automatically.

So, AVG.js use industry-recognized framework [React](https://facebook.github.io/react/) as the basis of its system built.

Another benefit from React is componentization whic not only means that you can easily modify and reuse your own or someone else's code, but also means that you can be very free to add and combine functions. For example: `Button Component + Sound Playback = Button Component with sound effects`, `Textwindow Component + Image Component = Textwindow with Character Avatar Component `.

Here, we also encourage you to share your the components with others, even if it is practicing works!

## Convenient Development and Debugging

The existing development method is to modify the code -> run -> modify the code -> run -> ... endless cycle, AVG.js will bring a new real-time game development experience.

The code editor and the browser are running at the same time, when you modify a line of code, press Save, the browser will be in the next moment real-time update your changes - and even the page is no need to refresh!

In addition, React and Pixi.js' Chrome dev-tools are also available for AVG.js, you can directly modify the component properties in the browser (e.g. image coordinates) without modifying the code.


