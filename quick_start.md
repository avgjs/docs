# 快速开始

## 安装

确保已经正确安装 [Nodejs v6.5+](https://nodejs.org)

我们推荐您使用我们编写的命令行工具创建和发布您的游戏：

```shell
npm install -g avg-cli
avg create mygame
```

之后会要求你输入项目名（文件夹名称）和游戏名，最后的输出类似于：

```
$ avg create mygame
? What's your project name? mygame
? What's your game name? My Game
? Your game project will be created at /Users/username/mygame 
continue? Yes
[INFO]  Please make sure you have access to github.com to download the latest template package
✔ Downloading the latest template...
✔ Unzipping...
✔ Initializing...
[INFO]  Your project has been created!
[INFO]  Run `cd mygame && npm run dev` to have a quick look.
```

## 启动开发

```shell
cd mygame
npm run dev
```

调试服务器将启动，并弹出浏览器页面

这时可以用任何代码编辑器打开 mygame 文件夹下的文件，开始修改模板工程，使之成为你的游戏项目。

每当你修改了文件并按下保存，浏览器中的画面将自动更新或刷新。

## 发布游戏

```shell
avg publish
```

发布流程将自动开始，结束后可在 `./dist` 文件夹找到发布后的完整游戏，你可以将其上传到服务器或启动本地服务器查看。

