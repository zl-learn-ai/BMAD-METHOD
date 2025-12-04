# CLI 命令

<cite>
**本文档引用的文件**   
- [bmad-cli.js](file://tools/cli/bmad-cli.js)
- [install.js](file://tools/cli/commands/install.js)
- [update.js](file://tools/cli/commands/update.js)
- [uninstall.js](file://tools/cli/commands/uninstall.js)
- [build.js](file://tools/cli/commands/build.js)
- [list.js](file://tools/cli/commands/list.js)
- [status.js](file://tools/cli/commands/status.js)
- [cleanup.js](file://tools/cli/commands/cleanup.js)
- [agent-install.js](file://tools/cli/commands/agent-install.js)
- [ui.js](file://tools/cli/lib/ui.js)
- [installer.js](file://tools/cli/installers/lib/core/installer.js)
- [package.json](file://package.json)
</cite>

## 目录
1. [简介](#简介)
2. [命令概览](#命令概览)
3. [详细命令参考](#详细命令参考)
4. [命令调用关系与执行流程](#命令调用关系与执行流程)
5. [错误处理与故障排除](#错误处理与故障排除)
6. [底层API交互](#底层api交互)
7. [性能优化建议](#性能优化建议)

## 简介
BMAD-METHOD CLI 是一个通用的AI代理框架命令行工具，用于安装、更新、管理和构建BMAD方法论中的AI代理和工具。该CLI提供了多个命令来管理BMAD安装，包括安装核心组件、更新现有安装、卸载、构建代理文件等。CLI的设计旨在简化BMAD方法论的使用，使开发者能够快速设置和配置他们的开发环境。

## 命令概览
BMAD-METHOD CLI 提供了以下主要命令：
- `install`: 安装BMAD核心代理和工具
- `update`: 更新现有的BMAD安装
- `uninstall`: 卸载BMAD安装
- `build`: 从YAML源文件构建代理XML文件
- `list`: 列出可用的模块
- `status`: 显示安装状态
- `cleanup`: 清理BMAD安装中的过时文件
- `agent-install`: 安装并编译带有个性化设置的BMAD代理

这些命令通过`commander`库注册，并从`tools/cli/commands/`目录下的相应JavaScript文件中加载。每个命令都有描述、选项和一个异步操作函数。

**Section sources**
- [bmad-cli.js](file://tools/cli/bmad-cli.js#L1-L41)

## 详细命令参考

### install 命令
`install`命令用于安装BMAD核心代理和工具。它会引导用户完成安装配置，包括选择模块、IDE集成和可选的AgentVibes TTS集成。

**语法**
```bash
bmad install [options]
```

**参数**
- 无

**选项**
- `--skip-cleanup`: 跳过自动清理遗留文件

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 安装成功或用户取消
- `1`: 安装失败

**示例**
```bash
# 安装BMAD
npx bmad-method install

# 安装BMAD并跳过清理
npx bmad-method install --skip-cleanup
```

**Section sources**
- [install.js](file://tools/cli/commands/install.js#L1-L125)

### update 命令
`update`命令用于更新现有的BMAD安装。它允许用户更新到最新版本，同时可以选择强制更新或进行干运行以查看将要更新的内容。

**语法**
```bash
bmad update [options]
```

**参数**
- 无

**选项**
- `-d, --directory <path>`: 安装目录，默认为当前目录
- `--force`: 强制更新，覆盖修改过的文件
- `--dry-run`: 显示将要更新的内容而不进行实际更改

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 更新成功
- `1`: 更新失败

**示例**
```bash
# 更新BMAD安装
npx bmad-method update

# 强制更新BMAD安装
npx bmad-method update --force

# 干运行更新，查看将要更改的内容
npx bmad-method update --dry-run
```

**Section sources**
- [update.js](file://tools/cli/commands/update.js#L1-L29)

### uninstall 命令
`uninstall`命令用于移除BMAD安装。它会删除BMAD相关文件和目录，可以选择跳过确认提示。

**语法**
```bash
bmad uninstall [options]
```

**参数**
- 无

**选项**
- `-d, --directory <path>`: 安装目录，默认为当前目录
- `--force`: 跳过确认提示

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 卸载成功或用户取消
- `1`: 卸载失败

**示例**
```bash
# 卸载BMAD
npx bmad-method uninstall

# 从指定目录卸载BMAD
npx bmad-method uninstall --directory /path/to/project

# 强制卸载BMAD，跳过确认
npx bmad-method uninstall --force
```

**Section sources**
- [uninstall.js](file://tools/cli/commands/uninstall.js#L1-L45)

### build 命令
`build`命令用于从YAML源文件构建代理XML文件。它可以重建所有代理或特定代理，并支持强制重建。

**语法**
```bash
bmad build [agent] [options]
```

**参数**
- `[agent]`: 要构建的代理名称（可选）

**选项**
- `-a, --all`: 重建所有代理
- `-d, --directory <path>`: 项目目录，默认为当前目录
- `--force`: 即使是最新的也强制重建

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 构建成功
- `1`: 构建失败

**示例**
```bash
# 构建所有代理
npx bmad-method build --all

# 构建特定代理
npx bmad-method build pm

# 从指定目录构建所有代理
npx bmad-method build --all --directory /path/to/project

# 强制重建特定代理
npx bmad-method build pm --force
```

**Section sources**
- [build.js](file://tools/cli/commands/build.js#L1-L459)

### list 命令
`list`命令用于列出可用的模块。它显示了所有可用的BMAD模块及其描述和版本。

**语法**
```bash
bmad list
```

**参数**
- 无

**选项**
- 无

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 列出成功
- `1`: 列出失败

**示例**
```bash
# 列出可用模块
npx bmad-method list
```

**Section sources**
- [list.js](file://tools/cli/commands/list.js#L1-L29)

### status 命令
`status`命令用于显示BMAD安装的状态。它提供了安装位置、版本、核心组件和已安装模块的信息。

**语法**
```bash
bmad status [options]
```

**参数**
- 无

**选项**
- `-d, --directory <path>`: 安装目录，默认为当前目录

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 状态显示成功
- `1`: 状态显示失败

**示例**
```bash
# 显示BMAD安装状态
npx bmad-method status

# 显示指定目录的BMAD安装状态
npx bmad-method status --directory /path/to/project
```

**Section sources**
- [status.js](file://tools/cli/commands/status.js#L1-L48)

### cleanup 命令
`cleanup`命令用于清理BMAD安装中的过时文件。它支持干运行、自动删除非保留文件、列出当前保留文件和清除保留文件列表。

**语法**
```bash
bmad cleanup [options]
```

**参数**
- 无

**选项**
- `-d, --dry-run`: 显示将要删除的文件而不实际删除
- `-a, --auto-delete`: 自动删除非保留文件而不提示
- `-l, --list-retained`: 列出当前保留的文件
- `-c, --clear-retained`: 清除保留文件列表

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 清理成功
- `1`: 清理失败

**示例**
```bash
# 清理过时文件
npx bmad-method cleanup

# 干运行，显示将要删除的文件
npx bmad-method cleanup --dry-run

# 自动删除非保留文件
npx bmad-method cleanup --auto-delete

# 列出当前保留的文件
npx bmad-method cleanup --list-retained

# 清除保留文件列表
npx bmad-method cleanup --clear-retained
```

**Section sources**
- [cleanup.js](file://tools/cli/commands/cleanup.js#L1-L142)

### agent-install 命令
`agent-install`命令用于安装并编译带有个性化设置的BMAD代理。它支持从特定路径安装代理，使用默认值而不提示，以及指定目标安装目录。

**语法**
```bash
bmad agent-install [options]
```

**参数**
- 无

**选项**
- `-s, --source <path>`: 特定代理YAML文件或文件夹的路径
- `-d, --defaults`: 使用默认值而不提示
- `-t, --destination <path>`: 目标安装目录（默认为当前项目BMAD安装目录）

**返回值**
- 成功时返回0
- 失败时返回1

**退出码**
- `0`: 代理安装成功
- `1`: 代理安装失败

**示例**
```bash
# 安装并编译BMAD代理
npx bmad-method agent-install

# 从特定路径安装代理
npx bmad-method agent-install --source /path/to/agent.yaml

# 使用默认值安装代理
npx bmad-method agent-install --defaults

# 指定目标安装目录
npx bmad-method agent-install --destination /path/to/destination
```

**Section sources**
- [agent-install.js](file://tools/cli/commands/agent-install.js#L1-L410)

## 命令调用关系与执行流程
BMAD-METHOD CLI 的命令通过`bmad-cli.js`文件中的`commander`库进行注册和管理。每个命令都有一个对应的JavaScript文件，其中定义了命令的描述、选项和操作函数。

当用户运行一个命令时，CLI会解析命令行参数，调用相应的操作函数，并执行相应的逻辑。例如，`install`命令会调用`ui.promptInstall()`来引导用户完成安装配置，然后调用`installer.install()`来执行实际的安装过程。

命令之间的调用关系如下：
- `install`命令依赖于`ui.js`和`installer.js`来完成安装过程
- `update`命令直接调用`installer.update()`来更新安装
- `uninstall`命令调用`installer.uninstall()`来卸载安装
- `build`命令调用`YamlXmlBuilder`来构建代理文件
- `list`命令调用`installer.getAvailableModules()`来获取可用模块
- `status`命令调用`installer.getStatus()`来获取安装状态
- `cleanup`命令调用`installer.performCleanup()`来清理过时文件
- `agent-install`命令调用`agent/installer.js`来安装和编译代理

**Section sources**
- [bmad-cli.js](file://tools/cli/bmad-cli.js#L1-L41)
- [ui.js](file://tools/cli/lib/ui.js#L1-L804)
- [installer.js](file://tools/cli/installers/lib/core/installer.js#L1-L2957)

## 错误处理与故障排除
BMAD-METHOD CLI 在每个命令的操作函数中都包含了错误处理机制。当发生错误时，CLI会捕获异常，显示错误消息，并返回非零退出码。

常见的错误包括：
- 文件或目录不存在
- 权限不足
- 网络连接问题
- 配置错误

故障排除建议：
- 确保有足够的权限访问相关文件和目录
- 检查网络连接是否正常
- 验证配置文件是否正确
- 查看详细的错误堆栈信息以定位问题

**Section sources**
- [install.js](file://tools/cli/commands/install.js#L110-L122)
- [update.js](file://tools/cli/commands/update.js#L23-L26)
- [uninstall.js](file://tools/cli/commands/uninstall.js#L39-L42)
- [build.js](file://tools/cli/commands/build.js#L67-L73)
- [list.js](file://tools/cli/commands/list.js#L23-L26)
- [status.js](file://tools/cli/commands/status.js#L42-L45)
- [cleanup.js](file://tools/cli/commands/cleanup.js#L136-L139)
- [agent-install.js](file://tools/cli/commands/agent-install.js#L403-L407)

## 底层API交互
BMAD-METHOD CLI 通过调用底层API来执行各种操作。这些API包括文件系统操作、配置管理、模块管理和IDE集成。

例如，`installer.js`文件中的`Installer`类提供了安装、更新、卸载和清理等操作的API。`ui.js`文件中的`UI`类提供了用户界面和交互的API。`agent/installer.js`文件提供了代理安装和编译的API。

CLI通过这些API与BMAD方法论的核心组件进行交互，实现了对BMAD安装的全面管理。

**Section sources**
- [installer.js](file://tools/cli/installers/lib/core/installer.js#L1-L2957)
- [ui.js](file://tools/cli/lib/ui.js#L1-L804)
- [agent/installer.js](file://tools/cli/lib/agent/installer.js#L1-L410)

## 性能优化建议
为了提高BMAD-METHOD CLI的性能，可以考虑以下建议：
- 使用`--force`选项来强制更新或重建，避免不必要的检查
- 使用`--dry-run`选项来预览更改，避免意外的修改
- 定期清理过时文件，保持安装的整洁
- 使用默认值而不提示，加快安装和配置过程
- 指定目标安装目录，避免不必要的搜索

通过这些优化，可以提高CLI的执行效率，减少用户的等待时间。

**Section sources**
- [update.js](file://tools/cli/commands/update.js#L10-L13)
- [build.js](file://tools/cli/commands/build.js#L31-L34)
- [cleanup.js](file://tools/cli/commands/cleanup.js#L9-L13)
- [agent-install.js](file://tools/cli/commands/agent-install.js#L25-L28)