---
title: 初识 React Hook
date: 2020-12-12
tags:
 - React
 - React Hook
categories: 
 - React
---

::: tip 哈哈哈
未完待续……
:::

## 什么是 React Hook

React Hook 是 React 团队在 v16.8 版本后推出的一套区别于 class 组件开发体系的全新 API，是 [函数式编程](https://baike.baidu.com/item/%E5%87%BD%E6%95%B0%E5%BC%8F%E7%BC%96%E7%A8%8B) 里，React 函数组件的副作用解决方案。如果对于函数式编程需要深入了解的，可以移步阮一峰大神写的一篇博客《[函数式编程入门教程](http://www.ruanyifeng.com/blog/2017/02/fp-tutorial.html)》。

这套 API 可以让我们不编写 class 的情况下使用 state 以及其他的 React 特性。

## 为什么是 React Hook

React Hook 是 React 的未来。

可能单凭这句话你还无法理解，但是看看隔壁 Vue3.0，也在推出相似的编程理念，都在重点关注可复用性、关注点分离这两点。

### 一. 类组件的缺点

React 的核心是组件。v16.8 版本之前，组件的标准写法是类（class），即使我们只是需要一个简单的功能，我们的组件也要变得很“重”，如果加入 Redux，业务逻辑将会变得更加复杂。

Redux 的作者 Dan Abramov 总结了类组件的几个缺点：

- 大型组件很难拆分和重构，也很难测试。
- 业务逻辑分散在组件的各个方法之中，导致重复逻辑或关联逻辑。
- 组件类引入了复杂的编程模式，比如 render props 和高阶组件。

### 二. 函数组件的限制

组件的最佳写法应该是函数组件，它很“轻”，不需要实例化。

但是很可惜，函数组件必须是纯函数，不能包含状态，也不支持生命周期方法，因此无法取代类组件。

**React Hook 的设计目的，就是加强版函数组件，完全不使用"类"，就能写出一个全功能的组件。**

## 如何使用 React Hook

React 约定，Hook 一律使用use前缀命名，便于识别。你要使用 xxx 功能，Hook 就命名为 usexxx。

### 一. 内置Hook

官方有提供一些内置的 Hook。

#### 1. 基础 Hook

##### 1) useState

- 用法

```javascript
const [state, setState] = useState(initialState);
```

- 解析

useState 是一个状态 Hook。在 Hook 出现之前，我们通常会把函数组件叫做 “无状态组件” ，现在 useState 的出现可以让函数组件使用状态。

useState 的入参是一个状态初始值，出参是一个包含状态以及更新状态的数组。

在初始渲染期间，返回的状态 (state) 与传入的第一个参数 (initialState) 值相同。

setState 函数用于更新 state。它接收一个新的 state 值并将组件的一次重新渲染加入队列。

``` javascript
setState(newState);
```

在后续的重新渲染中，useState 返回的第一个值将始终是更新后最新的 state。

- 举个例子

``` javascript
import React, { useState } from 'react';

function Example() {
  // 声明一个叫 “count” 的 state 变量。
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

在上面的例子中，我们的计数器是从零开始的，所以初始 state 就是 0。值得注意的是，不同于 this.state，这里的 state 不一定要是一个对象 —— 如果你有需要，它也可以是。这个初始 state 参数只有在第一次渲染时会被用到。

##### 2) useEffect

##### 3) useContext

#### 2. 额外的 Hook

##### 1) useReducer

##### 2) useCallback

##### 3) useMemo

##### 4) useRef

##### 5) useImperativeHandle

##### 6) useLayoutEffect

##### 7) useDebugValue

### 二. 自定义Hook

---

::: tip 提示
本文参考阮一峰大神的《[React Hooks 入门教程](http://www.ruanyifeng.com/blog/2019/09/react-hooks.html)》
:::