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
- 

##### References
- [기본적인 페이지 레이아웃(layout) 잡기](https://codingbroker.tistory.com/117)