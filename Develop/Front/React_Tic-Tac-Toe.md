# Tic-Tac-Toe
> React 틱택토 튜토리얼 과정 중 개념 정리<br>
> `이 자습서에서는 작은 틱택토 게임을 만들어 볼 것입니다.`<br>

### 주요 개념
컴포넌트<br>
- 작성 방법<br>
    함수를 파일 외부에서 접근 할 수 있도록 `export` 키워드 사용<br>
    `default` 키워드는 이 파일에서 이 함수가 주요 함수라는 것을 나타낸다.
    ```javascript
    export default function Square() {
        return <button className="square">X</button>;
    }
    ```
    이 때 `<button>` 은 jsx 엘리먼트이다. jsx는 JavaScript 코드와 HTML 태그의 조합으로 표시할 내용을 설명한다.
- Props 를 통한 데이터 전달<br>
    ```javascript
    function Square({ value }) {
        return <button className="square">{value}</button>;
    }
    ```
    `<Square value="1" />`<br>
    상위 컴포넌트에 하위 컴포넌트를 사용하고 Props를 전달하는 코드
    ```javascript
    export default function Board() {
        return (
            <>
            <div className="board-row">
                <Square value="1" />
                <Square value="2" />
                <Square value="3" />
            </div>
            <div className="board-row">
                <Square value="4" />
                <Square value="5" />
                <Square value="6" />
            </div>
            <div className="board-row">
                <Square value="7" />
                <Square value="8" />
                <Square value="9" />
            </div>
            </>
        );
    }
    ```
- 사용자와 상호작용 하기 위한 Status<br>
    `const [value, setValue] = useState(null);`<br>
    각 `Square`에 고유한 Status 인 `value` 변수를 생성했다.<br>
    기본 값은 `null` 이며 `setValue` 함수를 통해 값을 변경 할 수 있다.<br>
    당연히 타입 제한은 없다.
    ```javascript
    import { useState } from 'react';

    function Square() {
        const [value, setValue] = useState(null);
        ...
    ```
- 부모 컴포넌트의 Status 를 Props으로 자식 컴포넌트에게 전달<br>
    **여러 자식 컴포넌트에서 데이터를 수집하거나 두 자식 컴포넌트가 통신하길 원한다면 부모 컴포넌트에서 공유 `State` 를 선언한다.**<br>
    공유 변수 `squares` 의 값을 자식 컴포넌트에 Props로 전달
    ```javascript
    export default function Board() {
        const [squares, setSquares] = useState(Array(9).fill(null));
        return (
            <>
            <div className="board-row">
                <Square value={squares[0]} />
                <Square value={squares[1]} />
                <Square value={squares[2]} />
            </div>
            ...
    ```
- 자식 컴포넌트에서 부모 컴포넌트의 State에 접근 및 갱신<br>
    [**Javascript에서 지원하는 Closer 기능을 사용한다.**](https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures) <br>
    부모 컴포넌트에서 SetStatus 가 포함된 함수를 Prop으로 전달한다.<br>
    ```javascript
    export default function Board() {
        const [squares, setSquares] = useState(Array(9).fill(null));

        function handleClick() {
            const nextSquares = squares.slice();
            nextSquares[0] = "X";
            setSquares(nextSquares);
        }
        ...
      return (
        <>
        <div className="board-row">
            <Square value={squares[0]} onSquareClick={() => handleClick(0)} />
            // ...
    );
    ```
    이 때, **함수를 전달**하지 **함수를 호출**하지 않는다.<br>
    아래 코드는 함수가 호출되어  State를 변경하므로 Board 컴포넌트를 다시 렌더링하고,<br>
    렌더링하면 함수가 호출되는 구조이므로 무한 루프에 빠진다.
    ```javascript
    <Square value={squares[0]} onSquareClick={handleClick(0)} />
    ```

### 자잘한 팁 및 내용
JavaScript 관련 문법 문제, 기초적인 State, Component 사용법 등등...
- 불변성 : 데이터의 값을 직접 변경하기보다 변경 사항이 있는 복사본으로 데이터를 대체하는 방법론
    - 뒤로가기, 앞으로 가기 등의 기능을 만들 때 용이하다.
    - 부모 컴포넌트의 State가 변경되면 모든 자식 컴포넌트도 다시 렌더링된다.<br>
    이 때 컴포넌트가 데이터의 변경 여부를 아주 저렴한 비용을 주고 판단할 수 있다.
