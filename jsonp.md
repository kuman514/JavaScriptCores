# JSONP는 어떻게 동작하는가?

`JSONP(JSON with Padding)`는 다른 도메인에 있는 서버에서 클라이언트의 전역 함수를 호출함으로써 동작한다.   
   
`JSONP`는 `script` 태그로 리퀘스트를 보내며 보통 쿼리 파라미터에 `callback`을 붙인다.
```
https://example.com?callback=printData
```
서버에서는 데이터를 `callback` 파라미터로 전달된 `printData`라는 함수에 담아서 실행한다.   
```
<!-- https://mydomain.com -->
<script>
  function printData(data) {
    console.log(`My name is ${data.name}!`);
  }
</script>

<script src="https://example.com?callback=printData"></script>
```
```
// File loaded from https://example.com?callback=printData
printData({ name: "user name" });
```
클라이언트에는 `printData`라는 함수가 전역 스코프에 선언되어 있어야 한다. 다른 도메인의 스크립트가 클라이언트에서 실행되면서 클라이언트의 함수를 실행하고, 파라미터까지 전달할 수 있다.   
   
`JSONP` 구현을 위해서는 클라이언트와 서버가 `printData`라는 이름을 가진 함수를 사용할 것이고 어떻게 데이터를 보낼지 사전에 조율되어야 한다.

`JSONP`는 안전하지 않으며 보안에 문제를 야기할 수 있다고 한다. JSONP는 자바스크립트로 작동하기 때문에, 자바스크립트로 할 수 있는 다른 모든 행위를 할 수 있으므로, JSONP를 통해 데이터를 주고받는 상대가 신뢰되어야 한다.   
   
현재에 이르러, `JSONP`는 해킹으로 간주되니, `Cross-Origin Resource Sharing`을 이용한 구현이 더 권장된다.   
[CORS(Cross-Origin Resource Sharing) 둘러보기](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)   
   
출처: [프론트엔드 면접 핸드북 1](https://blog.rhostem.com/posts/2020-04-12-fe-interview-handbook-js-1)