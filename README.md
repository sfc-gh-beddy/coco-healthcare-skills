# Healthcare & Life Sciences Skills for AI Coding Assistants

A collection of domain-specific skills for AI coding assistants (Claude Code, Cortex Code, etc.) focused on healthcare and life sciences workflows.

These skills are adapted from [Anthropic's life-sciences repository](https://github.com/anthropics/life-sciences) for broader use.

## Available Skills

| Skill | Description | Use When |
|-------|-------------|----------|
| [single-cell-rna-qc](skills/single-cell-rna-qc/) | Quality control for single-cell RNA-seq data | QC analysis, filtering low-quality cells, scanpy/scverse workflows |
| [clinical-trial-protocol](skills/clinical-trial-protocol-skill/) | Generate clinical trial protocols for devices/drugs | Creating FDA submission docs, IDE/IND pathways |
| [scvi-tools](skills/scvi-tools/) | Deep learning for single-cell omics | Batch correction, multi-modal analysis, label transfer |
| [nextflow-development](skills/nextflow-development/) | Run nf-core bioinformatics pipelines | RNA-seq, variant calling, ATAC-seq analysis |

## Installation

### Option 1: Download Individual Skills

1. Navigate to the skill folder you want (e.g., `skills/single-cell-rna-qc/`)
2. Download the entire folder
3. Place it in your AI assistant's skills directory

### Option 2: Clone Entire Repository

```bash
git clone https://github.com/YOUR_USERNAME/healthcare-skills-md.git
```

### Option 3: Download as ZIP

Click the green "Code" button → "Download ZIP"

## Skill Structure

Each skill follows this structure:

```
skill-name/
├── SKILL.md           # Main instructions (required)
├── scripts/           # Python helper scripts
├── references/        # Domain documentation
└── assets/            # Templates (optional)
```

### SKILL.md Format

The `SKILL.md` file contains YAML frontmatter and markdown instructions:

```markdown
---
name: skill-name
description: Brief description for triggering the skill
---

# Skill Title

## When to Use This Skill
- Trigger conditions...

## How to Use
- Instructions...
```

## Using with Claude Code

For Claude Code, skills can be installed via the plugin system:

```
/plugin marketplace add YOUR_USERNAME/healthcare-skills-md
/plugin install single-cell-rna-qc@healthcare-skills-md
```

## Using with Cortex Code

For Cortex Code, copy the skill folder to your `.cortex/skills/` directory:

```bash
cp -r skills/single-cell-rna-qc ~/.cortex/skills/
```

## Skill Details

### Single-Cell RNA-seq QC

Automated quality control following scverse best practices:
- MAD-based filtering for counts, genes, and mitochondrial content
- Comprehensive visualizations (histograms, violin plots, scatter plots)
- Supports `.h5ad` and 10X `.h5` formats

**Requirements:** `anndata`, `scanpy`, `scipy`, `matplotlib`, `numpy`

### Clinical Trial Protocol

Generate clinical trial protocols for FDA submissions:
- Supports medical devices (IDE pathway) and drugs (IND pathway)
- Research similar trials via ClinicalTrials.gov
- Interactive sample size calculation
- Modular waypoint-based architecture

**Requirements:** `scipy`, `numpy`, ClinicalTrials.gov MCP server

### scvi-tools Deep Learning

Deep learning models for single-cell analysis:
- scVI/scANVI for integration and batch correction
- totalVI for CITE-seq (RNA + protein)
- PeakVI for ATAC-seq
- MultiVI for multiome (RNA + ATAC)
- veloVI for RNA velocity

**Requirements:** `scvi-tools`, `scanpy`, `anndata`, GPU recommended

### Nextflow Development

Run nf-core bioinformatics pipelines:
- RNA-seq (gene expression, differential expression)
- Sarek (germline/somatic variant calling)
- ATAC-seq (chromatin accessibility)
- Supports local FASTQs and GEO/SRA public data

**Requirements:** Docker, Nextflow, Java 11+

## Contributing

Contributions welcome! To add a new skill:

1. Create a new folder under `skills/`
2. Add `SKILL.md` with proper frontmatter
3. Include `scripts/` and `references/` as needed
4. Submit a pull request

## License

Skills are provided under the Apache License 2.0. See individual skill directories for specific licenses.

## Disclaimer

These skills are provided for educational and research purposes. They do not constitute medical, legal, or regulatory advice. Professional consultation is required for clinical applications.

## Acknowledgments

- Original skills by [Anthropic](https://github.com/anthropics/life-sciences)
- [scverse](https://scverse.org/) ecosystem
- [nf-core](https://nf-co.re/) community
