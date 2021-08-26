# vue-frame

首先你是否有以下经历：

- 在实际的开发过程中，从零开始建立一个前端项目让你头疼？
- 你想寻求快速搭建一个完整的项目的结构的方式，作为开发者的你只需要在生成的项目结构的基础上进行开发即可？

接下来将为你提供一个简单高效的方式———使用 vue-frame-cli 脚手架。

## vue-frame-cli 是什么？

vue-frame-cli 是一个全局安装的npm 包，提供了终端里的 vue-frame 命令。 它可以通过 vue-frame init 命令快速搭建并初始化一个标准的 Vue 项目。

## 为什么需要这样一套脚手架？

为什么需要 = 它能帮我们解决以下痛点问题。

- 前端项目配置越来越繁琐、耗时，而且都是重复性的工作；
- 项目结构不统一、不规范;
- 前端代码没有统一的代码规范，协同开发时代码难以阅读、code review 效率低;
- 前端开发依赖于后端接口数据，前后端分离的场景下，后端接口数据没有出来，前端如何mock假数据，模拟开发；
- 随着应用趋于复杂，非父子组件间的跨组件通信越来越频繁，前端如何优雅的使用Vuex，解决跨组件通信。
……

## 同开源框架 Vue 自身的 CLI 工具的区别？

参考并基于 vue-cli，但不仅仅是 vue-cli。

- 基于vue-cli，针对团队特定需求，生成一套更清晰易读的前端项目结构，更易为初接触者理解。
- 集成了统一的前端代码规范、Vuex、Mock数据等一系列项目搭建时的常用场景的最佳实践，这是 vue-cli 没有的。

vue-frame-cli 提前帮助开发者的你想好了搭建项目前期会遇到的种种，只需要你动动手指敲几行命令即可。

## 如何使用 vue-frame-cli ？

1. 生成项目

    你可以使用`vue-frame-cli`脚手架，以该`Git`项目为模板初始化一个标准的`Vue`项目（推荐）。

    ```bash
    npm install vue-frame-cli
    vue-frame init <your project name>
    cd <your project name>
    ```

    也可以克隆该`Git`项目至本地，注意克隆后需手动更改根目录下的`package.json`中的`name`、`author`、`description`。

    ```bash
    git clone https://github.com/zhangly409/vue-frame.git
    cd standard-vue-project
    ```

2. 安装前端项目依赖

    ```bash
    npm install
    ```

3. 启动前端`Mock`服务

    ``` bash
    node mock/server.js
    ```

4. 启动前端服务

    ```bash
    npm run serve
    ```

浏览器打开`http://localhost:8000/`即可访问。

## Feature

- <strong>优雅的项目目录结构。</strong>依照经典的MVC模式，将页面、组件、路由分开，抽离出公共模块，路由配置模块化，`Vuex`状态模块化，可以使得开发者更便捷的编写、维护、查找代码。
- <strong>分离数据转换逻辑与视图层。</strong>将复杂的数据转换逻辑剥离至中间层（Service），既减轻了`View`层代码，也解除了数据转换逻辑和页面之间的强绑定关系，便于复用。
- <strong>提供`Vuex`的模块化使用示例。</strong>轻松 get `Vuex`及`Vuex`模块化的使用方式。
- <strong>提供mock数据最佳实践。</strong>引入Mock.js实现模拟数据，一方面方便前后端分离并行开发;另一方面在接入真实的后端数据时，基本不需要修改代码，只需去掉mockjs，停止拦截真实的ajax。
- <strong>集成代码规范最佳实践。</strong>通过配置`Eslint`、`Prettier`、`editorconfig`，检测代码潜在问题的同时，也统一了团队代码规范。
- <strong>提供`Nginx`配置示例。</strong>通过配置`Nginx`解决前后端分离时前端请求的跨域问题。

## Standard Project Structure

```
standard-vue-project

├── README.md    // 项目说明

├── node_modules/    // 依赖包

├── public    // 静态资源文件夹，不经过 webpack
|    ├── favicon.ico
|    └── index.html    // 模板文件，构建时资源链接会被自动注入

├── mock    // mock 数据
|    ├── db.js    // mock 数据库
|    └── routes.js    // mock 路由
     └── server.js    // mock 服务相关配置

├── src

|    ├── assets    // 静态资源文件夹，经过 webpack
|    |    ├── icon
|    |    └── img
|    |        └── logo.png

|    ├── main.js    // 项目的入口文件

|    ├── App.vue    // 主组件

|    ├── router    // 路由入口
|    |    ├── index.js
|    |    └── modules
|    |        └── example.js

|    └── views    // 视图(原则：轻view，重component)
|        └── example
|            └── Example.vue

|    ├── components   // 页面组件
|    |    └── example
|    |        └── ExampleTable.vue

|    ├── store    // vuex 数据
|    |    ├── index.js
|    |    └── modules
|    |        └── example.js

|    ├── service    // 剥离出的数据转换逻辑
|    |    └── exampleService.js

|    ├── api    // 接口 js 文件
|    |    └── example.js

|    ├── common    // 公共模块
|    |    ├── api    // 公共 api
|    |    |    └── request.js
|    |    ├── components    // 公共业务组件
|    |    |    ├── basic
|    |    |    |    └── BasicTable.vue
|    |    |    └── layout
|    |    |        ├── AppFooter.vue
|    |    |        ├── AppHeader.vue
|    |    |        ├── AppSidebar.vue
|    |    |        └── index.js
|    |    ├── config    // 公共配置
|    |    └── utils    // 公共变量和函数
|    |        ├── functions.js
|    |        └── variables.js

|    ├── style    // 全局样式
|    |    ├── index.scss    // 主入口
|    |    ├── _table.scss
|    |    └── _variables.scss    // 全局 scss 变量

├── babel.config.js    // babel 配置

└── vue.config.js    // vue-cli3 配置

├── package.json    // npm 配置,存储所有已安装 npm 包的名称和版本

├── package-lock.json    // 锁定安装时的 npm 包的版本号

```

## Code Standards 使用

项目中已经安装和配置好 `Prettier` + `ESLint` 相关依赖包，方便通过命令行进行代码格式化。使用方法:

- 检测代码格式错误并提示

```bash
  eslint [file path]
```

- 检测代码格式错误并自动修复后进行格式化，对无法自动修复的错误进行提示

```bash
  eslint [file path] --fix
```

如使用编辑器`Vscode`，在编辑器的`Extensions`里搜索安装`Prettier`和`ESLint`相关插件，可进行如下配置，配置好后在开发过程中对代码规范错误会进行高亮提示以及保存时自动格式化代码。
在`Vscode`的`setting.json`文件里加上：
```bash
  "editor.codeActionsOnSave":  {"source.fixAll.eslint": true} //在保存的时候利用eslintrc.js里定义的规则自动格式化代码
```
