# highCharts使用-介绍和安装

> 中文官网 https://www.hcharts.cn/docs
>
> 中文api https://api.hcharts.cn/highcharts

### 三款产品

Highcharts 系列软件包含 Highcharts JS，Highstock JS，Highmaps JS 共三款软件，均为纯 JavaScript 编写的 HTML5 图表库。

#### Highcharts

Highcharts 支持的图表类型有直线图、曲线图、区域图、柱状图、饼状图、散状点图、仪表图、气泡图、瀑布流图等多达 20 种图表，其中很多图表可以集成在同一个图形中形成混合图。

![hcharts](/Users/dengwei/app/webTree/articles/highcharts_study/images/hcharts.png)

#### Highstock

Highstock 是用纯 JavaScript 编写的股票图表控件，可以开发股票走势或大数据量的时间轴图表。它包含多个高级导航组件：预设置数据时间范围，日期选择器、滚动条、平移、缩放功能。

![highstock](/Users/dengwei/app/webTree/articles/highcharts_study/images/highstock.png)

#### Highmaps

Highmaps 是一款基于 HTML5 的优秀地图组件。

Highmaps 继承了 Highcharts 简单易用的特性，利用它可以方便快捷的创建用于展现销售、选举结果等其他与地理位置关系密切的交互性地图图表。



![highmaps](/Users/dengwei/app/webTree/articles/highcharts_study/images/highmaps.png)

#### 相关之间的关系

Highstock 是完全包含 Highcharts 的，是在 Highcharts 的基础上增加了更多高级功能；Highmaps 则完全独立。

#### 混合使用（重要）

A. Highcharts + Highstock 时只需要引入 highstock.js

```Html
<script src="http://cdn.hcharts.cn/highstock/highstock.js"></script> 
```

B. Highcharts + Highmaps 混合使用是需要 引入 highcharts.js + map.js

```Html
<script src="http://cdn.hcharts.cn/highcharts/highcharts.js"></script> 
<script src="http://cdn.hcharts.cn/highmaps/modules/map.js"></script> 
```

C. Highstock + Highmaps 或 Highcharts + Highstock + Highmaps 混合使用时需引入 highstock.js + map.js

```Html
<script src="http://cdn.hcharts.cn/highstock/highstock.js"></script> 
<script src="http://cdn.hcharts.cn/highmaps/modules/map.js"></script> 
```

注意：上面说到的 Highstock 是完全包含 Highcharts 的，如果在同一个页面重复引用的话会报错。

### 功能模块

功能模块是在 Highcharts 主要功能的基础做的扩展，是由官方发布的功能包，常用功能模块有：

- 更多图表类型扩展模块（`highcharts-more.js`）
- 3D 图表模块 （`highcharts-3d.js`）
- 导出功能模块（`modules/exporting.js`）
- 金字塔图表类型（`modules/funnel.js`）
- 钻取功能模块（`modules/drilldown.js`）
- 数据加载功能模块（`modules/data.js`）



使用功能模块很简单，只需要引入对应的文件即可，唯一需要注意的是保证 highcharts.js 的引用顺序是在功能模块之前。

例如启用导出功能时需要引入的文件及顺序是：

```html
<script src="http://cdn.hcharts.cn/highcharts/highcharts.js"></script> 
<script src="http://cdn.hcharts.cn/highcharts/modules/exporting.js"></script>
```

### 使用highcharts

A.使用highcharts的CDN文件

`<script src="http://cdn.hcharts.cn/highcharts/highcharts.js"></script>`

B.使用npm安装

`npm install highcharts --save`

该命令包含了 Highcharts、Highstock、Highmaps 及所有的功能模块

### 加载highcharts

引入对应的模块有如下方式

#### require

```javascript
var Highcharts = require('highcharts');

// 在 Highcharts 加载之后加载功能模块
require('highcharts/modules/exporting')(Highcharts);
// 创建图表
Highcharts.chart('container', { 
      /*Highcharts 配置*/
});
```

#### import

```javascript
import Highcharts from 'highcharts/highstock';
import HighchartsMore from 'highcharts/highcharts-more';
import HighchartsDrilldown from 'highcharts/modules/drilldown';
import Highcharts3D from 'highcharts/highcharts-3d';

HighchartsMore(Highcharts)
HighchartsDrilldown(Highcharts);
Highcharts3D(Highcharts);

Highcharts.chart('container', { 
      /*Highcharts 配置*/
});
```

>  Vue + highcharts   http://blog.jianshukeji.com/2017/09/use-highcharts-with-vue/

