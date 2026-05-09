# Cross-species expression in human and African great apes

**Source:** Karaman MW et al., 2003. *Comparative analysis of gene-expression patterns in human and African great ape cultured fibroblasts*. Genome Res. PMID: [12840040](https://pubmed.ncbi.nlm.nih.gov/12840040/) | GEO: [GSE426](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE426)

## Background

Comparison of expression patterns across humans and African great apes (chimpanzee, bonobo, gorilla) in cultured fibroblasts. The goal is to identify lineage-specific expression changes that may underlie human-specific traits.

## Experimental design

| | |
|---|---|
| Organism | Human, Bonobo, Gorilla |
| Tissue | Cultured fibroblasts |
| Conditions | Human (18), Bonobo (10), Gorilla (11) |
| Samples | 39 |
| Platform | Affymetrix Human Genome U95 v2 Array ([GPL8300](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL8300)) |

## File: `african_apes.tsv`

- **Shape:** 12,252 genes × 39 samples
- **Scale:** Raw intensity (apply $\log_2$ before differential analysis)

## Notes

Cross-species comparison; the differential-expression question changes meaning in an evolutionary context (lineage-specific patterns rather than treatment effects). The matrix is post-cleaning from the original GEO submission (rows that did not map cleanly across species were dropped).


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/african_apes/african_apes.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/african_apes/african_apes.tsv")
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
