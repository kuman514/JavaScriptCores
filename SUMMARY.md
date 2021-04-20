# 요약 (내용이 틀렸거나 더 나은 내용 발견 시 개선)

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

> 객체의 속성이나 배열의 항목을 순회(iteration)하는 방법   
객체 속성 순회: `for ... in ...`, `Object.keys(obj).forEach(callback)`, `Object.getOwnPropertyNames(obj).forEach(callback)`.   
배열 항목 순회: `for ... in ...`, `for ... of ...`, `Array.prototype.forEach(callback)`, `for [index, el] of array.entries`.

> `가변(mutable)`과 `불변(immutable)`의 차이는 이미 선언된 값의 내용을 변경할 수 있느냐에 따라 나뉜다.   
가변: 원시값(Primitive Value)이 아닌 것, 즉 `객체(Object)`가 일반적으로 가변적이다.   
불변: 대표적으로 `원시값(Primitive Value)`, 즉 `number`, `string`, `boolean`, `symbol`, `null`, `undefined` 등등이 이에 속한다. `Object.freeze()`를 통해 객체를 불변으로 만들 수 있으나, 이는 `얕은 동결(Shallow Freeze)`이므로 객체 안 객체의 내용이 변경될 수 있다. `Immutable.js`를 사용하는 것도 좋다.

> 불변성(immutability) 구현 방법   
`const` 변수: 재할당을 방지할 수 있으나, 객체의 내용이 변할 수 있다.   
`Object.freeze()`: 객체의 내용이 변경되는 것을 방지할 수 있으나, 객체 안의 객체의 내용이 변경될 수 있다. 즉, `얕은 동결`.   
그 외: `Immutable.js` 사용 등등.

> `동기(sync)`와 `비동기(async)`의 차이점   
동기: 한 번에 한 가지를 처리함. 코드의 확실한 순차적 실행이 보장되나, 실행 시간이 긴 코드에 매우 비효율적.   
비동기: 한 번에 여러 가지를 병렬적으로 처리함. 실행 시간이 긴 코드를 UI 멈춤 없이 진행할 수 있다는 장점이 있다.

> `이벤트 루프(Event Loop)`: 싱글 스레드 루프. 콜 스택이 비었는지 확인하고, 태스크 큐에 실행할 작업이 있는지 확인한다. 콜 스택이 비었고 실행할 태스크가 있으면 태스크는 태스크 큐에서 제거되고, 실행을 위해 콜 스택에 추가된다. 이 핻동을 `틱(tick)`이라 부른다.   
`콜 스택(Call Stack)`: 현재 실행 중인 코드의 스택. 자바스크립트 엔진에는 메모리 힙과 콜 스택이 있으며, 코드는 실행될 때 `stack` 형태로 쌓인다.   
`태스크 큐(Task Queue)`: 자바스크립트 엔진 밖에 있는, 비동기적으로 실행된 이벤트 콜백이 보관되는 영역. `queue` 형태로 보관된다.

> ES5 생성자 함수와 ES6 클래스 간에는 부모 객체로부터의 상속을 구현하는 방법에서 큰 차이가 있다.   
`ES5 생성자 함수`: 해당 생성자 함수 내에 `부모생성자함수명.call(this, ...)` 호출.   
`ES6 class`: `class 클래스명 extends 부모클래스명`으로 상속을 명시한 후, `constructor(...)` 내에 `super(...)`만 해주면 된다.

> 화살표 함수 사용법: `(...) => {...}` (단, `(...)`은 파라미터, `{...}`은 함수 실행 내용)   
ES5 이전의 `function`과 화살표 함수의 차이점: 화살표 함수는 더욱 단순하며, `this`를 가리키는 함수 스코프 내의 `this`가 해당 화살표 함수를 호출한 객체에 의해 정해진다.

> `생성자 함수`에서 `메소드` 선언에 `화살표 함수`를 선언하는 것의 장점: 함수 생성 시점에서 결정된 `this`가 변경되지 않으며 항상 같은 객체를 가리키고 있다는 점이다. 이런 점은 특히 `React Component`에서 유용하다.

