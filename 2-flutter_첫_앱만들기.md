# 2 - flutter 로 처음 앱 만들기 (카운팅 앱)

일단 프로젝트를 만들려면, 생성해야 한다. 

vscode 라면 명령 팔레트를 열어서 (단축키 cirl + shift + p)  
> Flutter: New Project 

를 클릭해서 플로터 프로젝트의 기초를 생성한다. 

그리고, lib 폴더안의 main.dart 파일에서 앱을 개발하는데, (일단 다른 .dart 파일은 무시해도 좋다.)

기본으로 작성되어 있는 코드를 모두 지우고, 새로 쓰면서 뭐가 뭔지 알아보도록 하자. (완전히 왜 이렇게 쓰는지 하나하나 이해할려다기 보다는, 가볍게 걍 근가보다 하고 대강 이해해도 충분하다. 일단 처음 앱을 만들어 본다음에, 여기서 쓰이는 문법을 뒤에서 차근히 알아볼 것이다.)

### 앱 코드 작성하기 (main.dart)

```dart
import 'package:flutter/material.dart';
```

우선 패키지를 임포트(가져오기)한다. 얘도 파이썬 처럼 import 키워드를 사용할 수 있는데, 여기선 package중에서 material(매터리얼) 디자인을 가져온다. 

(앱 코드를 작성할 때 material 디자인으로 작성할 것이다.)

참고로 다트는 언어자체에서 ;(세미콜론)을 사용하기에 끝에다 ;를 붙여주자.

```dart
void main() => runApp(MyApp());
```
```dart
// 위 코드같이 해도 되고, 아래 코드처럼 해도 된다.
void main(){
  runApp(MyApp());
}
```

c언어에서 자주봤던 main() 함수는 프로그램의 시작점이다. 이함수를 기초로 해서 모든 프로그램이 실행이 되는건데, 여기서 main() 함수로 runApp(); , 말그대로 앱(App)을 실행(run)한다. 그리고 그안의 인자값인 MyApp() 이 실행되는 앱이 되는 것이다.

이 코드는 건들 필요가 없는 부분이다. 메인에서 앱을 구동하는 코드는 그대로 두고, 앱안에 뭐가 들어갈지 앱 클래스 안에서 정해주면 되는 것이다.

```dart
class extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```
이제 MyApp() 를 만들어줄 차례이다. 여기서 앱을 저장할 때, 두가지 방법이 있다. 정적인 stateless 와 동적인 statefull, 여기서는 기본적인 stateless 방식으로 만들어 주었다.   
st 만 쳐도, 자동완성으로 stless 를 볼 수 있는데, 클릭하면 위같이 자동으로 기본 statelsee 구조가 짜여저 나온다.

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp();
  }
}
```
여기에서 class 이름인 MyApp 을 적어주고, 

위젯 빌드 함수를 오버라이드 해서 빌드함수를 리턴할때,   
container()가 아니라, 아까 가져온 패키지, materialapp(매터리얼앱)으로 반환할 것이기 때문에, 컨테이너 대신에 메터리얼앱으로 바꿔준다.

그리고 메터리얼앱의 괄호안에 실제 앱의 내용을 넣어주면 되는 것이다.

```dart
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
```
그리고 MaterialApp의 괄호안에 요소를 넣어준다. title(제목)으로 :(클론)뒤에 문자열로 제목을 넣고,  
theme(테마)로 :(클론)뒤에 ThemeData()를 넣고, ThemeData() 괄호 안에 primarySwatch(기본적인 견본?): Colors.(색상) 으로 테마의 기본 색상을 지정할 수 있다. (나중에 앱바나 그런 것들의 기본색상이 여기서의 색상으로 된다.)

home: 으로 이제 새 위젯을 불러올 수 있다.
> home: 클래스이름(키: 값)

과 같은 형식인데, 여기선 MyHomePage() 란 위젯을 만들어줄 꺼다. title로 'Hi Flutter Home Page'를 지정해 주면서,

```dart
class  extends StatefulWidget {
  @override
  _State createState() => _State();
}

class _State extends State<> {
  @override
  Widget build(BuildContext context) {
    return Container(
      
    );
  }
}
```
MyHomePage() 는 stateFul로 만들어 줄껀데, 마찬가지로 ste 를 치면 나오는 steful 자동완성 기능을 이용해서 이렇게 한번에 만들어 줄 수 있다. 

그리고 클래스이름으로 아까의 MyHomePage 를 작성해 준다. 다중 커서 기능으로, 클래스 이름을 한번만 적어줘도, 필요한 데에 같이 이름이 적혀서 편리하다. ㅎㅎ

위의 코드 구조를 보면, 첫번째 클래스에서 state가 생성될때 호출되는 createState() 함수로 아래 클래스를 연결하는 형식이다. 그리고 아래 클래스에서 stateless 처럼 build 함수를 오버라이드 해서, 그 함수의 리턴값에 앱의 직접적인 내용이 들어간다.

```dart
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
    );
  }
}
```

이렇게 클래스이름으로 MyHomePage 를 적어주고, 아까 MyHomePage를 home: 에서 호출하면서 title: 'Hi Flutter Home Page' 라고 괄호안에 값을 넘겨줬는데,

여기서 그 값을 받을 수 있게, MyHomePage({Key key, this.title})로 key라는 이름의 Key와, (묘하게 말장난 같다;;) this.title 로, super(key : key) 와 같이 해서 넘겨준 값을 받을 수 있다.

근데 여기서 this.title 은 현재 클래스의 title 속성을 말하는 건데, 이렇게만 해주면 없다.. 그래서 final String title; 같이 해서 속성을 생성해줘야 된다.  
(final은 상수, 변하지 않는 값이란 선언이고, String은 문자열 자료형이란 뜻이고, title 은 이름이다.)

이제 아래 클래스로 넘어가서 직접적인 앱의 구성을 짜주자. return으로 컨테이너가 되있는데 Scaffold으로 바꿔주자. <a href="#link1"><sup>1</sup></a>


 ---

 <a name="link1">1 : scaffold 와 container 에 대해서 설명하려니까 길어져서 2#.md 에서 모아서 정리했다. 이말고도 다른 2.md 에서 보충하지 못한 설명들을 담았으니까 참고.