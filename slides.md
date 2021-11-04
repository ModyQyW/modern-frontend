---
theme: seriph
download: true
highlighter: shiki
---

# 现代前端开发

<br>

吴睿

[Repo](https://github.com/modyqyw/modern-fronted)

Powered by [Slidev](https://sli.dev/)

<!--

大家好。这次的分享会主要想跟大家分享一下我对现代前端开发的理解，算是一个拓宽视野性质的分享会。

-->

---

# 目录

- 工具链
- 框架和库
- Immutable & Mutable
- 自我驱动

---

# 怎么定义现代

综合国内外环境来定义，尤其需要考虑支持国内一些双核浏览器和移动应用，如 QQ 浏览器、360 浏览器、QQ、微信、支付宝等

- 废弃支持：已经不被官方支持的系统版本（如 WinXP、Win7、Win8、Android 4 - 7、iOS 8 - 11 等）、已经不被官方支持且非必需的浏览器版本（如 IE 6 - 11 等）
- 支持目标：Edge >= 79、Firefox >= 67、Chrome >= 63、Safari >= 12、Opera >= 50、iOS >= 12、Android >= 8、微信小程序基础库 >= 2.16（对应微信 8）、支付宝小程序基础库 >= 2.7（对应支付宝 10.1.92）

- 依据：[Android 版本列表](https://zh.wikipedia.org/wiki/Android%E7%89%88%E6%9C%AC%E5%88%97%E8%A1%A8)、[iOS 版本历史](https://zh.wikipedia.org/wiki/IOS%E7%89%88%E6%9C%AC%E5%8E%86%E5%8F%B2)、[支持原生 ESM script 标签](https://caniuse.com/es6-module)、[支持原生 ESM 动态导入](https://caniuse.com/es6-module-dynamic-import)、[支持 SVG](https://caniuse.com/?search=svg)、[支持 CSS Variables](https://caniuse.com/css-variables)、[移动应用软件高 API 等级预置与分发自律公约](https://baike.baidu.com/item/%E7%A7%BB%E5%8A%A8%E5%BA%94%E7%94%A8%E8%BD%AF%E4%BB%B6%E9%AB%98API%E7%AD%89%E7%BA%A7%E9%A2%84%E7%BD%AE%E4%B8%8E%E5%88%86%E5%8F%91%E8%87%AA%E5%BE%8B%E5%85%AC%E7%BA%A6)、[微信小程序基础库](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/)、[微信小程序运行时](https://developers.weixin.qq.com/miniprogram/dev/framework/runtime/env.html)、[支付宝小程序基础库](https://opendocs.alipay.com/mini/framework/lib)、[支付宝小程序 JavaScript 引擎](https://opendocs.alipay.com/mini/framework/implementation-detail)

**向下兼容越多，耗费的时间和精力、潜在的技术债也就越多。需要引导用户升级，参考 [旧版 Internet Explorer 淘汰行动](https://support.dmeng.net/kill-old-versions-of-ie.html) 和 [Browser Update](https://browser-update.org/zh/)。**

---

# 工具链

我们需要更好的包管理工具，我们需要更快的编译、构建、启动速度。

- [npm](https://docs.npmjs.com/)、[yarn](https://yarnpkg.com/) -> [pnpm](https://pnpm.io/)
- [webpack 4](https://v4.webpack.docschina.org/) -> [webpack 5](https://webpack.docschina.org/) ([模块联邦 Module Federation](https://webpack.docschina.org/concepts/module-federation/)) / [rollup 2](https://rollupjs.org/) / [vite 2](https://cn.vitejs.dev/)
- [babel](https://babeljs.io/) -> [swc](https://swc.rs/)、[esbuild](https://esbuild.github.io/)
- [terser](https://terser.org/) -> esbuild
- swc 使用了 [rust](https://www.rust-lang.org/zh-CN/)，esbuild 使用了 [go](https://golang.org/)，可以预测未来还会有更多的工具引入 javascript 和 [typescript](http://typescriptlang.org/) 之外的语言来做优化提速，比如用 rust 实现 [postcss](https://postcss.org/) 的 [postcss-rs](https://github.com/justjavac/postcss-rs)

**如果你不想了解这些较为底层一点的东西，直接用 vite 或者对应的框架和库，他们往往已经为你做好了封装。**

---

# 框架和库

我们需要默认就有更强的功能和更好的性能。

- [vue 3](https://v3.cn.vuejs.org/) - composition api，函数式编程思想，关注点分离，Vue 2.7 (2022 Q1) / [@vue/composition-api](https://github.com/vuejs/composition-api/blob/main/README.zh-CN.md) 允许 Vue 2 使用 Composition API
- [uni-app](https://uniapp.dcloud.io/) - 同时支持小程序和移动应用的框架，移动应用基于 webview，没别的可以选
- [pinia](https://pinia.esm.dev/) - 状态管理，良好的 typescript 支持，支持 vue 2 & 3，未来可能会并入 vuex 5，类似于 reach-router 和 react-router
- [nuxt](https://nuxtjs.org/) - ssr 框架
- [element-plus](https://element-plus.gitee.io/zh-CN/)、[naive](https://www.naiveui.com/)、[ant-design-vue](https://next.antdv.com/components/overview-cn/)、[chakra](https://next.vue.chakra-ui.com/)、[vuetify](https://vuetifyjs.com/)、[quasar](https://quasar.dev/)、[vant](https://youzan.github.io/vant/v3/)、[varlet](https://varlet.gitee.io/varlet-ui/)、[zarm-vue](https://zarm-vue.gitee.io/zarm-vue-next/) - UI 库
- [vue-use](https://vueuse.org/add-ons.html#gesture-vueuse-gesture) - hooks 包
- [vue-query](https://vue-query.vercel.app/)、[swrv](https://docs-swrv.netlify.app/) - 请求管理

---

# 框架和库

我们需要默认就有更强的功能和更好的性能。

- [react](https://beta.reactjs.org/) - hooks，函数式编程思想，关注点分离
- [react-native](https://reactnative.dev/) - [未来将默认使用新引擎 hermes](https://reactnative.dev/blog/2021/10/26/toward-hermes-being-the-default)，更好的性能和体验，[expo](https://expo.dev/) 已经支持
- [taro](https://docs.taro.zone/docs/README) - 同时支持小程序和移动应用的框架，移动应用基于 react-native
- [rax](https://rax.js.org/) - 同时支持小程序和移动应用的框架，移动应用基于 kraken
- [next](https://nextjs.org/) - ssr 框架
- [ant-design](https://ant.design/)、[ant-design-mobile](https://mobile.ant.design/zh)、[mui](https://mui.com/)、[zarm](https://zarm.design/)、[react-native-elements](https://reactnativeelements.com/)、[react-native-ui-kitten](https://akveo.github.io/react-native-ui-kitten/) - UI 库
- [redux-toolkit](https://redux-toolkit.js.org/)、[recoil](https://recoiljs.org/zh-hans/)、[constate](https://github.com/diegohaz/constate)、[unstated-next](https://github.com/jamiebuilds/unstated-next/blob/master/README-zh-cn.md) - 状态管理
- [react-use](https://github.com/streamich/react-use)、[ahooks](https://ahooks.js.org/zh-CN/) - hooks 包
- [react-query](https://react-query.tanstack.com/)、[swr](https://swr.vercel.app/zh-CN) - 请求管理

---

# 框架和库

我们需要默认就有更强的功能和更好的性能。

- [vuepress](https://vuepress.github.io/)、[vitepress](https://vitepress.vuejs.org/)、[dumi](https://d.umijs.org/zh-CN) - 文档
- [css modules](https://github.com/css-modules/css-modules)、[css variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) - 更好的 CSS
- [unocss](https://github.com/antfu/unocss)、[windicss](https://windicss.org/)、[tailwindcss](https://tailwindcss.com/) - 原子化 CSS，可以读一下 [重新构想原子化 CSS](https://antfu.me/posts/reimagine-atomic-css-zh)
- [immer](https://immerjs.github.io/immer/) - immutable

**[SSR、SSG 等渲染方式](https://github.com/PieNam/Blog/blob/main/4-XXR/%E5%95%A5%E6%98%AFXXR%EF%BC%9F%E8%AE%A4%E8%AF%86%E5%89%8D%E7%AB%AF%E9%A1%B9%E7%9B%AE%E6%B8%B2%E6%9F%93%E6%A8%A1%E5%BC%8F%E4%BB%AC.md)、[函数式编程](https://llh911001.gitbooks.io/mostly-adequate-guide-chinese/)和原子化 CSS 被越来越多人接受并使用，现在开始学并使用它们是比较好的时机。**

---

# Immutable & Mutable

接受不可变数据和可变数据。

- Immutable Data 就是一旦创建，值就不能再被更改的数据。相反，Mutable Data 就是创建后值还能被更改的数据。

```javascript
// Immutable way 基于 arr 返回一个新的数据，两者引用一致
function replaceItemAtIndex(arr, index, newValue) {
  return [...arr.slice(0, index), newValue, ...arr.slice(index + 1)];
}
// Mutable way 操作本来的数据 arr
function replaceItemAtIndex(arr, index, newValue) {
  arr.splice(index, 1, newValue);
}
```

- 由于我们很可能使用 typescript，不建议把 Mutable Data 的值更改成不同类型。

**Immutable in React & Mutable in Vue.**

---

# 自我驱动

前端可以不只是前端。

- BFF (Backends For Frontends) - 承担一部分后端开发工作，多一层业务处理和转发层。
- JavaScript / TypeScript 全栈 - 基于一门熟悉的语言，拓展到不同的领域，[express](https://expressjs.com/)、[koa](https://koajs.com/)、[egg](https://eggjs.org/)、[midway](https://www.midwayjs.org/)、[nest](https://nestjs.com/)、[“云”端的语雀：用 JavaScript 全栈打造商业级应用](https://zhuanlan.zhihu.com/p/101917567)。
- Serverless - 把大部分服务器配置、运维工作交给服务商，降低了全栈入门的门槛，[serverless framework](https://www.serverless.com/)。
- Electron、Tauri - 桌面应用开发。
- 还有 [很多东西](https://modyqyw.github.io/development/#%E8%AF%B4%E6%98%8E) 值得探索……
