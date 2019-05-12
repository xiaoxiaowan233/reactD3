##目录

|—gallery : antd + 平时练习的d3项目

|——public

|——|——index.html :主页面

|——src

|——|——index.js : react 加载入口，可以在package.json中配置

|——|——d3GalleryHome.js : 定义页面布局

|——|——d3GalleryNav.js : 定义导航

|——|——styles.css : 样式文件

|——|——|——barchart ： 条形图

|——|——|——|——barchartList.js: 控制barchart显示的模块（根据路由确定显示的条形图）

|——|——|——|——barchartListData.js: 导航到条形图时表中数据，d3绘制条形图svg宽度，高度定义

|——|——|——|——d3code: d3代码，结合d3库完成条形图的绘制

|——|——|——brush 

|——|——|——|——brushList.js: 控制brush显示的模块（根据路由确定显示的brush）

|——|——|——|——brushListData.js: 导航到brush表中数据，d3绘制brush时svg宽度，高度定义

|——|——|——|——d3code: d3代码，结合d3库完成brush的绘制

|——|——|——hierarchy

|——|——|——|——hierarchyList.js: 控制hierarchy显示的模块（根据路由确定显示的层级图）

|——|——|——|——hiearchyListData.js: 导航到hierarchy表中数据，d3绘制条形图svg宽度，高度定义

|——|——|——|——d3code: d3代码，结合d3库完成hierarchy图的绘制

|——|——|——linechart

|——|——|——|——linechartList.js: 控制linechart显示的模块（根据路由确定显示的折线图）

|——|——|——|——linechartListData.js: 导航到linechart表中数据，d3绘制折线图svg宽度，高度定义

|——|——|——|——d3code: d3代码，结合d3库完成折线图的绘制

|——|——|——piechart

|——|——|——|——piechartList.js: 控制piechart显示的模块（根据路由确定显示的饼图）

|——|——|——|——piechartListData.js: 导航到piechart表中数据，d3绘制饼图svg宽度，高度定义

|——|——|——|——d3code: d3代码，结合d3库完成饼图的绘制



###description

导航到barchart时，在d3GalleryHome.js中定义的布局，有两个div下图紫色&粉色部分，第一个div的组件为`ChartTypeList`，第二个div由路由控制，显示表中选中的d3图表

```react
<div style={{ padding: 24, background: "#fff", minHeight: 360 }}>
      <Route path="/:chartType" component={ChartTypeList} />
</div>

<div
className="chartDisplay"
style={{ padding: 24, minHeight: 500 }}
ref="myContent"
>
<Route exact path="/barchart/:id" component={barchartDisplay} />
<Route exact path="/linechart/:id" component={linechartDisplay} />
<Route exact path="/piechart/:id" component={piechartDisplay} />
<Route exact path="/brush/:id" component={brushDisplay} />
<Route exact path="/hierarchy/:id" component={hierarchyDisplay} />
</div>
```

![gallery01](/Users/liurenwan/Desktop/react/img/gallery01.png)



* 紫色div

紫色div加载的component在`d3ChartType.js`中定义

```react
import React from "react";
import { barchartList } from "./barchart/barchartList.js";
import { linechartList } from "./linechart/linechartList.js";
import { piechartList } from "./piechart/piechartList.js";
import { brushList } from "./brush/brushList.js";
import { hierarchyList } from "./hierarchy/hierarchyList.js";

export class ChartTypeList extends React.Component {
  render() {
    const curURL = this.props.match.url;
    switch (curURL) {
      case "/barchart":
        return barchartList();
      case "/linechart":
        return linechartList();
      case "/piechart":
        return piechartList();
      case "/brush":
        return brushList();
      case "/hierarchy":
        return hierarchyList();
      default:
        break;
    }

    return (
      <div>
        <h2>to do</h2>
      </div>
    );
  }
}

```



* 红色div

上述代码中，当红色区域为`/barchart/:id`时，展示组件`barchartDisplay`,这个组件在`barchart/barchartList.js中定义`

```react
<Route exact path="/barchart/:id" component={barchartDisplay} />
```

barchartDisplay组件， 根据路径，选中不同的条形图

```react
export function barchartDisplay({ match }) {
  switch (match.params.id) {
    case "1":
      return <D3Barchart01 match={match} />;
    case "2":
      return <D3Barchart02 match={match} />;
    case "3":
      return <D3Barchart03 match={match} />;
    case "4":
      return <D3Barchart04 match={match} />;
    case "5":
      return <D3Barchart05 match={match} />;
    case "6":
      return <D3Barchart06 match={match} />;
    case "7":
      return <D3Barchart07 match={match} />;
    case "8":
      return <D3Barchart08 match={match} />;
    case "9":
      return <D3Barchart09 match={match} />;
    case "10":
      return <D3Barchart10 match={match} />;
    case "11":
      return <D3Barchart11 match={match} />;
    case "12":
      return <D3Barchart12 match={match} />;
    default:
      break;
  }
  return <div>barchart to do </div>;
}
```

* 其他类型图显示类似



## codesandbox

[d3 + react](https://codesandbox.io/s/w280w2x0m8)



