# BottomNavigationView가 XML 화면에서 구현되지 않는 문제

프로젝트를 만들던 중 BottomNavigationView가 동작하지 않는 상황이 발생했다.
복잡할 것 없이 FrameLayout과 그 밑에 BottomNavigationView가 들어간 일반적인 구성이었으나 <br>
com.google.android.material.bottomnavigation.BottomNavigationView의 영역이 잡히지 않았다.

![bottomNavigationView Error](https://user-images.githubusercontent.com/91411447/162207845-5e055b3e-184f-45fb-84d0-86573a4fc882.png)

위 화면과 같이 메뉴가 아이콘을 갖고 있는 3개의 메뉴를 포함했음에도 나오지 않아 구글링을 열심히 해보았고, <br>
https://docs.microsoft.com/en-us/answers/questions/586952/bottomnavigationview-does-not-show-any-icons.html <br>
이 곳에서 답을 찾을 수 있었다. 문제는 머터리얼 라이브러리의 버전 문제였다. 1.5.0 버전에서 1.4.0 버전으로 다운그레이드 시킨 결과, <br>
![bottomNavigationView Resolve](https://user-images.githubusercontent.com/91411447/162208608-8ebe77d3-c026-499d-8255-0b9fe0dec700.png)

정상적으로 화면이 나오는 것을 볼 수 있었다.
