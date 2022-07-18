프로젝트 진행 중 상수를 추가하기 위해 app.gradle에 추가한 뒤 sync를 진행했음에도 BuildConfig.java 파일에 상수가 추가되지 않는 현상이 발생했다.  
혹시 잘못 입력하지 않았는지 몇 번이고 확인을 했으나 여전히 생성되지 않았다. (다행히 해당 파일에 직접 작성하는 짓은 하지 않았다..)  
<br>
해결 방법은 https://stackoverflow.com/questions/22604627/gradle-buildconfigfield-buildconfig-cannot-resolve-symbol  
이곳에서 찾을 수 있었는데, 여러 해결 방법을 시도한 끝에 겨우 해결할 수 있었다.

시도해본 해결 방법들은 다음과 같다.  
1. File 탭에서 > "Sync Project with Gradle Files"  
2. File 탭에서 > Invalidate Caches / Restart...  
3. buildConfigField "...", "...", "..." 형식을 buildConfigField ("...", "...", "...")로 변경 (이건 딱 봐도 안될 것 같았지만 혹시 모르니..)  
4. 구문 추가
``` 
android {
    buildFeatures {
        buildConfig = true
    }
}  
```
위처럼 제시되 방법들을 모두 시도했지만 되지 않았고, 나의 상황은 아래 방법을 통해 해결할 수 있었다.
1. Build -> Clean Project;
2. File -> Invalidate Caches / Restart...
3. Build -> Rebuild Project

이 오류로 인해 소중한 두 시간이 사라졌지만 해결됐음에 대단히 만족한다.  
다시 한 번 오류가 있을 때에는 구글링만한 것이 없다는 것을 느낄 수 있었다.
