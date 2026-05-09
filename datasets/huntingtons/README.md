# Huntington's disease blood transcriptomics

**Source:** Borovecki F et al., 2005. *Genome-wide expression profiling of human blood reveals biomarkers for Huntington's disease*. Proc Natl Acad Sci U S A. PMID: [16043692](https://pubmed.ncbi.nlm.nih.gov/16043692/) | GEO: [GSE8762](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE8762)

## Background

Huntington's disease (HD) is a fatal neurodegenerative disorder caused by an expanded CAG repeat in the *HTT* gene. This study profiled blood from HD patients and matched controls to identify peripheral expression signatures that could serve as biomarkers for disease progression and therapeutic response.

## Experimental design

| | |
|---|---|
| Organism | Human |
| Tissue | Peripheral blood lymphocytes |
| Conditions | Ctrl (10), HD (12) |
| Samples | 22 |
| Platform | Affymetrix Human Genome U133 Plus 2.0 Array ([GPL570](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL570)) |

## File: `huntingtons.tsv`

- **Shape:** 54,675 genes × 22 samples
- **Scale:** $\log_2$ (no transformation needed)

## Notes

Two-condition comparison; ports a standard differential-expression pipeline cleanly.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/huntingtons/huntingtons.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/huntingtons/huntingtons.tsv")
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
