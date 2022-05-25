---
title: "Tick_painter"
date: 2022-05-25T10:12:40+08:00
draft: true
---

```dart
late AnimationController _ctrl;
  late AnimationController _tickCtrl;

 _ctrl = AnimationController(vsync: this, duration: Duration(seconds: 3))
      ..forward();
    _tickCtrl =
        AnimationController(vsync: this, duration: Duration(seconds: 2));

    _ctrl.addStatusListener((status) {
      if (status == AnimationStatus.completed) {
        _tickCtrl.forward();
      }
    });

 CustomPaint(
              painter: TickPainter(_tickCtrl, _ctrl.isCompleted),
            ),

class TickPainter extends CustomPainter {
  late final Animation<double> repaint;
  final bool isCompleted;

  TickPainter(this.repaint, this.isCompleted) : super(repaint: repaint);

  @override
  void paint(Canvas canvas, Size size) {
    Paint paint = Paint()
      ..color = Color(0xff23FF53)
      ..style = PaintingStyle.stroke
      ..strokeCap = StrokeCap.round
      ..strokeJoin = StrokeJoin.round
      ..strokeWidth = 20.0.rpx;

    Path path = Path();
    path.moveTo(125.0.rpx, 160.0.rpx);
    path.lineTo(175.0.rpx, 210.0.rpx);
    path.lineTo(250.0.rpx, 135.0.rpx);
    PathMetrics pms = path.computeMetrics();
    if (isCompleted) {
      pms.forEach((pm) {
        canvas.drawPath(pm.extractPath(0, pm.length * repaint.value), paint);
      });
    }
  }

  @override
  bool shouldRepaint(covariant CustomPainter oldDelegate) => false;
}
```