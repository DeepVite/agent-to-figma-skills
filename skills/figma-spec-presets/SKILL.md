---
name: figma-spec-presets
version: 0.1.0
description: Optional typography and visual spec presets (Style A warm-orange compact docs; Style B indigo prototype-spec system) for writing structured product docs, dashboards, or prototype annotation canvases in Figma or OpenFigma. Use ONLY when the user explicitly requests a preset, Style A/B, or consistent prototype-spec visual tokens; never force onto freeform design tasks.
---

# Figma Spec Presets（可选排版与说明视觉预设）

提供两套面向产品文档、数据看板与原型旁白的**可选视觉预设**（字号阶梯、色板 Token、Auto-Layout 间距与语义构件），配合底层写入能力（如 `agent-to-figma` 或 OpenFigma 工具）使用。

> **防过拟合原则（Opt-in）**：本 Skill 是可选的视觉积木，不是强制页面脚本。**仅在用户明确要求套用样式预设 / Style A / Style B / 统一原型说明视觉时启用**；当用户需要自由创作、已有目标设计稿风格或未要求预设时，直接按需发挥，禁止强行拦截询问。

---

## 1. 快速选型对照（按需二选一）

| 维度 | Style A · 暖橙通用精简风（v1.1） | Style B · 靛蓝原型说明系统（v2.0） |
|---|---|---|
| **适用场景** | 通用产品文档、数据看板、轻量说明、沿用暖橙系旧页、紧凑高密度排版 | 原型旁白、PRD 模块拆解、交互与异常边界标注、需与产品 UI 清晰视觉隔离 |
| **画布与卡片** | `#F5F6F8` 画布 + `#FFFFFF` 无描边圆角卡 | `#0F172A` 深色头图 + `#F8FAFC` 画布 + `#FFFFFF` `1px #E2E8F0` 描边卡 |
| **正文 / 底线** | 正文 `13px/20px` · 注释 `11px/16px` | 正文 `14px/22px` · **底线 `12px/18px`**（适合 50% 缩放巡检） |
| **主色与语义** | 暖橙 `#D07A16` / `#FA8C16` + 单色状态色 | 靛蓝 `#4F46E5` + 完整语义三元组（主色 / 浅底 / 边框） |
| **专用构件** | 顶部 6px 装饰条、4×16 章节竖条、基础卡片与行表 | 编号标点项（Pin）、四类语义提示块（Callout）、胶囊标签（Badge）、异常兜底表（Table） |

---

## 2. 渐进式披露（只读命中的预设）

确定要使用某一套预设后，**只读取对应参考文档**，不要两份全读：

- 选用 **Style A（暖橙通用精简风）** → 读取 [`references/style-a.md`](references/style-a.md)
- 选用 **Style B（靛蓝原型说明系统）** → 读取 [`references/style-b.md`](references/style-b.md)

如果用户明确要求「用你们的原型说明预设」但未指定 A/B，用一句极简说明请用户在 Style A / Style B 中选一后再读取对应文件。

---

## 3. 边界与写作约定

- **底层连接与安全交给 `agent-to-figma`**：中继连接、频道选择、写前建独立隔离页（`create_page`）以及通用 Figma Plugin API 避坑全部由底层连通 Skill 负责，本 Skill 不重复也不绕过。
- **Token 与布局优先**：参考文档均同时提供 `#HEX` 与 `0–1` 浮点 RGBA（供写入工具直接填参）；优先用嵌套 Auto-Layout（`VERTICAL`/`HORIZONTAL`、`padding`、`itemSpacing`、`FILL`/`HUG`）表达结构，不写死脆性坐标。
- **按内容剪裁结构**：按本次信息密度自由组合卡片、表格、标点与提示块，不把每页都硬塞成同一种版式。
