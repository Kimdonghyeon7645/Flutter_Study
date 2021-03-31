# 플러터의 파일 구조 (File Structure)

플러터에선 ```lib``` 폴더에 어플리케이션 핵심 코드를 작성한다.  
이때 ```main.dart``` 외의 코드 파일들은 어떻게 폴더 구조로 정리해야 되지 않을까?  

생긴지 2~3년 된 플러터(Flutter)는 파일 구조를 지키는 게 필수는 아니지만, (프로젝트 생성시 폴더를 만들어 주지도 않는다.)  
개발자들이 자주 쓰는 파일 구조는 있다.

### 정리 * Summary

```lib``` 폴더 안에,  
```models, screens, service, utils, widgets``` 폴더로 파일을 분류해 저장한다. 

- models 폴더 (Collection of data)
    앱 전체에서 사용되는 데이터의 코드를 저장
 
- screens 폴더 (Screen/UI)
    앱에서 보여지는 부분의 코드를 저장

- widgets 폴더 (Widgets/Layouts)
    앱에서 자주 사용되는 위젯의 코드를 저장

- utils 폴더 (Function/logic)
    앱에서 자주 사용되는 기능(ex. 검증, 시간관련 함수, 이미지 캡처, 변환 함수)의 코드를 저장

- service 폴더 (= providers, Interactions outside)
    앱과 외부 인터페이스(ex. API, 파이어베이스)에 관한 코드를 저장

### 참고 * Reference

- [21년2월 작성 * Flutter – File Structure](https://www.geeksforgeeks.org/flutter-file-structure/)
- [20년5월 작성 * Flutter 플러터 파일 구조(디렉터리 구분, 폴더 작명)](https://zucca.tistory.com/101)
