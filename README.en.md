# AI Paper Writing Guide

🌐 [简体中文](README.md) · **English**　|　🚀 [Quick Start](#start-here) · 🛠️ [Writing Skill](#writing-skill) · 🤝 [Contribute](CONTRIBUTING.md)

**From a research question to a testable argument—and a clear, reproducible paper.**

A practical guide for researchers writing their first AI or machine learning paper, covering the process from developing an idea to submission and revision. Includes templates for paper outlines, experiment records, and reviewer responses. Always follow the official submission requirements of your target conference or journal.

Compiled by Haiqiang Li.

This README is available in English and Simplified Chinese. The linked guides, templates, checklists, and skill instructions are currently written in Chinese.

## Start here

| What you are working on | Suggested reading | What you will produce |
| --- | --- | --- |
| You have an idea but cannot clearly explain its contribution | [Full writing guide](docs/writing-guide.md) | A one-page statement of your claims and supporting evidence |
| You are ready to draft the paper | [Paper outline](templates/paper-outline.md) | A section structure with the questions each section should answer |
| Your experimental results are scattered across logs | [Experiment record template](templates/experiment-record.md) | Results traceable to their configurations |
| Your LaTeX files are difficult to maintain | [LaTeX and references](docs/latex-and-references.md) | A writing project organized by section with traceable changes |
| You are preparing for submission or internal review | [Submission checklist](checklists/submission.md) | A manuscript checked item by item |
| You have received reviewer comments | [Responding to reviewers](docs/rebuttal.md) / [Response template](templates/rebuttal.md) | A mapping from each concern to evidence and the relevant revision |
| You want to reuse the writing workflow with an assistant | [Writing skill usage guide](docs/skill-usage.md) | A reusable workflow for outlining, revision, and review |

## A general workflow

```text
Research question → Core claim → Validation plan → Results and figures
                                                       ↓
Revise the claim ← Check whether the evidence is sufficient
       ↓
Methods and experiments → Introduction and related work
       → Abstract and title → Internal review → Submission checks
```

Adapt this order to your research. Theory papers, empirical studies, dataset papers, and systems papers rely on different forms of evidence and do not need the same balance of sections.

### Start with five statements

1. What specific problem are we studying, and under what conditions?
2. What limitation of existing approaches can we demonstrate with evidence?
3. What new knowledge, capability, or method does this paper contribute?
4. Which observations, comparisons, derivations, or experiments support that claim?
5. Where does the conclusion hold, and what remains uncertain?

If you cannot write one of these clearly, do more research or narrow the claim before polishing the wording.

## How to use this repository

- Copy `templates/paper-outline.md` into your **private writing project** and fill in the research question and evidence.
- Create a copy of `templates/experiment-record.md` for each key experiment to record the data, configuration, and result sources.
- Work through `checklists/submission.md` before both internal review and formal submission.
- Contribute general advice here. Keep unpublished manuscripts, private data, and anonymous submission identifiers out of public issues.

No software installation is required to read this repository. The LaTeX snippets illustrate ways to organize a project; your target venue's template determines the actual compilation environment and packages.

## Writing skill

The repository includes [ai-paper-writing](skills/ai-paper-writing/SKILL.md) for outlining, revising prose, checking arguments, and responding to reviewers. It organizes claims and evidence from the supplied material, preserves numbers, notation, and citation keys, and lists missing information separately.

After copying the skill folder into `.agents/skills/ai-paper-writing/` in your paper project, you can invoke it in Codex:

```text
Use $ai-paper-writing to review my paper's introduction.
Check whether the problem, research gap, and contributions form a coherent argument.
Give suggestions only; do not edit the files yet. Respond in English.
```

See the [usage guide](docs/skill-usage.md) for installation steps, use without installation, and more examples.

## References and acknowledgments

Thanks to Ziheng Chen for *A Tutorial: Writing, Tools, Papers and Code*, and to [hzwer / DingXiaoH for WritingAIPaper](https://github.com/hzwer/WritingAIPaper). These resources offer valuable advice on organizing a writing project and presenting research clearly.

See [SOURCES.md](SOURCES.md) for references, additional typesetting resources, and the scope of the recommendations.

## Contributing and license

Suggestions that explain a concrete problem are welcome, especially those that include context, supporting evidence, and the conditions in which the advice applies. See [CONTRIBUTING.md](CONTRIBUTING.md). Original text and templates are licensed under [CC BY 4.0](LICENSE.md); rights to referenced material remain with its respective authors.
