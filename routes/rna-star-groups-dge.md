# Route: rna-star-groups-dge

Differential gene expression using DESeq2 for the `rna-star` results.

## Usage

After individual samples are processed with the `rna-star` route,
manually define proper group names in the `samples.groups.csv` sample sheet.

Run `rna-star-groups-dge` route from the same directory as `rna-star`.

```
sns/run rna-star-groups-dge
```

## Output

The `rna-star-groups-dge` route will create a `DGE-DESeq2-*` directory with the results. The name will contain the strand (determined automatically) and the number of samples in the sample sheet. The sample sheet can be modified to exclude problematic samples or change groupings for alternate analysis.

Results:

* `counts.raw.csv`: Matrix of raw counts.
* `counts.norm.csv`: Matrix of normalized counts that can be used to check the expression levels of specific genes across samples.
* `counts.norm.xlsx`: Matrix of normalized counts in Excel format to avoid potential auto-conversion of gene names.
* `counts.fpkm.csv`: Matrix of FPKMs.
* `counts.fpkm.xlsx`: Matrix of FPKMs in Excel format to avoid potential auto-conversion of gene names.
* `counts.vst.csv`: Matrix of counts after variance stabilizing transformation (VST) for clustering samples or other machine learning applications. These are log2-transformed and normalized with respect to library size. The point of VST is to remove the dependence of the variance on the mean.
* `plot.pca.png`: PCA plot that shows the samples based on their first two principal components. Useful for visualizing the overall effect of experimental covariates and batch effects.
* `dge.*`: Differential gene expression results between different groups.
* `plot.heatmap.*`: Heatmaps based on differentially expressed genes using multiple cutoffs.

Additional output:

* `input.groups.csv`: Input sample sheet.
* `input.counts.txt`: Input gene-sample matrix of raw counts.
* `deseq2.dds.RData`: DESeq2 object (dds) that can be loaded and modified in R if more complex analysis is needed.
* `deseq2.vsd.RData`: VST-transformed DESeq2 object (vsd) that can be loaded and modified in R if more complex analysis is needed.

General pipeline info: https://github.com/igordot/sns
