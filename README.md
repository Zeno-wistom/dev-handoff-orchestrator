# dev-handoff-orchestrator

一个供 Codex 开发流程使用的全局 Skill：**手动复制粘贴交接为唯一默认方式**，管理顾问协作、关键审批、双层进度和会话切换。Chrome / 应用内 Browser 自动咨询仅作为默认关闭的实验能力；不影响基本工作流。简单的一次性任务无需完整管理。

## 安装

在 Windows PowerShell 中，将仓库克隆到 Codex 用户级 Skill 目录：

```powershell
git clone https://github.com/Zeno-wistom/dev-handoff-orchestrator.git "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator"
```

Codex 也支持其他用户级 Skill 路径；请按当前版本的 Skill 文档配置。**正常使用无需绑定 Project、无需浏览器、无需创建 `.dev-handoff.local.json`。** 只有用户明确开启实验性自动咨询时，才需要准确指定 Project 与会话；绑定文件不得提交到共享仓库。

ChatGPT 项目指令模板位于 [`ChatGPT 项目级指令.md`](ChatGPT%20项目级指令.md)。它是**可选增强**，不需要每个项目都立刻配置；只要在 ChatGPT 当前会话粘贴 Codex 报告，即可完成手动交接。

## 日常使用（默认）

1. 与 ChatGPT 讨论需求，复制生成的 Codex Prompt。
2. Codex 编码、测试，输出**简短汇报**（完成、证据、风险、下一步及适用时的双层进度）。
3. 需要 ChatGPT 分析时，手动粘贴汇报；需要新会话时才请求完整六项交接 Prompt。
4. **不会默认连接浏览器、检查插件或索取 Project URL。**

已有本地安装的更新建议：在 Codex 不占用该目录、工作副本干净且远端已核对后，从安装目录运行 `git pull --ff-only`；出现本地改动就先停下核验，不强制覆盖。

## 更新与后续发布

此用户请求指定的仓库也是安装目录的 Git 工作副本。修改 Skill 后先运行内置结构校验：

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator"
```

然后检查 `git -C "$env:USERPROFILE\.codex\skills\dev-handoff-orchestrator" diff` 和状态；只提交本 Skill 的文件，不提交具体项目配置、密钥、token、日志或个人验证报告。完成提交并推送到 `origin/main`，记录 commit 与推送结果。除非用户要求仅本地保存，已授权的本 Skill 更新应同步推送至这个仓库，不代表可上传其他项目文件。

## 文件结构

- `SKILL.md`：简洁的启用条件和协作规则。
- `references/workflow.md`：默认手动循环、实验性浏览器绑定、咨询边界和会话恢复。
- `references/templates.md`：日常短报告、双层进度、审批、咨询与一次复制六项交接模板。
- `references/binding.example.json`：无绑定的示例结构。
- `ChatGPT 项目级指令.md`：供用户复制到 ChatGPT Project 的项目指令。

## 许可证

此仓库目前未附加许可证。仓库公开后，任何人可以在 GitHub 上查看和 fork；未附加许可证时，公开仓库不表示授予通用的复制、再分发或制作衍生作品的权利。若要开源再利用，请先选择适当许可证后再添加。

参考：[GitHub 关于为仓库选择许可证的说明](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)。
