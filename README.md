# Paper Review — 学术论文评审技能

**A multi-layered academic paper review skill for the Cowork desktop app.**  
Performs systematic reviews across language, logic, methodology, citations, and formatting — producing annotated revisions and structured Word review reports.

[![Skill](https://img.shields.io/badge/Cowork-Skill-blue)](https://github.com/midsummer16/paper_review)

---

## Overview

`paper-review` is a Cowork skill that automates academic paper review with a structured, five-pass pipeline. It reads papers in PDF, DOCX, LaTeX, or Markdown format and delivers:

- A **structural map** of the paper (chapters, figures, formulas, references)
- An **annotated revision** with inline suggestions tagged by severity
- A **formal DOCX review report** with categorized issues

The skill covers everything from typo-checking to deep methodological scrutiny — you control the depth.

---

## Features

### Layer 1 — Language & Formatting
- Typo and spelling check (Chinese and English)
- Punctuation consistency (mixed-language documents)
- Colloquialism detection and academic-style rewrites
- Heading numbering audit (no skipped or duplicate numbers)
- Figure/table cross-reference verification

### Layer 2 — Logic & Structure
- Intra-paragraph coherence: topic sentences, logical flow
- Inter-paragraph transitions: does each paragraph follow naturally?
- Section self-consistency: does each section deliver what its title promises?
- Global argument skeleton: can the core thesis be traced through all chapters?
- Section proportionality: are some sections bloated while others are starved?

### Layer 3 — Deep Academic Review
- Terminology consistency across the paper
- Math formula accuracy: symbol definitions, derivation gaps, dimensional consistency
- Reproducibility checklist: datasets, model architecture, hyperparameters, evaluation metrics
- Experimental rigor: do results support the conclusions? Is baseline comparison fair?

### Layer 4 — Figure & Table Quality
- Resolution and readability
- Axis labels, legends, and units
- Self-containedness: can the figure be understood without reading the main text?

### Layer 5 — Citation Verification
- Cross-reference check: every in-text citation has an entry in the bibliography (and vice versa)
- Web-search verification of key references for authenticity
- Honest reporting: unverifiable citations are marked as "not verified" rather than falsely flagged

---

## Installation

### For Cowork users

The skill is already available as `paper-review` in your Cowork skills menu. If not, install it:

1. Open Cowork
2. Type `/paper-review` in the chat
3. Or: ask Claude "install the paper-review skill"

### Manual installation

Save the [`SKILL.md`](./SKILL.md) to your Cowork skills directory.

---

## Usage

### Quick start

Upload your paper file, then type:

```
/paper-review
```

The skill will automatically detect the paper's structure and begin the five-pass review.

### Partial review

You can run only specific passes:

| Command | What it does |
|---------|-------------|
| `/paper-review` | Full five-pass review + report |
| "只做语言校对" | Pass 1 only (language & formatting) |
| "帮我过一下逻辑" | Pass 2 only (logic & structure) |
| "检查引用" | Pass 5 only (citation check) |

### Output

The skill produces two deliverables:

1. **Annotated revision** (`_reviewed.md` or `_reviewed.docx`) — the original paper with inline `[评审标注]` markers showing every suggested change, its severity, and the rationale.

2. **Review report** (`_review_report.docx`) — a formal Word document with:
   - Cover page with paper title and review date
   - Executive summary with dimension-level scores
   - Issues organized by severity: Must Fix / Suggested / Optional
   - Appendices: structural map and citation verification details

---

## Example

![Review report example](https://raw.githubusercontent.com/midsummer16/paper_review/main/assets/screenshot.png)

**Review annotation format:**

```
[评审标注 | 严重程度：必须 | 问题类型：逻辑]
原文：The model achieves good results in most cases.
建议：The model achieves a mean accuracy of 91.3% (σ=2.1) across all test splits,
outperforming the baseline by 4.7 percentage points.
理由：Avoid vague qualifiers; report specific metrics with variance for reproducibility.
```

---

## Supported Formats

| Format | Read | Annotate | Report |
|--------|------|----------|--------|
| `.pdf` | ✅ | ✅ | ✅ |
| `.docx` | ✅ | ✅ | ✅ |
| `.tex` | ✅ | ✅ | ✅ |
| `.md` | ✅ | ✅ | ✅ |

---

## Dependencies

- **Cowork desktop app** (or compatible Claude Agent environment)
- **WebSearch** — for citation verification (Pass 5)
- **python-docx** — for generating the formal Word review report (`pip install python-docx --break-system-packages`)

---

## Principles

- **Don't change the author's meaning.** Suggestions improve expression, not substance.
- **Flag uncertainty.** Unclear items get `[待确认]` markers — no forced changes.
- **Honest citations.** Web-unverifiable references are reported as "not found," not falsely accused.
- **Be constructive.** Every issue comes with a concrete fix suggestion and rationale.

---

## Contributing

This is a living skill. Suggestions for new review dimensions, better heuristics, or format-specific improvements are welcome.

1. Fork the repo
2. Edit [`SKILL.md`](./SKILL.md)
3. Submit a PR with a description of what you changed and why

---

## License

MIT © 2026 [midsummer16](https://github.com/midsummer16)

---

## Related

- [Cowork Documentation](https://docs.anthropic.com/en/docs/claude-for-desktop/cowork)
- [Cowork Skills Guide](https://docs.anthropic.com/en/docs/claude-for-desktop/cowork/skills)
