# Bilibili 直播开播时显示系统通知

这是一个 Nodejs 脚本，通过 Bilibili 的 API 获取直播间状态，在主播开播时显示系统原生通知，并且点击通知可以在浏览器里打开直播间。

效果图：

![效果图](https://saber.love/f/20230609_232047.png)

# 使用步骤

如果你不明白有些地方怎么操作，可以查看视频教程：https://www.bilibili.com/video/BV1dM4y1a7qA

## 下载代码

你可以在本 GitHub 页面下载压缩包并解压到一个文件夹里。

也可以自行 clone 本仓库到本地。

## 配置脚本

编辑 `index.js`（如果你没有代码编辑器，可以右键选择打开方式，用记事本打开），并在 `config` 里设置你要监控的直播间。

可以监控多个直播间；每个直播间必须填写房间号。

## 安装 Nodejs

如果你没有安装 Nodejs，请从官网下载安装包并安装。

https://nodejs.org/en/download

## 安装依赖

在代码文件夹里运行终端（例如，你可以先打开存放这个代码的文件夹，然后在地址栏输入 cmd 并回车）。

然后执行这个命令安装依赖：

```shell
npm i
```

等待执行完成即可。如果可以正常安装，就可以可以跳到下面的“启动”步骤。

如果报错了，可能是因为网络问题导致安装不了依赖，此时可以使用淘宝 npm 镜像来安装。方法如下：

先运行：

```shell
npm install -g cnpm --registry=https://registry.npmmirror.com
```

然后运行：

```shell
cnpm i
```

安装完依赖之后才可以运行脚本。

## 启动

运行命令：

```shell
node index.js
```

运行后没有弹出通知卡片是正常的，这表示监控的这些直播间都没有开播。

如果显示了错误信息则不正常，请检查依赖是否安装成功，可以尝试重新安装依赖。

--------------

## 默认只有开播会发送消息

代码里的函数 `showNotify` 用于发送提醒消息。

默认只有当主播开播时才会发送消息，如果你需要在下播时也发送消息，可以启用被注释掉的 `showNotify` 调用。

## 已知问题

### 通知会过期

当通知显示在右下角时，会停留 5 秒，然后消失，只保留在通知中心里。

通知消失时就是过期了，之后本代码无法监测到点击通知的动作，所以用户点击通知中心里的通知是不能打开直播间的。

### 在勿扰模式下不会显示通知

当系统处于勿扰模式时（例如用户处于全屏视频或全屏游戏中，或者使用专注时钟，或者手动开启勿扰模式），通知不会在右下角显示，只会保存在通知中心里，并且通知会立即过期。

有时这可能会导致用户在预期之外错过通知，不过现在我在 Windows 设置中没找到解决的办法。
