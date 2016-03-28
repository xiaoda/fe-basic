## CSS

- CSS的命名规范
```
参考bootstrap
.class-class
#idId
```

- CSS选择器有哪些？哪些属性可以继承？

```
* 1.id选择器（ # myid）
  2.类选择器（.myclassname）
  3.标签选择器（div, h1, p）
  4.相邻选择器（h1 + p）
  5.子选择器（ul > li）
  6.后代选择器（li a）
  7.通配符选择器（ * ）
  8.属性选择器（a[rel = "external"]）
  9.伪类选择器（a: hover, li: nth - child）
* 可继承的样式：font-size font-family color
* 不可继承的样式：border padding margin width height
```

- CSS样式的优先级和选择器权重

```
* !important > 内联样式 > id > class > tag
* /* 权重为1 */
  div{}
  /* 权重为10 */
  .class1{}
  /* 权重为100 */
  #id1{}
  /* 权重为100+1=101 */
  #id1 div{}
  /* 权重为10+1=11 */
  .class1 div{}
  /* 权重为10+10+1=21 */
  .class1 .class2 div{}
* 相同权重以最后定义的样式为准
```

- CSS盒子模型

```
* 有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 pading;
  盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)
* html顶部必须制定DOCTYPE，否则低版本IE浏览器使用IE盒子模型进行解析
```

- 常用的display值

```
block 块级元素：<div> <p>
inline 行内元素：<span>
inline-block 行内块元素：<button>
```

- position值

```
absolute
    生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位
fixed
    生成绝对定位的元素，相对于浏览器窗口进行定位
relative
    生成相对定位的元素，相对于其正常位置进行定位
static
    默认值。没有定位，元素出现在正常的流中
   （忽略 top, bottom, left, right z-index 声明）
```

- 居中一个div

```
div{width: 1000px; margin: 0 auto;}
```

```
div{
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100px;
    height: 100px;
    margin-top: -50px;
    margin-left: -50px;
}
```

```
div{
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100px;
    height: 100px;
    margin: auto;
}
```

- 浮动元素

```
float: left; // right

脱离文档流，父元素或者相邻节点需要清除浮动，否则父元素没有高度
清除浮动：overflow: auto; // hidden

.clearfix:after{content:".";display:block;height:0;clear:both;visibility:hidden}
.clearfix{*+height:1%;}
```

- CSS实现的一个三角形

```
* 原理：元素长、宽为0，把上、左、右三条边隐藏掉（颜色设为 transparent）
* 好处：减少图片使用

.triangle{
    width: 0;
    height: 0;
    border-width: 10px;
    border-style: solid;
    border-color: transparent transparent red transparent;
}
```

- CSS3的新特性

```
圆角 border-radius: 10px
阴影 box-shadow: 10px
文字特效 text-shadow
线性渐变 gradient
旋转 transform: rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);//旋转,缩放,定位,倾斜
```

- CSS3属性内核前缀

```
-webkit-border-radius: 10px;
   -moz-border-radius: 10px;
    -ms-border-radius: 10px;
        border-radius: 10px;
```

- CSS3新增伪类

```
p:first-of-type 选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
p:last-of-type  选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
p:only-of-type  选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
p:only-child    选择属于其父元素的唯一子元素的每个 <p> 元素。
p:nth-child(2)  选择属于其父元素的第二个子元素的每个 <p> 元素。
:enabled        :disabled 控制表单控件的禁用状态。
:checked        单选框或复选框被选中。
```

- SASS

    - 变量

    ```
    $font-stack: Helvetica, sans-serif;
    $primary-color: #333;

    body {
        font: 100% $font-stack;
        color: $primary-color;
    }
    ```

    - 嵌套

    ```
    .class1{
        width: 1000px;
        .class2{
            width: 500px;
        }
    }
    ```

    - 混合
    ```
    @mixin border-radius($radius) {
        -webkit-border-radius: $radius;
           -moz-border-radius: $radius;
            -ms-border-radius: $radius;
                border-radius: $radius;
    }

    .box {@include border-radius(10px);}
    ```

    - 扩展/继承

    ```
    .message {
        border: 1px solid #ccc;
        padding: 10px;
        color: #333;
    }

    .success {
        @extend .message;
        border-color: green;
    }

    .error {
        @extend .message;
        border-color: red;
    }
    ```