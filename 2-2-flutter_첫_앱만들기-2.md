# 2-2 - flutter 로 처음 앱 만들기 - 2편 (카운팅 앱)

1편에서 아래의 코드를 main.dart 에서 작성했다.
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Hi! Flutter~!',
      theme: ThemeData(primarySwatch: Colors.blueGrey),
      home: MyHomePage(title: 'Hi Flutter Home Page')
    );
  }
}

class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(widget.title),),
    );
  }
}
```
이것이 기본적으로 앱을 만들기 위한 셋팅이라면,  
이번에는 본격적으로 앱의 레이아웃과 위젯을 채워보도록 하자.

## 앱에 텍스트 추가하기

```dart
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(widget.title),),
      body: Center(
        child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
        ),
      ),
    );
  }
}
```
Scaffold 의 body 영역에서 Center()로 가로로 가운데 정렬한 레이아웃을 짜고,  
그안에 child: 로 Column() (행, 가로줄 여러개)를 지정한다. 그리고 그 괄호안에 mainAxisAlignment: 으로 정렬을 지정하는데,   
MainAxisAlignment.center 으로 세로로도 가운데로 정렬한다.

```dart
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(widget.title),),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('아무거나 대충 입력한 텍스트 입니다.'),
            Text('추가한 다음 텍스트 입니다.'),
          ],
        ),
      ),
    );
  }
}
```
그리고, children: 으로 행(Column)의 각각의 행 하나하나를 리스트의 요소로 넣어줄 수 있다.  
여기서는 Text()로 텍스트 위젯을 넣어줬다. 그리고 다음 요소로 다시 Text()로 텍스트 위젯을 넣어주면,

![image](https://user-images.githubusercontent.com/48408417/80986492-9a530b80-8e6b-11ea-9a36-18cc870a2034.png)
이렇게 하나 하나의 행으로, 텍스트가 들어가는 것을 볼 수 있다.

이제 이 텍스트를 만들려는 카운터 앱의 내용으로 바꿔주도록 하자.

```dart
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(widget.title),),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('버튼을 눌러서 숫자를 카운터 해보세요!'),
            Text(
              'Counter', 
              style: Theme.of(context).textTheme.display1,
            ),
          ],
        ),
      ),
    );
  }
}
```
Text 안의 문자열을 알맞게 고쳐줬고, Text에 스타일이 필요한것에는, 문자열 뒤에 style: 을 추가해서 Theme.of(context).textTheme.display1으로 스타일을 지정해줬다. 

Theme.of(context).textTheme.display1  
에서 Theme.of(context) 는 문법상 쓰는 의미없는 내용이고,  
textTheme.display1 로해서 textTheme(텍스트 테마)중에서 display1 스타일을 지정해주는 것이다.
![image](https://user-images.githubusercontent.com/48408417/80987069-76dc9080-8e6c-11ea-91ac-69516bb09093.png)

## 앱에 카운트 변수 추가해서 텍스트로 보여주기

```dart
class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(widget.title),),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('버튼을 눌러서 숫자를 카운터 해보세요!'),
            Text(
              '$_counter', 
              style: Theme.of(context).textTheme.display1,
            ),
          ],
        ),
      ),
    );
  }
}
```
이제 카운터가 저장될 변수를 만들어서, 출력하게 하자.  
이 클래스 안의 맨 위에, int _counter = 0; 으로 변수를 만들어 준다.  
(변수이름앞에 _을 붙이는 것은 private(클래스 내에서만 사용하는) 변수라는 뜻이다.)

그리고 아까의 Text()에서 임시로 카운트 되는 값이 들어가는 것을 'Counter'로 적어놓았던 것을, 변수로 바꾼다. (''안에 $변수이름을 넣으면 변수를 텍스트로 사용할 수 있게 한다.)

## 카운팅을 하는 버튼 만들기

마지막으로 카운팅을 하는(카운트 변수에 값을 추가하는) 버튼을 만들자.


