# 01강 리액트(React) 프로젝트 구성 및 깃 허브 연동하기

## 참조
### blog
- [1강 리액트(React) 프로젝트 구성 및 깃 허브 연동하기](https://ndb796.tistory.com/233?category=1032205)

## 변경 사항
### 프로젝트 초기화
- create-react-app 이용 <- yarn start 오류 해결 못함

### git
- Lectures 전체를 github에 연결

## file 생성/ 편집

### public/index.html
```
<!DOCTYPE html>
<html>
    <head>
        <title>Word Cloud Project</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <meta name="theme-color" content="#E2E2E2">
    </head>
    <body>
        <div id="app"></div>
        <script type="text/javascript" src="main.js"></script>
    </body>
</html>
```

### src/components/App.js (파일 이동)
* src/components/App.js <- src/App.js

```
import React from 'react';

class App extends React.Component {
    render() {
        return (
            <div>
                <h3>Hello World</h3>
            </div>
        );
    }
}

export default App;
```

### src/index.js
* 강좌에서는 src/main.js

```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './components/App';

ReactDOM.render(<App/>, document.getElementById('app'));
```

## file 삭제

- public/favicon.ico
- public/logo192.png
- public/logo512.png
- src/App.test.js
- src/logo.svg
- setupTests.js
- reportWebVitals.js