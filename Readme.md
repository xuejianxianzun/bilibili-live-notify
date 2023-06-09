# Bilibili 直播开播时显示系统通知

这是一个 Nodejs 脚本，通过 Bilibili 的 API 获取直播间状态，并且当状态变化时，显示系统原生通知。

效果图：

![效果图](https://saber.love/f/20230609_232047.png)

**注意：** 这个脚本目前只在 Windows 上验证过，尚不清楚在其他系统里能否成功发送通知。

# 使用步骤

## 安装 Nodejs

如果你没有安装 Nodejs，请从官网下载安装包并安装。

https://nodejs.org/en/download

## 下载代码

你可以在本 GitHub 页面下载压缩包并解压到一个文件夹里。

也可以自行 clone 本仓库到本地。

## 配置脚本

打开 `index.js`，并在其中配置你需要监控的直播间。

如果你需要监控多个直播间，可以复制 room_list 数组里的配置项，添加多个直播间。

每个直播间必须填写房间 id，其他的都可以不用修改。

## 安装依赖

在代码文件夹里运行终端（如 CMD），并执行以下命令安装依赖：

```shell
npm i
```

如果可以正常安装，就可以可以跳到下面的“启动”步骤。

如果你使用 npm 命令时因为网络问题导致安装不了依赖，可以使用淘宝 npm 镜像。

先运行：
```shell
alias cnpm="npm --registry=https://registry.npmmirror.com \
--cache=$HOME/.npm/.cache/cnpm \
--disturl=https://npmmirror.com/mirrors/node \
--userconfig=$HOME/.cnpmrc"
```

然后运行：

```shell
cnpm i
```

安装完依赖之后才可以运行脚本。

## 启动

```shell
node index.js
```

运行后没有任何输出是正常的。

如果显示了错误信息则不正常，请检查依赖是否安装成功，可以尝试重新安装一次。

--------------

## 默认只有开播会发送消息

代码里的函数 `showNotify` 用于发送提醒消息。

默认只有当主播开播时才会发送消息，如果你需要在下播时也发送消息，可以启用被注释掉的 `showNotify` 调用。
