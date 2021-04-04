# SPA(Single Page Application)은 무엇이며 그 특징은 무엇무엇이 있는가?

SPA(Single Page Application)는...
- 클라이언트 사이드에서 렌더링하는 웹사이트(웹앱)를 말한다.
- 앱이 보다 반응성 있게 느껴진다.
- 웹앱을 로딩할 때, 브라우저는 서버에서 초기 페이지와 함께 앱에 필요한 스크립트(프레임워크, 라이브러리, 앱 코드 등등 포함), 스타일시트를 내려받는다.
- 사용자가 다른 페이지를 이동하고자 할 때 새로고침이 없어, 페이지 깜빡임과 새로고침 딜레이를 볼 필요가 없다.
- 페이지의 URL은 HTML5 History API를 통해 기억된다.
- 새 페이지에 필요한 새 데이터는 브라우저에서 AJAX Request를 통해 서버에서 JSON 포맷으로 가져온다.
- 초기 로딩에서 가져온 자바스크립트를 통해, 데이터와 페이지를 동적으로 갱신한다.
- 스크립트와 스타일시트 등 받아야 할 리소스가 많기 때문에, 초기 페이지 로딩이 더욱 무거워진다.
- 서버에 더 적은 HTTP Request가 간다.
- 서버와 클라이언트 사이의 역할 구분이 명확해지므로, 서버 코드 수정 없이 다른 플랫폼의 새로운 클라이언트를 더욱 쉽게 만들 수 있다.
- 컨텐츠의 렌더링을 자바스크립트에 의존한다. 하지만 모든 검색 엔진이 크롤링 중에 자바스크립트를 실행하지는 않는다. 이것은 검색 엔진 최적화(SEO, Search Engine Optimization)에 장애물이 된다. 하지만 대부분의 경우 앱을 만들 때 SEO는 가장 중요한 요소가 아니다. 그리고 모든 컨텐츠가 검색 엔진에 의해 인덱싱될 필요도 없다. SEO가 필요하다면 서버사이드 렌더링을 사용하거나 Prerender같은 서비스를 사용해 “자바스크립트로 브라우저에서 렌더링하고, HTML을 저장하고, 크롤러에게 제공”하도록 할 수도 있다.
   
출처: [프론트엔드 면접 핸드북 2](https://blog.rhostem.com/posts/2020-04-13-fe-interview-handbook-js-2)