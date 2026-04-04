# Anbege Marketing Skills (安贝格营销 Agent 技能包)

A portable skill set for the Anbege (安贝格) marketing content factory system, designed for skills workflows.

## Skills

| Skill | Role | Trigger examples |
|-------|------|-----------------|
| `热点猎手` | Scan trends, score topics against brand pillars | "今日选题" "找热点" "scan trends" |
| `文案写手` | Generate scripts and copy from confirmed topics | "写脚本" "write script" "生成文案" |
| `视频制作` | Break scripts into storyboards + Dreamina CLI generation jobs | "做分镜" "generate video" "拆镜头" "即梦" "dreamina" |
| `审核运营` | Quality check scripts, assemble publish packs | "审核脚本" "review script" "质检" |

## Pipeline

```
热点猎手 → [you confirm] → 文案写手 → 视频制作 → 审核运营 → [you approve] → publish
```

## Installation

### Option 1: Copy into global Agent skills

```bash
git clone https://github.com/YOUR_USERNAME/anbege-marketing.git
cp -r anbege-marketing/skills/* "$Agent_HOME/skills/"
```

### Option 2: Keep the repo as a local workspace

```bash
git clone https://github.com/YOUR_USERNAME/anbege-marketing.git
cd anbege-marketing/skills
```

### Option 3: Ask Agent to install from GitHub

In a new Agent session, say:

> "Clone my skills from github.com/YOUR_USERNAME/anbege-marketing and install them into my Agent skills."

The agent will clone and copy the skills into place.

## Handoff Contract

Use the skills as a pipeline, but keep the handoff fields stable so downstream agents do not need to infer missing context.

| Upstream skill | Required handoff fields | Main output |
|-------|------|-----------------|
| `热点猎手` | topic title, source, pillar, format, audience tier, risk note | scored topic brief |
| `文案写手` | title, pillar, format, audience tier, brand mention level | final script with cover, comments, DM reply |
| `视频制作` | title, duration, shot list, subtitles, cover prompt | storyboard + generation prompts |
| `审核运营` | pass/fail result, issue list, publish readiness | review report + publish pack |

If a required field is missing, the current skill should state the assumption explicitly instead of silently guessing.

## Structure

Each skill is self-contained with its own reference files:

```
skills/
├── 热点猎手/
│   ├── SKILL.md
│   └── references/
│       ├── pillars.md
│       ├── scorecard.md
│       ├── audience.md
│       ├── evergreen-topics.md
│       └── taboo.md
├── 文案写手/
│   ├── SKILL.md
│   └── references/
│       ├── voice.md
│       ├── taboo.md
│       ├── formats.md
│       ├── offer.md
│       ├── hooks.md
│       └── cta.md
├── 视频制作/
│   ├── SKILL.md
│   └── references/
│       └── dreamina-cli-workflow.md  ← update this with your Jimeng / Dreamina CLI workflow
├── 审核运营/
│   ├── SKILL.md
│   └── references/
│       ├── review-rules.md
│       ├── voice.md
│       ├── taboo.md
│       ├── offer.md
│       ├── formats.md
│       ├── cta.md
│       ├── publish-checklist.md
│       └── iteration-rules.md
└── README.md
```

## Updating

When you update brand guidelines (voice, taboo, offer, etc.), update the reference files inside each skill that uses them. These skills are intentionally self-contained, so duplicated reference files must stay in sync.

## Video Producer Note

The `视频制作` skill includes a `dreamina-cli-workflow.md` reference file. Fill it in with your Jimeng / Dreamina CLI install, login, command usage, prompt rules, and troubleshooting steps. The skill will automatically use the latest version.
