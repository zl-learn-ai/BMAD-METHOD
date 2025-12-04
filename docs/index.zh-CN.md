# BMad 文档索引

所有BMad Method v6文档的完整地图，包含推荐的阅读路径。

---

## 🎯 开始使用（从这里开始！）

**新用户：** 根据您的情况从以下之一开始：

| 您的情况 | 从这里开始 | 然后阅读 |
| ---------------------- | --------------------------------------------------------------- | ------------------------------------------------------------- |
| **全新使用BMad** | [快速开始指南](./quick-start.zh-CN.md) | [BMM工作流指南](../src/modules/bmm/workflows/README.md) |
| **从v4升级** | [v4到v6升级指南](./v4-to-v6-upgrade.md) | [快速开始指南](./quick-start.zh-CN.md) |
| **棕地项目** | [棕地指南](../src/modules/bmm/docs/brownfield-guide.md) | [快速开始指南](./quick-start.zh-CN.md) |

---

## 📋 核心文档

### 项目级文档（根目录）

- **[README.md](../README.md)** - 主项目概述、功能摘要和模块介绍（[中文版](../README.zh-CN.md)）
- **[CONTRIBUTING.md](../CONTRIBUTING.md)** - 如何贡献、拉取请求指南、代码风格
- **[CHANGELOG.md](../CHANGELOG.md)** - 版本历史和重大变更
- **[CLAUDE.md](../CLAUDE.md)** - 此项目的Claude Code特定指南

### 安装与设置

- **[v4到v6升级指南](./v4-to-v6-upgrade.md)** - v4用户的迁移路径
- **[文档分片指南](./document-sharding-guide.md)** - 拆分大型文档以节省90%+的token
- **[Web捆绑包](./USING_WEB_BUNDLES.md)** - 在Claude Projects、ChatGPT或Gemini中使用BMAD代理，无需安装
- **[捆绑包分发设置](./BUNDLE_DISTRIBUTION_SETUP.md)** - 维护者的捆绑包自动发布指南

---

## 🏗️ 模块文档

### BMad Method (BMM) - 软件与游戏开发

敏捷AI驱动开发的旗舰模块。

- **[BMM模块README](../src/modules/bmm/README.md)** - 模块概述、代理和完整文档索引
- **[BMM文档](../src/modules/bmm/docs/)** - 所有BMM特定指南和参考：
  - [快速开始指南](./quick-start.zh-CN.md) - 构建第一个项目的分步指南
  - [快速规范流](../src/modules/bmm/docs/quick-spec-flow.md) - 快速0-1级开发
  - [规模自适应系统](../src/modules/bmm/docs/scale-adaptive-system.md) - 理解5级系统
  - [棕地指南](../src/modules/bmm/docs/brownfield-guide.md) - 处理现有代码库
- **[BMM工作流指南](../src/modules/bmm/workflows/README.md)** - **必读**
- **[测试架构师指南](../src/modules/bmm/testarch/README.md)** - 测试策略和质量保证

### BMad Builder (BMB) - 创建自定义解决方案

构建您自己的代理、工作流和模块。

- **[BMB模块README](../src/modules/bmb/README.md)** - 模块概述和功能
- **[代理创建指南](../src/modules/bmb/workflows/create-agent/README.md)** - 设计自定义代理

### 创意智能套件 (CIS) - 创新与创造力

AI驱动的创意思维和头脑风暴。

- **[CIS模块README](../src/modules/cis/README.md)** - 模块概述和工作流

---

## 🖥️ IDE特定指南

在开发环境中加载代理和运行工作流的说明。

**流行IDE：**

- [Claude Code](./ide-info/claude-code.md)
- [Cursor](./ide-info/cursor.md)
- [VS Code](./ide-info/windsurf.md)

**其他支持的IDE：**

- [Augment](./ide-info/auggie.md)
- [Cline](./ide-info/cline.md)
- [Codex](./ide-info/codex.md)
- [Crush](./ide-info/crush.md)
- [Gemini](./ide-info/gemini.md)
- [GitHub Copilot](./ide-info/github-copilot.md)
- [IFlow](./ide-info/iflow.md)
- [Kilo](./ide-info/kilo.md)
- [OpenCode](./ide-info/opencode.md)
- [Qwen](./ide-info/qwen.md)
- [Roo](./ide-info/roo.md)
- [Rovo Dev](./ide-info/rovo-dev.md)
- [Trae](./ide-info/trae.md)

**关键概念：** 主文档中每次提到「加载代理」或「激活代理」都链接到[ide-info](./ide-info/)目录以获取IDE特定说明。

---

## 🔧 高级主题

### 自定义代理

- **[自定义代理安装](./custom-agent-installation.md)** - 使用`bmad agent-install`安装和个性化代理
- **[代理定制指南](./agent-customization-guide.zh-CN.md)** - 自定义代理行为和响应

### 安装与捆绑

- [IDE注入参考](./installers-bundlers/ide-injections.md) - 代理如何安装到IDE
- [安装程序与平台参考](./installers-bundlers/installers-modules-platforms-reference.md) - CLI工具和平台支持
- [Web捆绑器使用](./installers-bundlers/web-bundler-usage.md) - 创建Web兼容捆绑包

---

## 🎓 推荐阅读路径

### 路径1：全新使用BMad（软件项目）

1. [README.md](../README.zh-CN.md) - 理解愿景
2. [快速开始指南](./quick-start.zh-CN.md) - 动手实践
3. [BMM模块README](../src/modules/bmm/README.md) - 理解代理
4. [BMM工作流指南](../src/modules/bmm/workflows/README.md) - 掌握方法论
5. [您的IDE指南](./ide-info/) - 优化您的工作流

### 路径2：游戏开发项目

1. [README.md](../README.zh-CN.md) - 理解愿景
2. [快速开始指南](./quick-start.zh-CN.md) - 动手实践
3. [BMM模块README](../src/modules/bmm/README.md) - 包含游戏代理
4. [BMM工作流指南](../src/modules/bmm/workflows/README.md) - 游戏工作流
5. [您的IDE指南](./ide-info/) - 优化您的工作流

### 路径3：从v4升级

1. [v4到v6升级指南](./v4-to-v6-upgrade.md) - 理解变化内容
2. [快速开始指南](./quick-start.zh-CN.md) - 重新定位
3. [BMM工作流指南](../src/modules/bmm/workflows/README.md) - 学习新的v6工作流

### 路径4：处理现有代码库（棕地）

1. [棕地指南](../src/modules/bmm/docs/brownfield-guide.md) - 旧代码的方法
2. [快速开始指南](./quick-start.zh-CN.md) - 遵循流程
3. [BMM工作流指南](../src/modules/bmm/workflows/README.md) - 掌握方法论

### 路径5：构建自定义解决方案

1. [BMB模块README](../src/modules/bmb/README.md) - 理解功能
2. [代理创建指南](../src/modules/bmb/workflows/create-agent/README.md) - 创建代理
3. [BMM工作流指南](../src/modules/bmm/workflows/README.md) - 理解工作流结构

### 路径6：为BMad做贡献

1. [CONTRIBUTING.md](../CONTRIBUTING.md) - 贡献指南
2. 相关模块README - 理解您要贡献的领域
3. [CONTRIBUTING.md中的代码风格部分](../CONTRIBUTING.md#code-style) - 遵循标准
