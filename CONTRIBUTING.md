# Contributing a Dataset

This collection is open to additions. To contribute a new dataset, follow the conventions below so that the loader template, READMEs, and downstream tooling work uniformly across all datasets.

## File layout

Each dataset lives in `datasets/{snake_case_name}/`. The folder must contain:

| Required | Description |
|----------|-------------|
| `{name}.tsv` | The expression matrix. Tab-separated. First column is the gene or probe identifier (used as the row index). Subsequent columns are the samples. Either raw intensity, log2-transformed, or log-ratio is fine; document the scale in the README. |
| `README.md` | Use the template described below. |
| `{name}.pdf` | The source paper, for offline reference. |

Optional supporting files:

- `{name}.samples.tsv`: a sample sheet (one row per sample, with at minimum a `Sample` column matching the column headers in `{name}.tsv` and a `Condition` column). Required when condition labels cannot be inferred from the column headers alone.
- `{name}.meta.csv`: per-sample metadata (age, sex, severity, batch) used in covariate-adjusted analyses.

## README template

Copy the structure from any existing dataset (`datasets/hdac1/README.md` is a clean example). The required sections, in order:

1. **Title** in `# Title format` (sentence case, no author/year parenthetical).
2. **Source** line: `**Source:** {first author} et al., {year}. *{paper title}*. {journal}. PMID: ... | GEO: ...`
3. **Background**: 1 to 3 sentences describing the biological question.
4. **Experimental design** table: organism, tissue, conditions with sample counts in parentheses, total samples, platform with GPL link.
5. **File**: shape (genes × samples) and scale (raw intensity / log2 / log-ratio).
6. **Notes** (optional) for dataset-specific quirks (covariates required, time-course, sample-sheet location, etc.).
7. **Load**: Python (`pandas.read_table`) and R (base `read.delim`) snippets. Both must use the canonical `https://media.githubusercontent.com/media/ahmedmoustafa/gene-expression-datasets/main/datasets/{name}/{name}.tsv` URL.
8. **First exploration**: a one-line per-language summary snippet (`describe().T[["min", "50%", "max"]]` or `sapply(...)`) plus a one-paragraph interpretation guide for the three scale states.

## Naming conventions

- **Folder names**: lowercase `snake_case`, no apostrophes (e.g., `huntingtons`, not `Huntington's`).
- **File names**: match the folder name (`huntingtons.tsv`, `huntingtons.pdf`, `huntingtons.samples.tsv`).
- **Column names within the TSV**: keep the names as they appear in the source data. Do not rename to a single house style; downstream readers rely on the original names for cross-referencing with the source paper.
- **Indices** (gene IDs): keep the original platform identifiers (Affymetrix probe IDs, Ensembl IDs, gene symbols). Do not translate.

## Data scale

Document the scale explicitly in the README. Three states are accepted:

- **Raw intensity**: positive values, max typically > 100 (microarray intensities, RNA-seq counts, TPM).
- **Log-transformed**: typically `log2(intensity)` or `log2(TPM + 1)`. Bell-shaped distribution, max usually under 18.
- **Log-ratio**: signed values; represent deviations from a reference (per-gene mean, time-zero, paired control).

The "First exploration" snippet in each README lets a user infer the scale by inspecting `min` and `max` directly.

## One canonical file per dataset

If your contribution requires preprocessing (cleaning bad rows, stripping a UTF-8 BOM, applying `log2`, filtering zero-variance genes), perform the cleanup *before* submission and ship a single canonical `{name}.tsv`. Do not submit `_clean.tsv`, `_log2.tsv`, or other variant siblings.

If a contributor finds the cleanup too aggressive or wants the raw data later, the original is recoverable from the source GEO accession.

## LFS

All `.tsv` files in `datasets/` are stored via Git LFS (see `.gitattributes`). New `.tsv` files are picked up automatically. Do not commit large data files outside LFS.

## Submission

Open a pull request with the new `datasets/{name}/` folder. Include in the PR description:

- The biological question the dataset answers.
- The PMID and GEO accession of the source paper.
- The number of samples and conditions.
- A short paragraph on why the dataset is a useful addition for teaching or reuse.

## License

By contributing, you agree that your contribution is released under the repository's existing license (see [`LICENSE`](LICENSE)).
