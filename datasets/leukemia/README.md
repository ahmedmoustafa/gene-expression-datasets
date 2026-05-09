# AML vs ALL classification

**Source:** Golub TR et al., 1999. *Molecular classification of cancer: class discovery and class prediction by gene expression monitoring*. Science. PMID: [10521349](https://pubmed.ncbi.nlm.nih.gov/10521349/)

## Background

The classic study that introduced gene-expression profiling as a tool for cancer classification. Bone marrow samples from 38 patients with acute leukemia (27 acute lymphoblastic leukemia, 11 acute myeloid leukemia) were profiled to ask whether expression patterns could distinguish the two diseases without prior biological knowledge.

## Experimental design

| | |
|---|---|
| Organism | Human |
| Tissue | Bone marrow |
| Conditions | ALL (27), AML (11) |
| Samples | 38 |
| Platform | Affymetrix Hu6800 (custom oligonucleotide array) |

## File: `leukemia.tsv`

- **Shape:** 7,129 genes × 38 samples
- **Scale:** Log-ratio, per-gene centered (~62% of values are negative; *do not* re-apply log)

## Notes

The matrix is normalized as a deviation from each gene's overall mean, so values are signed. Skip any `log2()` step in the pipeline; the data is already in log space.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/leukemia/leukemia.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/leukemia/leukemia.tsv")
data <- read.delim(url, row.names = 1, check.names = FALSE)
dim(data)
```

## First exploration

Beyond the load, get an immediate sense of the data:

### Python

```python
data.describe().T[["min", "50%", "max"]].head(8)
```

### R

```r
sapply(data[, 1:min(8, ncol(data))],
       function(x) c(min = min(x), median = median(x), max = max(x)))
```

A `min` near zero with `max` in the thousands indicates **raw intensities** (apply `log2` before any test). A `min` near 0 to 5 with `max` around 10 to 18 indicates **log2-transformed** data, ready for analysis. A negative `min` indicates a **per-gene-centered or log-ratio** matrix (deviations rather than absolute expression).
