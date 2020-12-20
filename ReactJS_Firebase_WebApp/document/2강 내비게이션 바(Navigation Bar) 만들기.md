# 01강 리액트(React) 프로젝트 구성 및 깃 허브 연동하기

## 참조
### blog
- [2강 내비게이션 바(Navigation Bar) 만들기](https://ndb796.tistory.com/234?category=1032205)

## material-ui 라이브러리 설치

```bash
C:\Dev\docMoon\trainings\Lectures\ReactJS_Firebase_WebApp\wordcloud>yarn add @material-ui/core @material-ui/icons
```

## file 편집/생성

### ./src/components/Appshell.js
```js
import React from 'react';
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
            <div className={classes.root}>
                <AppBar position="static">
                    <IconButton className={classes.menuButton} color="inherit" onClick={this.handleDrawerToggle}>
                        <MenuIcon/>
                    </IconButton>
                </AppBar>
                <Drawer open={this.state.toggle}>
                    <MenuItem onClick={this.handleDrawerToggle}>Home</MenuItem>
                </Drawer>
            </div>
        );
    }
}

export default withStyles(styles)(AppShell);
```

### ./src/components/App.js

```js
import React from 'react';
import AppShell from './AppShell';

class App extends React.Component {
    render() {
        return (
            <AppShell/>
        );
    }
}

export default App;
```
