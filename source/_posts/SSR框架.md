---
title: SSR框架
date: 2022-09-17 20:31:22
tags:
---

## 1. 两种渲染模式

### **SSR**

服务器端渲染 Server Side Render

传统服务端渲染：在服务端完成页面HTML的拼接处理，然后发送给浏览器，客户端只需要解析HTML。

<img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e1ed57e67c4445eeaef4b608e3b2fad9~tplv-k3u1fbpfcp-zoom-in-crop-mark:3024:0:0:0.awebp"  alt="image.png" style="zoom:50%;">



现代服务端渲染（同构渲染）：

<img src="https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/aee3f30e783e4f56871b2465e8bce3de~tplv-k3u1fbpfcp-zoom-in-crop-mark:3024:0:0:0.awebp?" alt="image.png" style="zoom:50%;" />

> SPA（single-page application）：单页面应用程序
>
> 通过动态重写当前页面来与用户交互，这种方法避免了页面之间切换打断用户体验。
>
> 在单页应用中，所有必要的代码（`HTML`、`JavaScript`和`CSS`）都通过单个页面的加载而检索，或者根据需要（通常是为响应用户操作）动态装载适当的资源并添加到页面，页面在任何时间点都不会重新加载，也不会将控制转移到其他页面。
>
> `react`、`vue`、`angular`、`ember`都属于SPA
>
> ps：https://juejin.cn/post/6975047761112596494
>
> ​        https://juejin.cn/post/6909849288206745614
>
> ​        https://juejin.cn/post/7104291213901037599

### **CSR**

客户端渲染 Client Side Render 

客户端请求时HTML为静态文件，在客户端自行根据JS生成DOM，首屏耗时较长。

<img src="https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/095b932a863a4eb591360ac29dc8d198~tplv-k3u1fbpfcp-zoom-in-crop-mark:3024:0:0:0.awebp?" alt="image.png" style="zoom:50%;" />



> ##### 如何判断当前页面是 SSR 还是 CSR？
>
> 查看网页源代码，如果 `<div id="root">` DOM 里的元素不为空，则是 SSR，否则为 CSR。

## 2. SSR

**核心：同构**

> 同构：客户端渲染和服务端渲染的整合
>
> 同一套代码在**服务端**执行一次，用于**服务端渲染**，在**客户端**执行一次，用于**接管页面的交互**



**优点：**

- **利于 SEO 搜索引擎收录** ==> 同步：搜索引擎爬虫是不会等待异步请求数据结束后再抓取信息的
- **加快首屏呈现时间** ==> SSR 服务器渲染标记在服务端渲染 html 后即可显示，而传统 SPA 需完整的 JS 下载完成才可执行
- 更快的数据库连接 ==> 数据获取过程在首次访问时在服务端完成，相比于从客户端获取，可能有更快的数据库连接



**缺点：**

- 程序需要具有通用性
- 传统ssr页面交互能力有限
- 运行环境单一 ==> 程序需处于 **node.js server** 运行环境。
- CPU消耗大，高流量场景需采用缓存策略
- 项目复杂度较大



> 几篇讲解的文章：
>
> - [vue官网SSR介绍](https://cn.vuejs.org/guide/scaling-up/ssr.html#server-side-rendering-ssr)
> - [从传统服务端渲染到客户端渲染再到现代化的服务端渲染](https://juejin.cn/post/7082711258952105992)
> - [一文吃透 React SSR 服务端渲染和同构原理](https://juejin.cn/post/6844903943902855176)
> - [React 中同构（SSR）原理脉络梳理](https://juejin.cn/post/6844903694870265870)
>



## [UmiJS](https://v3.umijs.org/zh-CN/docs/ssr)

> #### 预渲染
>
> 预渲染与服务端渲染唯一的不同点在于**渲染时机**，服务端渲染的时机是在用户访问时执行渲染（即**服务时渲染**，数据一般是最新的），预渲染的时机是在项目构建时，当用户访问时，数据不一定是最新的（如果数据**没有实时性**，则可以直接考虑预渲染）。
>
> 预渲染（Pre Render）在构建时执行渲染，将渲染后的 HTML 片段生成静态 HTML 文件。无需使用 web 服务器实时动态编译 HTML，适用于**静态站点生成**。
>
> #### [流式渲染](https://juejin.cn/post/7064759195710521381)
>
> 把 HTML 分块通过网络传输，然后客户端收到分块后逐步渲染，提升页面打开时的用户体验。使用占位符（骨架屏），待准备好择使用有效的组件填充。
>
> 背景：可能在SSR中，存在某个组件数据耗时久，对整个HTML生成产生阻塞；在 React SSR 中不支持客户端渲染常用的代码分割组合`React.lazy`和`Suspense`。

[缺陷](https://blog.csdn.net/supming1/article/details/109562620)

- 本地开发的时候，每次修改代码，node都会重启，此时服务器无法访问，开发效率低；
- 服务端渲染时，如果开启按需加载，会componentDidMount会执行两次

## [next.js](https://www.nextjs.cn/)

用于 生产环境的 React 框架

## [ssr-fc](https://doc.ssr-fc.com/)