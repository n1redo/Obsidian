# 创建Vue3工程
## 基于 vite 创建

`vite`是新一代前端构建工具，官网地址：https://vitejs.cn

`vite`优势如下：
- 轻量快速的热重载（`HMR`）,能实现极速的服务启动。
- 对`TypeScript`、`JSX`、`CSS`等支持开箱即用。
- 真正的按需编译，不再等待整个应用编译完成。
- `webpack`构建与`vite`构建对比图如下
![](image/Pasted%20image%2020240815134620.png)
![](image/Pasted%20image%2020240815134648.png)
- 具体操作如下
```nodejs
#创建命令
npm create vue@latest
```

总结：
- `vite`项目中，`index.html`是项目的入口文件，在项目最外层。
- 加载`index.html`后，`vite`解析`<script type="module" src="xxx">`指向的`JavaScript`。
- `Vue3`中是通过`createApp`函数创建一个应用实例。
# Vue3核心语法
## OptionsAPI 与 CompositionAPI

- `Vue2`的`API`设计是`Options`（配置）风格。
- `Vue3`的`API`设计是`Composition`（组合）风格。

**Options API 的弊端**
`Options`类型的`API`，数据、方法、计算属性等，是分散在：`data`，`methods`，`computed`中的，若想新增或者修改一个需求，就需要分别修改：`data`，`methods`，`computed`，不便于维护和复用。

**Composition API 的优势**
可以用函数的方式，更加优雅的组织代码，让相关功能的代码更加有序的组织在一起。
## 拉开序幕的 Set up
### setup 概述
`setup`是`vue3`中一个新的配置项，值是一个函数，它是`Composition API`“表演的舞台”，组件中所用到的：数据、方法、计算属性、监视...等等，均配置在`setup`中。

特点如下：
- `setup`函数返回的对象中的内容，可直接在模板中使用。
- `setup`中访问`this`是`undefined`。
- `setup`函数会在`beforeCreate`之前调用。它是“领先”所有钩子执行的。