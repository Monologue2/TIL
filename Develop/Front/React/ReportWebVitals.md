# reportWebVitals
> reportWebVitals.js 파일은 Create React App(CRA) 명령어를 통해 생성된 프로젝트의 일부로, 웹 애플리케이션의 성능 지표를 측정하고 보고하는 역할을 한다.
>
### 성능 지표
- CLS (Cumulative Layout Shift): 레이아웃 이동의 총량을 측정하여 페이지가 시각적으로 얼마나 안정적인지 평가합니다.
- FID (First Input Delay): 사용자가 처음으로 상호작용했을 때 브라우저가 이를 처리하는 데 걸린 시간을 측정합니다.
- FCP (First Contentful Paint): 페이지의 첫 번째 컨텐츠가 사용자에게 렌더링되는 시간을 측정합니다.
- LCP (Largest Contentful Paint): 페이지의 주요 콘텐츠가 사용자에게 렌더링되는 시간을 측정합니다.
- TTFB (Time to First Byte): 브라우저가 서버로부터 첫 번째 바이트를 받는 데 걸린 시간을 측정합니다.


### reportWebVitals 사용 예제
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import reportWebVitals from './reportWebVitals';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

// 성능 지표를 로그에 기록
reportWebVitals(console.log);
```

### FCP : First Contentful Paint
```javascript
# FCP (First Contentful Paint)
{name: 'FCP', value: 330.9000000022352, delta: 330.9000000022352, entries: Array(1), id: 'v2-1720686287107-3010615640208'}
```
`name: 'FCP'`
- First Contentful Paint를 나타내며, 페이지의 첫 번째 컨텐츠가 사용자에게 렌더링되는 시간을 측정합니다.

`value: 330.9000000022352`
- FCP의 실제 측정 값으로, 단위는 밀리초(ms)입니다. 여기서 330.9ms는 페이지의 첫 번째 컨텐츠가 사용자에게 렌더링되기까지 걸린 시간을 의미합니다.

`delta: 330.9000000022352`
- 이전 측정 값과의 차이를 나타냅니다. 이 경우, 초기 측정이기 때문에 value와 동일합니다.

`entries: Array(1)`
- 성능 측정을 위한 엔트리 목록을 포함하는 배열입니다. 여기에는 성능 측정과 관련된 자세한 정보가 들어 있을 수 있습니다.

`id: 'v2-1720686287107-3010615640208'`
- 측정 항목에 대한 고유 식별자입니다. 여러 성능 측정 값이 있을 때 이를 구분하는 데 사용됩니다.

### TTFB : Time to First Byte
```javascript
{name: 'TTFB', value: 13.300000000745058, delta: 13.300000000745058, entries: Array(1), id: 'v2-1720686287107-8752269999732'}
```

`name: 'TTFB'`
- Time to First Byte를 나타내며, 브라우저가 서버로부터 첫 번째 바이트를 받는 데 걸린 시간을 측정합니다.

`value: 13.300000000745058`
- TTFB의 실제 측정 값으로, 단위는 밀리초(ms)입니다. 여기서 13.3ms는 브라우저가 서버로부터 첫 번째 바이트를 받기까지 걸린 시간을 의미합니다.

`delta: 13.300000000745058`
- 이전 측정 값과의 차이를 나타냅니다. 이 경우, 초기 측정이기 때문에 value와 동일합니다.

`entries: Array(1)`
- 성능 측정을 위한 엔트리 목록을 포함하는 배열입니다. 여기에는 성능 측정과 관련된 자세한 정보가 들어 있을 수 있습니다.

`id: 'v2-1720686287107-8752269999732'`
- 측정 항목에 대한 고유 식별자입니다. 여러 성능 측정 값이 있을 때 이를 구분하는 데 사용됩니다.

##### References
