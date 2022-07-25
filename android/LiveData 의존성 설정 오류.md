TDD를 적용한 개발 연습 중 오류가 발생했다.
> Method getMainLooper in android.os.Looper not mocked. See http://g.co/androidstudio/not-mocked for details.
java.lang.RuntimeException: Method getMainLooper in android.os.Looper not mocked. See http://g.co/androidstudio/not-mocked for details.

과 같은 오류가 발생하였는데, 우선적으로 코드 중 어딘가 잘못 작성되었을 것이라 생각하여 다시 한 번 코드를 검토했다.(이러지 말았어야 했다..)
2시간 정도를 검토에 검토를 반복했음에도 아무런 이상이 없어 마침내 구글링을 하고 나서야 해결할 수 있었다.  
https://potato-idiot.tistory.com/entry/AndroidKotlin-Live-Data-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%98%A4%EB%A5%98-Method-getMainLooper-in-androidosLooper-not-mocked
이 곳에서 오류를 해결할 수 있었는데, 저 글의 작성자 또한 나와 같은 연습 중 같은 오류가 났음을 알 수 있었다.
작성자분 덕에 해결할 수 있었던 오류의 원인은 인용을 하자면
>  JUnit4 환경에서 라이브 데이터를 테스트하기 위해 필요한 것보다 전 버전의 디펜던시가 선언되어 있었다. 아래 코드는 프로젝트 생성 시 자동으로 선언되어 있었다.
앱 수준 build.gradle에 다음 코드를 추가해야 한다.
```
dependencies {
	testImplementation 'android.arch.core:core-testing:2.1.0'
}
```
라는 설명 방법과 함께 해결 방법을 기입해 주셨다.  
쉽게 찾을 수 있었는데 2시간 전에 제일 먼저 구글링하지 않은 것을 후회했다.

앞으로 처음보는 내용의 오류가 발생한다면 구글링을 먼저해야겠구나 라는 생각을 하게 되었다.
