TDD 기반 프로젝트 진행 중
```
import org.koin.androidx.viewmodel.ext.android.viewModel
```
구문이 import 되지 않는 오류가 발생했다. 곧바로 구글링을 했고 해결할 수 있었는데,  
https://stackoverflow.com/questions/60830215/by-viewmodels-kotlin-property-delegate-unresolved-reference  
링크에서 제시한 해결방안은,  

```
implementation "androidx.activity:activity-ktx:$activity_version"
```
을 build.gradle에 추가하여 해결할 수 있었다. 이유를 알고 싶었지만 찾지는 못하였다.  
다만, 해당 링크에 달린 해결 방안들이 모두 의존성을 수정하는 것을 보니 버전 상의 오류가 아닌가 싶다.  
비교적 빠르게 해결할 수 있어서 다행이었다.
