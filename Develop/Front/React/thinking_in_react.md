# Thinking in React
> React 로 UI를 구성하고 설계하는 방법

디자인과 시안에서부터 컴포넌트를 설계하고 배치하는 과정을 연습한다.

[Thinking in React](https://ko.react.dev/learn/thinking-in-react)
### 컴포넌트 계층으로 쪼개기
<img src="https://ko.react.dev/images/docs/s_thinking-in-react_ui_outline.png">

1. FilterableProductTable(회색): 예시 전체를 포괄한다.
2. SearchBar(파란색): 사용자의 입력을 받는다.
3. ProductTable(라벤더색): 데이터 리스트를 보여주고, 사용자의 입력을 기반으로 필터링한다.
4. ProductCategoryRow(초록색): 각 카테고리의 헤더를 보여준다.
5. ProductRow(노란색): 각각의 제품에 해당하는 행을 보여준다.

### 컴포넌트 구현
기능하지 않는 정적인 버전을 먼저 구축한다. `이때 State를 사용하지 않는다.`<br>
데이터 흐름과 기능은 바로 구현하지 않아도 된다.<br>
- 계층 구조에 따라 어디서부터 구현할 지 고민해보자.
    - Top-Down : 하향식, 쉽다. 프로젝트가 작을 때 유용하다.
    - Bottom-Up : 상향식, 큰 프로젝트에서 테스트를 작성하며 개발하기 좋다.

### State 구현
State를 관리할 데이터를 정하고 컴포넌트 간 데이터 흐름을 정한다.<br>
#### State로 관리할 데이터는?
1. 제품의 원본 목록은 props로 전달되었기 때문에 state가 아닙니다.
2. 사용자가 입력한 검색어는 시간이 지남에 따라 변하고, 다른 요소로부터 계산될 수 없기 때문에 state로 볼 수 있습니다.
3. 체크박스의 값은 시간에 따라 바뀌고 다른 요소로부터 계산될 수 없기 때문에 state로 볼 수 있습니다
4. 필터링된 제품 목록은 원본 제품 목록을 받아서 검색어와 체크박스의 값에 따라 계산할 수 있으므로, 이는 state가 아닙니다.
#### State의 위치와 데이터 흐름은?
1. 해당 state를 기반으로 렌더링하는 모든 컴포넌트를 찾으세요.
2. 그들의 가장 가까운 공통되는 부모 컴포넌트를 찾으세요. - 계층에서 모두를 포괄하는 상위 컴포넌트
3. state가 어디에 위치 돼야 하는지 결정합시다
    1. 대개, 공통 부모에 state를 그냥 두면 됩니다.
    2. 혹은, 공통 부모 상위의 컴포넌트에 둬도 됩니다.
    3. state를 소유할 적절한 컴포넌트를 찾지 못하였다면, state를 소유하는 컴포넌트를 하나 만들어서 상위 계층에 추가하세요.

#### useState() 
`useState()` `Hook`을 이용해서 state를 컴포넌트에 추가할 수 있다.<br> `Hooks`는 React 기능에 “연결할 수(hook into)” 있게 해주는 특별한 함수이다.

### 역 데이터 흐름
부모 컴포넌트에서 `State 업데이트 함수` 를 `props` 형태로 자식 컴포넌트에게 전달하면 자식 컴포넌트에서 부모 컴포넌트에 데이터를 전달할 수 있다.<br>
`onFilterTextChange={setFilterText}`, `onInStockOnlyChange={setInStockOnly}`
``` javascript
function FilterableProductTable({ products }) {
  const [filterText, setFilterText] = useState('');
  const [inStockOnly, setInStockOnly] = useState(false);

  return (
    <div>
      <SearchBar 
        filterText={filterText} 
        inStockOnly={inStockOnly}
        onFilterTextChange={setFilterText}
        onInStockOnlyChange={setInStockOnly} />
```

---
### 최종 Code
``` javascript
import { useState } from 'react';

// 상품 테이블과 검색 테이블을 자식 컴포넌트로 두는 필터링 가능한 상품 테이블 컴포넌트(최상위)
function FilterableProductTable({ products }) {
  const [filterText, setFilterText] = useState('');
  const [inStockOnly, setInStockOnly] = useState(false);
  return (
    <div>
      <SearchBar 
        filterText={filterText} 
        inStockOnly={inStockOnly}
        onFilterTextChange={setFilterText}
        onInStockOnlyChange={setInStockOnly} />
      <ProductTable 
        products={products} 
        filterText={filterText} 
        inStockOnly={inStockOnly} />
    </div>
  );
}

// 상품 카테고리명 컴포넌트
function ProductCategoryRow({ category }) {
  return (
    <tr>
        <th colSpan="2">
          {category}
        </th>
    </tr>
  );
}

// 상품명 컴포넌트
function ProductRow({ product }) {
  const name = product.stocked ? product.name :
    <span style={{ color: 'red' }}>
      {product.name}
    </span>;

  return (
    <tr>
      <td>{name}</td>
      <td>{product.price}</td>
    </tr>
  );
}

// 상품명,  상품카테고리 명을 자식으로 두는 컴포넌트, 상품 테이블
// State 에 따라 표기되는 상품이 달라짐
function ProductTable({products, filterText, inStockOnly}) {
  const rows = [];
  let lastCategory = null;

  // map과 forEach
  products.forEach((product)=> {
    if (
      product.name.toLowerCase().indexOf(
        filterText.toLowerCase()
      ) === -1
    ) {
      // 빈 컴포넌트, HTML에 아무것도 남기지 않음
      return;
    }
    if (inStockOnly && ! product.stocked) {
      return;
    }
    if (product.category !== lastCategory) {
      rows.push(
        <ProductCategoryRow
          category={product.category}
          key={product.category} />
      );
    }
    rows.push(
      <ProductRow
        product={product}
        key={product.name} />
    );
    lastCategory = product.category;
  });

  return (
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Price</th>
        </tr>
      </thead>
      <tbody>{rows}</tbody>
    </table>
  )
}

// 검색 테이블, CheckBox State, 검색 창 State
function SearchBar({filterText, inStockOnly, onFilterTextChange, onInStockOnlyChange}) {
  return (
    <form>
      <input type="text" 
      value={filterText}
      placeholder="Search..." 
      onChange={(e)=>onFilterTextChange(e.target.value)}
      />
      <label>
        <input type="checkbox"
        checked={inStockOnly} 
        onChange={(e)=>onInStockOnlyChange(e.target.checked)}/>
        {' '}
        Only show products in stock
      </label>
    </form>
  );
}



const PRODUCTS =  [
  {category: "Fruits", price: "$1", stocked: true, name: "Apple"},
  {category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit"},
  {category: "Fruits", price: "$2", stocked: false, name: "Passionfruit"},
  {category: "Vegetables", price: "$2", stocked: true, name: "Spinach"},
  {category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin"},
  {category: "Vegetables", price: "$1", stocked: true, name: "Peas"}
];

export default function App() {
  return <FilterableProductTable products={PRODUCTS} />;
}
```

---
##### References
- [Thinking in React](https://ko.react.dev/learn/thinking-in-react)