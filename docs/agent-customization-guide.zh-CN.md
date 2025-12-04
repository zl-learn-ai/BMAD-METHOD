# 代理定制指南

在不修改核心文件的情况下自定义BMad代理。所有自定义配置在更新时保持不变。

## 快速开始

**1. 定位自定义文件**

安装后，在以下位置找到代理自定义文件：

```
{bmad_folder}/_cfg/agents/
├── core-bmad-master.customize.yaml
├── bmm-dev.customize.yaml
├── bmm-pm.customize.yaml
└── ...（每个已安装代理一个文件）
```

**2. 编辑任何代理**

打开要修改的代理的`.customize.yaml`文件。所有部分都是可选的 - 只自定义您需要的内容。

**3. 重建代理**

编辑后，重建代理以应用更改至关重要：

```bash
npx bmad-method@alpha install # 然后选择编译所有代理的选项
# 或仅针对单个代理
npx bmad-method@alpha build <agent-name>

# 示例：
npx bmad-method@alpha build bmm-dev
npx bmad-method@alpha build core-bmad-master
npx bmad-method@alpha build bmm-pm
```

## 您可以自定义什么

### 代理名称

更改代理的自我介绍方式：

```yaml
agent:
  metadata:
    name: '海绵宝宝' # 默认："Amelia"
```

### 角色

替换代理的个性、角色和沟通风格：

```yaml
persona:
  role: '高级全栈工程师'
  identity: '住在菠萝屋里（海底）'
  communication_style: '海绵宝宝'
  principles:
    - '永不嵌套者，海绵宝宝开发者讨厌嵌套超过2层'
    - '优先组合而非继承'
```

**注意：** persona部分会替换整个默认角色（不会合并）。

### 记忆

添加代理将始终记住的持久上下文：

```yaml
memories:
  - '在蟹堡王工作'
  - '最喜欢的名人：大卫·哈塞尔霍夫'
  - '在Epic 1中学到，假装测试已通过是不酷的'
```

### 自定义菜单项

将您自己的工作流添加到代理菜单：

```yaml
menu:
  - trigger: my-workflow
    workflow: '{project-root}/custom/my-workflow.yaml'
    description: 我的自定义工作流
  - trigger: deploy
    action: '#deploy-prompt'
    description: 部署到生产环境
```

**不要包含：** `*` 前缀或 `help`/`exit` 项 - 这些会自动注入。

### 关键操作

添加代理启动前执行的指令：

```yaml
critical_actions:
  - '在进行更改前始终检查git状态'
  - '使用约定式提交消息'
```

### 自定义提示

为 `action="#id"` 菜单处理程序定义可重用提示：

```yaml
prompts:
  - id: deploy-prompt
    content: |
      将当前分支部署到生产环境：
      1. 运行所有测试
      2. 构建项目
      3. 执行部署脚本
```

## 实际示例

**示例1：为TDD自定义开发者代理**

```yaml
# {bmad_folder}/_cfg/agents/bmm-dev.customize.yaml
agent:
  metadata:
    name: 'TDD开发者'

memories:
  - '始终在实现前编写测试'
  - '项目使用Jest和React Testing Library'

critical_actions:
  - '在提交前审查测试覆盖率'
```

**示例2：添加自定义部署工作流**

```yaml
# {bmad_folder}/_cfg/agents/bmm-dev.customize.yaml
menu:
  - trigger: deploy-staging
    workflow: '{project-root}/.bmad-custom/deploy-staging.yaml'
    description: 部署到预发布环境
  - trigger: deploy-prod
    workflow: '{project-root}/.bmad-custom/deploy-prod.yaml'
    description: 部署到生产环境（需要批准）
```

**示例3：多语言产品经理**

```yaml
# {bmad_folder}/_cfg/agents/bmm-pm.customize.yaml
persona:
  role: '双语产品经理'
  identity: '美国和拉丁美洲市场专家'
  communication_style: '清晰、战略性、具有文化意识'
  principles:
    - '从第一天就考虑本地化'
    - '平衡业务目标和用户需求'

memories:
  - '用户说英语和西班牙语'
  - '目标市场：美国和拉丁美洲'
```

## 提示

- **从小处着手：** 一次自定义一个部分并重建以测试
- **备份：** 在进行重大更改前复制自定义文件
- **更新安全：** 您在`_cfg/`中的自定义配置在所有BMad更新中保持不变
- **按项目：** 自定义文件是按项目的，不是全局的
- **版本控制：** 考虑提交`_cfg/`以与团队共享自定义配置

## 模块级与全局配置

**模块级（推荐）：**

- 在`{bmad_folder}/_cfg/agents/`中按项目自定义代理
- 不同项目可以有不同的代理行为

**全局配置（即将推出）：**

- 设置适用于所有项目的默认值
- 使用项目特定的自定义配置覆盖

## 故障排除

**更改没有出现？**

- 确保编辑后运行了`npx bmad-method build <agent-name>`
- 检查YAML语法是否有效（缩进很重要！）
- 验证代理名称与文件名模式匹配

**代理未加载？**

- 检查YAML语法错误
- 如果取消注释，确保必需字段不为空
- 尝试恢复到模板并重建

**需要重置？**

- 删除`.customize.yaml`文件
- 运行`npx bmad-method build <agent-name>`重新生成默认值

## 下一步

- **[BMM代理指南](../src/modules/bmm/docs/agents-guide.md)** - 了解所有12个BMad Method代理
- **[BMB创建代理工作流](../src/modules/bmb/workflows/create-agent/README.md)** - 构建完全自定义的代理
- **[BMM完整文档](../src/modules/bmm/docs/README.md)** - 完整的BMad Method参考
