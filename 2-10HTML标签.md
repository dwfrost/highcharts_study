# HTML标签

最后修改时间：2017-09-28 17:15

HTMl标签（Lables）指的是可以放置在图表中任意位置的文字标签，由于最终的文字标签是以 SVG 渲染的，所以标签的内容只支持少量的 HTML 标签，包括：`<b>`、`<strong>`、`<i>`、`<em>`、`<br/>`、`<span>`，其中 可以通过 style 属性来设定样式，但是有效的样式仅限和文字相关的属性。HTML 标签的基本构造是：

```
labels: {
    style: {                         // 标签全局样式
        color: "#ff0000",
        fontSize: '12px',
        fontWeight: 'normal',
        fontFamily: ''        
    },
    items: [{                       // items 数组，可以设置多个标签
        html: 'html 标签内容',
        style: {                    // 标签样式，会继承和重写上层全局样式
            left: '50px',
            top: '100px',
            color: 'red',
            fontSize: '12px',
            fontWeight: 'normal',
            fontFamily: '' 
        }
    }]
}

```

![img](https://img.hcharts.cn/static/highcharts/images/docs/basic_lables_1.png)

[在线试一试](https://code.hcharts.cn/highcharts/hhhhLQ)

## 扩展内容

通过学习上面的内容我们知道，HTMl标签只能添加简单的文字标签，并且只能是在图标初始化的时候才能添加，那么对于添加文字标签，highcharts 有没有更方便的编程接口呢？

答案是有的，对应的 API 是 [Renderer](http://api.hcharts.cn/highcharts#Renderer)。

### Renderer

Renderer 是一个提供了原始绘图接口的对象，可以直接在图表上绘制基础的图形，包括圆形、矩形、线条、文字等，在主流浏览器中，对应的是 SVG 封装，IE8 以下则是 VML 封装。

Renderer 可以通过 chart.renderer （chart 为已经存在的图表对象）或 Highcharts.Renderer() 方式调用，对应的初始化方式有所不同：

- `chart.renderer`
- `Highcharts.Renderer(parentNode, width, height);`

其中 parentNode 表示图形希望被添加到的 html元素（dom）。

Renderer 支持链式编程，即可以在同一个表达式中多次调用相关的函数，例如：

```
chart.render.rect(
    // ... 省略代码
).attr(
    // ... 省略代码
).css(
    // ... 省略代码
);

```

更多关于 Renderer 的信息请参看 API 文档：[Renderer](http://api.hcharts.cn/highcharts#Renderer)。

### 通过 Renderer 添加文字标签

#### 1、Renderer.text()

构造方法：

```
Renderer.text(String str, Number x, Number y) 

```

参数列表：

- String str: 需要添加的文字
- Number x: 水平偏移
- Number y: 竖直偏移

[在线试一试](https://code.hcharts.cn/hcharts.cn/hhhhoD)

#### 2、Renderer.label()

Renderer.label() 支持更多高级属性，例如边框，背景等。

构造方法：

`Renderer.label (String str, Number x, Number y, String shape, Number anchorX, Number anchorY, Boolean useHTML, Boolean baseline, String className)`

参数列表：

```
String str:      标签内容
Number x:        水平偏移
Number y:        竖直偏移
String shape:    形状
Number anchorX:  如果形状中包含指示，例如 chevron 和 callout。anchorX 指定指示形状的 x 位置
Number anchorY:  如果形状中包含指示，例如 chevron 和 callout。anchorY 指定指示形状的 y 位置
Boolean useHTML: 是否开启 HTML 模式来渲染标签
Boolean baseline:是否让标签以文字的 baseline 来竖直对齐
String className:标签的父级元素 g 的类

```

![img](https://img.hcharts.cn/static/highcharts/images/docs/basic_lables_2.png)

[在线试一试](https://code.hcharts.cn/hcharts.cn/hhhhov)