# A failure occurred while executing org.jetbrains.kotlin.gradle.internal.KaptExecution

데이터 바인딩 작업 도중 'A failure occurred while executing org.jetbrains.kotlin.gradle.internal.KaptExecution' 오류가 발생하였고,
구글링 한 결과 의외로 쉽게 해결할 수 있었다.

https://stackoverflow.com/questions/62131564/a-failure-occurred-while-executing-org-jetbrains-kotlin-gradle-internal-kaptexec
이곳에서 해결할 수 있었는데,

[Analyze] -> [Inspect Code] -> 'whole project' 체크 과정을 진행한 결과, 오류가 발생한 부분을 상세히 알려주어 해결할 수 있었다.
나의 경우는 변수명을 잘못 입력했던 것이 원인이었다.
