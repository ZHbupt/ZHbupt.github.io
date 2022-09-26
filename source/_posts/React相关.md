---
title: React相关
date: 2022-09-14 20:43:43
tags:
---

## [react hooks](https://zh-hans.reactjs.org/docs/hooks-reference.html)

在渲染时，每个没有hooks的变量（包括方法）都会重新渲染，如有hooks则由依赖项决定是否重新渲染，重新run意味着地址发生变化；

因此在每次渲染时，有hooks的变量（包括方法）如果变化，但没有被监听到，则会取到上一次的地址，产生错误。

- **`useMemo`**
    使用场景：1.变量内有数据刷新时，使变量不随之刷新（变量刷新可能导致死循环）

* * *

- **`useCallback`**
- 方法中有变量地址变化时，方法地址才变化

* * *

- **`useEffect`**
    ==（return相当于vue beforeDestroy?==）
    赋值给 useEffect 的函数会在组件每轮渲染到屏幕之后执行。

* * *

- **`useLayoutEffect`**
    赋值给 useEffect 的函数在下一次绘制前被同步执行。（eg：对用户可见的dom变更）

# UmiJs

[约定式路由](https://juejin.cn/post/6844904197331091464)


