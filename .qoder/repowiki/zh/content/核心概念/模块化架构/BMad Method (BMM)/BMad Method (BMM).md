# BMad Method (BMM)

<cite>
**本文档中引用的文件**  
- [analyst.agent.yaml](file://src/modules/bmm/agents/analyst.agent.yaml)
- [pm.agent.yaml](file://src/modules/bmm/agents/pm.agent.yaml)
- [product-brief/workflow.md](file://src/modules/bmm/workflows/1-analysis/product-brief/workflow.md)
- [prd/workflow.md](file://src/modules/bmm/workflows/2-plan-workflows/prd/workflow.md)
- [architecture/workflow.md](file://src/modules/bmm/workflows/3-solutioning/architecture/workflow.md)
- [README.md](file://src/modules/bmm/README.md)
- [docs/README.md](file://src/modules/bmm/docs/README.md)
- [workflows-analysis.md](file://src/modules/bmm/docs/workflows-analysis.md)
- [workflows-planning.md](file://src/modules/bmm/docs/workflows-planning.md)
- [workflows-solutioning.md](file://src/modules/bmm/docs/workflows-solutioning.md)
- [workflows-implementation.md](file://src/modules/bmm/docs/workflows-implementation.md)
- [scale-adaptive-system.md](file://src/modules/bmm/docs/scale-adaptive-system.md)
- [brownfield-guide.md](file://src/modules/bmm/docs/brownfield-guide.md)
</cite>

## 目录
1. [引言](#引言)
2. [BMM 核心职责与架构设计](#bmm-核心职责与架构设计)
3. [BMM 四个阶段详解](#bmm-四个阶段详解)
   1. [分析阶段（1-analysis）](#分析阶段1-analysis)
   2. [计划阶段（2-plan-workflows）](#计划阶段2-plan-workflows)
   3. [解决方案阶段（3-solutioning）](#解决方案阶段3-solutioning)
   4. [实现阶段（4-implementation）](#实现阶段4-implementation)
4. [工作流结构与模板使用](#工作流结构与模板使用)
5. [BMM 与其他模块的集成关系](#bmm-与其他模块的集成关系)
6. [BMM 在企业级项目中的应用示例](#bmm-在企业级项目中的应用示例)
7. [规模自适应智能特性](#规模自适应智能特性)
8. [结论](#结论)

## 引言

BMad Method (BMM) 是一个AI驱动的敏捷开发工作流引擎，旨在通过结构化、智能化的流程管理，提升软件开发的效率与质量。BMM 模块作为BMAD方法论的核心，提供了一套完整的生命周期管理机制，涵盖从需求收集到代码实现的全过程。该方法论特别适用于绿色field（全新项目）和brownfield（现有项目）开发场景，能够根据项目复杂度自动调整工作流路径，确保开发过程既高效又严谨。

**Section sources**
- [README.md](file://src/modules/bmm/README.md#L1-L129)
- [docs/README.md](file://src/modules/bmm/docs/README.md#L1-L253)

## BMM 核心职责与架构设计

BMM 的核心职责是作为AI驱动的敏捷开发中枢，协调多个专业AI代理（Agent）协同工作，确保开发流程的连贯性与一致性。其架构设计基于模块化、分阶段的原则，将整个开发周期划分为四个主要阶段：分析、计划、解决方案和实现。每个阶段由特定的代理驱动，通过预定义的工作流文件（workflow）执行具体任务。

BMM 模块的结构包括：
- **agents/**：包含12个专业AI代理，如分析师、产品经理、架构师、开发人员等。
- **workflows/**：涵盖34个工作流，分布在四个开发阶段及测试阶段。
- **teams/**：预配置的代理团队组合，支持多代理协作。
- **testarch/**：全面的测试基础设施，确保代码质量。
- **docs/**：完整的用户文档，指导用户使用BMM。

BMM 通过代理间的协作与工作流的自动化执行，实现了从需求到交付的端到端管理。

**Section sources**
- [README.md](file://src/modules/bmm/README.md#L21-L33)
- [docs/README.md](file://src/modules/bmm/docs/README.md#L180-L189)

## BMM 四个阶段详解

### 分析阶段（1-analysis）

分析阶段是可选的探索与发现阶段，旨在帮助团队在进入详细规划前验证想法、理解市场并生成战略背景。该阶段主要由**分析师代理（analyst.agent.yaml）**驱动，执行以下关键工作流：

- **product-brief**：通过交互式对话创建产品简报，定义产品愿景与战略。
- **research**：进行市场、技术、竞争、用户和领域研究，生成研究报告。
- **brainstorm-project**：探索多种解决方案路径，评估架构与集成选项。

这些工作流帮助团队明确“做什么”和“为什么做”，为后续的规划阶段提供输入。例如，`product-brief`工作流会生成一份包含问题陈述、目标用户、MVP范围和财务影响的产品简报，直接作为PRD（产品需求文档）的输入。

**Section sources**
- [analyst.agent.yaml](file://src/modules/bmm/agents/analyst.agent.yaml#L34-L36)
- [workflows-analysis.md](file://src/modules/bmm/docs/workflows-analysis.md#L1-L267)

### 计划阶段（2-plan-workflows）

计划阶段是必经的规划环节，负责创建详细的需求文档和设计规范。该阶段由**产品经理代理（pm.agent.yaml）**主导，执行以下核心工作流：

- **create-prd**：创建产品需求文档（PRD），定义功能需求、用户故事和验收标准。
- **create-ux-design**：生成UX设计文档，包括用户流程图和界面原型。

PRD工作流采用“微文件架构”（micro-file architecture），将整个流程分解为多个步骤文件（step-file），确保每一步都按顺序执行，避免跳步或优化。该工作流还会自动加载前期分析阶段生成的`product-brief.md`等文档，作为上下文输入，确保信息的一致性。

**Section sources**
- [pm.agent.yaml](file://src/modules/bmm/agents/pm.agent.yaml#L26-L28)
- [prd/workflow.md](file://src/modules/bmm/workflows/2-plan-workflows/prd/workflow.md#L1-L62)

### 解决方案阶段（3-solutioning）

解决方案阶段专注于架构设计与用户故事的创建，确保技术实现的可行性与一致性。该阶段由**架构师代理（architect.agent.yaml）**驱动，执行以下关键工作流：

- **architecture**：通过协作式决策流程，生成架构决策文档（ADR），确保AI代理在实现时保持一致。
- **create-epics-and-stories**：基于PRD创建史诗（Epics）和用户故事（User Stories），为实现阶段做准备。

架构工作流强调“决策导向”的设计，而非模板驱动。它通过逐步引导用户做出关键架构决策，防止代理冲突，并确保系统的一致性。此阶段通常在BMad Method和Enterprise Method路径中是必需的。

**Section sources**
- [architecture/workflow.md](file://src/modules/bmm/workflows/3-solutioning/architecture/workflow.md#L1-L49)
- [workflows-solutioning.md](file://src/modules/bmm/docs/workflows-solutioning.md#L1-L638)

### 实现阶段（4-implementation）

实现阶段是迭代式的开发过程，涵盖冲刺规划、代码开发与审查。该阶段由**开发代理（dev.agent.yaml）**和**Scrum Master代理（sm.agent.yaml）**共同驱动，执行以下核心工作流：

- **sprint-planning**：规划冲刺，确定待办事项优先级。
- **create-story** 和 **dev-story**：创建并开发用户故事。
- **code-review**：执行代码审查，确保代码质量。
- **retrospective**：进行冲刺回顾，持续改进流程。

实现阶段遵循“一次一个故事”的纪律，确保每个用户故事都经过完整的生命周期：`待办 → 草稿 → 就绪 → 进行中 → 审查 → 完成`。代码审查工作流会自动加载TEA（测试架构师）代理的知识库，确保测试覆盖和质量标准。

**Section sources**
- [workflows-implementation.md](file://src/modules/bmm/docs/workflows-implementation.md#L1-L1634)
- [4-implementation/workflows](file://src/modules/bmm/workflows/4-implementation/)

## 工作流结构与模板使用

BMM 的工作流采用“步骤文件架构”（step-file architecture），每个步骤都是一个独立的指令文件，确保流程的严格顺序执行。核心原则包括：

- **微文件设计**：每个步骤文件自包含，仅在需要时加载。
- **即时加载**：仅当前步骤文件在内存中，不预加载后续步骤。
- **顺序执行**：必须按顺序完成所有步骤，禁止跳步。
- **状态跟踪**：通过输出文件的frontmatter中的`stepsCompleted`数组记录进度。
- **追加式构建**：通过追加内容的方式逐步构建最终文档。

例如，`product-brief`工作流从`step-01-init.md`开始，逐步引导用户完成产品愿景定义、目标用户分析、MVP范围界定等步骤，最终生成一份完整的产品简报。

**Section sources**
- [product-brief/workflow.md](file://src/modules/bmm/workflows/1-analysis/product-brief/workflow.md#L1-L59)
- [workflows-planning.md](file://src/modules/bmm/docs/workflows-planning.md#L1-L967)

## BMM 与其他模块的集成关系

BMM 与核心模块（Core）和其他模块（如BMB、BMBD）紧密集成，形成一个完整的AI代理生态系统。集成关系主要通过以下方式实现：

- **代理驱动**：BMM 使用来自Core模块的`bmad-master.agent.yaml`作为总协调者，同时调用BMB模块中的`bmad-builder.agent.yaml`进行构建任务。
- **多代理协作（Party Mode）**：通过`party-mode`工作流，BMM 可以召集来自BMM、CIS、BMB等模块的19+个代理进行实时协作，解决复杂问题。
- **配置共享**：BMM 与Core模块共享`config.yaml`配置文件，确保环境一致性。

例如，在执行`document-project`工作流时，BMM 会调用Core模块的`validate-workflow.xml`进行工作流验证，确保文档的完整性与正确性。

**Section sources**
- [README.md](file://src/modules/bmm/README.md#L104-L106)
- [analyst.agent.yaml](file://src/modules/bmm/agents/analyst.agent.yaml#L42-L44)

## BMM 在企业级项目中的应用示例

### 绿色field项目（Greenfield Project）

对于全新项目，BMM 推荐使用完整的四阶段流程：
1. **分析阶段**：运行`research`（市场/技术）和`product-brief`，验证市场可行性并定义产品愿景。
2. **计划阶段**：执行`create-prd`，生成详细的产品需求文档。
3. **解决方案阶段**：通过`architecture`工作流确定技术架构，创建用户故事。
4. **实现阶段**：进行冲刺规划、开发与代码审查，持续交付功能。

### brownfield项目（Brownfield Project）

对于现有项目，BMM 建议先进行文档化：
1. **文档阶段**：运行`document-project`工作流，自动分析现有代码库并生成项目上下文。
2. **跳过分析**：直接进入计划阶段，基于现有系统进行功能扩展或重构。
3. **实现阶段**：使用`correct-course`工作流处理技术债务或架构偏差。

**Section sources**
- [brownfield-guide.md](file://src/modules/bmm/docs/brownfield-guide.md#L1-L53)
- [workflows-analysis.md](file://src/modules/bmm/docs/workflows-analysis.md#L210-L217)

## 规模自适应智能特性

BMM 具备规模自适应智能特性，能够根据项目复杂度（Level 0-4）自动调整工作流路径：

- **Level 0-1**：适用于小功能或缺陷修复，推荐使用**Quick Flow**路径，仅需`spec → dev → review`三步。
- **Level 2**：适用于中等复杂度项目，执行PRD并可选架构设计。
- **Level 3-4**：适用于大型企业级项目，必须执行完整的PRD + 架构设计流程。

该特性通过`workflow-status`代理自动检测项目级别，并推荐相应的工作流路径，确保资源投入与项目需求相匹配。

**Section sources**
- [scale-adaptive-system.md](file://src/modules/bmm/docs/scale-adaptive-system.md#L1-L42)
- [README.md](file://src/modules/bmm/README.md#L84-L92)

## 结论

BMad Method (BMM) 作为一个AI驱动的敏捷开发工作流引擎，通过四个阶段的精细化管理，实现了从需求到交付的全流程自动化。其核心优势在于：
- **代理驱动**：通过专业AI代理（如分析师、产品经理、架构师）执行特定任务，确保专业性。
- **工作流自动化**：采用步骤文件架构，确保流程的严格顺序执行。
- **多模块集成**：与Core、BMB等模块无缝集成，形成强大的代理生态系统。
- **规模自适应**：根据项目复杂度智能调整工作流路径，提升效率。

无论是绿色field还是brownfield项目，BMM 都能提供灵活、高效的开发框架，帮助企业实现敏捷开发的智能化升级。