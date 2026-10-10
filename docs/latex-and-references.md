# LaTeX、引用与排版

本节介绍 LaTeX 文件组织、参考文献管理与常见排版问题，参考 Ziheng Chen 的 *A Tutorial: Writing, Tools, Papers and Code* 第 2–7 页。实际写作应从目标会议或期刊当年的官方模板开始，按需采用下文的组织方式与代码片段。

## 按职责拆分文件

```text
paper/
  main.tex
  preamble.tex
  references.bib
  sections/
    abstract.tex
    introduction.tex
    related-work.tex
    method.tex
    experiments.tex
    discussion.tex
  figures/
  appendix/
```

主文件处理文档结构，章节文件处理正文，导言区集中处理符号和宏包。可以用 `\input{sections/method}` 引入内容。文件名、图表路径与版本记录保持稳定，便于协作核对。

不要为了套用这个目录拆坏官方模板；正文篇幅很小时也无需过度拆分。使用 Git 管理私有写作工程时，提交前检查是否包含不应公开的素材与中间文件。

## 维护引用信息

从论文原始页面或出版方记录核对作者、题名、年份、卷期、页码和 DOI，再检查导出的 BibTeX，不盲信自动抓取结果。区分会议论文、期刊论文和预印本，并保持刊会名称的写法一致。

需要保留缩写大小写时，可在 `title` 中局部加花括号，例如 `{AI}`；不要默认把整个标题强制固定为一种大小写。文献类型和字段按实际出版记录及所用工具填写。

`\citet` / `\citep` 是 `natbib` 常见的叙述式 / 括号式引用命令，输出也受引用样式影响。不要把 `\cite` 的输出形式视为固定规则；使用 `biblatex` 时应按该工具链的命令与模板处理。

依据：[Overleaf — Natbib citation styles](https://www.overleaf.com/learn/latex/Natbib_citation_styles)。

## 公式为论证服务

对正文需要引用的公式，以及重要定义或结论编号。并非每个独立公式都必须有编号；例如 [JMLR 的格式检查表](https://www.jmlr.org/format/formatting-errors.html)就区分被引用或特别重要的公式。

一个公式多行共用编号，可以使用 `equation` 与 `aligned`；多条公式各有编号时可以使用 `align`，必要时通过 `\notag` 取消中间行编号。示意：

```latex
\begin{equation}
  \begin{aligned}
    J(\theta) &= L(\theta) \\
              &\quad + \lambda R(\theta).
  \end{aligned}
  \label{eq:objective}
\end{equation}
```

这里仅演示排版，不表示任何具体研究的方法。定义符号后用 `\eqref{eq:objective}` 引用，避免手写编号。使用 `amsmath` 时，自定义算子可写成 `\operatorname{score}`；已有算子使用 `\log` 等命令。公式标点应与句子语法一致。

进一步说明：[Overleaf — Aligning equations with amsmath](https://www.overleaf.com/learn/latex/Aligning_equations_with_amsmath)。

## 附录、图表与交叉引用

附录单独提交时，应让编号与引用足够明确；使用独立前缀还是连续编号，以目标要求为准。正文写清引用指向主文还是补充材料。

可在模板允许时使用 `cleveref` 统一对象引用、`booktabs` 改善表格规则线、`makecell` 处理单元格换行。它们是可选工具，不能替代对模板兼容性的检查。

先尝试拆分、精简或重排长公式与宽表，再考虑缩放。不要通过压缩行距、修改页边距或极小字号绕过页数限制。图题位置、标题大小写和附录顺序应查询目标指南，不从其他期刊照搬。

最终核查应在实际生成的 PDF 上完成：找未解析引用、越界公式、裁切文字、模糊图片和不一致的标点，而不只检查源文件。
