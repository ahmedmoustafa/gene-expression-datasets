# HDAC1 knockout in mouse embryonic stem cells

**Source:** Zupkovitz G et al., 2006. *Negative and positive regulation of gene expression by mouse histone deacetylase 1*. Mol Cell Biol. PMID: [16940178](https://pubmed.ncbi.nlm.nih.gov/16940178/) | GEO: [GSE5583](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE5583)

## Background

Histone deacetylase 1 (HDAC1) removes acetyl groups from histones and is generally considered a transcriptional repressor. This study compared expression profiles of wild-type and HDAC1-deficient mouse embryonic stem cells to identify the genes that depend on HDAC1 for their normal expression. About 7% of mouse genes were deregulated in the absence of HDAC1, including putative tumor suppressors and imprinted genes.

## Experimental design

| | |
|---|---|
| Organism | Mouse |
| Tissue | Embryonic stem cells |
| Conditions | WT (3), KO (3) |
| Samples | 6 |
| Platform | Affymetrix Murine Genome U74A v2 Array ([GPL81](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL81)) |

## File: `hdac1.tsv`

- **Shape:** 12,488 genes × 6 samples
- **Scale:** Raw intensity (apply $\log_2$ before differential analysis)

## Notes

The older U74A v2 array carries roughly a quarter of the probes of the IRF6 chip.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/hdac1/hdac1.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/hdac1/hdac1.tsv")
data <- read.delim(url, row.names = 1, check.names = FALSE)
dim(data)
```
