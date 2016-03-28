## JavaScript

- JS的基础数据类型

```
Undefined, Null, Boolean, Number, String
```

- JS的内置对象

```
Object 是 JavaScript 中所有对象的父对象

数据封装类对象：Object, Array, Boolean, Number 和 String
其他对象：Function, Arguments, Math, Date, RegExp, Error
```

- Array和Object

```
var arrayA = [];
arrayA[1] = 'a'
arrayA.length // 2

var objectA = {};
objectA[1] = 'a';
Object.keys(objectA).length // 1

var objectB = {x: 'a'};
objectB.x // 'a'
objectB['x'] // 'a'

var param = 'x';
objectB[param] // 'a'
```

- JS是弱类型语言

```
JS变量类型的自动转换
1 + '1' // '11'
0 == false // true
0 === false // false
```

- 变量作用域

```
JS只有Function内才有局部变量，ES6 let定义的变量拥有跨级作用域{}
变量必须用var定义，否则变量提升
var a = 1,
    b = 2;
function test() {
    var a = 3;
    b = 4;
}
console.log(a, b); // 3 2
```

- 延时执行函数setTimeout / setInterval

```
var handle = setTimeout(function() {
    // something
}, 0);
clearTimeout(handle);
```

- 匿名函数

```
(function($) {
    ...
})(window.jQuery);

用途：
for(var i = 1; i <= 5; i++) {
    setTimeout(function() {
        console.log(i); // 输出 66666
    });
}

解决办法：
for(var i = 1; i <= 5; i++) {
    (function(i) {
        setTimeout(function() {
            console.log(i); // 输出 12345
        });
    })(i);
}

或：
for(var i = 1; i <= 5; i++) {
    setTimeout(function(i) {
        console.log(i); // 输出 12345
    }.bind(null, i));
}

```

- 正则表达式

```
    new RegExp(pattern, attributes) // RegExp对象
    /^[a-z]*$/i // 正则字面量

    // test用来判断
    /^[a-z]*$/i.test('abc') // true
    /^[a-z]*$/i.test('123') // false

    // match用来获取
    /^[a-z]*$/i.match('abc') // ['abc']
    /^[a-z]*$/i.match('123') // null

```

- 数据存储方案cookies, sessionStorage, localStorage的区别

```
cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。
cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。
sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

存储大小：
    cookie数据大小不能超过4k。
    sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。

有期时间：
    localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
    sessionStorage  数据在当前浏览器窗口关闭后自动删除。
    cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭
```

- jQuery事件绑定

```
$('.class').on('click', function(e) {
    // 普通的事件绑定
});

$('body').on('click', '.class', function() {
    // 事件代理
});
```

- jQuery Ajax

```
$.ajax({
    url: '/',
    type: 'get', // post, jsonp
    data: {},
    headers: {}, // 请求头信息
    context: this, // 传入this
    cache: false // 缓存
}).done(function(data, textStatus, jqXHR) {
    // 成功
}).fail(function(jqXHR, textStatus, errorThrown) {
    // 失败
}).always(function(data, textStatus, jqXHR) {
    // 无论成功失败
});

get请求参数通过url发送，注意最大长度，超过则截断

跨域请求使用jsonp
jsonp的原理：动态插入script标签加载js文件，传入callback函数名，返回直接调用
```

- 前端MVC结构

```
Url
 ↓
Router
 ↓
Controller → ← Model
 ↓
View
```

- JS的模块化

```
/* 方法1 */
var ModuleA = (function() {
    var funcs = {};
    funcs.a = function() {
        return 1;
    }
})();
ModuleA.a(); // 1

/* 方法2 */
var ModuleB = function() {
    this.a = function() {
        return 1;
    }
}
ModuleB.prototype.b = function() {
    return 2;
}

var moduleB = new ModuleB();
moduleB.a(); // 1
moduleB.b(); // 2

/* ES6模块方法 */
var func = function() {
    return 1;
}
module.exports = func;

import a from './file';
a(); // 1
```
