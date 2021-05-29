### 참고 

https://stackoverflow.com/questions/54955789/flutter-image-network-not-working-on-release-apk

https://flutter.dev/docs/development/data-and-backend/networking



### 해결

```AndroidManifest.xml``` 파일에 권한 추가

```
<manifest xmlns:android...>
 ...
 <uses-permission android:name="android.permission.INTERNET" />		// 이부분
 <application ...
</manifest>
```

