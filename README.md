# Agent to Figma Skills

面向 AI Agent 的 Figma / 画布**可选写入规范、视觉预设、版式模板与内容 DSL Skill 仓库**，与底层连通桥 [`agent-to-figma`](https://github.com/DeepVite/agent-to-figma) 解耦维护。

## 两个仓库的边界

- **`agent-to-figma`（能力与连通层）**：只负责提供稳定、安全的 Figma 读写能力本身（MCP Server、WebSocket 中继、Figma 插件、安全红线、Plugin API 避坑），**不涉及** Agent 写入的内容、布局、质量、视觉效果与文案。
- **`agent-to-figma-skills`（规范与模板层）**：只沉淀**可选的（Opt-in）**上层排版预设、原型标注规范、组件模板与领域写作 DSL，**不重复**端口、中继、频道连接或通用插件排障。

## Skill 目录

| Skill | 版本 | 定位 | 触发方式 |
|---|---|---|---|
| [`agent-to-figma-skill-create-rules`](skills/agent-to-figma-skill-create-rules/SKILL.md) | `0.1.0` | 编写/迁移配合 `agent-to-figma` 的 Skill 时遵守的两仓边界与防过拟合规范 | 编写/重构 Figma 上层 Skill 时 |
| [`figma-spec-presets`](skills/figma-spec-presets/SKILL.md) | `0.1.0` | Style A（暖橙通用精简风 v1.1）与 Style B（靛蓝原型说明系统 v2.0）两套排版与组件预设，按需渐进加载 | **Opt-in**：仅在用户明确要求预设 / Style A / Style B 时 |

## 参考文档

- [`docs/TYPOGRAPHY-PRESETS.md`](docs/TYPOGRAPHY-PRESETS.md)：Style A / Style B 快速选型对照与人读完整规范。
- [`AGENTS.md`](AGENTS.md)：面向在本仓库协作的 AI Agent 的边界与工作约定。

## 前置依赖

使用本仓库里的模板 / 视觉类 Skill 写入 Figma 前，需先安装并连通 [`agent-to-figma`](https://github.com/DeepVite/agent-to-figma)（或同构的 OpenFigma 工具链）。
