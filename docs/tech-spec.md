# 技术规范文档 — 个人简历与作品集展示软件

## 技术选型

| 决策项 | 选择 | 原因 |
|--------|------|------|
| 运行环境 | 浏览器（Chrome/Edge/Firefox） | 用户只需双击文件，无需安装任何东西 |
| 文件结构 | 单个 HTML 文件 | 最简单，无需管理多个文件，方便备份和分享 |
| 前端技术 | 纯 HTML + CSS + JavaScript | 无框架依赖，无需 npm，不依赖网络 |
| 数据存储 | IndexedDB | 比 localStorage 容量大（数百MB），支持存储图片 |
| 图片存储 | Base64 编码存入 IndexedDB | 不需要文件系统，数据自包含，方便导出 |
| 图片压缩 | Canvas API | 上传时自动压缩，避免数据库过大 |
| 数据备份 | JSON 导出/导入 | 纯文本格式，方便迁移和恢复 |

## 不使用以下技术（及原因）

| 技术 | 不用的原因 |
|------|-----------|
| React/Vue/Angular | 需要构建工具，增加复杂度，对小白不友好 |
| Node.js/npm | 用户不需要安装任何东西 |
| 服务器/后端 | 这是纯个人展示工具，不需要联网 |
| 数据库（MySQL等） | 单机使用，浏览器内置存储足够 |
| CDN 外部资源 | 必须保证离线可用 |
| Electron | 需要安装打包，HTML 文件更简单 |

## 浏览器 API 使用

| API | 用途 |
|-----|------|
| IndexedDB | 持久化存储所有数据 |
| FileReader | 读取用户上传的图片文件 |
| Canvas | 压缩图片（限制最大宽度 800px，质量 0.7） |
| Blob / URL.createObjectURL | 导出 JSON 文件下载 |
| History API（可选） | 无刷新切换板块 |

## 数据模型设计

### 数据库：PortfolioDB
### 对象存储：userData

数据以单个 JSON 对象存储，结构如下：

```javascript
{
  profile: {
    name: "",           // 姓名
    title: "",          // 头衔/职业
    photo: "",          // 照片 base64
    bio: "",            // 个人简介
    hobbies: []         // ["爱好1", "爱好2"]
  },
  education: [
    {
      id: "唯一ID",
      school: "",       // 学校
      major: "",        // 专业
      degree: "",       // 学位
      startDate: "",    // 开始时间
      endDate: ""       // 结束时间
    }
  ],
  experience: [
    {
      id: "唯一ID",
      company: "",      // 公司
      position: "",     // 职位
      description: "",  // 职责描述
      startDate: "",
      endDate: ""
    }
  ],
  skills: [
    {
      id: "唯一ID",
      name: "",         // 技能名
      level: 80         // 熟练度 0-100
    }
  ],
  projects: [
    {
      id: "唯一ID",
      name: "",         // 项目名称
      description: "",  // 项目描述
      images: [],       // base64 图片数组
      tags: [],         // 技术标签
      link: "",         // 外部链接
      date: ""          // 项目时间
    }
  ],
  contact: {
    email: "",
    phone: "",
    social: []          // [{platform: "GitHub", url: ""}]
  }
}
```

## 图片处理规范

- 上传时用 Canvas 压缩：最大宽度 800px，JPEG 质量 0.7
- 转为 Base64 字符串存储
- 单张图片压缩后预计 50-200KB
- 建议总图片数量不超过 50 张，保持数据文件在 10MB 以内

## 安全考虑

- 管理模式使用简单密码（默认 "admin"），可修改
- 密码仅用于防止误操作，不涉及真正的安全需求
- 导出数据时提醒用户妥善保管备份文件
