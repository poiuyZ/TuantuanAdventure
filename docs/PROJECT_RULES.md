# 项目通用开发约束（PROJECT_RULES）

> 本文档与 `.qoder/rules/` 下四份规则保持一致，作为面向所有协作者的汇总入口。
> 权威来源：.qoder/rules/project-overview.md、cocos-development.md、coding-standards.md、safety-and-workflow.md。

## 1. 项目定位

- 《团团大冒险：萌兽来袭》，Q版卡通 Roguelike 生存割草，微信小游戏。
- 引擎固定 Cocos Creator 3.8.8，逻辑使用 TypeScript。
- 设计规划与已实现功能严格区分，详见 GAME_DESIGN.md。

## 2. Cocos 开发约束

- 场景、节点、组件、预制体使用 Cocos Creator 正规工作流。
- 不自行编写未经验证的 Cocos API；API 以 3.8.8 为准。
- 不随意手工修改 .scene、.prefab、.meta 文件；修改前先检查引用关系。
- 不把原生微信小游戏 Canvas 示例代码直接复制进 Cocos 工程。
- 优先使用组件生命周期、调度器和节点管理机制。

## 3. 编码约束

- 类名 PascalCase；方法/变量 camelCase；常量 UPPER_SNAKE_CASE；接口 I + PascalCase；枚举 PascalCase。
- 优先明确类型，避免滥用 any。
- 模块职责清晰；不跨模块修改内部状态；避免循环依赖。
- 复杂逻辑必须有注释；优先编写可测试的独立逻辑。
- tsconfig.json 的 strict 设置保持不变。

## 4. 安全与工作流约束

- 分阶段开发：先计划、后实施、再验证；只做当前授权阶段的内容。
- 修改前检查 Git 状态；不执行 git reset --hard / git clean / 强制操作。
- 不擅自删除、覆盖、重命名已有文件；批量删除必须先确认。
- 不升级 Cocos Creator 与项目依赖。
- 不擅自修改 package.json、tsconfig.json、构建配置。
- 不修改 library、temp、local、profiles 等自动生成目录。
- 不把未经验证的功能报告为完成；无法验证的标记「未验证」。
- 每阶段输出修改清单、测试结果、遗留问题。
- 可能破坏工程的操作必须先征求用户确认。