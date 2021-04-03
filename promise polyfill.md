# Promise와 Polyfill은 무엇인가?

`Promise`는 지금 당장이 아닌 나중에 비동기적으로 값을 리턴할 수 있는 객체이다. `Resolve`된 값이나 `Reject`된 사유(예: 네트워크 오류 등등)를 받을 수 있다.   
`Promise`는 `fulfilled`, `rejected`, `pending` 3가지의 중 하나의 상태를 가진다.   
`Promise`를 사용할 때 `fulfilled`, `rejected` 상태로 변경될 때 콜백을 전달 할 수 있다.

`Polyfill`은 특정 기능을 지원하지 않는 브라우저에서 개발자가 해당 기능을 제공하기 위해 구현해놓은 코드 조각이나 플러그인을 말한다.   
대표적인 `Polyfill`은 `jquery $.deferred`, `Q`, `Bluebird`가 있지만 전부 표준 스펙을 만족시키진 못한다.   
   
`ES6`는 `Promise`를 지원하며 `Polyfill`은 더 이상 필요하지 않다.