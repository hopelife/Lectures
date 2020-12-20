# 03강 라우터(Router) 활용하기

## 참조
### blog
- [3강 라우터(Router) 활용하기](https://ndb796.tistory.com/235?category=1032205)

## 라이브러리/패키지 설치

### react router

```bash
C:\Dev\docMoon\trainings\Lectures\ReactJS_Firebase_WebApp\wordcloud> yarn add react-router-dom
```

## file 편집/생성

### ./src/components/Home.js
```js
import React from 'react';
import Card from '@material-ui/core/Card';
import CardContent from '@material-ui/core/CardContent';

class Home extends React.Component {
    render() {
        return (
            <Card>
                <CardContent>
                    React 및 Firebase 기반의 워드 클라우드 프로젝트
                </CardContent>
            </Card>
        );
    }
}

export default Home;
```

### ./src/components/Texts.js

```js
import React from 'react';
import Card from '@material-ui/core/Card';
import CardContent from '@material-ui/core/CardContent';

class Texts extends React.Component {
    render() {
        return (
            <Card>
                <CardContent>
                    Texts 페이지
                </CardContent>
            </Card>
        );
    }
}

export default Texts;
```

### ./src/components/Words.js
```js
import React from 'react';
import Card from '@material-ui/core/Card';
import CardContent from '@material-ui/core/CardContent';

class Words extends React.Component {
    render() {
        return (
            <Card>
                <CardContent>
                    Words 페이지
                </CardContent>
            </Card>
        );
    }
}

export default Words;
```

### ./src/components/App.js
```js
import React from 'react';
import { HashRouter as Router, Route } from 'react-router-dom';
import AppShell from './AppShell';
import Home from './Home';
import Texts from './Texts';
import Words from './Words';

class App extends React.Component {
    render() {
        return (
            <Router>
                <AppShell>
                    <div>
                        <Route exact path="/" component={Home}/>
                        <Route exact path="/texts" component={Texts}/>
                        <Route exact path="/words" component={Words}/>
                    </div>
                </AppShell>
            </Router>
        );
    }
}

export default App;
```

### ./src/components/AppShell.js
```js
import React from 'react';
import { Link as RouterLink } from 'react-router-dom';
import Link from '@material-ui/core/Link';
import { withStyles } from '@material-ui/core/styles';
import AppBar from '@material-ui/core/AppBar';
import Drawer from '@material-ui/core/Drawer';
import MenuItem from '@material-ui/core/MenuItem';
import IconButton from '@material-ui/core/IconButton';
import MenuIcon from '@material-ui/icons/Menu';

const styles = {
    root: {
        flexGrow: 1,
    },
    menuButton: {
      marginRight: 'auto'
    },
};

class AppShell extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            toggle: false
        };
    }
    handleDrawerToggle = () => this.setState({toggle: !this.state.toggle})
    render() {
        const { classes } = this.props;
        return (
            <div>
                <div className={classes.root}>
                    <AppBar position="static">
                        <IconButton className={classes.menuButton} color="inherit" onClick={this.handleDrawerToggle}>
                            <MenuIcon/>
                        </IconButton>
                    </AppBar>
                    <Drawer open={this.state.toggle}>
                        <MenuItem onClick={this.handleDrawerToggle}>
                            <Link component={RouterLink} to="/">
                                Home
                            </Link>
                        </MenuItem>
                        <MenuItem onClick={this.handleDrawerToggle}>
                            <Link component={RouterLink} to="/texts">
                                Texts
                            </Link>
                        </MenuItem>
                        <MenuItem onClick={this.handleDrawerToggle}>
                            <Link component={RouterLink} to="/words">
                                Words
                            </Link>
                        </MenuItem>
                    </Drawer>
                </div>
                <div id="content" style={{margin: 'auto', marginTop: '20px'}}>
                    {React.cloneElement(this.props.children)}
                </div>
            </div>
        );
    }
}

export default withStyles(styles)(AppShell);
```