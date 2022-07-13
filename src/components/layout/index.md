---
group:
  title: 布局组件
---

## Layout 布局

通过基础的 24 分栏，迅速简便的创建布局。


### 基础布局

使用单一分栏创建基础的栅格布局。

通过 row 和 col 组件，并通过 col 组件的 `span` 属性我们就可以自由地组合布局，col组件的 `span` 属性默认是24。

```tsx
import React from 'react'
import { ElCol, ElRow } from 'umaso'

export default () => (
  <>
    {/* 在 ElRow中，ElCol直接占 24份 */}
    <ElRow className="row-bg">
      <ElCol span={24}><div className="grid-content bg-purple-dark"></div></ElCol>
    </ElRow>

    {/* 在 ElRow中，左 右 ElCol占 12份 */}
    <ElRow className="row-bg">
      <ElCol span={12}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={12}><div className="grid-content bg-purple-light"></div></ElCol>
    </ElRow>

    {/* 在 ElRow中，左 中 右 ElCol各占 8份 */}
    <ElRow className="row-bg">
      <ElCol span={8}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={8}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={8}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>

    {/* 在 ElRow中，四个 ElCol各占 6份 */}
    <ElRow className="row-bg">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple-light"></div></ElCol>
    </ElRow>

    {/* 在 ElRow中，六个 ElCol各占 4份 */}
    <ElRow className="row-bg">
      <ElCol span={4}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple-light"></div></ElCol>
    </ElRow>

    <br/>

    <style>{FillStyles()}</style>
  </>
)

function FillStyles() {
  return `
  .ElRow {
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 5px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
  `
}
```

### 分栏间隔

分栏(ElCol)之间存在间隔。

Row 组件 提供 `gutter` 属性来指定每一栏之间的间隔，默认间隔为 0。


```tsx
import React from 'react'
import { ElCol, ElRow } from 'umaso'

export default () => (
  <>
    {/* gutter=20 代表着： ElRow 左右margin 都是 -10，ElCol 左右padding +10 */}
    <ElRow gutter={20} className="row-bg">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>

    <br/>

    <style>{FillStyles()}</style>
  </>
)

function FillStyles() {
  return `
  .ElRow {
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 5px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
  `
}
```

### 混合布局

通过基础的 1/24 分栏任意扩展组合形成较为复杂的混合布局。



```tsx
import React from 'react'
import { ElCol, ElRow } from 'umaso'

export default () => (
  <>
    <ElRow gutter={20} className="row-bg">
      <ElCol span={16}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={8}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow gutter={20} className="row-bg">
      <ElCol span={8}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={8}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow gutter={20} className="row-bg">
      <ElCol span={4}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={16}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={4}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>

    <br/>

    <style>{FillStyles()}</style>
  </>
)

function FillStyles() {
  return `
  .el-row {
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 5px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
  `
}
```

### 分栏偏移

分栏支持偏移指定的份数。

通过制定 ElCol 组件的 `offset` 属性可以指定分栏偏移的份数。

```tsx
import React from 'react'
import { ElCol, ElRow } from 'umaso'

export default () => (
  <>
    <ElRow gutter={20} className="row-bg">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6} offset={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow gutter={20} className="row-bg">
      <ElCol span={6} offset={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6} offset={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow gutter={20} className="row-bg">
      <ElCol span={12} offset={6}>
        <div className="grid-content bg-purple"></div>
      </ElCol>
    </ElRow>

    <br/>

    <style>{FillStyles()}</style>
  </>
)

function FillStyles() {
  return `
  .el-row {
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 5px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
  `
}
```

### 对齐方式

通过 `flex` 布局来对分栏进行灵活的对齐。

将 `type` 属性赋值为 'flex'，可以启用 flex 布局，并可通过 `justify` 属性来指定 start, center, end, space-between, space-around 其中的值来定义子元素的排版方式，`justify` 属性默认为 start 。

```tsx
import React from 'react'
import { ElCol, ElRow } from 'umaso'

export default () => (
  <>
    <ElRow type="flex" gutter={4} className="row-bg">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow type="flex" gutter={4} className="row-bg" justify="center">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow type="flex" gutter={4} className="row-bg" justify="end">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow type="flex" gutter={4} className="row-bg" justify="space-between">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>
    <ElRow type="flex" gutter={4} className="row-bg" justify="space-around">
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple-light"></div></ElCol>
      <ElCol span={6}><div className="grid-content bg-purple"></div></ElCol>
    </ElRow>

    <br/>

    <style>{FillStyles()}</style>
  </>
)

function FillStyles() {
  return `
  .el-row {
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 5px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
  `
}
```


### 响应式布局

参照了 Bootstrap 的 响应式设计，预设了五个响应尺寸：`xs`、`sm`、`md`、`lg` 和 `xl`。  
- xs: 767px  
- sm: 768px  
- md: 992px  
- lg: 1200px  
- xl: 1920px  

```tsx
import React from 'react'
import { ElCol, ElRow } from 'umaso'

export default () => (
  <>
    <ElRow gutter={10} className="row-bg" >
      <ElCol xs={8} sm={6} md={4} lg={3} xl={1}>
        <div className="grid-content bg-purple"></div>
      </ElCol>
      <ElCol xs={4} sm={6} md={8} lg={9} xl={11}>
        <div className="grid-content bg-purple-light"></div>
      </ElCol>
      <ElCol xs={4} sm={6} md={8} lg={9} xl={11}>
        <div className="grid-content bg-purple"></div>
      </ElCol>
      <ElCol xs={8} sm={6} md={4} lg={3} xl={1}>
        <div className="grid-content bg-purple-light"></div>
      </ElCol>
    </ElRow>
    <ElRow gutter={10} className="row-bg" >
      {/*  响应式属性 xs sm md lg xl 都支持对象的形式，
          对象中可传递 span 分栏占用的份数  和 offset 分栏指定偏移的份数 */}
      <ElCol
        xs={{ span: 8, offset: 2 }}
        sm={{ span: 6, offset: 4 }}
        md={{ span: 4, offset: 6 }}
        lg={{ span: 3, offset: 7 }}
        xl={{ span: 1, offset: 9 }}>
        <div className="grid-content bg-purple"></div>
      </ElCol>
    </ElRow>

    <br/>

    <style>{FillStyles()}</style>
  </>
)

function FillStyles() {
  return `
  .el-row {
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 5px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
  `
}
```

## Layout API

### ElRow

| 参数    | 说明                                  | 类型   | 可选值                                      | 默认值 |
| ------- | ------------------------------------- | ------ | ------------------------------------------- | ------ |
| gutter  | 栅格间隔                              | number | —                                           | 0      |
| type    | 布局模式，可选 flex，现代浏览器下有效 | string | —                                           | —      |
| justify | flex 布局下的水平排列方式             | string | start/end/center/space-around/space-between | start  |
| align   | flex 布局下的垂直排列方式             | string | top/middle/bottom                           | top    |
| tag     | 自定义元素标签                        | string | html标签                                    | div    |

### ElCol

| 参数   | 说明                                   | 类型                                        | 可选值   | 默认值 |
| ------ | -------------------------------------- | ------------------------------------------- | -------- | ------ |
| span   | 栅格占据的列数                         | number                                      | —        | 24     |
| offset | 栅格左侧的间隔格数                     | number                                      | —        | 0      |
| push   | 栅格向右移动格数                       | number                                      | —        | 0      |
| pull   | 栅格向左移动格数                       | number                                      | —        | 0      |
| xs     | `<768px` 响应式栅格数或者栅格属性对象  | number/object (例如： {span: 4, offset: 4}) | —        | —      |
| sm     | `≥768px` 响应式栅格数或者栅格属性对象  | number/object (例如： {span: 4, offset: 4}) | —        | —      |
| md     | `≥992px` 响应式栅格数或者栅格属性对象  | number/object (例如： {span: 4, offset: 4}) | —        | —      |
| lg     | `≥1200px` 响应式栅格数或者栅格属性对象 | number/object (例如： {span: 4, offset: 4}) | —        | —      |
| xl     | `≥1920px` 响应式栅格数或者栅格属性对象 | number/object (例如： {span: 4, offset: 4}) | —        | —      |
| tag    | 自定义元素标签                         | string                                      | html标签 | div    |


## 响应式相关的隐藏类

参照了 Bootstrap 的 响应式设计，也提供了一系列类名，用于在某些条件下隐藏元素。这些类名可以添加在任何 DOM 元素或自定义组件上。如果需要，请自行引入以下文件：

```js
import 'umaso/lib/theme-chalk/display.css'
```
类名中的关键字含义如下：

- hidden：隐藏
- xs：视口`<768px` 时
- sm: 视口`≥768px` 时
- md: 视口`≥992px` 时
- lg: 视口`≥1200px` 时
- xl: 视口`≥1920px` 时
- only：刚好
- and: 同时
- down：以下
- up：以上

包含的类名及其含义如下：

- `hidden-xs-only` - 当视口刚好在 `xs` 尺寸时隐藏
- `hidden-sm-only` - 当视口刚好在 `sm` 尺寸时隐藏
- `hidden-sm-and-down` - 当视口在 `sm` 及以下尺寸时隐藏
- `hidden-sm-and-up` - 当视口在 `sm` 及以上尺寸时隐藏
- `hidden-md-only` - 当视口刚好在 `md` 尺寸时隐藏
- `hidden-md-and-down` - 当视口在 `md` 及以下尺寸时隐藏
- `hidden-md-and-up` - 当视口在 `md` 及以上尺寸时隐藏
- `hidden-lg-only` - 当视口刚好在 `lg` 尺寸时隐藏
- `hidden-lg-and-down` - 当视口在 `lg` 及以下尺寸时隐藏
- `hidden-lg-and-up` - 当视口在 `lg` 及以上尺寸时隐藏
- `hidden-xl-only` - 当视口刚好在 `xl` 尺寸时隐藏
