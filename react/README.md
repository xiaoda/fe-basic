## React

- 组件的生命周期

![React lifecycle](https://raw.githubusercontent.com/xiaoda/fe-basic/master/react/res/lifecycle.jpg)

```
例子：<Navbar active="index"/>

创建期

    getDefaultProps
        初始化this.props，如果父组件没有指定props中的某个键，则此处返回的对象中的相应属性将会合并到this.props

    getInitialState
        初始化this.state。可以访问this.props。

    componentWillMount
        组件挂载之前调用，此时可以修改this.state

    render
        通过this.props和this.state创建一个虚拟DOM

        1.不修改this.state
        2.不操作DOM
        3.不和浏览器交互

    componentDidMount
        组件挂载之后立刻调用，此时已有真实DOM，可以加载数据、调用其它类库等

存在期

    componentWillReceiveProps
        在组件接收到新的props的时候调用。在初始化渲染的时候，该方法不会调用
        老的props可以通过this.props获得
        componentWillReceiveProps: function(nextProps) {
            this.setState({
                active: nextProps.active
            });
        }

    shouldComponentUpdate
        如果你确定this.props或者this.state的改变不需要重新渲染，可以在这个方法里通过返回false来阻止组件的重新渲染返回false不会执行render以及componentWillUpdate, componentDidUpdate方法
        shouldComponentUpdate: function(nextProps, nextState){
            return this.state.active === nextState.active;
            //return false 则不更新组件
        }

    componentWillUpdate
        组件更新之前调用，和componentWillMount类似
        这时不要再去更新props或者state

    componentDidUpdate
        组件更新之后立刻调用，和componentDidMount类似

销毁时

    componentWillUnmount
        组件从DOM中移除的时候立刻被调用
        在这里执行任何必要的清理，比如定时器、事件监听、清除创建的DOM元素
```

- props和state的区别

```
相同点：
    1.可以通过父组件获得初始值
    2.可以在组件内设置初始值
    3.可以作为子组件的属性

不同点：
    props
        1.props是一个组件的配置
        2.组件内部不能修改props
        3.可以在子组件中被修改

    state
        1.state是一个组件的数据
        2.组件内部可以修改state
        3.不能在子组件中被修改

哪些数据应该使用state：
    1.组件内部通过操作会被修改的数据

哪些数据不该使用state：
    1.计算后的数据。数据的计算应该留到render内执行
    2.react组件。在render方法内创建react组件
    3.props已有的重复数据
```

- 属性和行内样式

```
render: function() {
    return (<div className="class-a" style={marginTop: '10px'}></div>);
}
```

- 数据循环输出到组件

```
render: function() {
    // data = [{...}, {...}]
    var commentNode = function(item, key) {
        return (
            <Comment key={key} author={item.author}>
                {item.text}
            </Comment>
        );
    });
    return (
        <div className="commentList">
            {this.state.data.map(commentNode)}
        </div>
    );
}
```

- JSX中的if else

```
/* return中的if */
render: function() {
    return (<div id={if (condition) { 'msg' }}>Hello World!</div>);
}

/* return之前使用if else */
render: function() {
    var loginButton;
        if (loggedIn) {
            loginButton = <LogoutButton />;
        } else {
            loginButton = <LoginButton />;
    }

    return (
        <nav>
            <Home />
            {loginButton}
        </nav>
    );
}

/* return中定义立即执行函数使用if else和switch */
render: function() {
    return (
        <section>
            <h1>Color</h1>
            <h3>Name</h3>
            <p>{this.state.color || "white"}</p>
            <h3>Hex</h3>
            <p>
                {(() => {
                    switch (this.state.color) {
                        case "red":   return "#FF0000";
                        case "green": return "#00FF00";
                        case "blue":  return "#0000FF";
                        default:      return "#FFFFFF";
                    }
                })()}
            </p>
        </section>
    );
}
```

- 组件间的通信

```
父 > 子：
    直接pass props

子 > 父：
    <Navbar active="index" onNavClick="this.handleNavClick"/>

    onNavClick: function(id) {
        this.props.onNavClick(id);
    }

没有父子关系的组件间通信：
    设置自己的全局事件系统。在componentDidMount订阅事件，在componentWillUnmount退订
````
