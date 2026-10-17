# GuTou-Work_Skills · 求职技能集

> 面向研发岗求职者的开源 Agent Skills 合集：每个技能一个独立目录，遵循 Agent Skills 规范（`SKILL.md`），兼容 Codex / Claude Code / WorkBuddy / 豆包工作 / ZCode 等客户端。

## 技能列表

| 技能 | 一句话介绍 | 适用人群 |
| --- | --- | --- |
| [求职项目雷达（job-project-radar）](./job-project-radar/) | 反问摸底 → GitHub 检索评分 → 完整克隆 → 深读吃透 → 产出可上简历的三版本项目描述 | AI 应用 / Agent / AI 全栈 / 后端方向求职者 |

*更多求职技能持续加入中。*

## 安装

### 方式一（最简单）：把仓库地址丢给 Agent，让它自己装

打开你的 Agent（Codex / Claude Code / WorkBuddy / 豆包工作 / ZCode 等），把仓库地址和这句话直接发给它：

> 把 https://github.com/YUMIGUTOUTANG/GuTou-Work_Skills 这个仓库里的技能安装到你的技能目录，装好后告诉我怎么触发。

只想装某一个技能时：

> 把 https://github.com/YUMIGUTOUTANG/GuTou-Work_Skills 里的 job-project-radar 技能装到你的技能目录。

Agent 会自己完成克隆与目录摆放；装好后**新开一个会话**（或重启客户端）即可使用。
如果客户端自带技能安装器（如 Codex 的 `$skill-installer`），也可以直接给它技能目录链接：
`https://github.com/YUMIGUTOUTANG/GuTou-Work_Skills/tree/main/job-project-radar`

### 方式二：手动克隆 + 复制 / 链接

先克隆本仓库：

```bash
git clone https://github.com/YUMIGUTOUTANG/GuTou-Work_Skills.git
```

然后把想用的技能目录复制（或链接）到你的客户端技能目录（目录名保持不变）：

| 客户端 | 技能目录 |
| --- | --- |
| Codex | `~/.agents/skills/`（用户级）或项目内 `.agents/skills/` |
| Claude Code | `~/.claude/skills/`（用户级）或项目内 `.claude/skills/` |
| WorkBuddy / CodeBuddy | `~/.codebuddy/skills/` 或项目内 `.codebuddy/skills/`；也可在技能市场导入 |
| 豆包工作 | 客户端「技能」页 → 导入本地技能文件 |
| ZCode | 工作区 `.agents/skills/`，`$` 调用 |
| 其他 | 任何支持 Agent Skills（`SKILL.md`）规范的客户端 |

示例（安装「求职项目雷达」）：

```bash
# macOS / Linux
cp -r GuTou-Work_Skills/job-project-radar ~/.agents/skills/

# Windows PowerShell
Copy-Item -Recurse GuTou-Work_Skills\job-project-radar $HOME\.agents\skills\

# Windows 目录联接（推荐长期使用：改仓库即时生效）
mklink /J "%USERPROFILE%\.agents\skills\job-project-radar" "D:\path\to\GuTou-Work_Skills\job-project-radar"
```

每个技能目录自带完整说明（`README.md`、`SKILL.md`、`references/`、`templates/`），安装后按其 README 使用即可。

## 贡献

- **新增技能**：在仓库根目录新建 `<技能名>/` 目录，包含符合 Agent Skills 规范的 `SKILL.md`（引用资料放 `references/`，模板放 `templates/`）；
- **改进现有技能**：直接提 PR；
- 提交前请确认：不包含任何个人隐私、本地路径信息。

## License

[MIT](./LICENSE)

---

## English Summary

**GuTou-Work_Skills** is an open-source collection of agent skills for tech job seekers. Each skill lives in its own directory and follows the Agent Skills standard (`SKILL.md`), compatible with Codex, Claude Code, WorkBuddy, Doubao Work, ZCode and more.

**Easiest install**: paste this repository URL into your coding agent and ask it to install the skill — it will clone and place the folder for you. Manual clone instructions above.

Current skills:

- **job-project-radar** — finds competitive open-source projects that match your stack, reads the chosen project thoroughly, and produces resume-ready project descriptions in three lengths (plus the project URL).
