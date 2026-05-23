# LingYunFrp Launcher

**LingYunFrp 桌面客户端** — 基于 Tauri v2 + React 19 构建的 FRP 隧道管理工具，提供直观的图形化界面来管理您的 frp 代理隧道。

---

## 功能特性

- **用户认证** — 登录与鉴权管理，自动维护会话状态
- **仪表盘** — 用户信息展示、签到、系统公告通知
- **隧道管理** — 创建、编辑、删除、启停 frp 代理隧道
- **智能端口选择** — 自动扫描本机监听端口，快速选取
- **运行日志** — 实时查看隧道运行日志，支持筛选与导出
- **系统设置** — 开机自启、日志路径、代理配置等
- **个性化定制** — 明暗主题、自定义主题色、毛玻璃背景、侧边栏样式
- **多语言支持** — 简体中文 & English 双语切换
- **托盘菜单** — 系统托盘快捷操作（显示/隐藏、退出）
- **自动更新** — 启动器与应用内核双更新通道，带进度反馈
- **窗口特效** — 支持 Acrylic / Mica 透明磨砂材质效果

## 技术栈

### 前端

| 技术 | 说明 |
|------|------|
| [React 19](https://react.dev/) | UI 框架 |
| [React Router v7](https://reactrouter.com/) | 客户端路由 |
| [TypeScript](https://www.typescriptlang.org/) | 类型安全 |
| [Tailwind CSS v4](https://tailwindcss.com/) | 原子化样式 |
| [shadcn/ui](https://ui.shadcn.com/) | Radix UI 组件库 |
| [Framer Motion](https://www.framer.com/motion/) | 声明式动画 |
| [i18next](https://www.i18next.com/) | 国际化框架 |
| [next-themes](https://github.com/pacocoursey/next-themes) | 主题切换 |
| [Vite](https://vitejs.dev/) | 构建工具 |
| [Tauri API](https://tauri.app/) | 桌面端桥接 |

### 后端 (Rust)

| 技术 | 说明 |
|------|------|
| [Tauri v2](https://tauri.app/) | 桌面应用框架 |
| [Tokio](https://tokio.rs/) | 异步运行时 |
| [Reqwest](https://docs.rs/reqwest/) | HTTP 客户端（支持 gzip、brotli） |
| [Serde](https://serde.rs/) | 序列化/反序列化 |
| [futures-util](https://docs.rs/futures-util/) | 异步流处理 |

## 快速开始

### 环境要求

- [Node.js](https://nodejs.org/) >= 18
- [pnpm](https://pnpm.io/) >= 8
- [Rust](https://www.rust-lang.org/) >= 1.70
- 系统依赖: [Tauri v2 系统依赖](https://v2.tauri.app/start/prerequisites/)

### 安装依赖

```bash
# 安装前端依赖
pnpm install
```

### 开发模式

```bash
# 启动 Tauri 开发模式
pnpm tauri dev
```

### 构建应用

```bash
# 构建生产安装包
pnpm tauri build
```

构建产物输出至 `src-tauri/target/release/bundle/`。

## 项目结构

```
LingYunFrp-React-Launcher/
├── src/                              # 前端源码 (React + TypeScript)
│   ├── components/
│   │   ├── layout/                   # 布局组件
│   │   │   ├── Layout.tsx            # 主布局
│   │   │   ├── Header.tsx            # 顶部栏
│   │   │   ├── BackgroundEffect.tsx  # 毛玻璃/背景效果
│   │   │   └── SideBars/             # 侧边栏（默认/悬浮/图标模式）
│   │   └── ui/                       # shadcn/ui 基础组件
│   ├── pages/
│   │   ├── Dashboard/                # 仪表盘（用户信息、公告、签到）
│   │   ├── Tunnels/                  # 隧道管理（CRUD、启停控制）
│   │   ├── Settings/                 # 系统设置（通用、个性化）
│   │   ├── Logs/                     # 运行日志查看
│   │   ├── Login.tsx                 # 登录页面
│   │   └── Tray.tsx                  # 托盘菜单页面
│   ├── hooks/                        # 自定义 Hooks
│   ├── stores/                       # 状态管理
│   │   ├── auth.tsx                  # 认证上下文
│   │   └── update.tsx                # 更新状态
│   ├── i18n/                         # 国际化
│   │   └── locales/
│   │       ├── zh-CN.json            # 简体中文
│   │       └── en-US.json            # English
│   ├── lib/
│   │   ├── http.ts                   # HTTP 请求封装（桥接 Rust 后端）
│   │   ├── theme.ts                  # 主题工具
│   │   └── utils.ts                  # 工具函数
│   ├── router/                       # 路由配置
│   ├── App.tsx
│   └── main.tsx
├── src-tauri/                        # Tauri (Rust) 后端
│   ├── src/
│   │   ├── lib.rs                    # Tauri 应用入口、托盘、命令注册
│   │   ├── main.rs                   # 程序入口
│   │   ├── config.rs                 # 配置管理（API 地址、版本、系统信息）
│   │   ├── http.rs                   # HTTP 请求（支持代理绕过选项）
│   │   ├── tunnel.rs                 # FRP 隧道进程管理（启动/停止/监控）
│   │   ├── ports.rs                  # 本地端口扫描
│   │   ├── log_store.rs              # 环形缓冲区日志存储
│   │   └── update.rs                 # 应用与 FRP 更新下载
│   ├── config.json                   # API 地址配置（dev/prod）
│   ├── icons/                        # 多平台应用图标
│   └── tauri.conf.json               # Tauri 窗口与打包配置
├── package.json
├── vite.config.ts
├── tsconfig.json
└── components.json                   # shadcn/ui 配置
```

## 核心架构

### 多窗口设计

应用包含两个独立窗口：

| 窗口 | 标签 | 尺寸 | 特性 |
|------|------|------|------|
| **主窗口** | `main` | 1200×600 | 无边框透明，Acrylic/Mica 特效，可调整大小 |
| **托盘菜单** | `tray_menu` | 260×308 | 无边框悬浮面板，失焦自动隐藏 |

### 隧道管理流程

1. 前端创建/编辑隧道配置
2. 生成 TOML 格式 frpc 配置文件
3. Rust 后端通过 `start_proxy` 命令启动 frpc 进程
4. 异步监控 stdout/stderr 输出，通过事件系统推送日志
5. 检测启动成功/超时，更新隧道状态
6. 停止时通过 `stop_proxy` 终止进程

### HTTP 请求

所有 HTTP 请求通过 Tauri `invoke` 桥接到 Rust 后端执行，而非前端直接发起，优势：
- 支持绕过系统代理（`no_proxy` 选项）
- 统一的超时控制与错误处理
- 避免 CORS 限制

## 开发指南

### 脚本命令

| 命令 | 说明 |
|------|------|
| `pnpm dev` | 启动前端开发服务器（端口 1420） |
| `pnpm build` | 构建前端生产包 |
| `pnpm preview` | 预览构建产物 |
| `pnpm tauri dev` | 启动 Tauri 开发模式 |
| `pnpm tauri build` | 构建桌面安装包 |

### 国际化

添加新语言：
1. 在 `src/i18n/locales/` 下创建 `{locale}.json`
2. 在 `src/i18n/index.ts` 中注册
3. 在 `src/pages/Settings/index.tsx` 中添加语言选项

### 配置

API 地址等配置在 `src-tauri/config.json` 中管理，根据构建模式（dev/prod）自动切换：

```json
{
  "dev": {
    "api_url": "https://dev-api.example.com"
  },
  "prod": {
    "api_url": "https://api.example.com"
  }
}
```
## 常见问题 FAQ

### 1. 启动报错/白屏怎么办？

- 请确保已正确安装 Node.js、Rust 环境。
- 删除 `node_modules` 和 `dist` 目录后重新 `pnpm install`。
- 检查是否有杀毒软件拦截。

### 2. 如何切换主题？

- 右边侧边栏设置中切换主题，也可以自定义主题颜色或者毛玻璃效果。

### 3. 如何反馈 Bug 或建议？

- 可通过下方联系方式反馈。
- 也可以在 GitHub 上提交 Issue。

## 贡献与反馈

欢迎提交 Issue 或 PR 参与项目改进。

- 官网：[https://www.lyfrp.cn](https://www.lyfrp.cn)
- 邮箱：1263115878@qq.com
- QQ群：882670857
- GitHub：[https://github.com/YCLY-IT/LingYunFrp-Client-Launcher](https://github.com/YCLY-IT/LingYunFrp-Official-Launcher)

---
