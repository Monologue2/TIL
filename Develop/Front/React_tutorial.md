# React
> 사용자 인터페이스(UI)를 구축하는 자바스크립트 라이브러리<br>
> 컴포넌트 기반 아키텍쳐를 통해 간단하고 재사용 가능한 UI 개발이 가능하다.
>
#### Requirement
- [Node.js](https://nodejs.org/en)
- npm

### Creating React App
리액트 프로젝트를 쉽게 생성할 수 있는 `Create React App` 을 사용하여 시작한다.
- 프로젝트 생성 후 디렉터리로 이동하기<br>
    ```bash
    # npx create-react-app <project_name>
    $ npx create-react-app my-react-app
    $ cd my-react-app
    ```
- 앱 실행<br>
    ```bash
    $ npm start
    ```
브라우저가 자동으로 열리며 `http://localhost:3000` 에서 앱을 확인 할 수 있다.

---

### React Component
컴포넌트는 재사용 가능한 UI 조각을 의미한다.
- 기본 리액트 컴포넌트<br>
    `src` 디렉터리 내의 `App.js` 파일을 확인하면 기본적인 리액트 컴포넌트를 확인할 수 있다.
- jsx<br>
    html과 유사한 문법으로 JS 코드 내에서 UI를 기술할 수 있다.
    ``` jsx
    import logo from './logo.svg';
    import './App.css';

    function App() {
        return (
            <div className="App">
            <header className="App-header">
                <img src={logo} className="App-logo" alt="logo" />
                <p>
                Edit <code>src/App.js</code> and save to reload.
                </p>
                <a
                className="App-link"
                href="https://reactjs.org"
                target="_blank"
                rel="noopener noreferrer"
                >
                Learn React
                </a>
            </header>
            </div>
        );
    }

    export default App;
    ```
    - `App.js` 파일을 수정해본 뒤 UI 확인하기<br>
        ```jsx
        import React from 'react';

        function App() {
        return (
            <div className="App">
            <header className="App-header">
                <h1>Hello, React!</h1>
            </header>
            </div>
        );
        }

        export default App;
        ```


### 상태와 이벤트 핸들링
리액트 컴포넌트는 State와 event를 관리할 수 있다.<br>
이로서 사용자 상호작용을 처리할 수 있다.
- 상태
    - `useState` Hook 를 사용하여 상태를 관리한다.<br>
    아래 코드는 상태를 사용하여 버튼 클릭 시 카운트를 증가시키는 예제다.<br>
    `상태 변수(count)와 상태를 갱신하는 함수(setCount)를 선언`<br>
    `const [count, setCount] = useState(0);`<br>
- 이벤트 핸들링
    - `onClick`, `onChange` 등의 이벤트 속성을 사용하여 사용자 이벤트를 처리한다.<br>
    - `Butten` 의 `onClick` 속성은 버튼이 클릭될 때마다 `setCount` 함수를 호출하여 Count를 증가시킨다.<br>
    ```jsx
    import React, { useState } from 'react';
    import './App.css';

    function App() {
        // 상태 변수(count)와 상태를 갱신하는 함수(setCount)를 선언
        // onClick, onChange 등의 이벤트 속성으로 사용자 이벤트 처리
        const [count, setCount] = useState(0);
        return (
            <div className="App">
            <header className="App-header">
                <h1>Count: {count}</h1>
                <button onClick={() => setCount(count + 1)}>Increment</button>
            </header>
            </div>
        );
    }

    export default App;
    ```

### 컴포넌트 분리와 재사용
- `src` 디렉터리에 `components` 디렉터리를 생성하고 `Button.js` 컴포넌트 파일을 작성한다.<br>
리액트 컴포넌트는 대문자로 구분된다.<br>
    ``` jsx
    import React from 'react'

    function Button({onclick, children}) {
        return (
            <button onClick={onClick}>
                {children}
            </button>
        );
    }

    export default Button
    ```
- `App.js` 에서 `Button` 컴포넌트 사용하기<br>
    `import Button from './components/Button';`<br>
    `<Button onClick={() => setCount(count + 1)}>Increment</Button>` 
    ```jsx
    import React, { useState } from 'react';
    import Button from './components/Button';

    import './App.css';

    function App() {
    // 상태 변수(count)와 상태를 갱신하는 함수(setCount)를 선언합니다.
    const [count, setCount] = useState(-10);

    return (
        <div className="App">
        <header className="App-header">
            <h1>Count: {count}</h1>
            <Button onClick={() => setCount(count + 1)}>Increment</Button>
        </header>
        </div>
    );
    }

    export default App;
    ```
### Styling
리액트 컴포넌트에 스타일을 추가할 수 있다.<br>

- 기본 CSS<br>
    `src/App.css` 를 수정한다.
    ```css
    .App-header {
        background-color: #282c34;
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-size: calc(10px + 2vmin);
        color: white;
    }

    button {
        font-size: 1rem;
        padding: 0.5em 1em;
        margin-top: 1em;
        cursor: pointer;
    }
    ```
    `App.js` 파일에 `App.css`파일을 Import 하여 스타일을 적용한다.
    ```jsx
    import `./App.css`;
    ```

- 이미지 표현하기<br>
`App.js`
    ```jsx
    import React, { useState } from 'react';
    import './App.css'
    // User 객체 생성
    const user = {
    name: 'Hedy Lamarr',
    imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
    imageSize: 150,
    };

    // 중괄호를 사용하면 Js 코드에서 일부 변수를 삽입할 수 있다.
    export default function Profile() {
    return (
        <>
        <h1>{user.name}</h1>
        <img
            className="avatar"
            src={user.imageUrl}
            alt={'Photo of ' + user.name}
            style={{
            width: user.imageSize,
            height: user.imageSize
            }}
        />
        </>
    );
    }
    ```
    `App.css`
    ```css
    .avatar {
        border-radius: 50%;
    }
    ```


---
##### References
- [LEARN REACT Quick Start](https://react.dev/learn)
- [React API Reference Overview](https://react.dev/reference/react)