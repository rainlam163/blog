---
title: 初识 React Hook（2）基础 Hook
date: 2020-12-13
tags:
 - React
 - React Hook
categories: 
 - React
---

## useState

### 用法

```javascript
const [state, setState] = useState(initialState);
```

### 解析

useState 是一个状态 Hook。在 Hook 出现之前，我们通常会把函数组件叫做 “无状态组件” ，现在 useState 的出现可以让函数组件使用状态。

useState 的入参是一个状态初始值，出参是一个包含状态以及更新状态的数组。

在初始渲染期间，返回的状态 (state) 与传入的第一个参数 (initialState) 值相同。

setState 函数用于更新 state。它接收一个新的 state 值并将组件的一次重新渲染加入队列。

``` javascript
setState(newState);
```

在后续的重新渲染中，useState 返回的第一个值将始终是更新后最新的 state。

### 举个例子

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

## useEffect

### 用法

``` javascript
useEffect(() => {
  fetchData(params); // 获取数据
}, [params]);
```

### 解析

useEffect 是一个副作用 Hook，我们可以把所有产生副作用的操作都通过这个 Hook 勾进来。什么是副作用呢？数据获取、设置订阅、设置定时器、记录日志以及手动更改 React 组件中的 DOM 都属于副作用。

useEffect 接收 2 个参数，第一个参数是一个函数，函数体是你要进行的副作用操作，第二个参数是一个依赖数组，只有在这个依赖数组的其中任意一个元素发生了变化时，组件重新渲染才会执行副作用操作。如果依赖是一个空数组，那么这个副作用操作只会在组件第一次渲染时执行。

useEffect 的副作用操作如果创建了计时器或者订阅等资源，可以在在副作用操作函数里面返回一个清除函数，这样组件在卸载前就会执行这个清除函数。

### 举个例子

```javascript
const [ count, setCount ] = useState(0);
const [ restart, setRestart ] = useState(false);

let interval = null;

useEffect(() => {
  if (restart) {
    setCount(0);
    interval = setInterval(() => {
      setCount(count + 1);
    }, 1000);
    return () => {
      clearInterval(interval);
    };
  }
}, [restart]);

setRestart(true);
```

上面的例子演示了 useEffect 的使用，每秒钟 count 自动加 1，但当 restart 由 false 变成 true 的时候，会清空 count 并从 0 开始重新计算。当组件即将销毁的时候，会清除计时器。

## useContext

### 用法

```javascript
const value = useContext(MyContext);
```

### 解析

接收一个 context 对象（React.createContext 的返回值）并返回该 context 的当前值。当前的 context 值由上层组件中距离当前组件最近的 <MyContext.Provider> 的 value prop 决定。

这是一个上下文的概念。我们通常在子组件通过这个 Hook 来跨级别使用祖先组件的数据，并且当上下文的值发生变化时，该 Hook 会重新出发渲染（即使祖先组件已经使用 React.memo，也会在组件本身使用 useContext时重新渲染）。

和 props 传递数据的区别在于，pros 只能一层层传递，但是 useContext 可以跨级别使用组件组件的数据。

### 举个例子

```javascript
const themes = {
  light: {
    foreground: "#000000",
    background: "#eeeeee"
  },
  dark: {
    foreground: "#ffffff",
    background: "#222222"
  }
};

const ThemeContext = React.createContext(themes.light);

function App() {
  return (
    <ThemeContext.Provider value={themes.dark}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme.background, color: theme.foreground }}>
      I am styled by theme context!
    </button>
  );
}
```

以上例子演示了跨组件使用数据的例子。