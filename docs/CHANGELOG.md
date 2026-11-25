# 变更日志（CHANGELOG）

## P0-02 项目基础结构建设（2026-11-25）

- Git 初始基线提交：`chore: initialize cocos creator project`（纳入 .gitignore、package.json、settings/、tsconfig.json，共 10 个文件）。
- 创建 assets 目录骨架：scenes、scripts（core/player/combat/monsters/skills/pets/progression/data/ui）、prefabs、textures、audio、resources/configs，空目录以 .gitkeep 保留。
- 创建根目录辅助目录：.qoder/rules、docs、tests、tools。
- 创建 4 份 Qoder 规则：project-overview.md、cocos-development.md、coding-standards.md、safety-and-workflow.md。
- 创建 6 份项目文档：GAME_DESIGN.md、TECHNICAL_DESIGN.md、PROJECT_RULES.md、MODULE_INTERFACES.md、TEST_PLAN.md、CHANGELOG.md。
- 第二次提交：`chore: establish game project structure and rules`。
- 未修改任何 Cocos 工程配置（package.json / tsconfig.json / settings / .gitignore 保持原样）。
- 未创建任何游戏脚本、场景、预制体或美术资源。
- 备注：assets 下新建目录的 .meta 文件将在下次打开 Cocos Creator 编辑器时自动生成。

## P0-01 工程只读审查（2026-11-25）

- 完成工程结构、配置、代码环境、Git 状态的只读审查。
- 确认：Cocos Creator 3.8.8 空项目，assets 为空，无脚本/场景/资源；TS 配置链路有效；library 缓存均为引擎内置资源。
- 确认：Git 已初始化（master 分支）但无提交；无远程仓库；微信小游戏构建未配置。
- 结论：无配置错误，项目处于未开发状态。审查报告已在会话中输出。