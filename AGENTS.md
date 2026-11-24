# AGENTS.md

Guidance for AI agents working inside `agent-to-figma-skills`.

## Repository Purpose

`agent-to-figma-skills` holds **optional** Figma / canvas writing skills, visual presets, typography specifications, layout templates, and domain content DSLs separated from [`agent-to-figma`](https://github.com/DeepVite/agent-to-figma).

## Boundary & Skill Authoring Rules

Before creating, migrating, or reviewing any skill in `skills/`, read [`skills/agent-to-figma-skill-create-rules/SKILL.md`](skills/agent-to-figma-skill-create-rules/SKILL.md) first.

Core boundary summary:
1. **`agent-to-figma` owns transport, execution, and safety**: relay/port/channel connection, MCP Zod schemas, declarative execution primitives, `create_page` isolation, and generic Plugin API pitfalls belong in `agent-to-figma`.
2. **`agent-to-figma-skills` owns content, layout, visuals, and domain DSLs**: typography scales, color tokens, component templates, prototype spec conventions, and domain writing styles live here as **opt-in** skills.
3. **Never force templates**: Keep skills scoped and optional so agents are not locked into one rigid style when users want freeform output.

## 回复风格(用户硬性要求)

凡是包含方案/建议/分析的回答,结尾必须追加一段 **【精炼回复】**,格式硬性要求:

1. 先输出一行 Markdown 分割线 `---`,紧接 **【精炼回复】** 标题;
2. 内容结构化,加粗小标题+短列表,禁止一大段文字:「结论」一两句话;「主要事项」逐条一行;
3. 决策项结构化:每个问题独立成块,问题单独一行加粗,下面每个选项各占一行(列表),标注推荐项,不抛开放性问题;
4. 口吻像下级向上级汇报:通俗直白、先结论后理由,最大化节省用户的阅读时间、理解成本和决策成本。

## 删除安全规则(用户硬性要求)

<!-- `_recycle/` 为项目级删除回收站目录，保留原目录结构与删除原因说明，请勿作为垃圾目录自动清理。 -->

- 批量整理、删除前,先列清单向用户确认,得到明确同意后再执行。
- 执行删除时不直接删除:把文件移到项目根目录的回收站文件夹(默认 `_recycle/`,项目已有约定则从约定),保持目录结构原样,便于随时恢复。
- 每个被删除的文件配一个 `<文件名>-delete reason.md`,写明:删除理由、原始位置、删除日期。
