# 요약

> `이벤트 위임`이란, `이벤트 버블링 현상`을 이용하여 상위 엘리먼트에게 이벤트 핸들링을 부여하는 기법이다.

> `this`가 정해지는 조건은 다음과 같다.   
1: `new Function()`이 가리키는 새로운 객체   
2: `.bind(thisArg)`, `.apply(thisArg, ...)`, `.call(thisArg, ...)`의 `thisArg`   
3: 객체의 멤버 함수(메소드)로써 호출   
4: 단순한 함수로써의 호출 (이때 `this`는 Node.js에선 `global`, 브라우저에선 `window`, Strict Mode에선 `undefined`)   
5: 위에서 중첩되는 조건이 있으면, 먼저 언급된 순서대로 우선순위를 가진다.   
6: ES6의 화살표 함수 `(...) => {...}`는 위의 조건을 모두 무시하고, 함수가 만들어진 시점에서 그 함수를 둘러싼 스코프 내의 `this`로 정한다.

> 모든 JavaScript 객체는 `__proto__`라는 속성을 가지고 있는데, 이는 객체의 원형(prototype)을 가리키는 것이다.   
이 떄, `JavaScript의 프로토타입 상속`은, 어떤 객체에서 한 속성을 찾고자 할 때, 그 속성이 해당 객체에 없을 경우, 그 객체의 `__proto__` 속성에서 해당 속성을 찾을 때까지, `__proto__`를 찾아가는 것을 반복함으로써 동작한다.   
일반적인 상속보다는 위임에 더 가까운 형태.

> `AMD`와 `CommonJS`의 차이점은 비동기이냐 동기이냐의 차이이다. 하지만, `ES6 모듈 시스템`은 저 둘을 대체했다.

> JavaScript에서의 IIFE(Immediately Invoked Function Expression) 사용 방법은 다음과 같다.   
1: `(function (...) {...})(...);`   
2: `void function (...) {...}(...);` (이 경우, return값은 무조건 `undefined`)

> `null`과 `undefined`와 선언되지 않은 변수에는 다음과 같은 차이가 있다.   
`null`: 당분간 사용하지 않을 변수에 임시적으로 할당해두는 명시적인 값.   
`undefined`: 선언은 되었으나, 아직 할당되지 않은 상태.   
선언되지 않은 변수: `let`, `var`, `const` 키워드를 통해 선언되지 않은 변수. 사용하지 말 것.

> 함수 내의 지역 변수는 함수 범위 밖에서는 접근할 수 없으며, 함수 실행이 끝나면 사용할 수 없다. 하지만, JavaScript는 함수를 리턴함으로써 함수 내 지역 변수에 접근할 수 있도록 도와주는데, 이렇게 형성된 함수를 `클로저`라고 부른다. 즉, `클로저`는 접근할 수 없는 영역인, 함수 내 지역 변수에 접근할 수 있는 통로를 제공한다. `클로저`는 데이터 프라이버시 / 모듈 패턴에서 `private` 메소드를 구현하기 위해 쓰인다.

> 배열을 리턴값 없이 단순히 순회하고자 한다면 `Array.prototype.forEach()`를, 각 요소가 맵핑된 새로운 배열을 리턴받고자 한다면 `Array.prototype.map()`을 사용할 것. 물론, 두 함수 모두, 원본 배열이 유지된다.

> `익명 함수`는 IIFE(Immediately Invoked Function Expression)와 callback에 쓰인다.

> 호스트 객체와 네이티브 객체 간 차이는 다음과 같다.   
호스트 객체: JavaScript가 돌아가는 런타임 환경에 따라 제공 여부가 달라지는 객체. (예를 들어, `global`과 `window`)   
네이티브 객체: JavaScript 언어의 일부로써, 환경에 구애받지 않고 어디서나 제공되는 ECMAScript 표준 객체. (예를 들어, `Number`, `Math`, `String`, `RegExp`, `Object`, `Function`)

> `Function()`은 단순히 함수를 호출하는 것이며, `new Function()`은 `Function` 객체의 생성자를 호출하여 `Function` 객체의 새로운 인스턴스를 만드는 것이다.

> `Function.prototype.call`과 `Function.prototype.apply`의 차이점은 다음과 같다.   
`Function.prototype.call`: 콤마(`,`)로 분리된 여러 개의 파라미터를 받는다.   
`Function.prototype.apply`: 파라미터 배열 하나를 받는다.

> `Function.prototype.bind(thisArg)`는 해당 함수 내의 `this`를 `thisArg`로 지정한 새로운 함수를 리턴시키는 함수이다.

> 누군가가 `document.write`를 쓰려고 할 때, `document.createElement`나 `document.createTextNode`나 `Node.appendChild` 등등을 사용하길 적극 권하자.

> `기능 탐지`: 오류 없이 일관적인 사용자 경험 제공을 위해, 어떤 기능이 있으면 그 기능을 사용하고, 없는 경우 별도의 코드로 핸들링하는 방법.   
`기능 추론`: 어떤 기능이 있으면 그 기능과 관련된 다른 기능까지 있을 것으로 추정하여, 해당 타 기능을 사용하는 방법. (권장되지 않는다.)   
`User Agent 문자열`: 브라우저가 제공하는 문자열. 애플리케이션 타입, 운영체제, 소프트웨어 벤더, 소프트웨어 버전 등등을 확인할 수 있다.