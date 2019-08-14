# dart-notes

# dart-notes

- [Dart的Event Loop](#Dart的EventLoop)

- [Future API](#FutureAPI)



## FutureAPI

Future表示一个延迟的计算过程、任务，但并不立即执行。Future可以注册回调函数来处理计算的返回值或异常。
Future的静态方法很丰富，如：

```
 //Future(dynamic computation()) 最常用的构造方法
 Future myFunc() {
  return new Future(() async {
    //Do something
    var result = await http.get();
    return result;
  });
}

// Future.delayed(Duration duration, [dynamic computation()])
await Future.delayed(Duration(microseconds: 500));

//Future.sync(dynamic computation()) 同步执行的任务

//Future.value([value])
int result = await Future.delayed(Duration(milliseconds: 2000),(){
  return Future.value(123);
});

```
Future实例可以调用的api如下：



