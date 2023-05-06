---
layout: post
title:  "【新】使用 ASF 进行挂卡"
---

曾经在去年写过一篇如何用 Mono 配合 ASF 进行云挂卡的教程。时隔一年，ASF 早已经推出了各平台对应的版本，因此重新写一篇教程。本教程只整理出作为个人用户常会使用的功能，对于进阶用户可以移步 SteamCN 论坛的[一篇文章](https://steamcn.com/t301016-1-1)深入研究。

# 准备工作

1. 下载对应平台的 [ASF](https://github.com/JustArchiNET/ArchiSteamFarm/releases)，并解压缩。
2. 安装对应平台的 [.NET Runtime](https://dotnet.microsoft.com/download) 环境，不同平台在官网都有教程，在此不再赘述。

# 配置和运行

在 `config/` 下新建一个扩展名为 `.json` 的文件，比如 `bot.json`，使用纯文本编辑器打开，写入下面的代码并保存。

```
{  "Enabled": true,                            // 总开关  "StartOnLaunch": true,                      // 自动运行  "SteamLogin": "{LoginName}",                // Steam 登录名  "SteamPassword": "{Password}",              // Steam 密码  "DismissInventoryNotifications": false,     // 开启小绿信  "FarmOffline": false,                       // 不开启离线挂卡（不显示正在游戏）  "HandleOfflineMessages": false,             // 不处理聊天信息  "AcceptGifts": false,                       // 不自动接收礼物  "ShutdownOnFarmingFinished": false,         // 挂卡结束保持在线}
```

以上是只使用基础功能的文件配置，稍后会说明一些进阶功能。

配置完成后，到 ASF 的根目录运行对应平台的主程序文件即可。

# 进阶操作

## 搭建 IPC 服务

使用纯文本编辑器打开 `config/ASF.json`，将其中的 `"IPC"` 字段设置为 `"true"`，然后重启 ASF，此时，IPC 服务会默认开启在 `127.0.0.1:1242` 上，可以直接使用浏览器打开。

## IPC

在 IPC 的网页上，你可以完成绝大多数设置。