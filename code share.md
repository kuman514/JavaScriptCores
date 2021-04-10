# JavaScript 파일 사이에서 코드를 공유하는 방법은?

JavaScript 환경에 따라 다르다.
- 브라우저 환경에서는 변수와 함수가 global scope에 선언되기 때문에, 모든 스크립트에서 서로 참조할 수 있다.
- 또는, RequireJS로 AMD를 사용해서 모듈화시킬 수도 있다.
- Node같은 서버 환경에서는 CommonJS를 사용한다. 각 파일은 모듈로 취급하며, module.export 문법으로 변수와 함수를 내보낼 수 있다.
- ES6에 AMD와 CommonJS를 대체할 수 있는 모듈 문법이 추가되었다. import와 export문을 브라우저와 서버 모두 사용할 수 있다.
   
출처: [프론트엔드 면접 핸드북 3](https://blog.rhostem.com/posts/2020-04-14-fe-interview-handbook-js-3)