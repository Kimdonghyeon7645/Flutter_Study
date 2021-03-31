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
      floatingActionButton: FloatingActionButton(
        // onPressed: ,
        tooltip: '',
        child : Icon(Icons.add)
      )
    );
  }
}
```
Scaffold 의 floatingActionButton: (맨 하단에 떠있는 버튼) 영역을 만들고, 거기에 FloatingActionButton()으로 버튼을 만들어주면, 버튼 영역이 맨하단에 추가되서 앱에 그려진다.

```dart
floatingActionButton: FloatingActionButton(
  //onPressed: ,
  tooltip: '누르면 숫자가 증가합니다.',
  child: Icon(Icons.add),
),
```
그리고, onPressed: (눌렀을 때의 동작, 여기선 일단 구현을 미룸.)과 tooltip:(툴팁, 클릭했을 때 해당 버튼의 텍스트(설명)상자를 띄움), 그리고, 실제 child: 로 해서 Icon()위젯을 만드는데, 그 모양은 Icons.add 로, 더하기 버튼 아이콘(이미 내장되있는 아이콘이다)을 추가한다.

![image](https://user-images.githubusercontent.com/48408417/81030815-23e2f780-8ec5-11ea-939e-b05d07e753a2.png)
이제 onPressed: 버튼을 눌렀을 때의 동작을 넣어주는데, 버튼을 눌렀을 때 함수를 호출하게 하고, 함수를 호출하는 코드를 적어준다음에, 전구버튼의, 함수 생성하기를 눌러서 함수를 호출한 함수를 만들어(정의해)준다.

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
      floatingActionButton: FloatingActionButton(
        onPressed: _iconCounter,    // 생각해보니까 ()로 함수를 호출해서 반환값을 넘겨주면 안됬었다. ()는 빼주자.
        tooltip: '누르면 숫자가 증가합니다.',
        child: Icon(Icons.add),
      ),
    );
  }
  void _iconCounter() {
    setState(() => _counter++);
  }
}
```
이렇게 _iconCounter 함수를 정의해 주는데, 여기서 _iconCounter 가 속한 위젯은, stateful 위젯이라고 했었다. 여기서 state 는 앱이 실행되는 도중에 얼마든지 변할 수 있는, 살아있는 데이터들이라고 했고, statefull 은, state가 full(차있는) 위젯이였다. 이 statefull 위젯은 setState()함수가 실행될 때, state의 값이 변하는 상태를 자동으로 알아서 새로 위젯을 앱에 그려준다. (위젯을 새 state 값으로 업데이트(수정)해준다.)

그리고 이제 setState 함수 안에, state 값을 변화하는 코드, 여기서는 _counter 변수의 값을 ++하게 하면 된다.  
이렇게 하면 버튼이 눌릴 때마다, _iconCounter 함수의 setState((){}) 함수의, _counter가 ++(+1)돼서 카운터값이 1이 증가하게 된다.

![image](https://user-images.githubusercontent.com/48408417/81031350-f4cd8580-8ec6-11ea-9809-5da6c87e0897.png)

그러면 이제 모든 코드가 완성됬다.  
숫자를 카운트하는 앱을 완성한 것이다!