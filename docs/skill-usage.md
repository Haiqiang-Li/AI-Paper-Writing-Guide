# 论文写作 skill 使用指南

`ai-paper-writing` 将本仓库的写作原则整理为可重复调用的工作流程。适合在整理研究材料、写作和修订时使用。

## 文件位置

```text
skills/ai-paper-writing/
  SKILL.md
  agents/
    openai.yaml
```

[SKILL.md](../skills/ai-paper-writing/SKILL.md) 是完整指令入口；`agents/openai.yaml` 提供 Codex 中的名称、描述和默认调用提示。整个文件夹可独立复制，不依赖仓库其他文件，也不需要 API 密钥或额外脚本。

## 方式一：直接在当前仓库使用

在能够访问本地文件的助手中，明确指定文件与任务：

```text
请读取 skills/ai-paper-writing/SKILL.md，按其中的流程审阅我的引言。
文件：paper/sections/introduction.tex
只检查问题、研究缺口和贡献是否连贯，先给修改建议，不修改文件。
```

这里的稿件路径为示例，请换成自己的实际路径。`skills/` 是本仓库用于分发 skill 的目录，不意味着所有客户端都会自动发现它。

## 方式二：安装到 Codex 写作项目

将 `skills/ai-paper-writing` 整个文件夹复制到目标写作项目的 `.agents/skills/` 下：

```text
my-paper/
  .agents/
    skills/
      ai-paper-writing/
        SKILL.md
        agents/openai.yaml
  sections/
  references.bib
```

在本仓库根目录运行以下 PowerShell 示例，先把目标路径改为实际论文目录：

```powershell
$paperProject = 'C:\Research\my-paper'
if (-not (Test-Path -LiteralPath $paperProject -PathType Container)) {
    throw '请先把 paperProject 改为实际存在的论文目录。'
}
$skillSource = Join-Path (Get-Location) 'skills\ai-paper-writing'
$skillParent = Join-Path $paperProject '.agents\skills'
$skillTarget = Join-Path $skillParent 'ai-paper-writing'
if (-not (Test-Path -LiteralPath (Join-Path $skillSource 'SKILL.md'))) {
    throw '请在 AI-Paper-Writing-Guide 仓库根目录运行。'
}
if (Test-Path -LiteralPath $skillTarget) {
    throw '目标 skill 已存在，请先比较版本，避免覆盖自己的修改。'
}
New-Item -ItemType Directory -Force -Path $skillParent | Out-Null
Copy-Item -LiteralPath $skillSource -Destination $skillTarget -Recurse
```

随后在目标论文项目中新开一个 Codex 会话，并明确调用 `$ai-paper-writing`。如果未被识别，可以先按方式一直接指定安装后的 `SKILL.md` 路径。

Codex 的仓库级 skill 目录可参考 [OpenAI 的仓库实践说明](https://developers.openai.com/blog/skills-agents-sdk)；skill 格式与编写方法见 [官方指南](https://learn.chatgpt.com/docs/build-skills)。不同客户端的发现与安装方式应以各自说明为准。

## 一次请求最好包含什么

- **任务**：提纲、起草、改写、审阅或审稿回复。
- **材料**：现有草稿、实验记录、图表、研究笔记或审稿意见的路径。
- **范围**：只处理哪一节，是否允许修改文件。
- **输出**：中文或英文、Markdown 或 LaTeX、大致长度。
- **约束**：必须保留的术语、符号、引用键和不能公开的内容。

没有结果时可以要求提纲或带待补项的摘要草案，不需要为了让文本完整而先编一个结果。

## 调用示例

### 从笔记到提纲

```text
使用 $ai-paper-writing 阅读 notes/research.md 和 results/summary.md。
先梳理问题、缺口、主张、证据和适用范围，再给出中文论文提纲。
缺少证据的贡献单独列出来，不补写实验结果。
```

### 改写英文摘要

```text
使用 $ai-paper-writing 改写 sections/abstract.tex，控制在 180–220 个英文词。
保持数字、比较条件和引用键不变，直接修改该文件。
如果发现原句结论超过现有证据，请说明并收窄表述。
```

### 检查引言

```text
使用 $ai-paper-writing 审阅 sections/introduction.tex。
关注研究问题是否具体、缺口是否有依据、贡献能否在正文找到证据。
按影响程度给出位置、问题和建议，暂不改文件。
```

### 检查实验论证

```text
使用 $ai-paper-writing，对照 sections/experiments.tex 和 results/records.md，
检查贡献与证据的对应关系、比较条件、统计口径和未覆盖的边界。
把已确认的问题与建议补做的实验分开，不实际运行实验。
```

### 草拟审稿回复

```text
使用 $ai-paper-writing，根据 reviews/comments.md 和 revisions/completed.md，
起草英文回复，按“问题—回答—证据—修改位置”组织。
只把 completed.md 中已完成的修改写为完成，其余列为待办。
不要上传文件或提交回复。
```

## 如何检查输出是否有用

首先核对事实与含义，再看语言是否流畅：数字有没有变化，限定条件有没有消失，引用是否真实，计划是否被写成结果。审阅建议应能指向具体段落或证据，方便逐项处理。

本仓库的 skill 不会自动上传稿件或发布内容。实际助手可访问哪些文件、是否联网以及是否允许编辑，仍由当前会话与运行环境控制。

## 更新

拉取仓库更新后，比较 `skills/ai-paper-writing/` 与已安装版本，再复制所需改动。已安装副本不会随仓库自动更新。若做了个人修改，先保留差异，不直接覆盖。
