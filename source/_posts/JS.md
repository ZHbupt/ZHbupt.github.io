---
title: JS
date: 2022-09-05 20:46:04
tags:
---
## e.getBoundingClientRect()
添加节点的布局位置的查询请求，相对于显示区域，以像素为单位，获取节点信息

```js
// ps：.content-header为类名
query.select('.header').boundingClientRect((res) => {this.headerHeight = res.height})
```



# moment

## moment().startOf(str) / [moment().endOf(str)](https://momentjscom.readthedocs.io/en/latest/moment/03-manipulating/04-end-of/)

```js
// 通过将原始的 moment 设置为时单位的开头/结尾来对其进行更改。
moment().startOf('year');  设置为今年的1月1日的00:00:00
moment().endOf('month');   设置为月末一天的23:59:59
```

## [moment().add()](http://momentjs.cn/docs/manipulating/add.html) / [moment().subtract()](http://momentjs.cn/docs/manipulating/subtract.html)

```js
// .add()
// 通过增加时间来改变原始的 moment。
// 若要增加时间，则传入要增加的时间的键、以及要增加的数量。

moment().add(Number, String);
moment().add(7, 'days');

moment().add(Duration);
moment().add(Object);

// .substract()
// 通过减去时间来改变原始的 moment。

moment().subtract(Number, String);
moment().subtract(60, 'seconds');

moment().subtract(Duration);
moment().subtract(Object);

```

# 同步/异步

![img](https://upload-images.jianshu.io/upload_images/3069847-240b0e152da84b94.png?imageMogr2/auto-orient/strip|imageView2/2/format/webp)

