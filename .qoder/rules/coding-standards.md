# 编码规范

## 命名规范

- 类名：PascalCase（如 `PlayerController`）。
- 方法和变量：camelCase（如 `moveSpeed`、`takeDamage`）。
- 常量：UPPER_SNAKE_CASE（如 `MAX_MONSTER_COUNT`）。
- 接口：I + PascalCase（如 `IDamageable`）。
- 枚举：PascalCase（如 `MonsterType`），枚举成员使用 PascalCase。
- 文件名与主导出类名保持一致。

## 类型规范

- 优先明确类型，避免滥用 `any`；确需使用时应附注释说明原因。
- 当前 tsconfig.json 的 `strict: false` 设置保持不变，不得擅自修改。
- 公共接口、数据结构显式声明类型，不依赖隐式推断对外暴露。

## 模块设计

- 模块职责清晰，按 assets/scripts 下的目录划分：core / player / combat / monsters / skills / pets / progression / data / ui。
- 不允许随意跨模块修改其他模块的内部状态；跨模块交互通过明确定义的接口或事件进行。
- 避免循环依赖；出现循环依赖时应通过接口下沉、事件解耦或调整模块边界解决。
- data 模块承载配置与数据定义，逻辑模块不硬编码散落的可调数值。

## 代码质量

- 复杂逻辑必须有必要的注释，说明意图与关键决策，而非复述代码。
- 优先编写可测试的独立逻辑：数值计算、成长公式、掉落逻辑等尽量与引擎组件解耦，便于在 tests 中验证。
- 不提交调试用的临时代码、注释掉的废弃代码块。