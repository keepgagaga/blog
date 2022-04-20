---
title: "Ios_mix_flutter"
date: 2022-04-18T21:17:14+08:00
draft: true
---

采用把 Flutter SDK 及 Flutter 代码通过 CocoaPods 嵌入 iOS 工程里的方法，这种方法要求本地要有 Flutter 开发环境。

bug one: iOS 项目可以在真机上运行，但在模拟器上运行就会出现 No such module 'FlutterPluginRegistrant' error。