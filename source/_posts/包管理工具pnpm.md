---
title: 包管理工具
date: 2022-09-29 19:28:38
tags:
---
# 包管理工具发展
## npm v3发布前
#### 处理依赖
```
node_modules
├── A
│   └── node_modules
│       └── foo
└── B
    └── node_modules
        └── foo
```
> **缺陷：**
> 层层嵌套，路径过长，可能发生依赖包找不到的问题
> 同一个包可能会有多个副本存在
## npm v3
#### 处理依赖
```
node_modules
├── A
├── B  
└── foo
```
> **优化：**
> 节约空间
>
> **缺陷：**
> 1.项目/包可以访问到并不依赖的包，可能产生安全问题
> 2.扁平化算法复杂，install慢
> 3.有些包不能被拉平，只有在指定node_modules下才能正常工作
> 4.不同包依赖同一个包的版本不同

## yarn
#### 处理依赖
与 npm v3 相同

## pnpm
#### 处理依赖
```
node_modules
├── foo -> ./.pnpm/foo@1.0.0/node_modules/foo
└── .pnpm
    ├── bar@1.0.0
    │   └── node_modules
    │       └── bar -> <store>/bar
    └── foo@1.0.0
        └── node_modules
            ├── foo -> <store>/foo
            └── bar -> ../../bar@1.0.0/node_modules/bar
```
> **优化：**
> 1.所有包在一级子目录下，保持了npm文件结构（只能访问自身依赖的包），依赖用软链接关联，节省了空间，同时也加快了安装速度
> 2.同一个包下分版本号存储，包拉平后不同版本的包都会保留，不会互相影响

##### 核心：
将所有的包都存放在一个资源仓库中，而每个项目的 node_modules 通过软链接的形式将包链接到资源仓库中

# pnpm + monorepo
1.初始化  `pnpm init`





