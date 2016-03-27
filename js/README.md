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

- JS是弱类型语言

```
JS变量类型的自动转换
1 + '1' // '11'
0 == false // true
0 === false // false
```

- 变量作用域

```
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

for(var i = 1; i <= 5; i++) {
    (function(i) {
        setTimeout(function() {
            console.log(i); // 输出 12345
        });
    })(i);
}

for(var i = 1; i <= 5; i++) {
    setTimeout(function(i) {
        console.log(i); // 输出 12345
    }.bind(null, i));
}

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
    type: 'get',
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
```