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
theme(테마)로 :(클론)뒤에 ThemeData()를 넣고, ThemeData() 괄호 안에 primarySwatch