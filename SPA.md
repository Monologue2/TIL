# SPA(Single Page Application)
> 웹 개발에서 사용하는 애플리케이션 디자인 방식 중 하나이다.<br>
사용자 경험을 향상시키기 위해 단일 HTML 페이지로 애플리케이션 전체를 로드하고,<br> 필요한 추가 리소스를 비동기적으로 로드하여 사용자와의 상호작용에 응답한다.
>
---
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



##### References
- [How To Serve a Single-Page Application Using Go](https://betterprogramming.pub/how-to-serve-a-single-page-application-using-go-4b9a38d92987)
- [SPA란 무엇인가](https://www.startupcode.kr/company/blog/archives/11)