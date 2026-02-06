# Healthcare & Life Sciences Skills for Cortex Code

A collection of domain-specific skills for [Cortex Code](https://docs.snowflake.com/user-guide/snowflake-cortex/cortex-agents) focused on healthcare and life sciences workflows.

These skills are adapted from [Anthropic's life-sciences repository](https://github.com/anthropics/life-sciences).

## Available Skills

| Skill | Description | Use When |
|-------|-------------|----------|
| [single-cell-rna-qc](skills/single-cell-rna-qc/) | Quality control for single-cell RNA-seq data | QC analysis, filtering low-quality cells, scanpy/scverse workflows |
| [clinical-trial-protocol](skills/clinical-trial-protocol-skill/) | Generate clinical trial protocols for devices/drugs | Creating FDA submission docs, IDE/IND pathways |
| [scvi-tools](skills/scvi-tools/) | Deep learning for single-cell omics | Batch correction, multi-modal analysis, label transfer |
| [nextflow-development](skills/nextflow-development/) | Run nf-core bioinformatics pipelines | RNA-seq, variant calling, ATAC-seq analysis |
| [instrument-data-to-allotrope](skills/instrument-data-to-allotrope/) | Convert instrument data to ASM format | Standardizing lab data for LIMS, data lakes |
| [scientific-problem-selection](skills/scientific-problem-selection/) | Research problem selection framework | Project ideation, troubleshooting, strategic decisions |

## Installation

Copy the skill folder to your `.cortex/skills/` directory:

```bash
# Clone the repo
git clone https://github.com/sfc-gh-beddy/coco-healthcare-skills.git

# Copy skills you want
cp -r coco-healthcare-skills/skills/single-cell-rna-qc ~/.cortex/skills/
cp -r coco-healthcare-skills/skills/scvi-tools ~/.cortex/skills/
```

Or download individual skill folders directly from GitHub.

## Skill Structure

Each skill follows this structure:

```
skill-name/
├── SKILL.md           # Main instructions (required)
├── scripts/           # Python helper scripts
├── references/        # Domain documentation
└── assets/            # Templates (optional)
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

### Instrument Data to Allotrope

Convert laboratory instrument files to standardized formats:
- Auto-detect instrument types (PDF, CSV, Excel, TXT)
- Output ASM JSON or flattened CSV
- Generate Python parser code for data engineering handoff

**Requirements:** `allotropy`, `pandas`, `openpyxl`, `pdfplumber`

### Scientific Problem Selection

Conversational framework for research decisions:
- Pitch and refine new project ideas
- Troubleshoot stuck research projects
- Navigate strategic scientific decisions
- Based on Fischbach & Walsh's decision tree framework

**Requirements:** None (conversational skill)

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
