# Agent to Figma Skills

面向 AI Agent 的 Figma / 画布**写入规范、视觉预设、版式模板与内容 DSL Skill 仓库**，与底层连通桥 [`agent-to-figma`](https://github.com/DeepVite/agent-to-figma) 解耦维护。

## 两个仓库的边界

- **`agent-to-figma`（能力与连通层）**：只负责提供稳定、安全的 Figma 读写能力本身（MCP Server、WebSocket 中继、Figma 插件、安全红线、Plugin API 避坑），**不涉及** Agent 写入的内容、布局、质量、视觉效果与文案。
- **`agent-to-figma-skills`（规范与模板层）**：只沉淀**可选的**上层排版预设、原型标注规范、组件模板与领域写作 DSL，**不重复**端口、中继、频道连接或通用插件排障。

## 当前内容

| Skill | 定位 | 状态 |
|---|---|---|
| [`agent-to-figma-skill-create-rules`](skills/agent-to-figma-skill-create-rules/SKILL.md) | 编写/迁移配合 `agent-to-figma` 的 Skill 时遵守的边界定义与防过拟合规范 | 已创建（v0.1.0） |

> 后续将从 `agent-to-figma` 迁移 Style A / Style B 预设及相关模板 Skill 至本仓库。

## 前置依赖

使用本仓库里的模板 / 视觉类 Skill 写入 Figma 前，需先安装并连通 [`agent-to-figma`](https://github.com/DeepVite/agent-to-figma)。
