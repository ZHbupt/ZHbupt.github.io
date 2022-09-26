---
title: TS
date: 2022-09-03 20:46:46
tags:
---
# Partial

## typescript忽略类型检查

- 单行忽略(添加到特定行的行前来忽略这一行的错误)

```tsx
// @ts-ignore
```

- 跳过对整个文件的检查 (添加文件首行)

```tsx
// @ts-nocheck
```

- 对某些文件的检查(添加文件首行)

```tsx
// @ts-check
```


