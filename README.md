# Quizgame Admin - Week 5

Quiz 后台管理课程项目，使用 Vue 2、Vue Router 3 和 Element UI 构建。

## 页面

- 用户管理：`/#/user`
- 题目管理：`/#/question`
- 首页默认跳转到用户管理，可通过左侧菜单切换页面。

当前使用本地示例数据，查询、编辑、删除及弹窗确认尚未接入后端。

## 安装和运行

需要 Node.js 和 npm。在项目根目录执行：

```bash
npm ci
npm run serve
```

打开终端提示的本地地址。

## 打包

```bash
npm run build
```

构建结果输出到 `dist/`。

## 代码检查

```bash
npm run lint
```

## 主要目录

```text
public/                       静态资源和 HTML 模板
src/App.vue                   应用入口及路由出口
src/main.js                   Vue 和 Element UI 初始化
src/router/index.js           路由配置
src/views/element/UserView.vue 用户管理页面
src/views/element/QuestionView.vue 题目管理页面
```

仓库保留 `package.json` 和 `package-lock.json` 以便安装依赖，忽略 `node_modules/`、`dist/`、本地环境配置、日志及编辑器配置。
