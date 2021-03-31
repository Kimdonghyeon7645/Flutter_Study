# 3-1 - flutter 앱을 웹으로 빌드

사실 Flutter 로, 데스크탑(PC)의 .exe 파일을 만들수도 있고, 웹 어플리케이션도 가능하다고 한다.

이번 장에서는 웹 애플리케이션으로 포팅해보는 작업을 해볼 것이다.  
지난시간에 만들었던 앱을 이용해서다.  
(이것에 대해서는 플러터 공식 사이트를 보고 참조하는 것이 좋다. 영상 강의를 찍은 후에 방식이 변했을지도 모르니까다.)

- 강의영상 : https://flutter.dev/docs/get-started/web
- 참고한 플러터 문서 : https://flutter.dev/docs/get-started/web

---

맨처음 우선은, 만들었던 앱 폴더로 가준다. (여기서는 hi_flutter) 그리고 그곳에서 터미널을 켜서 명령어를 입력해주자.  
(사실 굳이 앱 폴더안에서 꼭 명령어를 칠 필요 없는데, 중간에 명령어를 치고나서 앱 폴더 안으로 이동해줘야 되기 때문에, 귀찮으니 맨처음부터 여기서 명령어를 치자.)  
(걍 cd (앱폴더)로 폴더를 이동하면 된다.)

```
flutter channel beta
```
명령어를 쳐주자. 그리고 프롬프트가 다시 떴으면,
```
flutter upgrade
```
를 입력해주자. 그러면 로딩이 엄청 걸릴것이다. 참고 꾹 기다려주자. (중간에 갑자기 터미널이 닫혀서 당황했는데, ```flutter channel beta```명령어를 치고 기다려주다가, ```flutter upgrade```명령어를 치니 해결됬다.)

이렇게 성공적으로 다운로드가 끝났다면,  
```
flutter config --enable-web
```
를 입력해주자. 금방 설정이 완료됬다 뜰 텐데,  
이제 
```
flutter devices
```
명령어를 입력하면,

    2 connected device:

    Web Server • web-server • web-javascript • Flutter Tools
    Chrome     • chrome     • web-javascript • Google Chrome 81.0.4044.129

라고 출력된다면, 문제없이 진행되고 있는 것이다.

그러면 이제,
```
flutter create .
```
으로 입력후에,
```
flutter run -d chrome
```
으로 명령을 입력해주면,

크롬 창이 뜨고, 조금 기다리고 나서야 안드로이드 애플리케이션으로 만들었던 화면이 크롬 웹으로도 보여지는 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/48408417/82753537-5c5d5d80-9e01-11ea-8d41-7e386ed35132.png)
위와 같은 창이 뜰 것이다.  
위젯의 버튼을 클릭해보면, 위젯도 잘 동작하는 것을 볼 수 있다.

이렇게 모바일 어플리케이션을 웹 어플리케이션으로 동작시키는데에 성공한 것이다.

## 빌드

```
flutter build web
```
이렇게 하면 빌드도 할 수 있다고 한다. 참고하자. 그리고 항상 flutter dev 문서를 꼭 참고하고 참고하자.