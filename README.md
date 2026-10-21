# 我的 Kimi Skills 合集

这是我自己编写、在 Kimi Work（桌面端）中实际使用的四个 Skill。每个 Skill 就是一个文件夹，里面有一个 `SKILL.md`（入口指令文件），外加按需加载的参考资料、示例和评估用例。

## 什么是 Skill

Skill 是写给 AI Agent 看的「 reusable 操作手册」：把一套方法论、知识库或工作流写进 `SKILL.md`，Agent 遇到匹配的任务时会自动加载，按里面的流程和纪律执行，而不是每次临场发挥。

## 技能一览

| 技能 | 用途 | 触发方式（举例） |
| --- | --- | --- |
| `adversarial-review` | 对抗式审查：给想法 / 方案 / 计划找隐藏假设、逻辑漏洞、执行风险、事实错误和认知偏差，按严重程度排序并给修正建议 | 「帮我审查一下这个方案」「挑挑毛病」「红队视角」「stress test this plan」 |
| `first-principles` | 第一性原理分析：从不可再简化的基本事实和约束出发重新推导方案，摆脱「别人都这么做」的类比惯性 | 「用第一性原理分析」「这个问题的本质是什么」「除了常规做法还有别的路吗」 |
| `audio-program-teaching` | 《音频节目创作与教学》知识库：本科音频节目课程的备课、大纲、教案、PPT、PBL 项目指导（选题、脚本、录音、剪辑、发布评价） | 「帮我备音频课」「出一份教学大纲」「指导选题策划」 |
| `web-development-teaching-expert` | 《网页设计与制作》教学专家：HTML5 + CSS3 + JavaScript 课程的课时安排、课件、代码教学、作业命题、报错诊断 | 「准备网页设计课」「讲 HTML 第一课」「出期末考核题」 |

## 目录结构

```
kimi-skills/
├── adversarial-review/            # SKILL.md + references/ + examples/ + evals/
├── first-principles/              # SKILL.md + references/ + examples/ + evals/
├── audio-program-teaching/        # SKILL.md + chapters/(m00–m10) + glossary/cheatsheet/patterns
└── web-development-teaching-expert/  # SKILL.md + chapters/(ch01–ch10) + teaching/ 教学规范
```

每个技能的通用约定：

- `SKILL.md` —— 入口文件，顶部的 `name` / `description`（frontmatter）决定 Agent 什么时候调用它；正文是执行纪律和流程。
- `references/` 或 `chapters/` —— 按需加载的细节资料，避免一次性塞满上下文。
- `examples/` —— 完整示例，展示输出应该长什么样。
- `evals/` —— 测试用例和评估结果，用来验证技能是否按预期工作。

## 怎么使用

### 在 Kimi Work 中安装

把想要的技能文件夹整个复制到本机技能目录：

```
~/Library/Application Support/kimi-desktop/daimon-share/daimon/skills/
```

例如：

```bash
cp -R adversarial-review ~/Library/Application\ Support/kimi-desktop/daimon-share/daimon/skills/
```

重启或新开一个会话后，Agent 会在任务匹配时自动调用，不需要手动指定。

### 手动触发

直接在对话里用触发语，例如：

- 「帮我用第一性原理分析一下这个决定」
- 「对抗式审查一下这份商业计划」
- 「帮我备下周的网页设计课，32 课时怎么排」

### 在其他 Agent 平台使用

这套 Skill 是通用 Markdown 格式，不依赖 Kimi 私有 API：把文件夹放到任何支持 SKILL.md 约定的 Agent（如 Claude Code、Codex 等）的技能目录即可。注意 `audio-program-teaching` 和 `web-development-teaching-expert` 中涉及课件生成时默认配合 `kimi-slides`，在其他平台可改用各自的 PPT 工具。

## 自己写一个 Skill

最小结构：

```
my-skill/
└── SKILL.md
```

`SKILL.md` 开头写 frontmatter：

```markdown
---
name: my-skill
description: 一句话说清楚这个技能干什么、什么时候触发，多给几个触发语
---

# 正文写执行纪律、流程、输出格式
# 细节内容拆到 references/ 里，用相对路径引用，按需读取
```

要点：`description` 决定 Agent 会不会在正确时机找到它，要写清触发场景；正文别一次塞满，重内容拆文件按需加载；配 `examples/` 和 `evals/` 保证质量可验证。
