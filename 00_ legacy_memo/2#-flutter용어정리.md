# 2# - flutter 용어정리 
## 2 - flutter 로 처음 앱 만들기 (카운팅 앱) 보충 설명

사실 2.md 에서 앱을 만드면서, 선 구현, 후 이해 같은 형식이라, 세세한 내용(레이아웃 종류, 구조, 문법)은 다은 섹션에서 공부할 예정입니다.

##### 여기서는 0.md 파일에 이어서 플러터에 대한 기본 설명과 state, widget 같은 용어에 대해 설명합니다.

## Flutter 와 위젯

플러터 앱안에 있는 모든 것들은 다 **위젯(widget)** 이다. 텍스트부터 버튼, 스크린 레이아웃까지 모두 말이다.

이런 위젯들은 스크린에서 보여질 때 계층 순서를 가지고 배열된다. 

그리고 위젯들을 내부에 가지고 있을 수 있는 위젯을 **container 위젯** (위젯 컨테이너라고도 함)이라고 한다.  
(마치 html에서 태그안에 태그가 들어가듯, 플러터에서 container 위젯안에 다른 위젯들이 들어갈 수 있다.)

위젯은 트리구조로 구성되며,    
- 위젯들을 내부에 포함하고 있는 위젯(부모위젯)을 **container 위젯**, **상위위젯** 이라 하며,    
- 상위위젯에 포함된 위젯(자녀위젯)을 **하위위젯** 이라고 한다.

## 위젯의 타입, Stateless, Statefull

위젯은 두가지 타입이 있는데,

- 동적으로, setState() 함수가 호출되면 자동으로 화면에 위젯이 다시 그려지는, **Statefull 위젯**  
- 정적으로, 화면에 위젯을 다시 그리려면, 수동으로 화면을 리로드 해야되는, **Stateless 위젯** 

이 있다.

stateless 는 로드/빌드될 때에 한번 그려져서 이벤트와 사용자 동작으로 다시 그려지지 않기에, 성능이 좋고,

statefull 은 위젯이 살아있는 한, 내부의 데이터들을 다루기에, 성능은 좋지 않아도, 데이터값이 이벤트, 사용자 동작으로 변화하는 위젯을 그릴수 있다.

## State

statefull 위젯, stateless 위젯 에서 위젯은 알겠는데, state는 뭘까?  
statefull에서 위젯안에서 내부 데이터를 다룰 수 있었는데, 이 데이터는 위젯이 살아있는 한 동적으로 변할 수 있다.   
이러한 데이터들의 집합을 State 라고 하는 것이다.

그래서 statefull 은 내부에 state를 가지고 있기에(state가 full(차있기)하기에) state 'full' 이고,

stateless 는 state 가 없어서(state가 less(안차있기)하기에) state 'less' 다.

이런 state는 statefull 위젯의 인스턴스(위젯은 클래스로 만들고, 인스턴스로 위젯을 생성한다.)의 행동을 담당한다.  
위젯의 동작과, 레이아웃을 위한 정보를 가지고 있고, 이 state 가 변경되면, 자동으로 위젯은 리빌드 된다.

## Scaffold
build 함수의 return 값으로 container와 scaffold 등이 들어가는데, 얘 정체는 뭘까?

부르기는 스캐폴드, 발판이란 뜻을 가진 단어인데, 

- 최상단의 앱바(AppBar, 맨위에 있는 영역), 
- 중간영역(Body, 가운데 영역), 
- 최하단의 버튼(BottomNavigationBar, 네비게이션 버튼으로 맨아래에 있는 버튼영역), 
- 창위에 떠있는 버튼(FloatingActionButtonLocation, 내용들위에 떠있는 버튼영역) 

같은 것을 지원해주는 클래스다.
그니까 scaffold 클래스안에서 위같은 것들을 사용할 수 있는 것이다. 

## 참고 

https://medium.com/@dan_kim/%EB%B2%88%EC%97%AD-flutter-%EC%9C%84%EC%A0%AF-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0-1a22231d25c6

https://paulaner80.tistory.com/entry/Widget-State-BuildContext-%EA%B7%B8%EB%A6%AC%EA%B3%A0-InheritedWidget  
(여기서 기본 문법 말고도 다른 용어나 설명이 나와있으니, 나중에도 참고하자.)

https://dalgonakit.tistory.com/103
(scaffold 에대해 쉽게 설명해줘서 고마웠다. 다음에도 북마크해두고 자주 참고하자.)