# Yeast cell cycle time course

**Source:** Spellman PT et al., 1998. *Comprehensive identification of cell cycle-regulated genes of the yeast Saccharomyces cerevisiae by microarray hybridization*. Mol Biol Cell. PMID: [9843569](https://pubmed.ncbi.nlm.nih.gov/9843569/)

## Background

The classic cell cycle dataset. Yeast cultures were synchronized via three different methods (alpha factor, cdc15 arrest, cdc28 arrest, plus an elutriation series), then sampled at regular time points across one to two cell cycles. This subset is the alpha-factor time course (T0.0 through T6.5, 14 time points in 0.5-cycle increments).

## Experimental design

| | |
|---|---|
| Organism | Saccharomyces cerevisiae (budding yeast) |
| Tissue | Whole-cell yeast culture |
| Conditions | Time course: T0.0, T0.5, T1.0, ..., T6.5 (14 time points; no replicates per time point) |
| Samples | 14 |
| Platform | Custom yeast cDNA microarray |

## File: `cell_cycle.tsv`

- **Shape:** 6,006 genes × 14 time points
- **Scale:** Log-ratio (signed, vs reference time point)

## Notes

**Time course, no replicates.** A per-gene t-test does *not* apply. Standard methods for this dataset are time-series analyses: Fourier (`JTK_CYCLE`), autocorrelation, sinusoidal regression. A pivot to time-series methodology is required; a plain t-test framing will produce a wrong-shaped analysis.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/cell_cycle/cell_cycle.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/cell_cycle/cell_cycle.tsv")
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
