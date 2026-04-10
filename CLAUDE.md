# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

This is the **Anbege (安贝格) Marketing Skills** repository — a set of AI agent skill definitions for a Chinese window/door brand. It contains two independent pipelines:

1. **营销内容流水线** — produces short-video marketing content
2. **客户设计方案流水线** — guides customers from on-site opening photos to a full branded design proposal

There is no buildable code; the repo consists entirely of Markdown skill definitions and reference files.

## Pipelines

**营销内容流水线**（strict sequential）:

```
热点猎手 → [user confirms topic] → 文案写手 → 视频制作 → 审核运营 → [user approves] → publish
```

**客户设计方案流水线**（standalone, interactive）:

```
门窗设计师 (洞口照片 → 尺寸 → 开启方式 → 风格 → 颜色 → AI 出图 → 整屋延展 → 迭代 → 一键导出)
```

Each skill is defined by a `SKILL.md` (with YAML frontmatter: name, description, trigger phrases) and a `references/` directory containing brand knowledge files. `门窗设计师` additionally has an `assets/` directory for user-uploaded product/style/color/brand materials.

## Key Concepts

- **Content Pillars (P1–P5)**: Every piece of content must map to one of five pillars defined in `热点猎手/references/pillars.md` (健康人居, 高层安全, 静音节能, 智能窗场景, 审美升级).
- **Content Formats (F1–F4)**: F1 = 15s short video (default), F2 = 90s case study, F3 = 30s emotional hook, F4 = long-form image-text post. F1 is always the default unless explicitly requested otherwise.
- **Audience Tiers (Tier 1–6)**: Target audience segments defined in `热点猎手/references/audience.md`.
- **Scorecard**: Topics are scored on 5 dimensions (1–5 each, max 25) in `热点猎手/references/scorecard.md`.
- **Taboo list**: Hard red-line expressions that must never appear in any output. Each skill that produces text has its own copy in `references/taboo.md`.
- **Dreamina CLI**: Video/image generation uses the `dreamina` CLI tool (即梦), not web tools. Workflow documented in `视频制作/references/dreamina-cli-workflow.md`.

## Handoff Contract

Skills pass structured fields downstream. Required handoff fields are documented in the README table. If a required field is missing, the current skill must state the assumption explicitly rather than silently guessing.

## Reference File Duplication

Reference files (voice.md, taboo.md, offer.md, cta.md, formats.md) are intentionally duplicated across skills for self-containment. When updating brand guidelines, all copies across skills must be kept in sync.

## Output Paths

营销内容流水线：

- Trend reports: `data/trend-log.md`
- Scripts: `output/scripts/YYYY-MM-DD-[topic].md`
- Storyboards: `output/storyboards/YYYY-MM-DD-[topic].md`
- Videos/images: `output/videos/YYYY-MM-DD-[topic]/`
- Publish packs: `output/publish-packs/YYYY-MM-DD-[topic]/`

客户设计方案流水线（**所有目录与文件名必须中文**）：

- 项目状态: `output/设计方案/[客户-项目名]/项目状态.md`
- 洞口照片: `output/设计方案/[客户-项目名]/洞口照片/[房间标签]/[洞口编号]/照片/`
- 分格效果图: `output/设计方案/[客户-项目名]/分格效果图/[房间标签]/[洞口编号]/第[N]版/`
- 整屋效果图: `output/设计方案/[客户-项目名]/整屋效果图/[房间标签]/[洞口编号]/第[N]版/`
- 单洞口最终方案: `output/设计方案/[客户-项目名]/[房间标签]-[洞口编号]-最终方案.md`
- 导出成品方案: `output/设计方案/[客户-项目名]/成品方案/[客户姓名]-门窗设计方案-YYYY-MM-DD.md`

命名规则：
- `[洞口编号]` 用 `洞口01` `洞口02`，不用 `op-01`
- 版本号用 `第1版` `第2版` `最终版`，不用 `v1` `v2` `final`
- 子目录用 `照片/` `手绘/`，不用 `photos/` `sketches/`

## Language

All skill definitions, reference files, and generated content are in **Chinese (Simplified)**. The brand voice is conversational, warm, and advisory — never salesy or alarmist. Emotion intensity should stay at 3–5 on a 0–10 scale.
