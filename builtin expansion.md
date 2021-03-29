# JavaScript 내장 객체를 확장시키는 것은 바람직한가?

`JavaScript 내장 객체(Built-in Objects)`를 확장한다는 것은 객체의 `prototype`에 `function`이나 `property`를 추가하는 것을 뜻한다.
예를 들어, `JavaScript 내장 객체` 중 하나인 `Array`의 `prototype`에 `contain`이라는 메소드를 추가했다고 치자.   
   
하지만 이 행위는 매우 위험한 방법이다.
불러온 다른 라이브러리에서도 `Array`의 `prototype`에 `contain` 메소드를 추가했을 경우, 서로 같은 결과가 나오도록 만들지 않은 이상, 어느 한 쪽에는 반드시 문제가 발생할 것이기 때문이다.   
   
내장 객체를 확장해야 하는 경우는 `대체 코드(polyfill)`를 작성해야 할 때 뿐이다.
`인터넷 익스플로러`에서 지원하지 않는 `Array.prototype.includes` 메소드를 사용하려고 할 때, `Array.prototype`에 `includes` 메소드를 붙여야 할 경우 등등이 있다.