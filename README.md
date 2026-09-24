# Agent Skills

这里收录可复用的 Agent Skills。每个 Skill 以一个独立目录发布，包含标准 `SKILL.md`，并可带有 `references/` 等配套资料。核心说明使用 Agent Skills 通用格式，不依赖某一个厂商的提示词或工具名称。

## 🤖 适配范围

本仓库的兼容约定适用于**当前及后续收录的所有 Skill**：统一支持 **Pi、Codex、Claude Code、OpenCode**，不按单个 Skill 区分 Agent。新增或修改 Skill 时，必须保持 Agent Skills 通用格式，避免依赖某个 Agent 专属的提示词、工具名称或运行机制。

兼容的是 Skill 的说明文件和配套资料；各 Agent 是否能完成具体任务，仍取决于运行环境提供的能力。例如架构分析 Skill 需要读取仓库文件；要分析当前产品、生态、发布情况或标准，还需要网页搜索或等效的资料检索能力。

## 当前收录

- [problem-driven-architecture-analysis](problem-driven-architecture-analysis/SKILL.md)：从项目目标和问题链路出发，分析架构路线、生态位置与具体实现。

Skill 使用 `SKILL.md` 中的 `name`、`description` 和 Markdown 指令作为通用主体。`agents/openai.yaml` 是 Codex / OpenAI 插件界面的可选展示元数据；其他 Agent 可以忽略它，不影响 Skill 主体和 `references/` 的使用。

## 📦 安装、更新与卸载

推荐使用 Vercel 的 [`skills` CLI](https://github.com/vercel-labs/skills)，通过 `npx` 运行，无需全局安装。需要本机已有 Node.js 和 npm。命令中的仓库地址为 `system-thoughts/skills`，Agent 名称使用 CLI 的标识：`pi`、`codex`、`claude-code`、`opencode`。

### 安装

在要安装到的项目根目录执行。下面命令会把本仓库当前所有 Skill 安装到四种 Agent；新收录 Skill 后，再运行一次安装命令即可补装：

```sh
npx skills add system-thoughts/skills \
  --skill '*' \
  --agent pi --agent codex --agent claude-code --agent opencode \
  --yes
```

加 `--global` 可安装到用户级目录，供多个项目使用：

```sh
npx skills add system-thoughts/skills \
  --skill '*' \
  --agent pi --agent codex --agent claude-code --agent opencode \
  --global --yes
```

安装器会为所选 Agent 设置对应的 Skill 目录；若希望复制文件而不使用符号链接，可加 `--copy`。项目级安装随项目共享；用户级安装对当前用户生效。

### 更新

在安装时所用的相同范围内执行。项目级安装在项目根目录运行；用户级安装加 `--global`：

```sh
npx skills update --yes
npx skills update --global --yes
```

更新命令会更新已安装的 Skill。它不会自动安装之后才新增的 Skill；新增 Skill 时重新运行上方的安装命令。

### 卸载

卸载指定 Skill。项目级安装在项目根目录运行；用户级安装加 `--global`：

```sh
npx skills remove problem-driven-architecture-analysis --yes
npx skills remove problem-driven-architecture-analysis --global --yes
```

先运行 `npx skills list` 可查看当前已安装的名称。若要卸载多个 Skill，在命令中列出多个名称；卸载时不要使用 `--all`，因为它会移除该范围内安装的所有 Skill，不限于本仓库。

## 📚 Agent Skills 目录说明

Agent 的查找路径可能随版本、配置和安装方式变化；使用前可查阅各自的最新文档：

- [Pi Skills](https://pi.dev/docs/latest/skills)
- [Codex Skills](https://developers.openai.com/plugins/concepts/skills)
- [Claude Code 的 `.claude` 目录](https://code.claude.com/docs/en/claude-directory)
- [OpenCode Skills](https://opencode.ai/docs/skills)
- [Agent Skills 格式规范](https://agentskills.io/specification)
