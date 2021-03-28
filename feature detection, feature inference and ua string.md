# 기능 탐지 (Feature Detection)
`기능 탐지`란, 브라우저에서 어떤 기능을 포함한 코드 블럭을 사용할 수 있는지 확인하는 것, 그리고 지원 여부에 따라 다른 코드를 실행하여 오류 발생 없는, 일관적인 사용자 경험을 제공하는 것을 포함한다.   
`기능 탐지` 예시
```
if ("geolocation" in navigator) {
  // navigator.geolocation(내비게이터에서 지리적 위치 모듈)을 사용할 수 있을 때 실행할 코드
} else {
  // 지리상 위치 모듈을 사용할 수 없을 때 실행할 코드 (핸들링)
}
```

# 기능 추론 (Feature Inference)
`기능 추론`이란, 기능 탐지처럼 기능을 확인하지만, 그 기능을 사용하지 않고 다른 기능을 사용한다. 탐지된 기능이 있으면 관련된 다른 기능도 있을 것이라 추정하는 것이다.   
`기능 추론` 예시
```
if (document.getElementsByTagName) {
  element = document.getElementById(id)
}
```
위의 코드에서, `document`가 `getElementsByTagName`이라는 기능을 가지고 있을 때, 해당 기능 사용하진 않고, `document`가 제공하는 다른 관련 기능인 `getElementById`를 사용하겠다는 의미이다.   
그러나 기능 추론은 권장되지 않는다. 기능 탐지가 더욱 확실한 방법.

# UA 문자열 (User Agent String)
브라우저가 제공하는 문자열이다. `UA`를 통해 네트워크 프로토콜이 리퀘스트하는 대상의 애플리케이션 타입, 운영체제, 소프트웨어 벤더(vendor), 소프트웨어 버전을 확인할 수 있다. 브라우저에서, `navigator.userAgent`로 가져올 수 있다.   
하지만 UA 문자열은 파싱하기가 상당히 까다롭고, 잘못된 정보도 포함하고 있을 수도 있다. 아래의 사례를 보자.
```
"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Safari/537.36"
```
위의 코드는 macOS에서 실행한 Chrome 브라우저의 UA 문자열인데, `Chrome`과 `Safari`를 모두 포함하고 있다. 따라서, 위와 같은 문자열로 브라우저가 Safari임을 확인할 때, `Chrome`이 없으며 `Safari`가 있는지 확인해야만 한다.   
   
출처: [프론트엔드 면접 핸드북 1](https://blog.rhostem.com/posts/2020-04-12-fe-interview-handbook-js-1)