> `고차 함수`란, `파라미터로 함수`를 받거나 `함수를 리턴`하는 함수이다.

> `구조 분해 할당`이란, 배열이나 객체의 요소를 쪼개 할당시키는 것이다.   
배열 구조 분해 할당 예시: `a`, `b`, `c` -> `let [a, b, c] = [12, 34, 26];`   
객체 구조 분해 할당 예시: `f1`, `f2` -> `let {e1: f1, e2: f2} = {e1: 15, e2: 3};`

> `템플릿 리터럴`이란, 문자열 사이에 변수를 넣을 때 번거롭게 +를 덕지덕지 붙이지 않아도 되며, 개행 표현 시 `\n`을 굳이 쓰지 않아도 되는 문자열이다.

> `curry 함수`: 전달받은 파라미터가 1개 이상일 경우, 함수를 여러 개로 분리하고 연속으로 호출시켜 파라미터를 누적시킨 뒤, 파라미터가 모두 제공되면 실제 함수를 호출하는 패턴이다.   
함수 `currying` 방법: 맨 처음에 1개의 함수를 제공하고, 파라미터를 1개씩 제공하도록 함수를 쪼갠다. 예를 들어, 어떤 함수의 파라미터가 3개라면, 커링된 함수가 총 3번 호출되어야 처음에 제공된 함수가 호출된다.   
`curry 함수`의 장점: 함수형으로 작성된 코드를 더 읽기 쉽고 조합하기 쉽도록 하는데 유용하다.

> spread 문법   
`function spr (arr1, arr2) {return [...arr1, ...arr2];}`   
`function spr (obj1, obj2) {return {...obj1, ...obj2};}`   
배열이나 객체의 구조를 해제하여 원소들을 풀어낸다.   
rest 문법   
`const [a, b, ...other] = [1, 3, 6, 9, 10];`   
`const {a, b, ...other} = {a: 1, b: 3, c: 6, d: 9, e: 10};`   
배열이나 객체에서의 대응되는 원소들을 각 변수로 복사한 뒤, 남은 원소들을 `...rest변수명`에 배열/객체 구조로 담아낸다.

> JavaScript 파일 사이에서 `코드를 공유`하는 방법   
브라우저 환경: 변수와 함수가 전역에 선언되기 때문에 모든 스크립트에서 서로 참조할 수 있다. 또는 `RequireJS`로 `AMD`를 사용해서 모듈화시킬 수 있다.   
서버 환경(Node.js 등등): `CommonJS`의 `module.export`를 사용한다.   
공통: `ES6 모듈 문법`의 `import`문과 `export`문을 사용한다.

> `static 클래스 멤버`를 사용하는 이유: 특정한 객체 인스턴스에 구속되거나 영향을 받지 않고, 어떤 인스턴스에서 참조해도 동일한 값이 나온다. static 클래스 멤버는 주로 설정값이나 순수한 유틸리티 함수로 사용된다.

> `var`: 함수 레벨 (또는 전역) 스코프 / 호이스팅 시 `undefined` / 재선언 가능 / 재할당 가능.   
`let`: 블록 레벨 스코프 / 호이스팅 시 에러 / 재선언 불가 / 재할당 가능.    
`const`: 블록 레벨 스코프 / 호이스팅 시 에러 / 재선언 불가 / 재할당 불가.

> `스코프(scope)`란, 식별자(함수, 변수)를 찾아내기 위한 규칙을 말한다.   
`전역 스코프`: 어떤 함수에도 속하지 않은 스코프, 즉 함수 밖의 스코프.   
`함수 레벨 스코프`: 함수 선언부로 둘러싸인 코드의 범위.   
`블록 레벨 스코프`: 블록으로 둘러싸인 코드의 범위.   
`렉시컬 스코프(Lexical Scope)`: 함수가 어디서 선언되었느냐에 따라 결정되는 스코프.