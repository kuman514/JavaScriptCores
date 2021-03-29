# 자바스크립트의 same-origin 정책이란 무엇인가?

자바스크립트의 `same-origin 정책`은 다른 도메인의 스크립트를 사용한 해킹을 방지하는 정책이다.   
   
`동일 출처 정책(same-origin policy)`은 자바스크립트가 서로 다른 `도메인` 사이에 `리퀘스트`를 날리는 것을 방지한다. `출처(origin)`는 `프로토콜`, `포트(명시한 경우)`, `호스트 이름`으로 이루어진다. 즉, `동일 출처 정책`은 `프로토콜`과 `호스트 이름` 그리고 `포트 번호`까지 같아야 `리퀘스트`가 성공하는 것이다.   
   
다음 예시는 URL `http://store.company.com/dir/page.html`의 출처를 비교한 표이다.
URL | 결과 | 이유
:-- | :--: | :--
http://store.company.com/dir2/other.html | 성공 | 경로만 다름
http://store.company.com/dir/inner/another.html | 성공 | 경로만 다름
https://store.company.com/secure.html | 실패 | 프로토콜 다름
http://store.company.com:81/dir/etc.html | 실패 | 포트 다름 (http://는 80이 기본값)
http://news.company.com/dir/other.html | 실패 | 호스트 다름
   
   
자료 출처   
[프론트엔드 면접 핸드북 2](https://blog.rhostem.com/posts/2020-04-13-fe-interview-handbook-js-2)   
[MDN Web Docs - 동일 출처 정책](https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy)