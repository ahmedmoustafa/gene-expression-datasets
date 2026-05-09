# Sporadic Parkinson's disease blood transcriptomics

**Source:** Calligaris R et al., 2015. *Blood transcriptomics of drug-naive sporadic Parkinson's disease patients*. BMC Genomics. PMID: [26510930](https://pubmed.ncbi.nlm.nih.gov/26510930/) | GEO: [GSE72267](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE72267)

## Background

Parkinson's disease (PD) is a progressive neurodegenerative disorder defined clinically by motor symptoms but also accompanied by systemic non-motor manifestations. This study profiled blood from 40 sporadic PD patients (drug-naive, before any pharmacological treatment) and 20 healthy controls to identify peripheral signatures of the disease.

## Experimental design

| | |
|---|---|
| Organism | Human |
| Tissue | Whole blood |
| Conditions | Ctrl (19), PD (40) |
| Samples | 59 |
| Platform | Affymetrix Human Genome U133A 2.0 Array ([GPL571](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL571)) |

## File: `parkinsons.tsv`

- **Shape:** 22,277 genes × 59 samples
- **Scale:** $\log_2$ (no transformation needed)

## Notes

The original paper adjusted for sex, age, and treatment status. Without covariate adjustment, a per-gene t-test will produce a DEG list contaminated by demographic effects rather than disease biology.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/parkinsons/parkinsons.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/parkinsons/parkinsons.tsv")
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
