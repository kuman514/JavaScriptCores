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

> `익명 함수`는 `IIFE(Immediately Invoked Function Expression)`와 `callback`에 쓰인다.

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

> `AJAX(Asynchronus JavaScript And XML)`는 비동기적인 통신을 통해 표시 중인 화면을 새로고침하지 않고 동적으로 컨텐츠를 바꾸는 웹 기술이다. 최근에는 `XML`보다 `JSON`을 통해 데이터를 가져온다.

> `AJAX`의 장점: 새로고침 없는 동적인 컨텐츠, 한 번만 가져와도 되는 스크립트/스타일시트, 초기화되지 않는 페이지 상태, 서버와 클라이언트 사이의 명확한 역할 구분 등등   
`AJAX`의 단점: 어려워진 북마크, JavaScript 불허 페이지에서는 미작동, JavaScript를 사용하지 않는 웹 크롤러와의 낮은 호환성, 접속이 느리거나 스펙이 낮은 기기에서의 동작이 어려움 등등

> `JSONP(JSON with Padding)`는 다른 도메인에 있는 서버에서 클라이언트의 전역 함수를 호출함으로써 동작한다. 하지만, `JSONP`는 해킹으로 간주되니, `CORS(Cross-Origin Resource Sharing)`를 이용한 구현이 더 권장된다.

> `Templating`은 `React의 JSX`나 `Vue의 {{ ... }}` 또는 `ES6 템플릿 리터럴` 등등에 쓰인다.

> `호이스팅`은 변수와 함수를 선언부 위에서도 참조할 수 있게 해주는, JavaScript의 특징이다.   
변수를 그 선언부 위에서 참조할 경우, `var`는 `undefined`, `let`과 `const`는 에러가 발생한다. 그리고, 함수는 선언부 `function 함수명 (...) {...}`만 호이스팅되며, 함수 표현식 `변수 = function (...) {...}`나 `변수 = (...) => {...}`는 호이스팅되지 않는다.

> `이벤트 버블링`이란, 어떤 한 엘리먼트에서 발생한 이벤트가 최상위 엘리먼트에 다다를 때까지, 지나간 상위 엘리먼트마다 해당 이벤트 핸들러를 호출시키는 현상을 말한다.

> `attribute`는 HTML 태그에 정의된 속성으로, `DOM property`의 일부이다.

> `JavaScript 내장 객체`를 확장하는 것은, `polyfill` 작성을 제외하고, 권장되지 않는다. 내장 객체를 확장해놓은 서로 다른 라이브러리를 통합시킬 때, 충돌이 발생할 수 있기 때문이다.

> `document`의 `load` 이벤트와 `DOMContentLoaded`의 차이점   
`window.onload`: DOM과 페이지를 포함한 모든 리소스가 완전히 로딩될 때 이벤트를 발생시킨다.   
`DOMContentLoaded`: 페이지가 로딩되고 파싱되면 스타일시트, 이미지, 서브프레임의 완전 로딩을 기다리지 않고 이벤트를 발생시킨다.

> `==`와 `===`의 차이점   
`==`: 느슨한 등가 연산자. 필요하면 타입을 변환시켜 등가 비교할 수도 있다.   
`===`: 엄격한 등가 연산자. 타입 변환 없이 있는 값 그대로 등가 비교한다. JavaScript에서 이 연산자가 `==`보다 권장된다.

> JavaScript의 `동일 출처 정책(Same-origin Policy)`은 다른 도메인의 스크립트를 통한 해킹을 방지하며, `출처(origin)`는 `프로토콜`, `호스트명`, `포트 번호`로 이루어진다. 즉, 동일 출처 정책은 `프로토콜`과 `호스트명`과 `포트 번호`(명시한 경우)이 모두 동일해야 리퀘스트를 사용할 수 있다는 정책이다.

> `duplicate(array); // array: [1,2,3,4,5] -> result: [1,2,3,4,5,1,2,3,4,5]` 구현 방법   
`...`(ES6 spread): `function duplicate (array) { return [...array, ...array]; }`   
`Array.prototype.concat()`: `function duplicate (array) { return array.concat(array); }`

> `Ternary 연산자`는 말 그대로 3개의 항(operand)을 가진, 삼항 연산자이다.   
삼항 연산자는 `(논리식) ? (true일 때의 표현식) : (false일 때의 표현식)`으로 이루어진다.

> `'use strict'`는 해당 스코프에서 `엄격 모드(Strict Mode)`를 적용하겠다는 의미이다. 오류 방지를 위해, 일부 기능을 제한하는 모드이므로, 사용이 권장된다.   
적용 방법: 전역 스코프(전체 스크립트) 또는 함수 내 스코프(해당 함수에만)에서 `'use strict'` 입력, 모듈에서는 기본적으로 엄격 모드.   
장점: 의도되지 않은 전역변수 선언 방지, 삭제 불가 속성 삭제 방지, 함수 파라미터명 중복 방지, 전역 스코프의 `this`가 `undefined`, 그 외에도 일반적인 코딩 실수 방지 등등.    
단점: 필요한 기능을 못 쓸 수도 있음, 서로 다른 엄격 모드로 작성된 스크립트와 결합 시 오류가 발생할 수 있음, `function.caller`와 `function.arguments`에 접근할 수 없음.

> 변수와 함수 이름의 충돌을 방지하려면, 웹사이트의 전역 스코프를 건드리지 않는 것이 좋다.

> `SPA(Single Page Application)`이란, 클라이언트 사이드에서 렌더링하는 웹사이트(웹앱)를 말한다. 장단점은 `AJAX`와 거의 유사하다.

> `Promise`: 지금 당장이 아닌 나중에, 비동기적으로 값을 리턴할 수 있는 객체. `Resolved`된 값이나 `Reject`된 이유를 알 수 있고, `fulfilled`/`rejected`/`pending`으로 3가지 상태가 있으며, `fulfilled`/`rejected`됐을 때의 콜백을 전달할 수 있다.   
`Polyfill`: 브라우저에서 지원하지 않는 기능을 제공하기 위해 개발자가 구현한 코드 조각이나 플러그인. ES6에선 더이상 필요하지 않다.

> `callback` 대신 `Promise`를 사용할 때의 장단점   
장점: 가독성 향상, `.then()`을 통한 순차적 비동기 작업, `Promise.all()`을 통한 쉬운 병렬 처리, `callback`의 잘못된 실행이나 숨은 에러/예외 방지.   
단점: `Promise`를 지원하지 않는 브라우저에 대한 `polyfill` 작성 필요, 조금 더 복잡해지는 코드.

> JavaScript로 컴파일되는 언어: `TypeScript`, `CoffeeScript`, `Elm`, `PureScript`.   
이들의 장점: JavaScript가 가진 오랜 문제점과 잘못된 사용(안티 패턴/전역 스코프 사용/부적절한 truthy/falsy 값 확인 등등)을 방지, 간결한 코드와 편리한 문법 사용, (`TypeScript` 한정) 정적 타입 지원.   
이들의 단점: 항상 표준보다 뒤쳐져있음, 라이브러리/튜토리얼/리소스/툴의 양이 관련 커뮤니티의 규모에 의존, IDE/editor 지원이 빈약할 수 있음 등등.

> JavaScript 디버깅 툴: `Google Chrome 개발자 도구`, `React Dev Tool`, JavaScript 코드에 `debugger`문 삽입, `console.log()`, `Redux DevTools` 등등