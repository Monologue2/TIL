# Layout
> Flex, Grid Css layout
>

웹 페이지의 레이아웃을 구성하는 방법은 크게 두가지가 있다.
- 큰 단위에서 작은 단위
- Grid Cell을 나누고 범위를 할당

---
### Flex + Grid, 큰 단위에서 작은 단위로
> 가장 큰 요소부터 하위 요소를 점진적으로 나누는 방식

Body를 Header, Main, Footer의 영역으로 나누고, Main을 다시 각 구역으로, 각 구역을 세부구역으로 나눕니다.<br>

- index.html - main : 각 구획의 역할에 따라 section, article을 활용할 시 +
    ``` html
    <main>
        <div class="box-container">
            <div class="box-item">1</div>
            <div class="box-item">2</div>
            <div class="box-item">3</div>
            <div class="box-item">4</div>
            <div class="box-item">5</div>
            <div class="box-item">6</div>
            <div class="box-item">7</div>
            <div class="box-item">8</div>
        </div>
    </main>
    ```
- index.css
    ``` css
    main {
        background: #f2f4f7;
        min-height: 700px;
    }

    /* 박스 컨테이너, 외부 레이아웃과 내부 자식 요소의 위치를 설정한다 */
    .box-container {
        width : 1080px;
        margin : auto; 
        /* Grid Layout 모듈 활성화, align-items, justify-items, align-content, justify-content 로 정렬 가능 */
        display: grid;
        /* 각 행의 길이 */
        grid-template-columns: 740px 330px;
        /* 각 열 가로줄 길이 */
        grid-template-rows: 120px 310px 890px 130px; 
        /* 자식 요소 간 간격 */
        gap: 10px
    }

    /* 박스 컨테이너의 자식 요소인 박스 아이템 */
    .box-item {
        background-color: skyblue;
        width: 100%;
        height: 100%;
        /* 폰트 사이즈 */
        font-size: 40px;
        /* 테두리 */
        border: 1px solid #dee3eb;
        /* 내부 문자 정렬 */
        text-align: center
    }
    ```

##### References
- [기본적인 페이지 레이아웃(layout) 잡기](https://codingbroker.tistory.com/117)