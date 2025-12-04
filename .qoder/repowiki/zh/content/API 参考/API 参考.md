# API 参考

<cite>
**本文档中引用的文件**   
- [package.json](file://package.json)
- [bmad-cli.js](file://tools/cli/bmad-cli.js)
- [README.md](file://tools/cli/README.md)
- [install.js](file://tools/cli/commands/install.js)
- [build.js](file://tools/cli/commands/build.js)
- [list.js](file://tools/cli/commands/list.js)
- [status.js](file://tools/cli/commands/status.js)
- [update.js](file://tools/cli/commands/update.js)
- [uninstall.js](file://tools/cli/commands/uninstall.js)
- [agent-install.js](file://tools/cli/commands/agent-install.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)
- [dependency-resolver.js](file://tools/cli/installers/lib/core/dependency-resolver.js)
- [config-collector.js](file://tools/cli/installers/lib/core/config-collector.js)
- [yaml-xml-builder.js](file://tools/cli/lib/yaml-xml-builder.js)
- [xml-handler.js](file://tools/cli/lib/xml-handler.js)
- [web-bundler.js](file://tools/cli/bundlers/web-bundler.js)
</cite>

## 目录
1. [简介](#简介)
2. [CLI 命令参考](#cli-命令参考)
3. [核心 API 接口](#核心-api-接口)
4. [XML 和 YAML 处理库](#xml-和-yaml-处理库)
5. [程序化使用指南](#程序化使用指南)
6. [错误代码和异常处理](#错误代码和异常处理)
7. [性能优化建议](#性能优化建议)

## 简介
BMAD-METHOD 是一个用于敏捷 AI 驱动开发的框架，提供了一套完整的 CLI 工具和 API 接口，用于安装、构建、管理和更新 AI 代理。本 API 参考文档详细介绍了 CLI 工具的每个公共命令、底层 API 函数、XML 和 YAML 处理库的使用方法，以及为开发者提供的程序化使用指南。

**Section sources**
- [package.json](file://package.json)
- [bmad-cli.js](file://tools/cli/bmad-cli.js)
- [README.md](file://tools/cli/README.md)

## CLI 命令参考
BMAD-METHOD 的 CLI 工具提供了多个命令，用于管理 AI 代理的生命周期。以下是每个命令的详细说明。

### install 命令
`install` 命令用于安装 BMAD 核心代理和工具。

**语法**
```bash
bmad install [options]
```

**参数**
- `--target <path>`: 目标项目目录
- `--modules <list>`: 要安装的模块列表，用逗号分隔（例如：bmm, bmb）
- `--ides <list>`: 要配置的 IDE 列表，用逗号分隔（例如：codex, claude-code）
- `--non-interactive`: 跳过所有提示

**返回值**
- 成功时返回 0
- 失败时返回非零值

**使用示例**
```bash
# 交互式安装
npm run install:bmad

# 直接使用 CLI
node tools/cli/bmad-cli.js install --target /path/to/project --modules bmm,bmb --ides codex
```

**Section sources**
- [install.js](file://tools/cli/commands/install.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

### build 命令
`build` 命令用于从 YAML 源文件构建代理 XML 文件。

**语法**
```bash
bmad build [agent] [options]
```

**参数**
- `[agent]`: 要构建的代理名称（可选）
- `-a, --all`: 重新构建所有代理
- `-d, --directory <path>`: 项目目录
- `--force`: 即使是最新的也强制重新构建

**返回值**
- 成功时返回 0
- 失败时返回非零值

**使用示例**
```bash
# 构建特定代理
bmad build pm

# 重新构建所有代理
bmad build --all

# 检查构建状态
bmad build
```

**Section sources**
- [build.js](file://tools/cli/commands/build.js)
- [yaml-xml-builder.js](file://tools/cli/lib/yaml-xml-builder.js)

### list 命令
`list` 命令用于列出可用的模块。

**语法**
```bash
bmad list
```

**参数**
- 无

**返回值**
- 成功时返回 0
- 失败时返回非零值

**使用示例**
```bash
# 列出可用模块
bmad list
```

**Section sources**
- [list.js](file://tools/cli/commands/list.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

### status 命令
`status` 命令用于显示安装状态。

**语法**
```bash
bmad status [options]
```

**参数**
- `-d, --directory <path>`: 安装目录

**返回值**
- 成功时返回 0
- 失败时返回非零值

**使用示例**
```bash
# 显示安装状态
bmad status
```

**Section sources**
- [status.js](file://tools/cli/commands/status.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

### update 命令
`update` 命令用于更新现有的 BMAD 安装。

**语法**
```bash
bmad update [options]
```

**参数**
- `-d, --directory <path>`: 安装目录
- `--force`: 强制更新，覆盖修改过的文件
- `--dry-run`: 显示将要更新的内容而不进行更改

**返回值**
- 成功时返回 0
- 失败时返回非零值

**使用示例**
```bash
# 更新现有安装
bmad update
```

**Section sources**
- [update.js](file://tools/cli/commands/update.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

### uninstall 命令
`uninstall` 命令用于卸载 BMAD 安装。

**语法**
```bash
bmad uninstall [options]
```

**参数**
- `-d, --directory <path>`: 安装目录

**返回值**
- 成功时返回 0
- 失败时返回非零值

**使用示例**
```bash
# 卸载 BMAD 安装
bmad uninstall
```

**Section sources**
- [uninstall.js](file://tools/cli/commands/uninstall.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

### agent-install 命令
`agent-install` 命令用于安装特定的代理。

**语法**
```bash
bmad agent-install [options]
```

**参数**
- `--agent <name>`: 要安装的代理名称
- `--target <path>`: 目标项目目录

**返回值**
- 成功时返回 0
- 失败时返回非零值

**使用示例**
```bash
# 安装特定代理
bmad agent-install --agent pm --target /path/to/project
```

**Section sources**
- [agent-install.js](file://tools/cli/commands/agent-install.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

## 核心 API 接口
BMAD-METHOD 提供了多个核心 API 接口，用于代理安装器、配置收集器和依赖解析器。

### 代理安装器 (Agent Installer)
代理安装器负责安装和配置 AI 代理。

**接口**
- `install(config)`: 安装代理
- `uninstall(config)`: 卸载代理
- `update(config)`: 更新代理

**参数**
- `config`: 包含安装配置的对象

**返回值**
- 成功时返回 `success: true`
- 失败时返回 `success: false`

**Section sources**
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

### 配置收集器 (Config Collector)
配置收集器负责收集和管理代理的配置。

**接口**
- `collectAllConfigurations(modules, projectDir)`: 收集所有模块的配置
- `collectModuleConfig(moduleName, projectDir)`: 收集单个模块的配置

**参数**
- `modules`: 模块列表
- `projectDir`: 项目目录
- `moduleName`: 模块名称

**返回值**
- 成功时返回配置对象
- 失败时抛出异常

**Section sources**
- [config-collector.js](file://tools/cli/installers/lib/core/config-collector.js)

### 依赖解析器 (Dependency Resolver)
依赖解析器负责解析和管理代理的依赖关系。

**接口**
- `resolve(bmadDir, selectedModules, options)`: 解析依赖关系
- `createWebBundle(resolution)`: 创建 Web 捆绑包

**参数**
- `bmadDir`: BMAD 安装目录
- `selectedModules`: 选定的模块列表
- `options`: 解析选项

**返回值**
- 成功时返回解析结果对象
- 失败时抛出异常

**Section sources**
- [dependency-resolver.js](file://tools/cli/installers/lib/core/dependency-resolver.js)

## XML 和 YAML 处理库
BMAD-METHOD 使用 XML 和 YAML 处理库来管理和转换代理配置文件。

### YAML 到 XML 转换器 (YamlXmlBuilder)
YamlXmlBuilder 类负责将 YAML 文件转换为 XML 格式。

**接口**
- `buildFromYaml(agentYamlPath, customizeYamlPath, options)`: 从 YAML 文件构建 XML 内容
- `buildAgent(agentYamlPath, customizeYamlPath, outputPath, options)`: 构建代理 XML 文件

**参数**
- `agentYamlPath`: 代理 YAML 文件路径
- `customizeYamlPath`: 自定义 YAML 文件路径（可选）
- `outputPath`: 输出文件路径
- `options`: 构建选项

**返回值**
- 成功时返回构建结果对象
- 失败时抛出异常

**Section sources**
- [yaml-xml-builder.js](file://tools/cli/lib/yaml-xml-builder.js)

### XML 处理器 (XmlHandler)
XmlHandler 类负责处理 XML 文件，包括解析和构建。

**接口**
- `injectActivation(agentContent, metadata)`: 注入激活块
- `buildFromYaml(yamlPath, customizePath, metadata)`: 从 YAML 源构建代理

**参数**
- `agentContent`: 代理内容
- `metadata`: 元数据
- `yamlPath`: YAML 文件路径
- `customizePath`: 自定义文件路径
- `metadata`: 构建元数据

**返回值**
- 成功时返回处理后的 XML 内容
- 失败时抛出异常

**Section sources**
- [xml-handler.js](file://tools/cli/lib/xml-handler.js)

## 程序化使用指南
开发者可以通过调用内部 API 来构建自定义工具。以下是一些常见的使用场景。

### 构建自定义代理
通过调用 `YamlXmlBuilder` 类的 `buildFromYaml` 方法，可以构建自定义代理。

**示例**
```javascript
const { YamlXmlBuilder } = require('../lib/yaml-xml-builder');
const builder = new YamlXmlBuilder();

const xml = await builder.buildFromYaml('/path/to/agent.yaml', '/path/to/customize.yaml', {
  includeMetadata: true,
  forWebBundle: false
});
```

### 管理代理配置
通过调用 `ConfigCollector` 类的 `collectAllConfigurations` 方法，可以管理代理配置。

**示例**
```javascript
const { ConfigCollector } = require('../installers/lib/core/config-collector');
const collector = new ConfigCollector();

const config = await collector.collectAllConfigurations(['bmm', 'bmb'], '/path/to/project');
```

### 解析依赖关系
通过调用 `DependencyResolver` 类的 `resolve` 方法，可以解析代理的依赖关系。

**示例**
```javascript
const { DependencyResolver } = require('../installers/lib/core/dependency-resolver');
const resolver = new DependencyResolver();

const resolution = await resolver.resolve('/path/to/bmad', ['bmm', 'bmb'], { verbose: true });
```

**Section sources**
- [yaml-xml-builder.js](file://tools/cli/lib/yaml-xml-builder.js)
- [config-collector.js](file://tools/cli/installers/lib/core/config-collector.js)
- [dependency-resolver.js](file://tools/cli/installers/lib/core/dependency-resolver.js)

## 错误代码和异常处理
BMAD-METHOD 提供了详细的错误代码和异常处理机制，以帮助开发者诊断和解决问题。

### 常见错误代码
- `1`: 通用错误
- `2`: 文件不存在
- `3`: 权限被拒绝
- `4`: 磁盘空间不足

### 异常处理
在调用 API 时，应使用 try-catch 语句来捕获和处理异常。

**示例**
```javascript
try {
  const result = await installer.install(config);
  console.log('安装成功');
} catch (error) {
  console.error('安装失败:', error.message);
}
```

**Section sources**
- [install.js](file://tools/cli/commands/install.js)
- [build.js](file://tools/cli/commands/build.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)

## 性能优化建议
为了提高 BMAD-METHOD 的性能，建议采取以下措施：

### 缓存配置
缓存代理配置可以减少重复的文件读取和解析操作。

### 批量操作
尽量使用批量操作来减少 I/O 操作的次数。

### 异步处理
使用异步处理来避免阻塞主线程。

**Section sources**
- [installer.js](file://tools/cli/installers/lib/core/installer.js)
- [config-collector.js](file://tools/cli/installers/lib/core/config-collector.js)
- [dependency-resolver.js](file://tools/cli/installers/lib/core/dependency-resolver.js)