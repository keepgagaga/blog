---
title: "Flutter_responsive"
date: 2022-04-26T10:21:00+08:00
draft: false
---

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