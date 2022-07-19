프로젝트 진행 중 오류가 발생했다. 
```
Execution failed for task ':app:kaptDebugKotlin'.  
> A failure occurred while executing org.jetbrains.kotlin.gradle.internal.KaptWithoutKotlincTask$KaptExecutionWorkAction   
> java.lang.reflect.InvocationTargetException (no error message)  
```
라는 내용의 오류였는데 대부분의 해결 방법들은 오류의 이유가 나오지 않고 '코틀린의 버전만 바꾸면 된다' 라는 내용만 있을 뿐이었다.  
물론 해결이 될 것 같다는 생각이 들었으나 뭔가 오류가 난 이유가 있으면 좋겠다고 생각했다. (해결이 된다해도 찝찝한...)  
구글링을 아무리해봐도 마땅히 순응할만한 해결 방법을 찾지 못하던 중,  
https://stackoverflow.com/questions/62131564/a-failure-occurred-while-executing-org-jetbrains-kotlin-gradle-internal-kaptexec  
이 링크의 한 답글이 말하는 바에 의하면 내가 검색한 오류의 내용은 의미가 없는 오류 내용이라하여 의미있는 오류의 내용을 구글링해야한다고 말한다.  
위 말을 수용하여 아래의 내용으로 새롭게 구글링한 결과,
```
error: Not sure how to convert a Cursor to this method's return type (java.lang.Object).
```
https://issuetracker.google.com/issues/236612358  
이 곳에서 그럴듯한 내용의 해결 방법을 찾을 수 있었다.

답변자의 말에 의하면, 
> 문제는 Kotlin의 @Metadata 주석 및 Room이 읽는 방식의 변경과 관련된 것 같다.  
Room 2.4.2는 Kotlin 1.7 정보 읽기를 지원하지 않는 kotlinx-metadata-jvm 라이브러리의 이전 버전을 사용하고 있다.  
Room 2.5.0에서와 같이 라이브러리를 업데이트했다. 이 문제를 해결하려면 주석 프로세서 경로에 종속성을 추가하여 강제로 업그레이드를 해야한다.  
즉, Room 2.4.x를 사용하는 경우 kapt "org.jetbrains.kotlinx:kotlinx-metadata-jvm:0.5.0"을 추가해야한다.  
한편, Room 2.5.x는 아직 개발 중이므로 Kotlin 1.7과 호환되는 Room 2.4.3을 출시하기 위해 노력할 것이다.

라고 한다. 참고로 나의 코틀린 버전은 1.7.10 이고 Room 버전은 2.4.2 이므로 위의 오류 설명의 내용과 일치했다.  
위의 내용을 참고하여 해당 코드를 추가한 결과, 오류가 나지 않은 것을 확인할 수 있었다.  

마냥 오류가 나면 언짢았지만, 이전처럼 오류를 검색했던 방식들은 무대포식이였음을 알 수 있었고 올바른 오류 검색 과정에 따라  
깔끔하게 해결할 수 있어서 의미있는 오류였다고 생각했다.
