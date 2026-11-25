# Cocos 开发规范

## 引擎与语言

- 引擎固定使用 Cocos Creator 3.8.8，不升级、不混用其他版本。
- 游戏逻辑统一使用 TypeScript。
- 任何引擎 API 以 3.8.8 对应版本的 API 为准（参考 temp/declarations/cc.d.ts 与官方 3.8 文档）。

## 资源工作流

- 场景、节点、组件、预制体一律使用 Cocos Creator 编辑器的正规工作流创建和维护。
- 不随意手工修改 .scene、.prefab、.meta 等资源文件。
- 修改场景和资源前，先检查其引用关系（uuid 引用、组件依赖、资源依赖），避免破坏引用。
- 不创建虚假的场景、预制体、图片或音频资源占位内容。

## 编码约束

- 不自行编写未经验证的 Cocos API 调用；不确定的 API 先查声明文件或文档确认。
- 不把原生微信小游戏 Canvas 示例代码直接复制进 Cocos 工程；微信平台能力通过 Cocos 提供的适配层与构建流程接入。
- 优先使用 Cocos 组件生命周期（onLoad / start / update / onDestroy 等）、调度器（schedule）和节点管理机制，避免自建脱离引擎的循环与定时器。

## 自动生成目录

- library、temp、local、profiles 为 Cocos 自动生成目录，不手工修改，不纳入版本管理。