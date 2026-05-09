# Medulloblastoma molecular subgroups

**Source:** Robinson G et al., 2012. *Novel mutations target distinct subgroups of medulloblastoma*. Nature. PMID: [22722829](https://pubmed.ncbi.nlm.nih.gov/22722829/) | GEO: [GSE37418](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE37418)

## Background

Medulloblastoma is a malignant pediatric brain tumor with four molecular subgroups (G3, G4, SHH, WNT). This study integrated whole-genome sequencing with expression profiling to identify subgroup-specific mutations and pathways.

## Experimental design

| | |
|---|---|
| Organism | Human |
| Tissue | Brain tumor (primary medulloblastoma) |
| Conditions | G3 (16), G4 (39), SHH (10), WNT (8) |
| Samples | 73 |
| Platform | Affymetrix Human Genome U133 Plus 2.0 Array ([GPL570](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL570)) |

## File: `medulloblastoma.tsv`

- **Shape:** 54,675 genes × 73 samples
- **Scale:** $\log_2$ (no transformation needed)

## Notes

Sample condition labels are *not* in the column names; load `medulloblastoma.samples.tsv` for the sample-to-subgroup mapping. Multi-condition design requires either pairwise t-tests with shared FDR or one-way ANOVA.


## Loading

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/medulloblastoma/medulloblastoma.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```
