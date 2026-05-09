# BRCA1 / BRCA2 heterozygosity expression markers

**Source:** Salmon AY et al., 2013. *Determination of molecular markers for BRCA1 and BRCA2 heterozygosity using gene expression profiling*. Cancer Prev Res (Phila). PMID: [23341570](https://pubmed.ncbi.nlm.nih.gov/23341570/)

## Background

Identified expression-based markers that distinguish lymphoblastoid cell lines from BRCA1 and BRCA2 mutation carriers from controls, with the goal of supporting non-invasive screening for hereditary breast cancer susceptibility.

## Experimental design

| | |
|---|---|
| Organism | Human |
| Tissue | Lymphoblastoid cell lines |
| Conditions | Ctrl (9), BRCA1 (9), BRCA2 (8) |
| Samples | 26 |
| Platform | Affymetrix Human Genome U133A Array |

## File: `breast_cancer.tsv`

- **Shape:** 22,277 genes × 26 samples
- **Scale:** $\log_2$ (no transformation needed)

## Notes

Three-condition design encoded directly in column names (`Ctrl_*`, `BRCA1_*`, `BRCA2_*`); no separate sample sheet needed. Suitable analyses are pairwise t-tests with shared FDR (Ctrl-vs-BRCA1, Ctrl-vs-BRCA2, BRCA1-vs-BRCA2) or one-way ANOVA across the three groups.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/breast_cancer/breast_cancer.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/breast_cancer/breast_cancer.tsv")
data <- read.delim(url, row.names = 1, check.names = FALSE)
dim(data)
```
