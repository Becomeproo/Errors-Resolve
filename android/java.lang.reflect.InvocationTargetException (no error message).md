# java.lang.reflect.InvocationTargetException (no error message)
배웠던 내용을 복습하던 중 이전과 비슷하지만 다른 오류가 발생했다.

이것은, <br>
>Execution failed for task ':app:kaptDebugKotlin'.
>> A failure occurred while executing org.jetbrains.kotlin.gradle.internal.KaptExecution
>>> java.lang.reflect.InvocationTargetException (no error message)

내용의 오류였는데 이전과 같은 오류라 생각하여

https://github.com/Becomeproo/Errors-Resolve/blob/master/android/A%20failure%20occurred%20while%20executing%20org.jetbrains.kotlin.gradle.internal.KaptExecution.md

링크의 해결 과정을 진행하였으나 여전히 오류가 발생했고 이번에는 구글링을 해도 만족스러운 결과를 얻을 수 없었다. <br>
그래서 분명 아무 문제 없던 부분이었기 때문에 실행됐던 파일과 비교해본 결과...
```
@PrimaryKey val isbn: String?,
```
데이터 클래스의 PrimaryKey 값을 Nullable로 선언해 두었다.. <br>
앞으로 조심해서 작성하도록 해야겠다.
