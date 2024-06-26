# Props VS State
> Props와 State 이라는 두 개의 데이터 모델이 존재한다.<br>
> 이 두 데이터 모델의 성격은 매우 다르다.
>

### Props
`Props`는 **함수를 통해 전달되는 인자**와 유사하다.<br>
- 부모 컴포넌트로부터 자식 컴포넌트로 데이터를 넘긴다. (State를 넘기는 경우가 많다.)
- ex) `color` Props를 자식 컴포넌트로 전달하여 원하는 형태로 커스터마이징

### State
`State`는 컴포넌트의 **메모리**와 유사하다.
- 주로 부모 컴포넌트에 저장된다.
- 컴포넌트가 정보를 추적할 수 있게 하는 저장 장소이다.
- 변화하며 상호작용을 만들어낸다.

#### 어떤 내용을 State로 관리하는가?
- 시간이 지나도 변하지 않나요? 그러면 확실히 state가 아닙니다.
- 부모로부터 props를 통해 전달됩니까? 그러면 확실히 state가 아닙니다.
- 컴포넌트 안의 다른 state나 props를 가지고 계산 가능한가요? 그렇다면 절대로 
state가 아닙니다!

그 외에는 State 일 것이다.

### 결론
`Props` 와 `State`는 서로 다르지만 함께 동작한다.<br>


---


##### References
- [Thinking in React](https://ko.react.dev/learn/thinking-in-react)