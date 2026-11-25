# 模块职责与接口规划（MODULE_INTERFACES）

> **设计草案**：本文档描述未来模块的职责与接口方向。
> 所有模块、类、接口**均未实现**，命名与签名在实现阶段可能调整。

## core（assets/scripts/core/）

- 职责：游戏入口、局内流程状态机（准备/进行中/升级暂停/结算）、事件总线、全局服务定位。
- 规划接口方向：
  - `GameManager`：局开始/结束、暂停/恢复、状态查询。
  - `EventBus`：`on / off / emit` 类型安全事件（如 monster-killed、level-up、player-dead）。
  - `GameEvents`：事件名与载荷类型定义。

## player（assets/scripts/player/）

- 职责：玩家角色移动（摇杆输入驱动）、属性（生命/移速/拾取范围等）、受击与死亡。
- 规划接口方向：
  - `PlayerController`（Component）：接收移动输入向量。
  - `PlayerStats`：属性读写、加成计算（纯逻辑，可测试）。

## combat（assets/scripts/combat/）

- 职责：伤害计算、索敌（最近/范围）、命中判定、经验/金币掉落物管理。
- 规划接口方向：
  - `IDamageable`：`takeDamage(amount)`、`isDead`。
  - `DamageCalculator`：纯函数伤害公式。
  - `TargetFinder`：轻量距离索敌（不依赖引擎物理，待技术验证）。

## monsters（assets/scripts/monsters/）

- 职责：怪物生成器（波次/时间曲线）、追踪 AI、6 种普通怪物行为、BOSS 机制、对象池。
- 规划接口方向：
  - `MonsterSpawner`：按配置驱动生成节奏。
  - `MonsterBase`（Component）：追踪、受击、死亡掉落。
  - `WaveSchedule`：波次配置解析（纯逻辑）。

## skills（assets/scripts/skills/）

- 职责：6 种初始技能的定义、自动释放、目标选择、升级分支。
- 规划接口方向：
  - `ISkill`：`id`、`level`、`tick(dt)`、`upgrade()`。
  - `SkillRegistry`：技能配置注册与实例化。

## pets（assets/scripts/pets/）

- 职责：3 只宠物的跟随、辅助攻击/增益、出战管理。
- 规划接口方向：
  - `PetBase`（Component）：跟随目标、行为 tick。
  - `PetConfig`：宠物数据定义。

## progression（assets/scripts/progression/）

- 职责：经验累积与升级曲线、三选一选项生成与选择应用、金币结算、胜负判定。
- 规划接口方向：
  - `LevelSystem`：`addExp()`、升级事件（纯逻辑，可测试）。
  - `UpgradeOptionPool`：三选一候选生成（权重规则待定）。
  - `RunResult`：结算数据（存活时长/击杀数/金币）。

## data（assets/scripts/data/）

- 职责：配置加载（resources/configs JSON）、本地存档读写与版本管理。
- 规划接口方向：
  - `ConfigStore`：类型化配置访问。
  - `SaveSystem`：`load() / save()`，基于 sys.localStorage（微信适配待验证）。

## ui（assets/scripts/ui/）

- 职责：虚拟摇杆、HUD（血条/经验条/计时/击杀数）、升级三选一面板、结算界面、主界面。
- 规划接口方向：
  - `Joystick`（Component）：输出归一化移动向量事件。
  - `HudView` / `LevelUpPanel` / `ResultPanel`：订阅事件刷新，不持有玩法状态。

## 依赖方向（规划）

ui → progression / combat / player；monsters / skills / pets → combat / data；全部模块可用 core 基础设施；data 不依赖玩法模块。禁止循环依赖。