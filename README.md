# vue3-roadmap

更新于：2023/6/28

很多读者会来问我，Vue 该怎么规划学习路线，或者大概进行到某个阶段了，该怎样继续深入。所以我决定根据我自己学习的心路历程，总结一篇 **Vue 从入门到精通**的路线。

跟着这篇文章走下来，对 Vue 以及它整个周边生态的理解一定会超过很多人，包括但不限于：

- Vue 的入门、深入以及原理
- Vite 的入门、深入以及原理
- Vue 周边生态，社区推荐

## 相关资料

**笔者已经将仓库内容里的重要资料整理在公众号「前端从进阶到入院」，还附赠了帮助上千人拿到 offer 的面经。大家可以关注公众号发送「资料」获取。**

![qrcode_for_gh_d2b31290dd8b_258](https://user-images.githubusercontent.com/23615778/134800856-9a44fa9a-4f1b-4884-a0b6-b58c5f3331df.jpg)

## 入门

这里可以参考一下尤雨溪以前写的答案[新手向：Vue 2.0 的建议学习顺序](https://zhuanlan.zhihu.com/p/23134551)，官方作者直接给出的推荐路线足够权威。

首先从[官方文档](https://cn.vuejs.org/guide/essentials/template-syntax.html)入手，Vue 的中文文档是公认做的比较友好的，能帮助你渐进式的入门这个框架。

如果你之前从来没有接触过 Vue、React 这些现代框架，那么建议你先不管脚手架的那些方式，最简单的就是直接建个 HTML 文件，通过 CDN 的方式引入 Vue 写写 demo，先大概把玩一下，熟悉基本语法。

当然只跟着官网学也有缺陷，就是你可能只是掌握了一些干巴巴的知识点，但是不知道怎样在实践项目中融会贯通，所以我推荐官网过一遍以后，也可以跟着培训机构在 B 站上发的免费课程再进一步巩固基础，在实战案例中加深你对知识点的理解：[4 个小时带你快速入门 Vue](https://www.bilibili.com/video/BV12J411m7MG)。

然后继续来一个电商后台管理的项目，或者其他类似的 B 站自行搜索，更加贴近公司实战级别的项目：[Vue 实战项目：电商管理系统（Element-UI）](https://www.bilibili.com/video/BV1E7411c7M8)

当然，如果你舍得花一些钱，那肯定是能享受到更好的课程和服务的，比如慕课网的这门课：[Vue2.5-2.6-3.0 开发去哪儿网 App 从零入门到项目实战](https://coding.imooc.com/class/203.html) 可以让你入门 Vue2，大致了解 Vue3。

如果你因为公司的技术栈原因选择直接从 Vue3 开始学习，那么推荐：

- [免费课：2021 年最新，Vue3.0 极速上手（全套完整版）](https://www.bilibili.com/video/BV1VK4y1o7GS)
- [收费课：Vue3 开发企业级音乐 Web App](https://coding.imooc.com/class/503.html)。

付费课讲的一定是更加详细的，看个人经济情况选择吧。

## Vue2 -> Vue3

这个章节可以选择性学习，适合对于 Vue2 已经比较熟悉，但还没有深入了解 Vue3 的同学，通过几篇简单的文章了解一下这两个大版本之间的差异，对于进一步的学习是很有帮助的。

- [带你体验 Vue2 和 Vue3 开发组件有什么区别](https://zhuanlan.zhihu.com/p/139590941)

- [Vue3 究竟好在哪里？（和 React Hook 的详细对比）](https://juejin.im/post/5e9ce011f265da47b8450c11)

- [Vue.js 3.0 响应式 API 比 2.x 好在哪儿？](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247493060&idx=2&sn=7a8437e8a51ff84c22e4bdc7f49927aa&chksm=eb07ddbddc7054abcb8f8595d93295ac5c680581d3272e743cba3e7a5b7b4fc2c3448a632ba9&token=431470234&lang=zh_CN#rd)

## 进阶

### 整体学习

#### Vue2：

推荐 Aresn 老师的这本小册吧，他是 iView 组件库的作者，对于 Vue 的理解可以说是非常深入了。

- [Vue.js 组件精讲 - Aresn - 掘金小册](https://juejin.cn/book/6844733759942557704)

#### Vue3：

Vue3 的课程，这里推荐资深讲师大圣老师全职以后出的第一个作品 《玩转 Vue 3 全家桶》，他在开课吧的时候就主导了众多 Vue 课程的设计，经验非常老道。这本小册侧重于 Vue3 的基础和实战，可以帮助你把整套 Vue3 的全家桶都搞明白：

- [玩转 Vue 3 全家桶](http://gk.link/a/10BoR)

### 熟练运用

对于 Vue 你必须非常熟练的运用，官网的 api 你基本上要全部过一遍。并且你要利用一些高级的 api 去实现巧妙的封装。举几个简单的例子：

1.  你要知道怎么用`slot-scope`去做一些数据和 ui 分离的封装。
    以[vue-promised](https://github.com/posva/vue-promised)这个库为例。
    Promised 组件并不关注你的视图展示成什么样，它只是帮你管理异步流程，并且通过你传入的`slot-scope`，在合适的时机把数据回抛给你，并且帮你去展示你传入的视图。

```vue
<template>
  <Promised :promise="usersPromise">
    <!-- Use the "pending" slot to display a loading message -->
    <template v-slot:pending>
      <p>Loading...</p>
    </template>
    <!-- The default scoped slot will be used as the result -->
    <template v-slot="data">
      <ul>
        <li v-for="user in data">{{ user.name }}</li>
      </ul>
    </template>
    <!-- The "rejected" scoped slot will be used if there is an error -->
    <template v-slot:rejected="error">
      <p>Error: {{ error.message }}</p>
    </template>
  </Promised>
</template>
```

2.  你需要熟练的使用`Vue.extend`，配合项目做一些命令式 API 的封装。并且知道它为什么可以这样用，推荐 [从零开始徒手撸一个 vue 的 toast 弹窗组件](https://juejin.cn/post/6844903604902428679)

3.  你要开始使用`JSX`来编写你项目中的复杂组件了。

官方插件，一些使用例子在文档里都有：

- [JSX for Vue2](https://github.com/vuejs/jsx-vue2)
- [JSX for Vue3](https://github.com/vuejs/babel-plugin-jsx)

教程：

- [Vue2：在 Vue 中使用 JSX 的正确姿势(有福利)](https://juejin.cn/post/6844903620689788936)
- [前端Vuer，请收下这份《Vue3中使用JSX简明语法》](https://juejin.cn/post/7114063575122984973)

官方提供了一个预览 Jsx 编译结果的网站 [Vue 3 JSX Explorer](https://vue-next-jsx.netlify.app/)

应用了 JSX 插件以后，你就可以以这样的方式书写你的组件：

```js
const App = () => (
  <>
    <span>I'm</span>
    <span>Fragment</span>
  </>
);
```

是不是非常像 React？灵活性更强了。

4.  你要深入了解 Vue 中 nextTick 的原理，并且知道为什么要用微任务队列优于宏任务队列，结合你的 eventloop 知识深度思考。最后融入到你的`异步合并优化`的知识体系中去。\
    [Vue 源码详解之 nextTick：MutationObserver 只是浮云，microtask 才是核心！](https://segmentfault.com/a/1190000008589736)

5.  你要能理解 Vue 中的高阶组件。关于这篇文章中为什么 slot-scope 不生效的问题，你不能看他的文章讲解都一头雾水。（需要你具备源码知识）

- [探索 Vue 高阶组件 | HcySunYang](https://segmentfault.com/p/1210000012743259/read)
- [Vue 进阶必学之高阶组件 HOC](https://juejin.im/post/5e8b5fa6f265da47ff7cc139)

6.  对于 Vuex 的使用必须非常熟练，知道什么时候该用 Vuex，知道怎么根据需求去编写 Vuex 的 plugin，合理的去使用 Vuex 的 subscribe 功能完成一些全局维度的封装，比如我对于 Vuex 中 action 的错误处理懒得一个个去`try catch`，就封装了一个[vuex-error-plugin](https://github.com/sl1673495/vuex-error-plugin/blob/master/plugin.js)。代码很简单，重要的是去理解为什么能这样做。这里用了 `monkey patch` 的做法，并不是很好的实践，仅以此作为引子。

7.  理解虚拟 DOM 的本质，虚拟 DOM 一定比真实 DOM 更快吗？这篇是尤雨溪的回答，看完这个答案，相信你会对虚拟 DOM 有更进一步的认识和理解。\
    [网上都说操作真实 DOM 慢，但测试结果却比 React 更快，为什么？](https://www.zhihu.com/question/31809713/answer/53544875)

8.  Vue 动态组件的玩法，这篇文章比较综合，可以学到不少技巧：[你可能不知道的 Vue 动态组件骚操作](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247499572&idx=2&sn=8cfcbb756d5f972d4f4ee1e4f2111dbc&chksm=eb07c74ddc704e5b7722a1a6b67b7d69ece2edd3c40faedb814eea79e3547c2d56eee9a9f95c&token=431470234&lang=zh_CN#rd)

9.  可以把 [vue-element-admin](https://github.com/PanJiaChen/vue-element-admin) 这个项目学习一遍，掌握这个后台管理系统里的架构设计，还有一些精妙的细节写法。配套文章：[手摸手，带你用 Vue 撸后台系列](https://juejin.cn/post/6844903476661583880)

## 路由

对于 Vue Router 的使用必须非常熟练，知道什么需求需要利用什么样的 router 钩子，这样才能 hold 住一个大型的项目，这个我觉得官方文档里过一遍就足够了，从入门到进阶的都有。Vue3 是配合 Vue Router 4 使用的。

- [Vue Router 4 官网](https://router.vuejs.org/zh/introduction.html)

Vue2 的同学就看 [Vue Router 3.x 的文档](https://v3.router.vuejs.org/zh/installation.html)就好

### 原理

腾讯的同学写的一整套原理解析，非常详细：
- [Vue Router 4 For Vue3 源码解析](https://juejin.cn/post/7144890513143889950?spm=a2c6h.12873639.article-detail.6.5b56a86cFE6g0o)

- [Vue Router 3.x For Vue2 的源码解析](https://ustbhuangyi.github.io/vue-analysis/v2/vue-router/)

## 状态管理

Vue2 和 3 通用的官方状态管理库是 [Pinia](https://github.com/vuejs/pinia)，只学这一个就行。 

官网全中文，非常良心，值得认真过一遍 [Pinia 官网文档](https://pinia.vuejs.org/zh/ssr/)

机智的你一定发现了，上述不少点都提到需要具备源码知识。没错，在我学习 Vue 的过程中，我发现在应用熟练的阶段就去学习源码，会让后面的进阶学习变得更加轻松。如果没有源码知识，你很难理解 Vue 内部的构造，自然也很难理解为什么 JSX 和 template 都可以实现一个组件，也难以理解 extend 这种高级 API 内部到底做了什么。

### 原理

[Pinia（Vuex5.0 ?） 源码分析](https://juejin.cn/post/6984054351379562509)

[Pinia 源码分析 1 —— 初始化](https://zhuanlan.zhihu.com/p/616990123)

[Pinia 源码分析 2 —— 相关 methods 与 api 的解析](https://zhuanlan.zhihu.com/p/616990833)

## mini 源码

直接入手学习正式版的源码可能跨度有点大，这里推荐 mini-vue 的源码教程，可以让你对 Vue 的内部原理有一个大致的了解。

尤雨溪亲自上阵，带你实现一个简易的响应式：[尤雨溪教你写 Vue](https://www.bilibili.com/video/BV1d4411v7UX)

以及开课吧的[手写 mini-vue](https://www.bilibili.com/video/BV1Rt4y1B7sC)

## 源码深入

这里我给出 Vue2 和 Vue3 的源码学习路线推荐，你可以根据所在公司的技术栈，或者自己未来的规划自行选择学习。当然有时间精力的话都学也可以，两者的实现方式还是差别挺大的。

在深入源码之前，可以先学习一点阅读源码的理论技巧，让后续的学习事倍功半。

[如何阅读前端源码的通用技巧，以 Vetur 为例](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247499600&idx=1&sn=97e3c753215e39cfdd9cee78f60e050a&chksm=eb07c729dc704e3f339dc9b29e35fbf58082a8d33e681c1a5cef0df3713ed5fc54d10bcb3627&token=431470234&lang=zh_CN#rd)

为什么要学源码？这篇文章也许可以解答你的疑惑：[关于为什么我推荐大家看 Vue 源代码的随想](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247496231&idx=2&sn=fcec40ce8d48a6bffe5207bed5186ae8&chksm=eb07ca5edc704348a2c18f02169ef451a2332b1527a4857f13b16b11c011bc0865e8c0ce4e39&token=431470234&lang=zh_CN#rd)

### Vue2

- 由于 Vue 的源码写的非常精美，而且阅读难度不是非常大，很多人也选择去阅读 Vue 的源码。视频课这里推荐黄轶老师的 Vue 源码课程。这里也包括了 Vuex 和 vue-router 的源码。\
  推荐黄轶老师在慕课网的课程，[Vue.js 源码全方位深入解析 （含 Vue3.0 源码分析）](https://coding.imooc.com/class/228.html)，贵是贵点但是物有所值。

- 推荐 HcySunYang 大佬的《Vue 逐行级别的源码分析》，这份文档已经不维护了，我整理起来放在了**本文配套资料**里，这份资料确实是对 Vue 的解析做到了逐行的级别，几乎所有的难点都有所涵盖。可以单独看，但最好是结合视频课来查漏补缺。

- 当然，同作者的《Vue 从零实现渲染器》也是宝藏，脱离框架讲解了 vnode 和 diff 算法的本质，最终从零实现了一个渲染器。配套资料里同样有。

- 如果对于某个难点，视频和电子书都没能让你彻底理解的话，可以再结合社区一些优秀的源码分析文章来补缺，比如[汪图南的 Vue2 源码分析](https://juejin.cn/user/3597257776564174/posts)。

### Vue3

Vue3 相比较 Vue2 来说，是一次完全的重写，里面也蕴含了这些年框架设计、理念的不断进步。所以也是非常值得去深入学习原理的。

#### 整体学习

这里推荐这个开源电子书，尤雨溪本人 Sponsor 过：[Vue3 源码解析](https://diy4869.github.io/vue-next-analysis/page/my.html)。

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/005cf3f163c648ba8287b5cc21776f19~tplv-k3u1fbpfcp-watermark.image?)

#### 响应式

我个人是对于 Vue3 的响应式部分学习比较深，如果你已经非常熟悉 Vue2 的响应式原理了，那么 Vue3 的响应式原理对你来说应该没有太大的难度。甚至在学习之中你会相互比较，知道 Vue3 为什么这样做更好，Vue2 还有哪部分需要改进等等。

Vue3 其实就是把实现换成了更加强大的 Proxy，并且把响应式部分做的更加的抽象，甚至可以，不得不说，Vue3 的响应式模型更加接近响应式类库的核心了，甚至 react-easy-state 等 React 的响应式状态管理库，也是用这套类似的核心做出来的。

推一波自己的文章吧，细致了讲解了 Vue3 响应式的核心流程（当然，随着版本的进步，很多代码对不上了，但是核心思想不变）：

- [Vue3 的响应式和以前有什么区别，Proxy 无敌？（源码级详解）](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247483711&idx=1&sn=e4c59cd3a742ba8384c05b6d1fb520b7&chksm=eb043946dc73b0501fc5d848f3cd330e1d9386afa27578d349cd918212f7e36de9bf7767f97a&token=431470234&lang=zh_CN#rd)

- [从零带你手把手实现 Vue3 响应式原理-上](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247483736&idx=1&sn=7ffba2b40fa0ddacd1ad0a34c4afad7d&chksm=eb043921dc73b037b637f83a9344f9ffb40f0c514cce6cb2de609093d20860c436cd4d307db8&token=431470234&lang=zh_CN#rd)

- [从零带你手把手实现 Vue3 响应式原理-下（Map 和 Set 的处理）](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247483747&idx=1&sn=735d86b80e363112c9b5244e66697e3f&chksm=eb04391adc73b00c6e0a9b7187119b2c3ffe78d18ca281a789179717313bab6a7b83e49b8df3&token=431470234&lang=zh_CN#rd)

- [深度解析：Vue3 如何巧妙的实现强大的 computed](https://juejin.cn/post/6844904053638447117)

#### 其他部分

- [深入解析 Vue 3 组件库 element-plus 架构源码](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247489991&idx=1&sn=6dd5a9891b2fce9a7f15402c9e07d86a&chksm=eb0421bedc73a8a848b9c9e8101f1e7fc1bf39a3a12a26586bdaea46360dc8183ef515b4d3d8&token=431470234&lang=zh_CN#rd)

- [我从 17w star 的 Vuejs 中学到了什么？](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247489895&idx=1&sn=97e78fa4108bad3251479f507123ff9d&chksm=eb04211edc73a80844e8c5deafb2004fbadef1f6c3dfccf52cfccdd27ddff7982cce3b7a9db1&token=431470234&lang=zh_CN#rd)

- [精读《Vue3 DOM diff 最长上升子序列》](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247496892&idx=2&sn=9be67aca74fe684442a344f5da352101&chksm=eb07ccc5dc7045d38bf49a5f3e4585dd6216cd466299561fcea1557fb22df60c35e2d7053b13&token=431470234&lang=zh_CN#rd)

- [从 Vue3 源码中那些实用的基础工具函数中，我学到了什么？](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247500294&idx=2&sn=dcc6ee708f6bd78ae90a714701b06ee8&chksm=eb07fa7fdc707369eb540d5fd9c289db22dddbfc97540f976246c8244a8fdd1fd66e81e96440&token=431470234&lang=zh_CN#rd)

## 优化

对于一个框架掌握是否深入，一个很好的标准就是你能否结合日常业务和原理进行优化，能拿到什么样的优化结果，这个对于你在职场上的成绩也是非常有帮助的。

- 首先强推一篇：[揭秘 Vue.js 九个性能优化技巧](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247491159&idx=1&sn=d1d78bdd47a12395f098a234e35c0c75&chksm=eb04262edc73af38013e0b06796672b30068291be3299a88889f577642dae47e3206637c6c87&token=431470234&lang=zh_CN#rd)，几乎把常用的优化技巧都涵盖到了，作为性能优化学习的开篇非常不错。

- [Vue Table 组件提速 10 倍的秘密](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247501270&idx=2&sn=61c581eac4b5850a3cab9f8605d4b451&chksm=eb07fdafdc7074b9304a5d1d46e9339ffd1b2e08c5f2e6c2e91d49c3b4c702c51aef0fa4793d&token=431470234&lang=zh_CN#rd)

- [让 Vue.js 3.2 创建节点提升 200% 速度的秘密](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247500914&idx=2&sn=93316e4e43c204c55b109b9286671c72&chksm=eb07fc0bdc70751d0226e689ac4a6827d9984936f8cdc316a8e60cb34e957e51a2b40a50bc60&token=431470234&lang=zh_CN#rd)

- [Vue.js 3.2 响应式性能暴增的秘密](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247500773&idx=2&sn=5a73cf931cbf0f2abd5a59e5dcebb5ae&chksm=eb07fb9cdc70728a26d00690f3ebc7a963316e07892ed88f90ee896d24f4e6efee381c279d72&token=431470234&lang=zh_CN#rd)

- 公司内的业务实战总结，可以看这篇里 Vue 优化的部分：[在字节跳动做在线讲义，如何死磕前端性能优化？](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247497462&idx=2&sn=807dae4d0f4716db0fb5784be416efeb&chksm=eb07ce8fdc7047993109478c692d3ede64de269b131e75c9338c3acf389a8883cc67bdfc7ddf&token=431470234&lang=zh_CN#rd)

- [Vue3 Table 性能优化，减少 85% 渲染耗时](https://juejin.cn/post/7194516447932973112)

## Vite

作为扬言要打倒 Webpack 的新时代开发工具，Vite 对于 DX（开发者体验）的提升是巨大的。

Vite 别出心裁的利用了浏览器的原生 ES Module 支持，直接在 html 文件里写诸如这样的代码：

```html
// index.html
<div id="app"></div>
<script type="module">
  import { createApp } from "vue";
  import Main from "./Main.vue";

  createApp(Main).mount("#app");
</script>
```

Vite 会在本地帮你启动一个服务器，当浏览器读取到这个 html 文件之后，会在执行到 import 的时候才去向服务端发送 Main.vue 模块的请求，Vite 此时在利用内部的一系列黑魔法，包括 Vue 的 template 解析，代码的编译等等，解析成浏览器可以执行的 js 文件返回到浏览器端。

这就保证了只有在真正使用到这个模块的时候，浏览器才会请求并且解析这个模块，最大程度的做到了按需加载。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a1812b82754f4b4fa121f6f043ae09bd~tplv-k3u1fbpfcp-zoom-1.image "屏幕截图.png")

先来听听作者本人聊 Vite：

- [【译】听尤雨溪聊：下一代前端构建工具 ViteJS 中英双语字幕](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247493131&idx=2&sn=93f7bdf295e97ab07ea2e980c5064732&chksm=eb07de72dc70576442741131254d367732b7a519754ede0d02d3e2acb827d3260517c37f855f&token=431470234&lang=zh_CN#rd)

文档是最基本要过一遍的：

- [Home | Vite 官方中文文档](https://cn.vitejs.dev/)

Bilibili 视频上手教程：

- [# Vite 世界指南（带你从 0 到 1 深入学习 vite）](https://www.bilibili.com/video/BV1GN4y1M7P5?p=1&vd_source=a850c680ef980902c7e1735b756c742a)

综合实践以及深入运用：

- Vite 官网列出的酷炫项目，够学一辈子的，挑选几个看看就行。[awesome-vite](https://github.com/vitejs/awesome-vite)

- [用 Vite 构建静态网站，还原 Vitepress 的能力](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247497222&idx=1&sn=f5491f8daad1e1e7b8f855b00890d698&chksm=eb07ce7fdc7047690f61d8d4b31392ac4bbc9c607f72aedc81f536436376a242291639ac21da&token=431470234&lang=zh_CN#rd)

- 还有强烈推荐本站神三元的小册，我和他是同事，知道他在公司内就在做类 Vite 的 unbundle 工具，对于 Vite 的源码他早就了如指掌：[掘金小册-深入浅出 Vite](https://s.juejin.cn/ds/idPJdj9/)

原理的话，推荐这本电子书，需要注意的是 Vite 的变化非常快，源码细节不一定完全对的上，但是通过电子书掌握大致原理完全没问题：

- [Vite Design](https://vite-design.surge.sh/guide/)

各个公司也在推 Vite 或者自研类 Vite 的开发工具，比如抖音，总结出的心血之作把类 Vite 工具研发中遇到的坑都讲的很清楚。

- [渐进式类 Vite 的 Unbundled 开发工具探索之路](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247497053&idx=2&sn=b6dfc326b30bce49f5a5442868c9b6e3&chksm=eb07cd24dc7044328c5c0f36c1f8b7a8cd8ed211b9fa7e759490ea6989a698317fc8607c4229&token=431470234&lang=zh_CN#rd)

## 开源动态

想要成为框架的优秀开发者，关注框架社区是必不可少的一步。记得在某推上关注 Evan you，然后经常和他互动的 Vue 团队的人都可以关注一波，英文看不懂就装个划词翻译插件慢慢看。

- [如何从零到一成为 Vue3 组件库 Naive UI 的贡献者？](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247502349&idx=1&sn=ab395cd27d4622bcfc0add354eed8f10&chksm=eb07f274dc707b62e04b9ec38b46f458fe66b699850f667cc0fada9039ccde86d2ebfcd617f1&token=431470234&lang=zh_CN#rd)

- [Vue3 Core Contributor：我的专业是学电焊的，入学前是电脑盲](https://mp.weixin.qq.com/s?__biz=MzI3NTM5NDgzOA==&mid=2247498708&idx=1&sn=5995f57f9173709c1d3908e9c7b6e523&chksm=eb07c3addc704abbe28a020a9b027b23adf19ebade86f63e2da3dcf58b8af64c051658524832&token=431470234&lang=zh_CN#rd)

- [尤雨溪现场飙歌！新加坡的新生活、如何做决策、成功靠运气吗？如何面对黑粉](https://www.bilibili.com/video/BV1yc411G7ek/?spm_id_from=333.337.search-card.all.click&vd_source=a850c680ef980902c7e1735b756c742a)

**知乎**推荐关注：

- [尤雨溪 - 知乎](https://www.zhihu.com/people/evanyou)

- [黄轶 - 知乎](https://www.zhihu.com/people/huang-yi-50-6)

- [HcySunYang - 知乎](https://www.zhihu.com/people/hcysunyang)

- [Anthony Fu - 知乎](https://www.zhihu.com/people/antfu)

- [ssh-晨曦时梦见兮（凑个数）](https://www.zhihu.com/people/ssh-fe)

## 如何获取本仓库资料

在 [前端从进阶到入院](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/15d5bd203bc3499c8b40b996595803cb~tplv-k3u1fbpfcp-zoom-1.image) 里回复「资料」，即可领取本文配套的**源码电子书、面试重要资料**，源码是本文学习的重点章节，面试资料也已经帮助上千人拿到 Offer。


![qrcode_for_gh_d2b31290dd8b_258](https://user-images.githubusercontent.com/23615778/134800856-9a44fa9a-4f1b-4884-a0b6-b58c5f3331df.jpg)
