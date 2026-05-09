# Yeast cell cycle synchronization (Spellman 1998)

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

**Time course, no replicates.** The lecture's per-gene t-test does *not* apply. Standard methods for this dataset are time-series analyses: Fourier (`JTK_CYCLE`), autocorrelation, sinusoidal regression. A group can use this dataset only if they pivot the methodology to time series; a plain t-test framing will produce a wrong-shaped analysis.


## Loading

```python
import pandas as pd

URL = ("https://media.githubusercontent.com/media/ahmedmoustafa/"
       "gene-expression-datasets/main/datasets/cell_cycle/cell_cycle.tsv")
data = pd.read_table(URL, index_col=0)
data.shape
```
