---
title: "Flutter_pulldown_refresh_and_reach__bottom"
date: 2022-04-26T09:42:42+08:00
draft: false
---

# 下拉刷新

最简单的方法，使用 RefreshIndicator 组件，在 onRefresh 里刷新数据即可

# 上拉加载更多

通过获取 ScrollController 的 maxScrollExtent 来确定有没有到底，然后在此基础上做加载更多的操作

