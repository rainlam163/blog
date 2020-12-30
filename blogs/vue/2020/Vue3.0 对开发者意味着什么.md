---
title: Vue3.0 对开发者意味着什么
date: 2020-12-12
tags:
 - Vue
 - Vue3.0
categories: 
 - Vue
---

Vue3.0 在响应性系统升级为 Proxy 机制外，还提供了一套全新的 API，就像 React Hook API 一样，Vue3.0 的全新 API 也是渐进式的，我们依然可以使用 Vue2.x 的 API 去开发，但是官方当然是推荐使用全新的 API 去开发 —— 就像 React 也推荐使用 React Hook 去开发一样。

接下来我会重点从开发思维模式转变的角度去分析一下 Vue3.0 全新 API 带来的编程快感。

## Vue2.x 的开发模式

事实上，Vue 之所以这么受欢迎，主要是因为它的学习门槛极低，因为它的设计初衷是为了迎合传统的 web 开发人员，html + js + css 的模式，从而降低学习成本，快速地为企业带来收益。