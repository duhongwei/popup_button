<!-- 
This README describes the package. If you publish this package to pub.dev,
this README's contents appear on the landing page for your package.

For information about how to write a good package README, see the guide for
[writing package pages](https://dart.dev/guides/libraries/writing-package-pages). 

For general information about developing packages, see the Dart guide for
[creating packages](https://dart.dev/guides/libraries/create-library-packages)
and the Flutter guide for
[developing packages and plugins](https://flutter.dev/developing-packages). 
-->

和 flutter 提供的 PopupMenuButton 类似，都是 tap 一个 widget 弹出一个popup,但是 PopupButton 可以自定义显示位置。

## Features

1. 定义 popup 的显示位置，可以在 button的左面，上面，右面 或 下面。
2. 定义 popup 的对齐方式，start,center,end
3. button 可以通过 child 属性 定义为任意 widget。
4. popup 可以通过 builder 方法 返回 任意 widget。


## Usage

```dart
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
          child: PopupButton(
        direction: PopupDirection.bottom,
        offset: Offset.zero,
        child: Container(
          color: Colors.blueAccent,
          width: 50,
          height: 20,
        ),
        builder: (context) {
          return Container(
            color: Colors.green,
            width: 100,
            height: 50,
          );
        },
      )),
    );
  }
```
## direction 定义位置
位置 是相对于 button 的。 direction 是 一个 enum ，有四个值 PopupDirection.left,PopupDirection.top,PopupDirection.right,PopupDirection.bottom
## align 定义对齐方式 ，默认是居中

align 是一个 enum ，有四个值 Align.start, Align.center ,Align.end

## offset 定义 偏移

direction 和 align 决定好 位置 和对齐后， 如果还想进行微调，可以定义 offset。offset是 相对于 button 的偏移。

比如 Offset(10,20)
1.  PopupDirection.left 的时候， Offset(10,20) 表示向左偏移 10,向下偏移 20
2.  PopupDirection.right 的时候， Offset(10,20) 表示向右偏移 10,向下偏移 20
3.  PopupDirection.top 的时候， Offset(10,20) 表示向右偏移 10,向上偏移 20

## Additional information

PopupButton 相比于 PopupMenuButton 最大的优点就是可以完全自定义 UI 和 位置。

除了直接使用 PopupButton 还可以使用,showPopup 函数。

```dart
Future showPopup(
    {required BuildContext context,
    required RelativeRect position,
    required Widget child,
    bool useRootNavigator = false,
    required PopupDirection direction,
    required PopupAlign align})
```

如果 要退出, 用 pop
```dart
Navigator.of(context).pop() 
```

