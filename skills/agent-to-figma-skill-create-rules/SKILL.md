---
name: agent-to-figma-skill-create-rules
version: 0.1.0
description: Boundary rules and authoring guidelines for creating or refactoring skills that pair with agent-to-figma. Use when creating a new Figma writing, layout, preset, template, or DSL skill, migrating styles out of agent-to-figma, or deciding whether a rule, schema, or pitfall belongs in agent-to-figma vs agent-to-figma-skills.
---

# Agent to Figma — Skill 创建与边界规范

编写、拆解或评审任何配合 `agent-to-figma` 使用的上层 Skill 时，遵守本规范，确保两仓职责纯净且不压制模型能力。

## 1. 两仓边界黄金法则

> **`agent-to-figma` 只负责写入能力本身；`agent-to-figma-skills` 只负责可选的内容、布局、视觉与模板规范。**

判断一项内容该放哪边，做一次剥离测试：**「如果把画布内容换成完全不同的领域和风格，这条规则或 Schema 是否依然成立？」**

| 维度 | 保留在 `agent-to-figma`（能力与连通层） | 放入 `agent-to-figma-skills`（内容与审美层） |
|---|---|---|
| **连接与运行** | Relay（`3055`）、WebSocket 频道发现、`manifest.json`、客户端 MCP 安装 | 禁止重复写端口/中继启动步骤或排障指南；仅注明依赖 `agent-to-figma` |
| **Schema 与 DSL** | **协议与执行器 Schema/DSL**：MCP 工具 Zod 入参、声明式建树原语 `create_tree` 结构、颜色 `0–1` RGBA 类型约定 | **业务与版式 Schema/DSL**：PRD 说明页骨架、原型旁白卡结构、看板 JSON 模板、组件布局蓝图 |
| **规则与约束** | **数据安全红线**：写前 `create_page` 建隔离页、删改前确认、坐标冲突检测 `dry_run` | **审美与文案规范**：字号阶梯、色板 Token、间距节奏、中英文空格、内容必须包含的业务模块 |
| **API 避坑** | **通用引擎怪癖**：`fillColor.a=0` 变不透明、`figma.mixed` 报错、`dynamic-page`、Windows `@params.json` | 原则上不写；仅当某模板**特定构件**依赖非显性属性（如 4px 竖条需 `layoutSizingVertical: "FILL"`）时附 1 行提示 |

## 2. 上层 Skill 编写四条硬规则

1. **必须可选（Opt-in），禁止强制锁死**
   - 写清适用场景与触发边界，只提供可选风格/模板，**禁止**写「写任何 Figma 画布前必须先问用户选样式 X/Y」这类全局拦路规则。
   - 当用户需要自由探索或已有明确设计稿风格时，允许模型直接发挥，不要套壳过拟合。
2. **渐进式披露（Progressive Disclosure）**
   - `SKILL.md` 保持精简（触发条件、选型对照、结构骨架、引用路由），不要把整套色板、全量字号表或大段示例直接堆在入口文件。
   - 具体 Token、组件规格与 DSL Schema 拆入 `references/`，按当前任务只读命中的文件。
3. **Token 与工具友好表达**
   - 颜色同时给出 `#HEX`（给人/可读性）与 `0–1` 浮点 RGBA（给 `agent-to-figma` 工具直接填参），减少模型换算误差。
   - 布局规范优先描述嵌套 Auto-Layout 语义（方向、`padding`、`itemSpacing`、`FILL`/`HUG`），避免写死脆弱的绝对像素坐标。
4. **守住安全底线但不越权**
   - 模板 Skill 可提醒在独立页内构建，但不得指令 Agent 绕过确认去覆盖或删除用户已有页面；连接与执行失败排障交回 `agent-to-figma`。

## 3. 新建 Skill 目录与规范检查

```text
skills/<skill-name>/
├── SKILL.md           # 必填：kebab-case name（与目录一致）、version、精准 description（≤1024 字，前 ~250 字写清用途与触发时机）
├── CHANGELOG.md       # 独立自建 skill 同步维护版本记录
└── references/        # 按需：大块 Token 表、模板 DSL Schema、具体样例
```

### 发布前自检清单（5 项全过才算合格）

- [ ] **无连通噪音**：正文没有抄写 `npm run relay`、3055 端口排查或通用 `pitfalls.md` 内容。
- [ ] **无强制拦截**：没有要求模型在无关任务中强行套模板或必问模板选择。
- [ ] **边界清晰**：所含 Schema/DSL 描述的是「内容长什么样」，而非底层桥接协议。
- [ ] **按需加载**：大体积规范表与 DSL 样本已放进 `references/`，且 `SKILL.md` 写明何时读取。
- [ ] **命名合规**：目录名与 frontmatter `name` 完全一致（小写字母 + 数字 + 连字符），`description` 准确且不与其他 Skill 抢触发。
