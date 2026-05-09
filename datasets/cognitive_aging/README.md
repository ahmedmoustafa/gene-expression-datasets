# Cognitive aging in rat hippocampus

**Source:** Kadish I et al., 2009. *Hippocampal and cognitive aging across the lifespan: a bioenergetic shift precedes and increased cholesterol trafficking parallels memory impairment*. J Neurosci. PMID: [19211887](https://pubmed.ncbi.nlm.nih.gov/19211887/) | GEO: [GSE9990](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE9990)

## Background

Hippocampal expression profiles were collected from rats at five ages spanning the lifespan (3, 6, 9, 12, and 23 months). Memory and cognitive testing was paired with the expression measurements to identify bioenergetic and lipid-trafficking shifts that precede memory impairment.

## Experimental design

| | |
|---|---|
| Organism | Rat |
| Tissue | Hippocampus, CA1 region (microdissected) |
| Conditions | 5 age points: M3 (9), M6 (9), M9 (9), M12 (9), M23 (13) |
| Samples | 49 |
| Platform | Affymetrix Rat Expression 230A Array ([GPL341](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL341)) |

## File: `cognitive_aging.tsv`

- **Shape:** 15,923 genes × 49 samples
- **Scale:** Raw intensity (apply $\log_2$ before differential analysis)

## Notes

Time course in age, not a two-group study. Sensible analyses are 5-condition one-way ANOVA or a continuous-age linear model (treating month-of-age as a covariate). A plain two-group t-test does not directly apply.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/cognitive_aging/cognitive_aging.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/cognitive_aging/cognitive_aging.tsv")
data <- read.delim(url, row.names = 1, check.names = FALSE)
dim(data)
```
