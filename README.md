# Agent Skills

这里收录可复用的 Agent Skills。每个 Skill 以一个独立目录发布，包含标准 `SKILL.md`，并可带有 `references/` 等配套资料。核心说明使用 Agent Skills 通用格式，不依赖某一个厂商的提示词或工具名称。

## 🤖 适配范围

本仓库的兼容约定适用于**当前及后续收录的所有 Skill**：统一支持 **Pi、Codex、Claude Code、OpenCode**，不按单个 Skill 区分 Agent。新增或修改 Skill 时，必须保持 Agent Skills 通用格式，避免依赖某个 Agent 专属的提示词、工具名称或运行机制。

兼容的是 Skill 的说明文件和配套资料；各 Agent 是否能完成具体任务，仍取决于运行环境提供的能力。例如架构分析 Skill 需要读取仓库文件；要分析当前产品、生态、发布情况或标准，还需要网页搜索或等效的资料检索能力。

## 当前收录

- [problem-driven-architecture-analysis](problem-driven-architecture-analysis/SKILL.md)：从项目目标和问题链路出发，分析架构路线、生态位置与具体实现。

Skill 使用 `SKILL.md` 中的 `name`、`description` 和 Markdown 指令作为通用主体。`agents/openai.yaml` 是 Codex / OpenAI 插件界面的可选展示元数据；其他 Agent 可以忽略它，不影响 Skill 主体和 `references/` 的使用。

## 📦 安装位置

| Agent | 项目级目录 | 用户级目录 |
| --- | --- | --- |
| Pi | `.agents/skills/`（也支持 `.pi/skills/`） | `~/.agents/skills/`（也支持 `~/.pi/agent/skills/`） |
| Codex | `.agents/skills/` | `~/.agents/skills/` 或 `~/.codex/skills/` |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| OpenCode | `.agents/skills/`（也支持 `.opencode/skills/`） | `~/.agents/skills/`（也支持 `~/.config/opencode/skills/`） |

Pi、Codex 和 OpenCode 可以直接共用 `.agents/skills/`。Claude Code 使用 `.claude/skills/`；同一个 Skill 目录完整复制过去即可。项目级安装只对当前仓库生效，用户级安装可跨项目使用。

## 🚀 安装

以下命令在本仓库根目录执行。将 `DEST` 改为上表中对应 Agent 的目录；例如 Pi、Codex、OpenCode 的项目级安装用 `.agents/skills`，Claude Code 用 `.claude/skills`。用户级安装时可将它设为 `$HOME/.agents/skills`、`$HOME/.claude/skills` 等对应目录。

```sh
SKILL=problem-driven-architecture-analysis
DEST=.agents/skills
mkdir -p "$DEST/$SKILL"
cp -a "$SKILL/." "$DEST/$SKILL/"
```

安装其他 Skill 时，把 `SKILL` 改成对应目录名。请复制整个目录，这样 `references/` 等相对路径资源会一并保留。

## 🔄 更新

先更新本仓库的源文件，再将 Skill 同步到安装位置：

```sh
git pull
SKILL=problem-driven-architecture-analysis
DEST=.agents/skills
rsync -a --delete "$SKILL/" "$DEST/$SKILL/"
```

`rsync -a --delete` 会让安装副本与仓库版本一致，也会清除该 Skill 安装目录内已从源版本移除的文件。仓库中的副本和本机安装副本是分开的；更新仓库不会自动更新已安装的 Skill。若没有 `rsync`，删除该 Skill 的安装目录后，按上面的安装步骤重新复制。

## 🧹 卸载

卸载单个 Skill 时，删除对应 Agent 目录下的同名子目录即可：

```sh
SKILL=problem-driven-architecture-analysis
DEST=.agents/skills
rm -rf "$DEST/$SKILL"
```

卸载项目级副本不会影响用户级副本，反之亦然。请确认 `DEST` 指向 Skill 安装目录后再执行删除命令。

## 📚 Agent Skills 目录说明

Agent 的查找路径可能随版本、配置和安装方式变化；使用前可查阅各自的最新文档：

- [Pi Skills](https://pi.dev/docs/latest/skills)
- [Codex Skills](https://developers.openai.com/plugins/concepts/skills)
- [Claude Code 的 `.claude` 目录](https://code.claude.com/docs/en/claude-directory)
- [OpenCode Skills](https://opencode.ai/docs/skills)
- [Agent Skills 格式规范](https://agentskills.io/specification)
