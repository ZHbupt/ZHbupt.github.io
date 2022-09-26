---
title: Vue相关
date: 2022-09-03 20:44:51
tags:
---
# 微信小程序

# Uni-app

## 模块化路由

[pages.json配置页面路由](https://www.wenjiangs.com/doc/opeuhodusr)

使用pages.json 文件用来对 uni-app 进行全局配置
**注：tab页面只可以放在主包中；分包不能和主包文件放在同一个文件夹中**

```json
//pages数组
// 主包（越小越好）
"pages": [
    {
      "path": "pages/defaultLogin/index",
      "style": {
        "navigationBarTitleText": "",
        "enablePullDownRefresh": false,
        "navigationStyle": "custom"
      }
    },
    {
      "path": "pages/index/index",
      "style": {
        "navigationBarTitleText": "首页",
        "enablePullDownRefresh": true,
        "navigationStyle": "custom",
        "usingComponents": {}
      }
    },
    {
      "path": "pages/estate-list/index",
      "style": {
        "navigationStyle": "custom",
        "enablePullDownRefresh": true
      }
    }
  ],
 // 分包
  "subPackages": [
    {
      "root": "pages/login",
      "pages": [
        {
          "path": "byMobile/index",
          "style": {
            "navigationBarTitleText": "",
            "enablePullDownRefresh": false
          }
        },
        {
          "path": "userAgreement/index",
          "style": {
            "navigationBarTitleText": "用户协议",
            "enablePullDownRefresh": false
          }
        }
      ]
    },
    {
      "root": "pages/statistics",
      "pages": [
        {
          "path": "analyze/index",
          "style": {
            "navigationBarTitleText": "",
            "enablePullDownRefresh": true,
            "navigationStyle": "custom"
          }
        }, 
        {
          "path": "customer-list/index",
          "style": {
            "navigationBarTitleText": "客户列表",
            "enablePullDownRefresh": true
          }
        }
      ]
    }
  ]
    
  
```

[easycom自动引入组件](https://uniapp.dcloud.io/collocation/pages?id=easycom)

```json
// 自动从@/components引入以v-、b-开头的组件，使用到该名称组件不需import
"easycom": {
    "^v-(.*)": "@/components/v-$1/index.vue",
    "^b-(.*)": "@/components/b-$1/index.vue",
  }

// 注意！！！！！
// 以上为例，如果有其他以v-、b-开头的组件不在@/components中，未自行引入会报错
```

## [scroll-view](https://uniapp.dcloud.io/component/scroll-view.html)

`@scroll`在iOS松手时才触发的问题：添加`enhanced`属性

`scroll-top`如果本次和上次相同，设置不生效

```js
this.scrollTop = this.scrollTop === 0 ? 0.001 : 0
// 或者
this.scrollTop = Math.random()
```



## 独有 API

`uni.navigateTo({url})`页面跳转
- 不生效？
  -  url前加“/”
  -  在pages.json中配置要跳转的页面
  `uni.navigateBack()`返回原页面
  `uni.setNavigationBarTitle({title})`动态设置标题

## 一些生命周期
`onShow`、 `onHide`等生命周期在页面级使用；对应组件级生命周期为 `onPageShow`、`onPageHide`

> [uni-app黑魔法：小程序自定义组件运行到H5平台](https://ask.dcloud.net.cn/article/37086)

`onPageScroll`

## 分包复用

自动化分包：[小程序跨分包复用代码方案](https://imbant.github.io/blog/2021/07/20/%E5%B0%8F%E7%A8%8B%E5%BA%8F%E8%B7%A8%E5%88%86%E5%8C%85%E5%A4%8D%E7%94%A8%E4%BB%A3%E7%A0%81%E6%96%B9%E6%A1%88/)



# vue-class-components
# [vue-property-decorator](https://github.com/kaorun343/vue-property-decorator)

## @Prop 

- type 
可能为多种类型eg： `[Number, String]`



# 方法

[v-model](https://cn.vuejs.org/v2/guide/components-custom-events.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BB%84%E4%BB%B6%E7%9A%84-v-model)

# diff算法
判断节点复用，减少dom操作--->virtual Dom

只用key--->一些情况需要判断节点类型

# 希望使用的规范

## 刷新使用时间戳

eg：

```typescript
@Prop({ type: Number, default: new Date().getTime() })
  refreshTimestamp!: number
```






