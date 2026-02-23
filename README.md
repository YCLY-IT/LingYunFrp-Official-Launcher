# 凌云FRP 图形化客户端

凌云FRP（LingYunFRP）是一款基于 Tauri + Vue3 + TypeScript 的跨平台内网穿透客户端，提供现代化的图形界面，方便用户进行 FRP 配置和管理。

## 项目简介

- **前端技术栈**：Vue 3、TypeScript、Vite、Naive UI、Pinia、Vue Router
- **后端/桌面端**：Tauri（Rust），支持系统托盘、通知、单实例等特性
- **适用平台**：Windows、macOS、Linux

## 主要功能

- 图形化管理 FRP 配置
- 一键启动/停止 FRP 服务
- 实时日志查看
- 自动检测和提示新版本
- 支持多主题（明暗模式切换）
- 系统托盘快捷操作
- 多平台打包与分发

## 目录结构

```
LingYunFrp-Client-Launcher/
├── src/                # 前端源码
│   ├── api/            # API 封装
│   ├── components/     # 公共组件
│   ├── views/          # 页面视图
│   ├── stores/         # 状态管理
│   ├── router/         # 路由配置
│   ├── assets/         # 静态资源
│   └── main.ts         # 前端入口
├── src-tauri/          # Tauri 后端（Rust）
│   ├── src/            # Rust 源码
│   ├── tauri.conf.json # Tauri 配置
│   └── Cargo.toml      # Rust 依赖
├── public/             # 公共资源
├── dist/               # 构建产物
├── package.json        # 前端依赖与脚本
├── vite.config.ts      # Vite 配置
└── README.md           # 项目说明
```

## 主要依赖

- 前端：`vue`、`naive-ui`、`pinia`、`vue-router`、`axios`、`highlight.js`、`dayjs` 等
- Tauri 插件：`@tauri-apps/api`、`@tauri-apps/plugin-notification`、`@tauri-apps/plugin-opener` 等
- Rust 后端：`tauri`、`reqwest`、`tokio`、`serde` 等

## 快速开始

### 环境准备

- Node.js 16+
- Rust 1.60+
- pnpm（推荐）

### 安装依赖

```bash
pnpm install
```

### 启动开发环境

```bash
pnpm run tauri dev
```

### 打包发布

```bash
pnpm run tauri build
```

## 常见问题 FAQ

### 1. 启动报错/白屏怎么办？

- 请确保已正确安装 Node.js、Rust 环境。
- 删除 `node_modules` 和 `dist` 目录后重新 `pnpm install`。
- 检查是否有杀毒软件拦截。

### 2. 如何切换主题？

- 右上角点击主题切换按钮，或在设置面板中选择。

### 3. 如何自定义 FRP 配置？

- 在主界面可视化编辑，或手动导入配置文件。

### 4. 如何反馈 Bug 或建议？

- 可通过下方联系方式反馈。
- 也可以在 GitHub 上提交 Issue。

## 贡献与反馈

欢迎提交 Issue 或 PR 参与项目改进。

- 官网：[https://www.lyfrp.cn](https://www.lyfrp.cn)
- 邮箱：1263115878@qq.com
- QQ群：882670857
- GitHub：[https://github.com/YCLY-IT/LingYunFrp-Client-Launcher](https://github.com/YCLY-IT/LingYunFrp-Official-Launcher)

---
