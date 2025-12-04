# BMad Method & BMad Core

[![稳定版本](https://img.shields.io/npm/v/bmad-method?color=blue&label=stable)](https://www.npmjs.com/package/bmad-method)
[![Alpha版本](https://img.shields.io/npm/v/bmad-method/alpha?color=orange&label=alpha)](https://www.npmjs.com/package/bmad-method)
[![许可证: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Node.js 版本](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org)
[![Discord](https://img.shields.io/badge/Discord-Join%20Community-7289da?logo=discord&logoColor=white)](https://discord.gg/gk8jAdXWmj)

## AI驱动的敏捷开发，从Bug修复扩展到企业级应用

**构建更多，架构梦想**（BMAD）提供 **19个专业AI代理**和**50+指导性工作流**，适应您项目的复杂度——从快速Bug修复到企业级平台。

> **🚀 v6是从v4开始的重大升级！** 完整的架构改造、规模自适应智能、可视化工作流以及强大的BMad Core框架。v4用户：这改变了一切。[查看新特性 →](#v6版本新特性)

> **📌 v6 Alpha状态：** 接近Beta质量，稳定性大幅提升。文档正在完善中。新视频即将在[BMadCode YouTube](https://www.youtube.com/@BMadCode)发布。

## 🎯 为什么选择 BMad Method？

与通用AI编程助手不同，BMad Method提供由专业代理驱动的**结构化、经过实战检验的工作流**，这些代理深谙敏捷开发。每个代理都拥有深厚的领域专长——从产品管理到架构到测试——无缝协作。

**✨ 核心优势：**

- **规模自适应智能** - 自动调整计划深度，从Bug修复到企业系统
- **完整开发生命周期** - 分析 → 计划 → 架构 → 实现
- **专业化专长** - 19个具有特定角色的代理（产品经理、架构师、开发者、UX设计师等）
- **成熟的方法论** - 基于敏捷最佳实践并结合AI增强
- **IDE集成** - 支持Claude Code、Cursor、Windsurf、VS Code

## 🏗️ BMad Core的强大力量

**BMad Method**实际上是构建在**BMad Core**（**C**ollaboration **O**ptimized **R**eflection **E**ngine，协作优化反思引擎）之上的复杂模块。这一革命性架构意味着：

- **BMad Core** 提供人机协作的通用框架
- **BMad Method** 利用Core提供敏捷开发工作流
- **BMad Builder** 让您创建与BMad Method一样强大的自定义模块

通过**BMad Builder**，您可以架构简单的代理和极其复杂的领域特定模块（法律、医疗、金融、教育、创意），这些模块很快将可以在**官方社区市场**分享。想象一下构建和分享您自己的专业AI团队！

## 📊 实际效果展示

<p align="center">
  <img src="./src/modules/bmm/docs/images/workflow-method-greenfield.svg" alt="BMad Method工作流" width="100%">
</p>

<p align="center">
  <em>完整的BMad Method工作流，展示所有阶段、代理和决策点</em>
</p>

## 🚀 三步开始使用

### 1. 安装 BMad Method

```bash
# 安装 v6 Alpha（推荐）
npx bmad-method@alpha install

# 或安装稳定版 v4 用于生产环境
npx bmad-method install
```

### 2. 初始化您的项目

在IDE中加载任意代理并运行：

```
*workflow-init
```

这将分析您的项目并推荐正确的工作流轨道。

### 3. 选择您的轨道

BMad Method通过三个智能轨道适应您的需求：

| 轨道 | 适用场景 | 计划方式 | 启动时间 |
| ------------------ | ------------------------- | ----------------------- | ------------- |
| **⚡ 快速流** | Bug修复、小功能 | 仅技术规范 | < 5分钟 |
| **📋 BMad Method** | 产品、平台 | PRD + 架构 + UX | < 15分钟 |
| **🏢 企业级** | 合规、规模化 | 完整治理套件 | < 30分钟 |

> **不确定？** 运行 `*workflow-init` 让BMad分析您的项目目标。

## 🔄 工作原理：四阶段方法论

BMad Method通过经过验证的开发生命周期指导您：

1. **📊 分析**（可选）- 头脑风暴、研究和探索解决方案
2. **📝 计划** - 创建PRD、技术规范或游戏设计文档
3. **🏗️ 解决方案** - 设计架构、UX和技术方法
4. **⚡ 实现** - 故事驱动的开发与持续验证

每个阶段都有专门的工作流和协作代理，提供卓越的结果。

## 🤖 认识您的团队

**12个专业代理**协同工作：

| 开发 | 架构 | 产品 | 领导 |
| ----------- | -------------- | ------------- | -------------- |
| 开发者 | 架构师 | 产品经理 | Scrum Master |
| UX设计师 | 测试架构师 | 分析师 | BMad Master |
| 技术文档撰写者 | 游戏架构师 | 游戏设计师 | 游戏开发者 |

**测试架构师**与`@seontechnologies/playwright-utils`集成，提供生产就绪的基于fixture的工具。

每个代理都带来深厚的专业知识，并可根据您团队的风格进行定制。

## 📦 包含内容

### 核心模块

- **BMad Method (BMM)** - 完整的敏捷开发框架
  - 12个专业代理
  - 4个阶段34个工作流
  - 规模自适应计划
  - [→ 文档中心](./src/modules/bmm/docs/README.md)

- **BMad Builder (BMB)** - 创建自定义代理和工作流
  - 构建从简单代理到复杂模块的任何内容
  - 创建领域特定解决方案（法律、医疗、金融、教育）
  - 在即将推出的社区市场分享您的创作
  - [→ Builder指南](./src/modules/bmb/README.md)

- **创意智能套件 (CIS)** - 创新与问题解决
  - 头脑风暴、设计思维、讲故事
  - 5个创意促进工作流
  - [→ 创意工作流](./src/modules/cis/README.md)

### 主要特性

- **🎨 可定制代理** - 修改个性、专长和沟通风格
- **🌐 多语言支持** - 分别设置沟通和代码输出语言
- **📄 文档分片** - 大型项目节省90%的token
- **🔄 更新安全** - 您的自定义配置在更新中保持不变
- **🚀 Web捆绑包** - 在ChatGPT、Claude Projects或Gemini Gems中使用

## 📚 文档

### 快速链接

- **[快速开始指南](./docs/quick-start.zh-CN.md)** - 15分钟介绍
- **[完整BMM文档](./src/modules/bmm/docs/README.md)** - 所有指南和参考
- **[代理定制](./docs/agent-customization-guide.zh-CN.md)** - 个性化您的代理
- **[所有文档](./docs/index.zh-CN.md)** - 完整文档索引

### 面向 v4 用户

- **[v4 文档](https://github.com/bmad-code-org/BMAD-METHOD/tree/V4)**
- **[v4 到 v6 升级指南](./docs/v4-to-v6-upgrade.md)**

## 💬 社区与支持

- **[Discord社区](https://discord.gg/gk8jAdXWmj)** - 获取帮助、分享项目
- **[GitHub Issues](https://github.com/bmad-code-org/BMAD-METHOD/issues)** - 报告Bug、请求功能
- **[YouTube频道](https://www.youtube.com/@BMadCode)** - 视频教程和演示
- **[Web捆绑包](https://bmad-code-org.github.io/bmad-bundles/)** - 预构建的代理捆绑包

## 🛠️ 开发

对于BMad代码库的贡献者：

```bash
# 运行所有质量检查
npm test

# 开发命令
npm run lint:fix      # 修复代码风格
npm run format:fix    # 自动格式化代码
npm run bundle        # 构建web捆绑包
```

查看[CONTRIBUTING.md](CONTRIBUTING.md)了解完整的开发指南。

## v6版本新特性

**v6相对于v4代表了完整的架构革命：**

### 🚀 主要升级

- **BMad Core框架** - 模块化架构，支持自定义领域解决方案
- **规模自适应智能** - 从Bug修复到企业级自动调整
- **可视化工作流** - 精美的SVG图表展示完整方法论
- **BMad Builder模块** - 创建和分享您自己的AI代理团队
- **50+工作流** - 从v4的20个增加，覆盖每个开发场景
- **19个专业代理** - 增强了可定制的个性和专长
- **更新安全的自定义** - 您的配置在所有更新中保持不变
- **Web捆绑包** - 在ChatGPT、Claude和Gemini中使用代理
- **多语言支持** - 分别设置沟通和代码语言
- **文档分片** - 大型项目节省90%的token

### 🔄 面向 v4 用户

- **[全面升级指南](./docs/v4-to-v6-upgrade.md)** - 分步迁移
- **[v4文档存档](https://github.com/bmad-code-org/BMAD-METHOD/tree/V4)** - 旧版参考
- 尽可能向后兼容
- 通过安装程序检测实现平滑迁移路径

## 📄 许可证

MIT许可证 - 详见[LICENSE](LICENSE)。

**商标：** BMAD™和BMAD-METHOD™是BMad Code, LLC的商标。

---

<p align="center">
  <a href="https://github.com/bmad-code-org/BMAD-METHOD/graphs/contributors">
    <img src="https://contrib.rocks/image?repo=bmad-code-org/BMAD-METHOD" alt="贡献者">
  </a>
</p>

<p align="center">
  <sub>为人机协作社区用❤️构建</sub>
</p>
