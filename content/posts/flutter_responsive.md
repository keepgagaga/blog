---
title: "Flutter_responsive"
date: 2022-04-26T10:21:00+08:00
draft: false
---

很早之前找到的一个方案，使用下来感觉没啥毛病，除了每个页面都要引入麻烦些，原方案还拓展了 int，但感觉 double 能兼容 int 的绝大部分场景，偷个懒就只用 double 了。

使用的时候按照设计图当前的尺寸改一下 standardWidth ，比如这里的意思就是当前设计图的尺寸是按 750 宽度设计的。

```dart
class SizeFit {
  static late MediaQueryData _mediaQueryData;
  static late double screenWidth;
  static late double screenHeight;
  static late double rpx;
  static late double px;

  static void initialize(BuildContext context, {double standardWidth = 750}) {
    _mediaQueryData = MediaQuery.of(context);
    screenWidth = _mediaQueryData.size.width;
    screenHeight = _mediaQueryData.size.height;
    rpx = screenWidth / standardWidth;
    px = screenWidth / standardWidth * 2;
  }

  // 按照像素来设置
  static double setPx(double size) {
    return SizeFit.rpx * size * 2;
  }

  // 按照rpx来设置
  static double setRpx(double size) {
    return SizeFit.rpx * size;
  }
}

extension DoubleFit on double {
  double get px {
    return SizeFit.setPx(this);
  }

  double get rpx {
    return SizeFit.setRpx(this);
  }
}

// use

Widget build(BuildContext context) {
  SizeFit.initialize(context);
  return Container(
    width: 100.rpx,
    height: 100.rpx,
    color: Colors.red,
  );
}


```