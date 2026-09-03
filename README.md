# GenshinPiano Website

GenshinPiano 的官方网站仓库，提供产品介绍、软件下载、在线文档、更新日志以及中英文页面。

The official website repository for GenshinPiano, featuring software downloads, bilingual documentation, release notes, and an interactive 21-key practice studio with multiple instrument sounds.

- 网站：[https://tozyx.github.io/](https://tozyx.github.io/)
- 软件源码：[tozyx/GenshinPiano](https://github.com/tozyx/GenshinPiano)
- 发布版本：[GitHub Releases](https://github.com/tozyx/GenshinPiano/releases)

> GenshinPiano 是非米哈游、HoYoverse 官方项目。本仓库只包含网站源码，不包含游戏本体或官方资源。
> GenshinPiano is an unofficial fan-made project and is not affiliated with or endorsed by HoYoverse.

## 网站功能

- 自动匹配浏览器语言，并支持中英文手动切换
- 产品功能、下载、FAQ、隐私说明等完整页面
- 可搜索的中英文在线使用文档
- 从 GitHub Releases 获取版本信息、下载文件与更新日志
- 真实软件界面截图和可滑动语言切换
- 支持键盘、鼠标和触屏的交互式琴键演示
- 响应式布局、sitemap、robots 和基础 SEO
- 通过 GitHub Actions 自动构建并部署到 GitHub Pages

## 技术栈

- [Astro](https://astro.build/)
- TypeScript
- 原生 HTML、CSS 和浏览器 JavaScript
- pnpm
- GitHub Actions / GitHub Pages

网站采用静态输出，不依赖应用服务器。最新版本信息由浏览器读取 GitHub 公共 API；API 不可用时会回退到 GitHub Releases 页面。

## 本地开发

需要：

- Node.js 24 LTS，最低版本为 22.12
- pnpm 11

安装依赖：

```powershell
pnpm install
```

启动开发服务器：

```powershell
pnpm dev
```

默认访问：

```text
http://localhost:4321
```

构建生产版本：

```powershell
pnpm build
```

构建结果生成在 `dist/`。

本地预览生产构建：

```powershell
pnpm preview
```

## 项目结构

```text
.
├─ public/                    静态资源、图标和软件截图
├─ src/
│  ├─ components/            导航、页脚、琴键演示、截图和更新日志组件
│  ├─ layouts/               页面公共布局与 SEO 元数据
│  ├─ pages/                 中文页面
│  │  └─ en/                 英文页面
│  └─ styles/                全局样式与响应式布局
├─ .github/workflows/        GitHub Pages 构建与部署工作流
├─ astro.config.mjs          Astro 配置
└─ package.json              项目脚本与依赖
```

## 页面与语言

中文页面位于根路径，例如：

- `/features/`
- `/download/`
- `/docs/`
- `/changelog/`
- `/faq/`

英文页面使用 `/en/` 前缀，例如 `/en/docs/`。

语言切换会保存在浏览器本地存储中。首次访问时，网站根据浏览器首选语言选择中文或英文。

## 参考与致谢

本项目的在线练习功能在设计和实现过程中参考了以下优秀的开源项目：

- [Specy/genshin-music](https://github.com/Specy/genshin-music)：参考了原神 21 键乐器布局、琴键图标处理、乐器音色配置和交互设计；练习页使用的部分图标与音频资源亦来源于该项目。感谢作者 Specy 及所有贡献者的工作。
- [VanillaNahida/WindsongLyre-Sim](https://github.com/VanillaNahida/WindsongLyre-Sim)：在早期调研阶段参考了网页琴键界面和乐器资源组织方式。感谢作者 VanillaNahida 及所有贡献者提供的思路与实现。

GenshinPiano 的网站结构和练习功能为独立实现。第三方资源的具体来源、许可与版权说明请查看 [THIRD_PARTY_NOTICES.md](./THIRD_PARTY_NOTICES.md)。

## 开源许可

本仓库自行编写的网站代码采用 [MIT License](./LICENSE) 开源。第三方图标、音频及其他资源不因本仓库采用 MIT License 而改变其原有版权或许可条件，详情请参阅 [THIRD_PARTY_NOTICES.md](./THIRD_PARTY_NOTICES.md)。
## 发布

`GPiano` 是当前网站发布分支。推送到该分支后，GitHub Actions 会：

1. 安装 pnpm 和 Node.js 24
2. 使用锁文件安装依赖
3. 执行 `pnpm build`
4. 上传 `dist/`
5. 部署到 GitHub Pages

也可以在 Actions 页面手动运行部署工作流。

发布前建议执行：

```powershell
pnpm build
git diff --check
```

## 内容维护

- 修改中文页面：`src/pages/`
- 修改英文页面：`src/pages/en/`
- 修改完整文档：`src/pages/docs.astro` 和 `src/pages/en/docs.astro`
- 修改公共视觉样式：`src/styles/global.css`
- 更新软件截图：`public/screenshots/`
- 下载和更新日志数据来自 [GenshinPiano Releases](https://github.com/tozyx/GenshinPiano/releases)

新增页面后，应同步更新 `src/pages/sitemap.xml.ts` 和中英文导航。
