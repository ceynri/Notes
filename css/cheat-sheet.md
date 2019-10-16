---
title: "CSS 小抄"
date: "2019-09-27"
---

# CSS 小抄

层叠样式表 (**C**ascading **S**tyle **S**heets)

## 目录 <!-- omit in toc -->

- [创建样式](#创建样式)
- [层叠次序](#层叠次序)
- [定位](#定位)
- [选择器](#选择器)
  - [种类](#种类)
  - [选择器分组](#选择器分组)
  - [子元素选择器](#子元素选择器)
  - [相邻兄弟选择器](#相邻兄弟选择器)
  - [伪类](#伪类)
  - [伪元素](#伪元素)
  - [属性选择器](#属性选择器)
- [框模型](#框模型)
  - [结构](#结构)
  - [边距的值复制](#边距的值复制)
  - [外边距合并](#外边距合并)
- [链接](#链接)
- [表格](#表格)
- [媒介类型](#媒介类型)
- [属性前缀](#属性前缀)
- [动画](#动画)
  - [transition](#transition)
  - [animation](#animation)
    - [cubic-bezier](#cubic-bezier)
- [参考](#参考)

<br/>

## 创建样式

**外部样式表**

外部引入：

```html
<head>
<link rel="stylesheet" href="mystyle.css">
</head>
```

`type="text/css"`现在一般都可以省略不写了，浏览器一般默认 stylesheet 都是 css。

<br/>

**内部样式表**

在 \<head> 标签里写 css：

```html
<head>
<style>
  p {margin-left: 20px;}
</style>
</head>
```

<br/>

**内联样式**

<p style="color: darkgreen; margin-left: 20px">
直接给元素添加属性：
</p>

```html
<p style="color: darkgreen; margin-left: 20px">
直接给元素添加属性：
</p>
```

<br/>

## 层叠次序

按优先度由低到高：

- 浏览器缺省设置
- 外部样式表
- 内部样式表
- 内联样式

<br/>

## 定位

说到 CSS 定位，就离不开 position 属性。position 的六个属性值：

- **static**（默认）  
  默认值，元素出现在正常的流中。

- **relative**  
  相对定位，元素框相对原位置偏移某个距离，元素仍然会占据原来的空间。

- **absolute**  
  绝对定位，相对于其第一个非 static 定位的父元素定位，在文档流完全删除。

- **fixed**  
  绝对定位，相对于浏览器窗口进行定位。

- **sticky**  
  （CSS3 新增属性）类似于 relative 与 fixed 的混合：一开始是 relative，随着滚动超过阈值时转变为 fixed 定位。

- **inherit**  
  从父元素继承 position 属性的值。

使用绝对定位后，需要使用 top/bottom/left/right/z-index 等属性去调整位置。

<br/>

## 选择器

### 种类

**按选择对象：**

- 元素选择器 `tagname`
- id 选择器 `#id`
- 类选择器 `.class-name`
- 属性选择器 `[property]`
- 属性和值选择器 `[property=value]`

**按选择方式：**

- 派生选择器（上下文选择器）
  - 后代选择器
  - 子元素选择器
  - 相邻兄弟选择器
- 伪类/伪元素

<br/>

### 选择器分组

使用逗号分隔，不加逗号则为后代选择器：

```css
/* 选择 p 和 span */
p, span { ... }
/* 选择作为 p 的后代的 span */
p span { ... }
```

当 class 与 id 用来作为某选择器的后代时，之间不用加空格：

```css
#sidebar p { ... }
div#sidebar { ... }
```

<br/>

### 子元素选择器

```css
/* “>”左右的空格是可选的 */
h1 > strong { ... }
```

<br/>

### 相邻兄弟选择器

```css
/* 会选中紧接在 h1 后的 p */
h1 + p { ... }
```

<br/>

### 伪类

伪类是描述被选择的元素的“状态/性质”的。

| 属性              | 描述                          | CSS |
| ----------------- | ----------------------------- | --- |
| :active           | 被激活的元素                  | 1   |
| :hover            | 当鼠标悬浮在元素上方          | 1   |
| :link             | 未被访问的链接                | 1   |
| :visited          | 已被访问的链接                | 1   |
| :focus            | 拥有键盘输入焦点的元素        | 2   |
| :first-child      | 作为父元素第一个子元素的元素  | 2   |
| :lang(*language*) | 带有指定 lang 属性的元素      | 2   |
| :nth-child(*n*)   | 作为父元素第*n*个子元素的元素 | 3   |

常见容易误导的“p:first-child”并非选择“p 的第一个子元素”，而是选择“作为其父元素的第一个子元素的 p”。

<br/>

### 伪元素

伪元素更多地是用来选择被选择元素的“特定部分/附属”的。

| 属性          | 描述               | CSS版本 |
| ------------- | ------------------ | ------- |
| :first-letter | 文本的第一个字母   | 1       |
| :first-line   | 文本的首行         | 1       |
| :before       | 在元素之前添加内容 | 2       |
| :after        | 在元素之后添加内容 | 2       |

注意伪类、伪元素冒号前后都不应有空格。

<br/>

### 属性选择器

- 属性选择器 `[property]`
- 属性和值选择器 `[property=value]`

| 选择器             | 描述                 |
| ------------------ | -------------------- |
| [attribute]        | 指定属性             |
| [attribute=value]  | 指定属性和值         |
| [attribute~=value] | 属性值中包含指定词汇 |
| [attribute*=value] | 包含指定值           |

Ps:这玩意真的用过么¿

<br/>

> 更多选择器索引参考：[W3School CSS 选择器参考手册](https://www.w3school.com.cn/cssref/css_selectors.asp)

<br/>

## 框模型

### 结构

由内到外：

- element
  - width
  - height
- padding
- border
- margin

![box-model.jpg](https://i.loli.net/2019/09/28/h9wWfyePTgOJ5IV.jpg)

::: warning 注意

对于一个元素，width 属性指的是内容区的宽度而不包含 padding、border（这两个仅在IE6之前的版本会包含在 width 中）。

:::

<br/>

### 边距的值复制

边距的四个值按照 上、右、下、左 的顺时针排序。

| 值的个数 | 效果            |
| -------- | --------------- |
| 4个      | 上 右 下 左     |
| 3个      | 上 (左=右) 下   |
| 2个      | (上=下) (左=右) |
| 1个      | (上=右=下=左)   |

![value-of-replication](https://www.w3school.com.cn/i/ct_css_margin_value.gif)

例子：

| 简写                          | 实际                              |
| ----------------------------- | --------------------------------- |
| padding: 10px;                | padding: 10px 10px 10px 10px;     |
| padding: 10px 0.25em;         | padding: 10px 0.25em 10px 0.25em; |
| padding: 10px 0.25em 2ex;     | padding: 10px 0.25em 2ex 0.25em;  |
| padding: 10px 0.25em 2ex 20%; | -                                 |

<br/>

### 外边距合并

多个垂直外边距发生“接触”时会相互合并并取其中的最大值。

这甚至会发生在内容为空的元素本身的上外边距与下外边距、元素的外边距与元素内的元素的外边距。

![margin-merge1](https://www.w3school.com.cn/i/ct_css_margin_collapsing_example_4.gif)

![margin-merge2](https://www.w3school.com.cn/i/ct_css_margin_collapsing_example_2.gif)

<br/>

## 链接

- a:link - 未访问的链接
- a:visited - 已访问的链接
- a:hover - 鼠标指针位于链接的上方
- a:active - 链接被点击的时刻

同时设置多个状态时，需要注意顺序： a:hover 必须位于 a:link、a:visited 之后，a:active 必须位于最后。

<br/>

## 表格

奇数行上色：

```css
.table-name tr.alt td
{
    background-color:#EAF2D3;
}
```

<br/>

## 媒介类型

用来指定对于不同的设备访问采用不同的 CSS 样式。

以下例子在浏览器显示页面或者打印页面时采用不同的字体与字号：

```css
@media screen {
    p.test {font-family:verdana,sans-serif; font-size:14px}
}

@media print {
    p.test {font-family:times,serif; font-size:10px}
}
```

除了判断使用设备种类以外，对于响应式布局，我们也可以通过检查屏幕的宽度来判断是否是 PC/移动设备。

```css
/*  移动设备  */
@media screen and (min-device-width: 480px) and (max-device-width: 750px){
    ...
}
/*  PC  */
@media screen and (min-width: 960px){
    ...
}
```

关于 min/max-width 与 min/max-device-width 的区别：

- width 获得的是浏览器宽度，device-width 是设备屏幕的宽度。
- min/max-width 会随着浏览器窗口的大小变化而变化，往往用于 PC 端不同页面尺寸。
- min/max-device-width 则不会随着浏览器或者手机由竖屏转向横屏而变化，适用于手机端适配。

<br/>

## 属性前缀

为了兼容性，前端在许多方面产生了对不同浏览器进行单独定义的情况。CSS 亦不例外，某些为了兼容旧版本浏览器的历史遗留问题，或者使用某些浏览器最新的、暂未统一标准的实验性属性，都有可能出现带属性前缀的属性。

常见属性前缀：

- `-webkit-`代表 safari、chrome 私有属性
- `-moz-`代表 firefox 浏览器私有属性
- `-ms-`代表 ie 浏览器私有属性
- `-o-`代表 Opera 浏览器

值得注意的是：从网上阅读 CSS 文章时也要注意文章的发表日期，有可能以前存在的兼容性问题在新版本中已经不用考虑了。

<br/>

## 动画

**[未完成]**

### transition

```css
span {
    transition: <prop> <time>;
    -webkit-transition: <prop> <time>;
}
```

如：
```css
span {
    transition: all 0.5s;
    /* 或者 */
    transition: background 0.5s;
}
```

- transform-origin
    ```css
    div {
        transform-origin: x-axis y-axis z-axis;
    }
    ```
    
    用于修旋转的中心的位置。

    默认值为`50% 50% 0`

<br/>

### animation

#### cubic-bezier

```css
div {
animation: <duration> <scope> cubic-bezier(<x1>, <y1>, <x2>, <y2>) [infinite];
}
```
常用预设属性

- **linear** cubic-bezier(0,0,1,1) / cubic-bezier(1,1,0,0)
- **ease** cubic-bezier(0.25,0.1,0.25,1)
- **ease-in** cubic-bezier(0.42,0,1,1)

<br/>

## 参考

- W3School CSS 教程：<https://www.w3school.com.cn/css/index.asp>
- W3School CSS 参考手册：<https://www.w3school.com.cn/cssref/index.asp>
- 掘金 | CSS布局说：<https://juejin.im/post/59c9baac5188253fbe465bfd> | [@zimo](https://juejin.im/user/59354d1eac502e0068b3305d)