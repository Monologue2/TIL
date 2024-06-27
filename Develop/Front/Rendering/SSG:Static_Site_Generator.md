# SSG: Static Site Generator
> 항상 동일한 내용을 보여주는 웹사이트를 만드는데 최적화된 방법.<br>
> 리액트 앱을 미리 HTML로 렌더링 합니다.
>

리액트 앱은 클라이언트에서 렌더링된다. 사용자의 브라우저는 먼저 JavaScript 번들을 다운로드 한 다음 사용자가 컨텐츠를 보기 전에 JavaScript 번들을 실행한다.<br>
이는 꽤 느리다.

SSG는 HTML을 사전 렌더링하여 React 컴포넌트를 HTML 파일로 변환하고 HTML 파일을 클라이언트에 전송하여 많은 처리나 대역폭 사용 없이 사용자에게 빠르게 표시할 수 있다.<br>
이는 SSR 처체 프로세스가 각 사용자 요청에 수행되지 않고 빌드 시간에 수행된다.<br>
즉 SSG는 SSR보다 훨신 더 빠르다.

### SSG의 필요성
- SEO: 검색 엔진 최적화는 크롤러가 페이지를 쉽게 인덱싱 할 수 있도록 하기 때문에 SSG를 수행하는 최고의 이점 중 하나다.
- 속도: 브라우저가 사전에 많은 처리를 하지 않아도 되기 때문에 HTML 페이지를 제공하는게 사용자에게 훨씬 더 빠른 경험을 선사한다. 사전 렌더링을 통해 브라우저는 HTML을 쉽게 가져와 바로 렌더링 할 수 있다.
- CDN을 사용한 캐싱: HTML 페이지를 구축해놓으면 CDN 캐싱이 빛을 본다. 페이지는  사용자에게 더 가까이 저장되므로 훨씬 빠르게 접근할 수 있다. 모든 요청은 서버가 페이지를 렌더링할 때까지 기다릴 필요가 없으며 CDN에서 페이지를 수신하기만 하면 되기 때문에 계산 리소스와 비용을 절약할 수 있다.

### 조건
> "사용자 요청 전에 미리 페이지를 렌더링 할 수 있는가?" 의 여부에 따라 <br>SSG를 사용할 지 말지 결정할 수 있다.<br>

빌드 시 미리 페이지를 렌더링 할 수 있는 한 어떤 프로젝트라도 SSG를 사용할 수 있다.
- 마케팅 웹 사이트
- 블로그 및 문서
- 포트폴리오 웹 사이트


##### References
- [What the heck is SSG?](https://dev.to/anshuman_bhardwaj/what-the-heck-is-ssg-static-site-generation-explained-with-nextjs-5cja)
- [SPA, SSG, SSR](https://www.daleseo.com/spa-ssg-ssr/)