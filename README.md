# Healthcare & Life Sciences Skills for Cortex Code

A collection of domain-specific skills for [Cortex Code](https://docs.snowflake.com/user-guide/snowflake-cortex/cortex-agents) focused on healthcare and life sciences workflows.

These skills are adapted from [Anthropic's life-sciences repository](https://github.com/anthropics/life-sciences), with additional Snowflake-optimized skills for clinical data workflows.

## Available Skills

### From Anthropic Life Sciences

| Skill | Description | Use When |
|-------|-------------|----------|
| [single-cell-rna-qc](skills/single-cell-rna-qc/) | Quality control for single-cell RNA-seq data | QC analysis, filtering low-quality cells, scanpy/scverse workflows |
| [clinical-trial-protocol](skills/clinical-trial-protocol-skill/) | Generate clinical trial protocols for devices/drugs | Creating FDA submission docs, IDE/IND pathways |
| [scvi-tools](skills/scvi-tools/) | Deep learning for single-cell omics | Batch correction, multi-modal analysis, label transfer |
| [nextflow-development](skills/nextflow-development/) | Run nf-core bioinformatics pipelines | RNA-seq, variant calling, ATAC-seq analysis |
| [instrument-data-to-allotrope](skills/instrument-data-to-allotrope/) | Convert instrument data to ASM format | Standardizing lab data for LIMS, data lakes |
| [scientific-problem-selection](skills/scientific-problem-selection/) | Research problem selection framework | Project ideation, troubleshooting, strategic decisions |

### Snowflake Healthcare Skills (New)

| Skill | Description | Use When |
|-------|-------------|----------|
| [fhir-data-transformation](skills/fhir-data-transformation/) | Transform FHIR R4 to Snowflake tables | Parsing FHIR bundles, healthcare interoperability |
| [omop-cdm-modeling](skills/omop-cdm-modeling/) | OMOP Common Data Model ETL | Observational research, OHDSI analytics |
| [variant-annotation](skills/variant-annotation/) | Annotate genomic variants | ClinVar, gnomAD, clinical variant interpretation |
| [survival-analysis](skills/survival-analysis/) | Kaplan-Meier & Cox regression | Clinical outcomes, time-to-event analysis |

## Installation

Copy the skill folder to your `.cortex/skills/` directory:

```bash
# Clone the repo
git clone https://github.com/sfc-gh-beddy/coco-healthcare-skills.git

# Copy skills you want
cp -r coco-healthcare-skills/skills/single-cell-rna-qc ~/.cortex/skills/
cp -r coco-healthcare-skills/skills/fhir-data-transformation ~/.cortex/skills/
cp -r coco-healthcare-skills/skills/survival-analysis ~/.cortex/skills/
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

### FHIR Data Transformation

Transform FHIR R4 resources into Snowflake tables:
- Parse FHIR Bundles and NDJSON
- Extract Patient, Observation, Condition, MedicationRequest, etc.
- Flatten nested structures for SQL analytics
- Code system mapping (SNOMED, LOINC, RxNorm)

**Requirements:** `fhir.resources`, `pandas`, `snowflake-connector-python`

### OMOP CDM Modeling

Transform clinical data to OMOP Common Data Model:
- Snowflake DDL for OMOP CDM v5.4
- Vocabulary mapping (ICD-10 → SNOMED, NDC → RxNorm)
- ETL patterns for PERSON, CONDITION_OCCURRENCE, DRUG_EXPOSURE
- Data quality checks

**Requirements:** `pandas`, `snowflake-connector-python`, Athena vocabularies

### Variant Annotation

Annotate genomic variants with clinical databases:
- ClinVar pathogenicity classification
- gnomAD population allele frequencies
- Variant filtering strategies (clinical vs. research)
- ACMG classification support

**Requirements:** `cyvcf2`, `pandas`, `pysam`

### Survival Analysis

Clinical outcomes analysis:
- Kaplan-Meier survival curves
- Log-rank test for group comparisons
- Cox proportional hazards regression
- Publication-ready plots with risk tables

**Requirements:** `lifelines`, `pandas`, `matplotlib`

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
- [OHDSI](https://ohdsi.org/) for OMOP CDM
- [HL7 FHIR](https://hl7.org/fhir/) community