- 렌더링 기준 : `Set..` 함수를 통해 컴포넌트의 State가 변경될 경우 해당 컴포넌트와 해당 컴포넌트의 자식 컴포넌트들을 다시 렌더링한다.
- `<li key={user.id}>`, 리스트의 키 지정하기<br>
key는 React에서 특별히 미리 지정된 Property이다.<br>
동적인 리스트를 만들 때 적절한 Key를 할당하는걸 강력하게 추천한다. <br>
리스트가 다시 렌더링 될 때 React는 각 리스트 항목의 Key를 가져와서 이전 리스트 항목과 일치하는 Key를 비교하고, 새로운 Key는 컴포넌트를 생성하고, 삭제된 Key는 컴포넌트를 삭제하고, 동일한 Key는 해당 컴포넌트는 이동한다.<br>
key가 지정되지 않은 경우, React는 경고를 표시하며 배열의 인덱스를 기본 key로 사용한다. 배열 인덱스를 key로 사용하면 리스트 항목의 순서를 바꾸거나 항목을 추가/제거할 때 문제가 발생한다.
- Javascript `...` 전개 구문<br> Iterable 한 객체의 모든 항목을 열거한다.
- Javascript `map` <br>
    `sqaures` 인수는 `history`의 각 엘리먼트를 순회하고, `move`는 각 배결 인덱스를 순회한다.
    ```javascript
    function handlePlay(nextSquares) {
        setHistory([...history, nextSquares]);
        setXIsNext(!xIsNext);
    }

    const moves = history.map((squares, move) => {
        let description;
        if (move > 0) {
            description = 'Go to move #' + move;
        } else {
            description = 'Go to game start';
        }
        return (
            <li>
                <button onClick={() => jumpTo(move)}>{description}</button>
            </li>
        );
    });
    ```
- 중복되는 State는 피하라
---
### 추가 도전 과제
1. 현재 이동에 대해서만 버튼 대신 “당신은 #번째 순서에 있습니다…”를 표시해 보세요.
2. Board를 하드 코딩 하는 대신 두 개의 루프를 사용하여 사각형을 만들도록 다시 작성해 보세요.
3. 동작을 오름차순 또는 내림차순으로 정렬할 수 있는 토글 버튼을 추가해 보세요.
4. 누군가 승리하면 승리의 원인이 된 세 개의 사각형을 강조 표시해 보세요. (아무도 승리하지 않으면 무승부라는 메시지를 표시하세요. )
5. 이동 히스토리 목록에서 각 이동의 위치를 형식(열, 행)으로 표시해 보세요.
---
### 최종 코드
``` javascript
import { useState } from "react";

function Square({ value, onSquareClick }) {
  // const [value, setValue] = useState(null);

  // function handleClick() {
  // console.log("clicked!");
  //   setValue("X");
  // }
  return (
    <button className="square" onClick={onSquareClick}>
      {value}
    </button>
  );
}

function Board({ xIsNext, squares, onPlay }) {
  // const [xIsNext, setXIsNext] = useState(true);
  // const [squares, setSquares] = useState(Array(9).fill(null));

  function handleClick(i) {
    if (squares[i] || calculateWinner(squares)) {
      return;
    }
    const nextSquares = squares.slice();
    if (xIsNext) {
      nextSquares[i] = "X";
    } else {
      nextSquares[i] = "O";
    }
    // nextSquares[i] = "X";
    // setSquares(nextSquares);
    // setXIsNext(!xIsNext);
    onPlay(nextSquares);
  }

  const winner = calculateWinner(squares);
  let status;
  if (winner) {
    status = "Winner: " + winner;
  } else {
    status = "Next player: " + (xIsNext ? "X" : "O");
  }

  return (
    <>
      <div className="status">{status}</div>
      <div className="board-row">
        <Square value={squares[0]} onSquareClick={() => handleClick(0)} />
        <Square value={squares[1]} onSquareClick={() => handleClick(1)} />
        <Square value={squares[2]} onSquareClick={() => handleClick(2)} />
      </div>
      <div className="board-row">
        <Square value={squares[3]} onSquareClick={() => handleClick(3)} />
        <Square value={squares[4]} onSquareClick={() => handleClick(4)} />
        <Square value={squares[5]} onSquareClick={() => handleClick(5)} />
      </div>
      <div className="board-row">
        <Square value={squares[6]} onSquareClick={() => handleClick(6)} />
        <Square value={squares[7]} onSquareClick={() => handleClick(7)} />
        <Square value={squares[8]} onSquareClick={() => handleClick(8)} />
      </div>
    </>
  );
}

export default function Game() {
  const [xIsNext, setXIsNext] = useState(true);
  // 다 비어있는 배열 최초 선언
  const [history, setHistory] = useState([Array(9).fill(null)]);
  const [currentMove, setCurrentMove] = useState(0);
  const currentSquares = history[currentMove];

  function handlePlay(nextSquares) {
    const nextHistory = [...history.slice(0, currentMove + 1), nextSquares];
    // 2차원 배열이 되는 구조...
    // setHistory([...history, nextSquares]);
    setHistory(nextHistory);
    setCurrentMove(nextHistory.length - 1);
    setXIsNext(!xIsNext);
  }

  function jumpTo(nextMove) {
    //TODO
    setCurrentMove(nextMove);
    // 짝수면 xIsTrue 가 true
    setXIsNext(nextMove % 2 === 0);
  }

  const moves = history.map((squares, move) => {
    let description;
    if (move > 0) {
      description = "Go to move #" + move;
    } else {
      description = "Go to move Start";
    }
    return (
      <li key={move}>
        <button onClick={() => jumpTo(move)}>{description}</button>
      </li>
    );
  });

  return (
    <div className="game">
      <div className="game-board">
        <Board xIsNext={xIsNext} squares={currentSquares} onPlay={handlePlay} />
      </div>
      <div className="game-info">
        <ol>{moves}</ol>
      </div>
    </div>
  );
}

function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6]
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}

```

##### References
- [자습서: 틱택토 게임](https://ko.react.dev/learn/tutorial-tic-tac-toe#)