---
title: "Circle_point_painter"
date: 2022-05-25T10:13:02+08:00
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
              painter: CirclePainter(_ctrl, _ctrl.isCompleted),
            ),

class CirclePainter extends CustomPainter {
  late final Animation<double> repaint;
  final bool isCompleted;

  CirclePainter(this.repaint, this.isCompleted) : super(repaint: repaint);

  @override
  void paint(Canvas canvas, Size size) {
    Paint paint = Paint()
      ..color = Color(0xFFE8B98F)
      ..style = PaintingStyle.stroke
      ..strokeWidth = 5.0.rpx;

    Path path = Path();
    var rect = Rect.fromCenter(
        center: Offset(0.0.rpx, 0.0.rpx), width: 340.0.rpx, height: 340.0.rpx);
    path..arcTo(rect, 0, pi * 1.9999999, true); //这个问题还没解决
    canvas.drawPath(path, paint);
    PathMetrics pms = path.computeMetrics();
    if (!isCompleted) {
      pms.forEach((pm) {
        Tangent? tangent = pm.getTangentForOffset(pm.length * repaint.value);
        canvas.drawCircle(
            tangent!.position, 5, Paint()..color = Color(0xFFE8B98F));
      });
    }
  }

  @override
  bool shouldRepaint(covariant CustomPainter oldDelegate) {
    return false;
  }
}
```