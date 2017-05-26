---
title: react native 学习笔记
---

## Plan

- 首先看完 The Basics 所有章节
- 记录下重点内容，以及可能是坑的东东。所谓的坑，大多数是没搞清楚罢了。
  - 重点记录章节中标红的部分，注意事项、与 web 差异等


## Notes

- flex 布局
  - flex 参数值接受一个值，数字类型；与 web 不同。
  - flex 元素的父元素必须指定了 flex 属性 或者 同时制定 width & height 属性。
  - flex 在 rn 中默认的 flexDirection 是 column；web 中是 row。
  - alignItems: stretch 时 cross axis 不能制定固定大小（fiexed demension）
- network
  - 支持 fetch api
  - 支持 await/async 语法
  - ios 默认开启 ATS(App Transport Security)，即默认屏蔽非 https 的请求。
  - 支持 xhr，native 侧的 xhr 没有 cors 的限制

