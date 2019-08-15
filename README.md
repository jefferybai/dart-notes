# dart-notes

# dart-notes

- [Dart的Event Loop](#Dart的EventLoop)

- [Future](#Future)



## Future

dart中当执行return await () async {}的时候，实际上返回的是一个延迟计算的Future对象.

Future表示一个延迟的计算过程、任务，它的执行遵循Dart的Event Loop策略。

#### 创建Future的两种方式（推荐第一种）
```
//第一种
Future myFunc() {
  return new Future(() async {
    //Do something
    var result = await http.get();
    return result;
  });

//第二种 多用于自定义的class中
Future<String> myFunc() {
  Completer<String> comp = new Completer<String>();
  //Do something
  comp.complete("...");

  return comp.future;
}

```
  


#### Future类的静态方法
```
 //Future(dynamic computation()) 
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
Future的公共方法
```
//then：异步操作逻辑在这里写。
new Future(() => futureTask)  //  异步任务的函数
        .then((m) => "futueTask execute result:$m")  //   任务执行完后的子任务
        .then((m) => m.length)  //  其中m为上个任务执行完后的返回的结果

//whenComplete：异步完成时的回调。
new Future(() => futureTask)  //  异步任务的函数
        .then((m) => "futueTask execute result:$m")  //   任务执行完后的子任务
        .then((m) => m.length)  //  其中m为上个任务执行完后的返回的结果
        .then((m) => printLength(m))
        .whenComplete(() => whenTaskCompelete);


//catchError：捕获异常或者异步出错时的回调。
 
```

