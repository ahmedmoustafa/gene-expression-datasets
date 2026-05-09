# Diet effects on brain expression in mice

**Source:** Somel M et al., 2008. *Human and chimpanzee gene expression differences replicated in mice fed different diets*. PLoS One. PMID: [18231591](https://pubmed.ncbi.nlm.nih.gov/18231591/) | GEO: [GSE6285](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE6285)

## Background

Tested whether expression differences observed between human and chimpanzee brains could be reproduced in mice fed diets differing in composition. The four diets were: a chimpanzee-style diet (vegetables, fruit, yogurt), a McDonald's fast-food diet, an institute-cafeteria human diet, and a standard mouse pellet diet. Provides a model for the role of diet in driving species-specific brain expression patterns.

## Experimental design

| | |
|---|---|
| Organism | Mouse (NMR1, female, 8 weeks old) |
| Tissue | Brain (right cerebral hemisphere) |
| Conditions | 4 diets (chimpanzee, fast-food, human-cafeteria, pellet) × 2 processing batches × 3 replicates |
| Samples | 24 |
| Platform | Affymetrix Mouse Genome 430 2.0 Array ([GPL1261](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL1261)) |

## File: `primates_diet.tsv`

- **Shape:** 43,014 genes × 24 samples
- **Scale:** Raw intensity (apply $\log_2$ before differential analysis)

## Notes

Multi-condition design; small per-cell sample size (3) limits the resolution of any one comparison.


## Load

### Python

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/primates_diet/primates_diet.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```

### R

```r
url <- paste0("https://media.githubusercontent.com/media/ahmedmoustafa/",
              "gene-expression-datasets/main/datasets/primates_diet/primates_diet.tsv")
data <- read.delim(url, row.names = 1, check.names = FALSE)
dim(data)
```
