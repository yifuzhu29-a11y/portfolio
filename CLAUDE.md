# CLAUDE.md — 项目工作指引

## 项目简介

这是一个**个人简历与作品集展示软件**，运行在 Windows 上。用户是不懂代码的小白。

- **最终产物**：一个 `index.html` 文件，双击即可在浏览器中打开使用
- **核心功能**：展示简历（基本信息、教育、工作、技能、爱好）、展示作品集（项目卡片+图片）、搜索、内置编辑管理
- **技术栈**：纯 HTML + CSS + JS，无框架、无依赖、无需网络

---

## 标准文档路径索引

每次开发前，先阅读对应的标准文档：

| 文档 | 路径 | 用途 |
|------|------|------|
| 功能需求 | [docs/requirements.md](docs/requirements.md) | 查看所有功能点及优先级 |
| 技术规范 | [docs/tech-spec.md](docs/tech-spec.md) | 查看技术选型、数据模型、API使用 |
| 设计规范 | [docs/design-spec.md](docs/design-spec.md) | 查看配色、字体、间距、组件样式 |
| 执行步骤 | [docs/execution-steps.md](docs/execution-steps.md) | 查看当前进度和下一步计划 |

---

## 工作规则

### 分阶段执行
1. 严格按照 `docs/execution-steps.md` 中的阶段和步骤执行
2. **每次只做一个步骤**，完成后停下来让用户确认结果
3. 每步做完后，更新 `docs/execution-steps.md` 中对应步骤为 `[x]`
4. 用户确认无误后，再进入下一步

### 开发日志
1. 每次开发会话结束时，更新当天的 `dev-log/YYYY-MM-DD.md`
2. 如果没有当天的日志文件，创建一个新的
3. 日志包含三个部分：今日完成、待办事项、备注
4. 在「今日完成」中列出本次会话实际完成的具体事项
5. 在「待办事项」中列出下一步要做的事

### 代码风格
- 所有注释和界面文字使用**中文**
- HTML/CSS/JS 全部内嵌在一个 `index.html` 文件中
- 不使用任何外部依赖（CDN、npm、图片URL）
- CSS 变量定义在 `:root` 中，颜色值参考设计规范
- JS 使用 ES6+ 语法，函数命名清晰
- 每个功能模块用注释分隔

### 沟通原则
- 用户是不懂代码的小白，解释时用通俗语言，避免技术术语
- 每一步完成后，用简单的话告诉用户"做了什么"和"怎么查看效果"
- 遇到需要用户决策的地方，给出明确推荐并解释原因

---

## 关键文件一览

```
e:\Vibe Coding\Portfolio\
├── CLAUDE.md              ← 本文件
├── index.html             ← 主程序（所有代码在此）
├── docs/
│   ├── requirements.md    ← 功能需求
│   ├── tech-spec.md       ← 技术规范
│   ├── design-spec.md     ← 设计规范
│   └── execution-steps.md ← 执行步骤
└── dev-log/
    └── YYYY-MM-DD.md      ← 每日开发日志
```
