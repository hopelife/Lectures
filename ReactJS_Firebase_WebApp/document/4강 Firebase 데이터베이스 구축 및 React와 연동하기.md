# 03강 라우터(Router) 활용하기

## 참조

### blog
- [4강 Firebase 데이터베이스 구축 및 React와 연동하기](https://ndb796.tistory.com/236?category=1032205)

### youtube
- [React와 Firebase로 앱 개발하기 5강 - Firebase DB 구축 및 React와 연동](https://www.youtube.com/watch?v=DIc_nPKBrVA&list=PLRx0vPvlEmdCjiCfu4QB6tV7cZS4ZoTOQ&index=5)


## 라이브러리/패키지 설치

### 파이어베이스 생성/설정
0. 파이어베이스 접속
- [구글 파이어베이스 콘솔](https://console.firebase.google.com/)

1. 프로젝트 생성하기
- 프로젝트 추가
- 약관 동의
- 프로젝트 만들기 클릭

2. 데이터베이스 페이지 확인
- [프로젝트 생성 완료](https://console.firebase.google.com/u/0/?pli=1)
- '계속' 버튼 클릭
- 

3. 데이터베이스에 단어(Word) 데이터 구축
- 'words'


  (단, 원래는 ID 값으로 0, 1, 2와 같은 단순한 숫자를 넣지 않습니다. 이는 예시 데이터를 구성하기 위해 넣은 것이며, 실제 DB 연동 작업을 마쳤을 때에는 이러한 예시 데이터를 삭제해야 오류가 발생하지 않습니다.)

4. 규칙(Rule) 설정을 통한 외부 접속 허용

5. 단어(Word) API 호출 테스트

### 

## file 편집/생성

### ./src/components/Words.js

* Note: 변경 사항
- '!=' -> '!=='

```js
import React from 'react';
import Card from '@material-ui/core/Card';
import CardContent from '@material-ui/core/CardContent';
import Typography from '@material-ui/core/Typography';

const databaseURL = "https://wordcloud-7631d-default-rtdb.firebaseio.com/";

class Words extends React.Component {
    constructor() {
        super();
        this.state = {
            words: {}
        };
    }

    _get() {
        fetch(`${databaseURL}/words.json`).then(res => {
            if(res.status !== 200) {
                throw new Error(res.statusText);
            }
            return res.json();
        }).then(words => this.setState({words: words}));
    }

    shouldComponentUpdate(nextProps, nextState) {
        return nextState.words !== this.state.words
    }

    componentDidMount() {
        this._get();
    }

    render() {
        return (
            <div>
                {Object.keys(this.state.words).map(id => {
                    const word = this.state.words[id];
                    return (
                        <div key={id}>
                            <Card>
                                <CardContent>
                                    <Typography color="textSecondary" gutterBottom>
                                        가중치: {word.weight}
                                    </Typography>
                                    <Typography variant="h5" component="h2">
                                        {word.word}
                                    </Typography>
                                </CardContent>
                            </Card>
                            <br/>
                        </div>
                    );
                })}
            </div>

        );
    }
}

export default Words;
```
