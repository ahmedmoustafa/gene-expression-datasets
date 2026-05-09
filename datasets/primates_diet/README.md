# Diet effects on liver expression in mice

**Source:** Somel M et al., 2008. *Human and chimpanzee gene expression differences replicated in mice fed different diets*. PLoS One. PMID: [18231591](https://pubmed.ncbi.nlm.nih.gov/18231591/) | GEO: [GSE6285](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE6285)

## Background

Tested whether expression differences observed between human and chimpanzee liver tissue could be reproduced in mice fed diets differing in composition. Provides a model for the role of diet in driving species-specific expression patterns.

## Experimental design

| | |
|---|---|
| Organism | Mouse |
| Tissue | Liver |
| Conditions | 8 diet groups (chimpanzee, fast-food, human-cafeteria, pellet × 2 batches each), 3 replicates per group |
| Samples | 24 |
| Platform | Affymetrix Mouse Genome 430 2.0 Array ([GPL1261](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL1261)) |

## File: `primates_diet.tsv`

- **Shape:** 43,014 genes × 24 samples
- **Scale:** Raw intensity (apply $\log_2$ before differential analysis)

## Notes

Multi-condition design; small per-cell sample size (3) limits the resolution of any one comparison.


## Loading

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/primates_diet/primates_diet.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```
