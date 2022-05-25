---
title: "旧识新知"
date: 2022-04-22T11:16:32+08:00
draft: false
---

<!-- 前端总有一些知识是你不知道的。

也许框架帮你处理好了这些事情，但知道这些东西是无关乎框架的，是长久的。 -->

有很多标签和属性都是以前遇到但熟视无睹的，因为很多时候并不影响功能实现，都是选择性无视的，但闲来无事的时候还是想搞清楚这些奇奇怪怪的东西都是干嘛的。

* og 属性

```html
<meta property="og:site_name" content="..." />
```

* 专为苹果设备优化的信息
```html
 <meta name="apple-mobile-web-app-title" content="..." />
```

* theme
```html
<meta name="theme-color" content="#ffffff" />
```

这是 Apple 状态栏颜色元标记的适当 Web 标准式等效物。它告诉浏览器为周围的 UI 设置主题。Android 上的 Chrome 和桌面上的 Brave 在这方面都做得很好。您可以在内容中放置任何 CSS 颜色，甚至可以使用该media属性仅针对特定媒体查询显示此颜色，例如支持深色主题。您还可以在 Web 应用清单中定义此属性和其他属性。

* origin-trial
```html
<meta http-equiv="origin-trial" content="..." />
```
 
* text-size-adjust
```html
html{-ms-text-size-adjust:100%;-webkit-text...
```
 

假设您没有移动响应站点，并且您在小屏幕上打开它，因此浏览器可能会调整文本大小以使其更大以便更易于阅读。CSStext-size-adjust属性可以使用值 none 禁用此功能，也可以指定允许浏览器放大文本的百分比。

* body{margin:0;}

因为不同的浏览器具有不同的默认样式（用户代理样式表），您希望通过重置属性来覆盖它们，以便您的网站在不同设备上看起来相同。在这种情况下，Twitter 告诉浏览器删除 body 标签的默认边距。这只是为了减少浏览器的不一致，但我更喜欢规范化样式而不是重置它们，即跨浏览器应用相同的默认值而不是完全删除它们。人们甚至过去使用* { margin: 0 }它完全是矫枉过正并且对性能不利，但现在导入类似normalize.cssor reset.css（甚至更新的东西）并从那里开始是很常见的

* <link rel="search" type="application/opensearchdescription+xml" href="/opensearch.xml" title="Twitter">

告诉浏览器用户可以将 Twitter 添加为搜索引擎。

* <link rel="preload" as="script" crossorigin="anonymous" href="https://abs.twimg.com/responsive-web/client-web/polyfills.cad508b5.js" nonce="MGUyZTIyN2ItMDM1ZC00MzE5LWE2YmMtYTU5NTg2MDU0OTM1" />

有许多可以讨论的有趣属性，尤其是nonce.

* <link rel="alternate" hreflang="x-default" href="https://twitter.com/" />

用于国际登陆页面。

* :focus:not([data-focusvisible-polyfill]){outline: none;}

用于在不使用键盘导航时移除焦点轮廓（CSS:focus-visible选择器在此处填充）。