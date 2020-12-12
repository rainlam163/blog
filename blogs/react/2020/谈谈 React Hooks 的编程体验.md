---
title: 谈谈 React Hooks 的编程体验
date: 2020-12-12
tags:
 - React
 - React Hooks
categories: 
 - React
---

::: tip 哈哈哈
未完待续……
:::

## 什么是 React Hooks

React Hooks 是 React 团队在 v16.8 版本后推出的一套区别于 class 组件开发体系的全新 API，是 [函数式编程](https://baike.baidu.com/item/%E5%87%BD%E6%95%B0%E5%BC%8F%E7%BC%96%E7%A8%8B) 里，React 函数组件的副作用解决方案。如果对于函数式编程需要深入了解的，可以移步阮一峰大神写的一篇博客《[函数式编程入门教程](http://www.ruanyifeng.com/blog/2017/02/fp-tutorial.html)》。

这套 API 可以让我们不编写 class 的情况下使用 state 以及其他的 React 特性。

## 为什么是 React Hooks

React Hooks 是 React 的未来。

可能单凭这句话你还无法理解，但是看看隔壁 Vue3.0，也在推出相似的编程理念，都在重点关注可复用性、关注点分离这两点。

### 类组件的缺点

React 的核心是组件。v16.8 版本之前，组件的标准写法是类（class），即使我们只是需要一个简单的功能，我们的组件也要变得很“重”，如果加入 Redux，业务逻辑将会变得更加复杂。

Redux 的作者 Dan Abramov 总结了类组件的几个缺点：

- 大型组件很难拆分和重构，也很难测试。
- 业务逻辑分散在组件的各个方法之中，导致重复逻辑或关联逻辑。
- 组件类引入了复杂的编程模式，比如 render props 和高阶组件。

### 函数组件的限制

组件的最佳写法应该是函数组件，它很“轻”，不需要实例化。

但是很可惜，函数组件必须是纯函数，不能包含状态，也不支持生命周期方法，因此无法取代类组件。

`React Hooks 的设计目的，就是加强版函数组件，完全不使用"类"，就能写出一个全功能的组件`。

## 如何使用 React Hooks

React 约定，Hook 一律使用use前缀命名，便于识别。你要使用 xxx 功能，Hook 就命名为 usexxx。

### 默认Hooks

### 自定义Hooks

## 编程体验
---

::: tip 提示
本文参考阮一峰大神的《[React Hooks 入门教程](http://www.ruanyifeng.com/blog/2019/09/react-hooks.html)》
:::