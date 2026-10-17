# 求职项目雷达（Job Project Radar）

> 帮求职者找到匹配自身技术栈、能写进简历、有区分度的开源项目——吃透之后，直接产出可上简历的项目描述。
>
> 本技能是 [GuTou-Work_Skills](../README.md) 求职技能集中的一个，目录名为 `job-project-radar`。

[English Summary](#english-summary) · [快速开始](#快速开始) · [安装](#安装) · [工作原理](#工作原理) · [常见问题](#常见问题)

---

## 这是什么

一个 Agent Skill（技能包）：装在 Codex、Claude Code、WorkBuddy、豆包工作、ZCode 等支持 Agent Skills 的客户端里，当求职者说"帮我找个能写进简历的开源项目"时自动触发。

它解决求职中最头疼的两件事：

- **简历挂**：项目经历千篇一律（课程设计、跟练项目），过不了筛选；
- **一面挂**：简历有项目，但经不起追问——说不清架构、讲不出取舍、数字没有口径。

## 它做什么（一条流水线）

1. **反问摸底**：先问清楚目标岗位方向、技术栈、背景类型，输出「候选人画像卡」，并追问"还有什么要补充的"；
2. **检索评分**：在 GitHub 上按 6 维 rubric 检索打分（业务真实性 / 链路可拆分 / 深度挖掘空间 / 指标可写性 / 岗位族对齐 / 区分度），自动规避"红海套路项目"；
3. **候选短名单**：给出 3~5 个候选（含匹配点、简历增益点、红海风险、上手成本）+ 推荐首选，你选定一个；
4. **完整克隆**：把项目完整拉取到你的工作目录；
5. **深读吃透**：分层精读全部核心模块，产出《深读笔记》（含真实素材、挑战叙事、参数细节）；
6. **产出文案**：生成**精简 / 中间 / 详细**三个版本的简历项目描述 + 项目地址，可直接复制使用。

### 示例产出（节选 · 结构示意）

> **智能客服知识问答系统开发与优化（电商售后场景）** ｜ 2025.03 - 2025.06 ｜ 独立开发
>
> - 针对售后知识分散、人工回复慢的问题，搭建 RAG 问答系统：Top5 召回率从 65% 提升至 90%，回答准确率从 54% 提升至 89%（测试集 800 条，LLM+人工双评）；
> - 引入引用溯源与低置信兜底策略，高峰期平均响应从 3.2s 降至 1.4s；
>
> 注：以上为结构示意，量化指标请按自身实际情况校准。

## 快速开始

安装后，在对话里直接说（任一即可触发）：

- "求职项目雷达"
- "帮我找一个能写进简历的开源项目"
- "我项目经历没东西可写，帮我找个项目"

然后按它的反问回答 3~4 个问题，跟着流程走即可。

## 安装

**最简单的方式**：打开你的 Agent（Codex / Claude Code / WorkBuddy / 豆包工作 / ZCode 等），直接发这句话——

> 把 https://github.com/YUMIGUTOUTANG/GuTou-Work_Skills 里的 job-project-radar 技能装到你的技能目录，装好告诉我怎么触发。

Agent 会自己完成克隆与安装（若它没有文件写入权限，改用下面的手动方式）。装好后**新开一个会话**（或重启客户端）即可触发。

**手动方式**：本技能是 [GuTou-Work_Skills](../README.md) 技能集中的一个。克隆技能集，把 `job-project-radar` 目录复制（或链接）到对应客户端的技能目录：

```bash
git clone https://github.com/YUMIGUTOUTANG/GuTou-Work_Skills.git
cp -r GuTou-Work_Skills/job-project-radar "<技能目录>/job-project-radar"
```

| 客户端 | 技能目录 | 备注 |
| --- | --- | --- |
| Codex | `~/.agents/skills/`（用户级）或项目内 `.agents/skills/` | 支持软链接；`/skills` 查看、`$job-project-radar` 触发 |
| Claude Code | `~/.claude/skills/`（用户级）或项目内 `.claude/skills/` | 自然语言自动触发 |
| WorkBuddy / CodeBuddy | `~/.codebuddy/skills/` 或项目内 `.codebuddy/skills/`；也可在「技能市场 → 添加技能 → 上传技能」导入 | 与本仓库同为 SKILL.md 结构 |
| 豆包工作 | 客户端「技能」页 → 导入本地技能文件 | 技能文件开头需含 YAML 名称与描述，本仓库符合 |
| ZCode | 工作区 `.agents/skills/`，用 `$` 调用技能 | 以官方文档为准 |
| 其他 | 任何支持 Agent Skills（`SKILL.md`）规范的客户端 | Cursor / Gemini CLI / GitHub Copilot 等见各自文档 |

> 小技巧：Windows 用户可以用目录联接（`mklink /J`）把技能目录链接到技能集的 `job-project-radar` 文件夹，更新仓库内容即自动生效。

## 工作原理

全部工作流写在 `SKILL.md`，方法论细节在 `references/`（渐进式加载，只在需要时读取）：

| 文件 | 内容 |
| --- | --- |
| `SKILL.md` | 全流程编排与铁律 |
| `references/01-interview.md` | 反问问题库、背景四分类与包装策略、画像卡 |
| `references/02-search-rubric.md` | 检索策略、6 维评分、短名单格式、降级策略 |
| `references/03-red-ocean-list.md` | 红海 / 套路项目排除规则 |
| `references/04-deep-read.md` | 深读协议、吃透判定、防注入与安全 |
| `references/05-resume-writing.md` | 三版本结构、措辞规范、失败模式、示例骨架 |
| `references/06-metrics-menu.md` | 指标菜单、数字纪律、量级与跨度参考 |
| `templates/` | 输出文件模板（简历描述 / 深读笔记） |

## 常见问题

- **需要 GitHub 令牌吗？** 不需要，零配置即可运行；登录 `gh` CLI 会启用代码搜索等增强能力，检索质量更高。
- **会往我的目录里写什么？** 一个完整克隆的项目目录 + `求职简历-<项目名>.md` + `深读笔记-<项目名>.md`，都在调用时的工作目录下。
- **会运行项目代码吗？** 默认不会（不构建、不安装依赖、不执行仓库脚本）。
- **支持哪些方向？** AI 应用 / Agent / AI 全栈 / 后端；嵌入式等方向暂不支持。
- **量化数字是真实的吗？** 是按行业口径生成的**示例量级**，请按自身情况校准，并确保每个细节都能讲清楚——这个工具只帮你写得专业，讲得清楚要靠你自己把项目吃透。
- **我是非 AI 方向的后端呢？** 可以用，但方法论对 AI 方向覆盖最完整。

## 设计原则

- 场景真实性优先于技术炫技；
- 有区分度优先于高 star；
- 吃透优先于早点出文案。

## 贡献

- 欢迎补充「红海项目信号」：只加特征化描述，不点名攻击具体个人 / 机构；
- 欢迎提交指标写法与范文结构改进；
- 提交前请确认：不包含任何个人隐私、本地路径信息。

## License

[MIT](../LICENSE)

---

## English Summary

**Job Project Radar** is an agent skill for job seekers (AI application / Agent / AI full-stack / backend roles). It asks a few questions to understand your stack and background, searches GitHub for open-source projects that fit, scores candidates with a 6-dimension rubric (business realism, splittable pipeline, depth, measurable outcomes, role alignment, differentiation), fully clones the chosen project, reads it thoroughly, and produces ready-to-use resume descriptions in three lengths plus the project URL.

Works with any client that supports the Agent Skills standard (`SKILL.md`): Codex, Claude Code, WorkBuddy, Doubao Work, ZCode, and more. Requires only `git`; `gh` CLI is optional (recommended). Licensed under MIT.
