# Robot.txt 설정
> 사이트 및 웹사이트를 수집할 수 있도록 허용하거나 제한하는 국제 권고안이다. <br>
> IETF에서 2022년 2월에 표준화 문서를 발행했다

robots.txt 파일은 항상 사이트의 루트 디렉터리에 위치해야 하며 로봇 배제 표준을 따르는 일반 텍스트 파일로 작성된다.

별도의 웹 마스터와의 수집 조건 대한 협약이 있는 경우나, 광고주 정보 취득, 링크 미리보기 생성 등 특수 용도의 로봇은 robot.txt 내의 규칙을 따르지 않거나 완벽하게 준수하지 않을 수 있다.

개인 정보를 포함하여 외부에 노출되면 안되는 콘텐츠는 robot.txt 설정 외 로그인 기능과 다른 방법을 통하여 보호하거나 다른 차단 방법을 사용해야한다.

### 위치
- 사이트의 루트 디렉터리에 위치한다.
- txt(text/plain)으로 접근 할 수 있어야한다.

### HTTP 응답 코드에 따른 처리 
- 2xx : robot.txt 규칙 해석 후 사용
- 3xx, 4xx : 5회 이상의 HTTP redirect 이후 모두 허용으로 해석
- 5xx : 모두 허용하지 않음

### 규칙 예제
- 같은 호스트, 프로토콜 및 포트 번호 하위 페이지에서만 유효하다.
    - `http.//www.example.com/robot.txt` 의 내용은 `http://example.com/` 와 `https:///example.com/` 에 적용되지 않는다.
- API 서버와 Front 서버가 분리된 경우에는?

- User-agent : 어떤 검색엔진 로봇에 대해 수집을 허용할지, `*` 은 모두 허용, `Yeti`는 네이버
    ``` plaintext
    User-agent: *
    Disallow: /
    User-agent: Yeti
    Allow: /
    ```
- Allow, Disallow : 수집 여부를 정한다.<br>
    모두 허용
    ``` plaintext
    User-agent: *
    Allow: /
    ```
    Root 페이지만 수집 허용
    ``` plaintext
    User-agent: *
    Disallow: /
    Allow: /$
    ```
    모든 사이트 데이터 수집 비허용
    ``` plaintext
    User-agent: *
    Disallow: /
    ```
    `/private-image`, `/private-video` 등을 수집 비허용
    ``` plaintext
    User-agent: Yeti
    Disallow: /private*/
    ```
### 유의 사항 및 팁
- [JavaScript 및 Css 수집 허용](https://searchadvisor.naver.com/guide/seo-advanced-javascript)
- [favicon 수집 허용](https://searchadvisor.naver.com/guide/markup-favicon)
- [sitemap.xml 지정](https://searchadvisor.naver.com/guide/request-feed)
- 웹 마스터 도구를 사용하여 Robot.txt의 수집 여부를 확인하기


##### References
- [Robots Exclusion Protocol](https://www.rfc-editor.org/rfc/rfc9309)
- [Naver robots.txt 설정하기](https://searchadvisor.naver.com/guide/seo-basic-robots)