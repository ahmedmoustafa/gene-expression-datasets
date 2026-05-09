# IRF6 knockout and cleft lip / palate

**Source:** Ingraham CR et al., 2006. *Abnormal skin, limb and craniofacial morphogenesis in mice deficient for interferon regulatory factor 6 (Irf6)*. Nat Genet. PMID: [17041601](https://pubmed.ncbi.nlm.nih.gov/17041601/) | GEO: [GSE5800](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE5800)

## Background

Variants in the Interferon Regulatory Factor 6 (*IRF6*) gene cause Van der Woude syndrome, the most common syndromic form of cleft lip and palate. This study profiled gene expression in skin from $Irf6^{-/-}$ knockout and $Irf6^{+/+}$ wild-type mouse embryos at E17.5 to identify candidate IRF6 target genes that may be implicated in the unexplained ~30% of VWS cases.

## Experimental design

| | |
|---|---|
| Organism | Mouse |
| Tissue | Skin (E17.5 embryos) |
| Conditions | WT (3), KO (3) |
| Samples | 6 |
| Platform | Affymetrix Mouse Genome 430 2.0 Array ([GPL1261](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL1261)) |

## File: `irf6.tsv`

- **Shape:** 45,101 genes × 6 samples
- **Scale:** Raw intensity (apply $\log_2$ before differential analysis)

## Notes

Used as the in-class case study in BIOT 5206 Lecture 8. The lecture pipeline log-transforms this dataset as a teaching moment.


## Loading

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/irf6/irf6.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```
