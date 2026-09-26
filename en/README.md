<p align="center">
  <a href="../README.md">Repository home</a> · <strong>English</strong> · <a href="../zh-CN/README.md">简体中文</a>
</p>

# Feed This to Your AI Agent. Avoid the UI Mistakes That Cause Hours of Rework.

### 把这份指南交给 AI Agent，避开那些会造成数小时返工的 UI 设计错误

*Vibe coding moves quickly. UI mistakes compound even faster.*

Give [`GUIDE.md`](GUIDE.md) to your AI coding agent once at the start of a UI task. The agent can apply it immediately while designing, implementing, or repairing the interface—without forcing the project into one visual style.

The guide turns lessons from real UI failures into practical safeguards: avoiding patch-on-patch CSS, preserving approved parts of the interface, defining interaction and persistence states, managing visual assets, diagnosing scrolling and positioning problems, and verifying the complete user journey instead of one isolated screen.

> **Use it in one step:** attach [`GUIDE.md`](GUIDE.md) once when starting the AI coding task and say: “Read this guide first. Apply the relevant safeguards while working on this UI, without limiting visual exploration.”

**[Read the English guide](GUIDE.md)** · **[阅读简体中文版](../zh-CN/README.md)**

**[Download the English package (.zip)](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/Human-AI-UI-Collaboration-Guide-v1.0.0-EN.zip)** · [下载简体中文包](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/Human-AI-UI-Collaboration-Guide-v1.0.0-zh-CN.zip)

## One upload per task window

| Situation | What to do |
|---|---|
| Starting a new task or chat | Attach `GUIDE.md` once, together with the product goal or current UI context. |
| Continuing in the same task window | Keep working normally. There is no need to upload the guide again. |
| The work begins to drift | Remind the agent to follow the guide or point it to the relevant section. |
| Opening a separate task or chat | Attach the guide again unless it is already available through shared project Sources or workspace instructions. |

## What it helps prevent

- Hiding an old design under new color blocks, pseudo-elements, or duplicate layers.
- Changing approved parts of the interface while repairing one local issue.
- Treating a behavioral or state problem as if it were only a CSS problem.
- Leaving empty, loading, success, error, refreshed, or restored states inconsistent.
- Opening an isolated component or result page and calling the whole product verified.
- Repeating subjective visual tweaks without identifying the structural cause.
- Shipping obsolete experiments and visual assets alongside the approved version.

## Repository structure

```text
human-ai-ui-collaboration-guide/
├── README.md                       Bilingual repository entrance
├── en/
│   ├── README.md                   English instructions
│   ├── GUIDE.md                    English guide and prompts
│   ├── CHANGELOG.md                English version history
│   └── COPYRIGHT-AND-PERMISSIONS.md
└── zh-CN/
    ├── README.md                   中文使用说明
    ├── GUIDE.md                    中文指南与提示词
    ├── CHANGELOG.md                中文版本记录
    └── COPYRIGHT-AND-PERMISSIONS.md
```

## What is inside each download

English package:

```text
Human-AI-UI-Collaboration-Guide-v1.0.0-EN/
├── README.md                       Start here
├── GUIDE.md                        Full guide and ready-to-use prompts
├── CHANGELOG.md                    Version history
└── COPYRIGHT-AND-PERMISSIONS.md    Usage terms
```

Simplified Chinese package:

```text
人机协作UI设计与开发经验避雷指南-v1.0.0-zh-CN/
├── README.md                       中文使用入口
├── GUIDE.md                        中文完整指南与可复制提示词
├── CHANGELOG.md                    中文版本记录
└── COPYRIGHT-AND-PERMISSIONS.md    中文版权与使用权限
```

The two language packages are independent. English readers do not need to navigate through Chinese files, and Chinese readers do not need to search inside an English-first archive.

## Choose a reading path

| Task | Start with | Continue with |
|---|---|---|
| Greenfield or zero-to-one design | Sections 1–5 | Sections 18–19 and relevant parts of Section 23 |
| Major redesign | Sections 2.2, 5, and 8–10 | Sections 17–20 |
| Targeted UI repair | Sections 2.3 and 6–16 | Sections 19–20 and the relevant risk module in Section 23 |
| Prompt preparation | Sections 21–22 | Add only the safeguards required by the current task |

## Read online

- [English edition](GUIDE.md)
- [简体中文版](../zh-CN/GUIDE.md)

## Download version 1.0.0

| Edition | Independent publication package |
|---|---|
| English | [Download the English ZIP](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/Human-AI-UI-Collaboration-Guide-v1.0.0-EN.zip) |
| Simplified Chinese | [Download the Simplified Chinese ZIP](https://github.com/cherliangvisual/human-ai-ui-collaboration-guide/releases/download/v1.0.0/Human-AI-UI-Collaboration-Guide-v1.0.0-zh-CN.zip) |

## A practical workflow

1. Attach the guide before UI work begins.
2. Provide the product goal or current interface, plus the boundaries of the requested change.
3. Ask the agent to use only the safeguards relevant to the current task.
4. Review major visual decisions before the agent changes production code.
5. Verify the complete user journey before treating the task as finished.

## Publication information

- Version: 1.0.0
- Published: 26 September 2026
- Author: **Cher Liang (梁卓滢)**
- GitHub: [@cherliangvisual](https://github.com/cherliangvisual/)
- Change history: [CHANGELOG.md](CHANGELOG.md)

## Copyright and permissions

Copyright © 2026 Cher Liang (梁卓滢). All rights reserved.

This publication is available for reading and personal, non-commercial reference. You may also provide it as private task context to an AI assistant that you use for your own project. Neither the reader nor the AI may publicly upload, redistribute, translate, adapt, rewrite, or publish a substitute version of the guide. It is not released under an open-source, open-content, or Creative Commons license.

Read the complete [copyright and permissions notice](COPYRIGHT-AND-PERMISSIONS.md).
