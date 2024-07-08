# Div
> Division : 레이아웃을 만들거나 콘텐츠를 나누는 컨테이너로 사용되는 태그.<br>
>`div` 컨테이너를 통해 레이아웃을 자유롭게 구성하는 방법을 알기 위해 작성
- 대부분의 HTML 태그는 자체적으로 의미가 있지만 `div`는 자체적으로 특별한 의미가 없다.
- `division` 의 줄임말로 사용된다.
- 의미가 있는 태그를 사용할 수 없는 상황에서 `div`를 사용한다.
    - 의미가 있는 태그 : `artivle` , `nav` 등
- `div` 태그에 `role` 속성을 사용하여 구조와 의미를 부여할 수 있다.
- 단순 텍스트나 텍스트에 관련된 MarkUp 등에 스타일이나 속성의 범위를 적용하려면 [`span` 태그를 사용하라.](https://codingeverybody.kr/html-span-%ed%83%9c%ea%b7%b8-%ec%98%ac%eb%b0%94%eb%a5%b8-%ec%9d%b4%ed%95%b4%ec%99%80-%ec%82%ac%ec%9a%a9-%eb%b0%a9%eb%b2%95/) `div` 태그는 적당하지 않다.


### 활용 예제

#### 시각적 스타일을 위한 장식용 컨테이너
`div` 태그로 스타일을 위한 시각적 장식용 컨테이너로 활용한 예제

```html
<div class="container" aria-hidden="true">
    <div class="circle circle-1"></div>
    <div class="circle circle-2"></div>
    <div class="clrcle circle-3"></div>
</div>
```
- `aria-hidden` : 스크린 리더 및 보조 기술을 사용하는 유저 대상, `true`인 경우 해당 요소와 그 안에 포함된 콘텐츠는 접근성 기술을 통해 감지 되지 않는다.
    - SEO 에 노출되지 않는다.
    - 스크린 리더 : 컴퓨터나 모바일 화면의 텍스트를 TTS를 통해 읽어주는 소프트웨어
```css
.container {
    position: relative;
    height: 200px;
}

.circle {
    position: absolute;
    width: 50px;
    height: 50px;
    border-radius: 50%;
}

.circle-1 {
    top:0;
    background-color: red;
}

.circle-2 {
    top: 80px;
    left: 100px;
    background-color:green;
}

.circle-3 {
    bottom: 0;
    left: 50px;
    background-color: blue;
}
```

##### References
- [div 태그의 올바른 이해와 사용 방법](https://codingeverybody.kr/html-div-%ED%83%9C%EA%B7%B8-%EC%98%AC%EB%B0%94%EB%A5%B8-%EC%9D%B4%ED%95%B4%EC%99%80-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95/)