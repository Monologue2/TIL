# SPA: Single Page Application
> 서버에서 완전한 페이지를 불러오지 않고, 현재 페이지를 동적으로 다시 작성하여 사용자와 소통하는 웹 애플리케이션 또는 웹 사이트
>

클라이언트의 브라우저에서 Javascript를 이용하여 단일 웹페이지 상의 HTML 요소를 동적으로 생성하고 조작한다.<br>
이러한 접근은 연속된 페이지 간의 사용자 경험의 간섭을 막고, 애플리케이션이 데스크톱 애플리케이션처럼 동작하도록 만든다.<br>
HTML, JavaScript, Css 등 필요한 모든 코드는 하나의 페이지로 불러오거나 필요한 경우 동적으로 문서에 추가한다. 보통 사용자의 동작에 응답하는 방식이다.<br>
문서는 프로세스 중 어떤 지점이라도 다시 불러들이지 않고, 위치 해시, HTML5 히스토리 API를 사용하여 애플리케이션 안에서 개개의 문서를 판별한다.

### 주요 특징
1. 초기 로딩 
    - 단일 HTML 페이지를 로드한 뒤 필요한 JavaScript와 CSS 파일을 비동기적으로 로딩한다.
2. 라우팅(Routing)
    - 페이지가 전환 될 때 전체 페이지를 다시 로드하지 않고, JavaScript를 통해 클라이언트 측에서 URL을 변경한다.
    - 이 때 페이지 리로드 없이 콘텐츠를 업데이트한다.
3. 속도 및 성능
    - 필요한 부분만 업데이트하므로 더 빠르고 유연하다.
4. 상태 관리
    - SPA는 클라이언트 측에서 애플리케이션의 상태를 관리하고, 서버와 통신하여 데이터를 관리한다.
5. 프레임워크
    - SPA를 개발하기 위해 React, Angular, Vue.js 등을 사용한다.
6. SEO(Search Engine Optimization, 검색 엔진 최적화) 관리의 어려움
    - 페이지가 클라이언트 측에서 렌더링되기 때문에 검색 엔진이 모든 콘텐츠를 크롤링하기 어렵다.
    - SSR(Server Side Rendering) 또는 SSG(Static Site Genarating)이 사용된다.

### 강점
- UX가 확실하게 개선된다. 클라이언트가 모든 페이지를 가지고 있으므로 데스크톱 애플리케이션같은 사용자 경험을 제공한다.
- 최초 한 번 JavaScript 코드를 받은 뒤 서버와 네트워크 통신을 할 필요가 없으므로 페이지 별로 끊어지지 않는다.
- 서버 부담이 적다.
- Front와 Back이 비교적 명확히 구분된다.
### 약점
- 지나치게 JavaScript에 의존하여 지원하지 않는 브라우징 환경에서 작동하지 않는다.
- 최초 로딩시 시간이 걸리거나, 컴포넌트의 수가 많을 경우 렌더링에 시간이 오래 걸린다.
- SEO 측면에서 상당히 불리하다.
    - 이는 최초 html에 `meta` 태그로 정보를 추가하여 해결한다.



##### References
- [Single Page Application](https://ko.wikipedia.org/wiki/%EC%8B%B1%EA%B8%80_%ED%8E%98%EC%9D%B4%EC%A7%80_%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98)
- [SPA, SSG, SSR](https://www.daleseo.com/spa-ssg-ssr/)
- [SPA 란?](https://blcan.tistory.com/18)
- [How To Serve a Single-Page Application Using Go](https://betterprogramming.pub/how-to-serve-a-single-page-application-using-go-4b9a38d92987)
- [SPA란 무엇인가](https://www.startupcode.kr/company/blog/archives/11)