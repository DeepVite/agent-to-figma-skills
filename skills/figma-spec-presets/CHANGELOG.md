# Changelog — figma-spec-presets

## [0.1.0] - 2026-11-24

- 从 [`agent-to-figma`](https://github.com/DeepVite/agent-to-figma) 迁移 Style A（暖橙通用精简风 v1.1）与 Style B（靛蓝原型说明系统 v2.0）至独立可选 Skill。
- 按 `agent-to-figma-skill-create-rules` 完成边界提纯：
  - 转为严格 Opt-in 可选触发，移除原主仓「写前必问样式 A/B」的强制拦截规则。
  - 为 `references/style-b.md` 补齐全量色彩 Token 的 `0–1` 浮点 RGBA 换算值。
  - 移除 `references/style-b.md` 中混入的通用 Plugin API 避坑（交回主仓 `pitfalls.md`），仅保留构件级 Auto-Layout 提示。
