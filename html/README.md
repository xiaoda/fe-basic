# HTML

- 顶部

```
<!DOCTYPE html>
<html>
<head>
    <!-- 编码 -->
    <meta charset="UTF-8">
    <!-- IE浏览器渲染模式 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <!-- 国产浏览器内核选择 -->
    <meta name="renderer" content="webkit">
    <title>51IDC|安畅</title>
    <!-- 关键词以英文逗号分隔 -->
    <meta name="keywords" content="51idc,安畅">
    <meta name="description" content="安畅（证券代码831315）是国内最大的管理式云服务商。"/>
</head>
<body>
</body>
</html>
```

- 资源文件的位置

```
CSS文件放在head头部，保证DOM加载完可以立即应用样式，不会发生样式抖动
JS文件放在body底部，防止脚本阻塞浏览器加载、渲染进程，保证页面渲染速度
涉及到样式的JS文件如jQueryUI也需要放在head头部，防止JS修改页面元素样式造成样式抖动
```

- 常见的浏览器内核

```
Webkit/Blink: Chrome, Safari, iOS所有浏览器和安卓绝大多数浏览器, 国产浏览器
Trident: ~ IE11, 国产浏览器
Edge: IE Edge
Gecko: Firefox
```

- HTML5有哪些新特性、移除了那些元素？

```
* HTML5 不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加
  绘画 canvas
  用于媒介回放的 video 和 audio 元素
  本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失
  sessionStorage 的数据在浏览器关闭后自动删除
  语意化更好的内容元素，比如 article, footer, header, nav, section
  表单控件 calendar, date, time, email, url, search
  新的技术 webworker, websockt, geolocation

* 移除的元素：
  纯表现的元素：basefont, big, center, font, s, strike, tt, u
  对可用性产生负面影响的元素：frame, frameset, noframes
```