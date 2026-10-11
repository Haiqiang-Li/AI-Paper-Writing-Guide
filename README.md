# AI 论文写作指南

🌐 **简体中文** · [English](README.en.md)　|　🚀 [快速开始](#从这里开始) · 🛠️ [写作 Skill](#写作-skill) · 🤝 [参与贡献](CONTRIBUTING.md)

**从研究问题到可检验的论证，再到清晰、可复现的论文。**

面向第一次撰写 AI / 机器学习论文的研究者，介绍从研究构思到投稿修订的写作过程，附论文提纲、实验记录和审稿回复模板。具体投稿要求请以目标会议或期刊的官方指南为准。

整理：Haiqiang Li。

## 从这里开始

| 你正在做什么 | 建议阅读 | 完成后的产物 |
| --- | --- | --- |
| 有想法，但讲不清贡献 | [完整写作指南](docs/writing-guide.md) | 一页研究主张与证据清单 |
| 准备开始写正文 | [论文提纲](templates/paper-outline.md) | 章节骨架与每节要回答的问题 |
| 实验结果分散在日志里 | [实验记录模板](templates/experiment-record.md) | 可追踪到配置的结果记录 |
| LaTeX 文件难以维护 | [LaTeX 与排版](docs/latex-and-references.md) | 分章节、可追踪的写作工程 |
| 准备交稿或内部评审 | [提交前检查表](checklists/submission.md) | 一份逐项核实的稿件 |
| 收到审稿意见 | [审稿回复方法](docs/rebuttal.md) / [回复模板](templates/rebuttal.md) | 问题、证据、修改位置对应表 |
| 想在助手中复用写作流程 | [写作 skill 使用指南](docs/skill-usage.md) | 可调用的提纲、改写与审阅流程 |

## 一条通用工作流

```text
研究问题 → 核心主张 → 验证方案 → 结果与图表
                         ↓
修改主张 ← 检查证据是否足够
    ↓
方法与实验正文 → 引言与相关工作 → 摘要与标题 → 内部评审 → 投稿检查
```

这是一种可调整的顺序。理论研究、实证研究、数据集或系统论文的证据形式不同，不必套用相同章节比例。

### 先写这五句话

1. 我们研究的是哪一个具体问题，发生在什么条件下？
2. 已有方法在哪个有证据支持的方面还不够？
3. 本文新增的知识、能力或方法是什么？
4. 哪些观察、比较、推导或实验支持这一主张？
5. 这个结论在哪些范围内成立，哪些地方还不能判断？

写不清某一句时，先补研究或缩小主张，不急于润色措辞。

## 怎么使用本仓库

- 先复制 `templates/paper-outline.md` 到自己的**私有写作工程**，填写问题与证据。
- 为每次关键实验复制一份 `templates/experiment-record.md`，记录数据、配置与结果来源。
- 在内部评审和正式提交前各检查一次 `checklists/submission.md`。
- 只在本仓库提交通用建议；不要把未公开稿件、私有数据或匿名投稿标识提交到公开 Issues。

本仓库不需要安装软件即可阅读。LaTeX 片段仅作组织方式示范，实际编译环境和宏包由目标会议/期刊模板决定。

## 写作 skill

仓库附带 [ai-paper-writing](skills/ai-paper-writing/SKILL.md)，可用于提纲、正文改写、论证检查和审稿回复。它按已有材料组织主张与证据，保留数字、符号及引用键，并将缺失信息单独列出。

复制到论文项目的 `.agents/skills/ai-paper-writing/` 后，可在 Codex 中调用：

```text
使用 $ai-paper-writing 审阅我的论文引言，检查问题、缺口与贡献是否连贯。
只给建议，先不修改文件。
```

安装步骤、无需安装的用法与更多示例见 [使用指南](docs/skill-usage.md)。

## 参考与致谢

感谢 Ziheng Chen 的 *A Tutorial: Writing, Tools, Papers and Code*，以及 [hzwer / DingXiaoH 的 WritingAIPaper](https://github.com/hzwer/WritingAIPaper)。两份资料分别对写作工程与论文表达提供了许多有用的建议。

参考文献、补充排版资料和建议的适用范围见 [SOURCES.md](SOURCES.md)。

## 贡献与许可

欢迎提交能说明问题的修改建议，尤其是含上下文、依据和适用范围的建议。参见 [CONTRIBUTING.md](CONTRIBUTING.md)。原创文字与模板采用 [CC BY 4.0](LICENSE.md)；引用资料的权利归原作者。
