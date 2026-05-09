# COVID-19 severity blood transcriptomics

**Source:** Overmyer KA et al., 2021. *Large-Scale Multi-omic Analysis of COVID-19 Severity*. Cell Syst. PMID: [33096026](https://pubmed.ncbi.nlm.nih.gov/33096026/) | GEO: [GSE157103](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE157103)

## Background

Multi-omic profiling (transcriptome, proteome, metabolome) of plasma from 102 hospitalized COVID-19 patients and 26 controls, with severity stratified by ICU admission. Designed to identify molecular signatures distinguishing severe (ICU) from mild (NonICU) COVID-19.

## Experimental design

| | |
|---|---|
| Organism | Human |
| Tissue | Plasma |
| Conditions | 2×2 factorial: ICU+COVID (50), NonICU+COVID (50), ICU+NonCOVID (16), NonICU+NonCOVID (10) |
| Samples | 126 |
| Platform | Illumina NovaSeq 6000 (RNA-seq, polyA) ([GPL24676](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL24676)) |

## File: `covid19.tsv`

- **Shape:** 18,318 genes × 126 samples
- **Scale:** $\log_2(\text{TPM} + 1)$ (no transformation needed)

## Notes

The matrix has been pre-processed: TPM-normalized, log-transformed via `log2(TPM + 1)`, and zero-variance rows (genes never detected) removed. Per-sample metadata (age, sex, severity, condition) is in `covid19.meta.csv`. The analytical question is the *interaction* between COVID status and severity, which requires a covariate-adjusted linear model (e.g., `pydeseq2`, `limma`); a plain two-group t-test will produce a DEG list dominated by ICU/age/sex effects.


## Loading

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/covid19/covid19.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```
