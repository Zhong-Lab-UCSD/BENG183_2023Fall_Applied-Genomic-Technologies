# Under the hood of DESeq2
#### Team 24: Minyoung Ahn, Joelle Faybishenko, Monica Park
## Contents
- [Introduction](#introduction)
- [Addressing problems specific to RNA-seq data](#addressing-problems-specific-to-rna-seq-data)
- [DESeq2 pipeline overview](#deseq2-pipeline-overview)
- [Sample-specific size factor estimation](#sample-specific-size-factor-estimation)
- [Gene-specific dispersion estimation](#gene-specific-dispersion-estimation)
- [Obtaining fold changes](#obtaining-fold-changes)
- [Testing for differential expression](#testing-for-differential-expression)
- [References](#references)
## Introduction
The ability to obtain the entire transcriptome of a biological sample through high-throughput RNA-sequencing has created a need for tools that enable analysis of this data. One of the most powerful and widely used tools for this purpose is DESeq2 which applies a variety of statistical tools to identify genes that are differentially expressed between two or more experimental conditions, such as treatment versus control groups. 

Briefly, the steps of differential expression analysis of RNA-seq data are as follows:
1. Reads from an RNA-seq experiment are mapped to the host genome using STAR or an analogous alignment tool.
2. Using the alignments from the previous step expression levels for each gene are quantified, for instance using featureCounts or htseq-count. 
4. Normalization across samples and differential expression analysis is done using DESeq2.
5. With the set of differentially expressed genes, many types of downstream analysis can be performed such as heatmaps generation or functional enrichment analysis on the gene set. 

In this paper, we will explore the statistical pipeline that DESeq2 uses to identify differentially expressed genes. 
## Addressing problems specific to RNA-seq data
To begin, DESeq2 is a tool used in the differential expression step of the RNA-seq pipeline to statistically model and test gene expression data. Given a gene expression matrix containing raw counts, DESeq2 aims to find statistically significant differences between conditions. This difference can be calculated by a linear regression, where the slope of the line represents a “fold change,” a ratio showing to what extent a gene is differentially expressed in an experimental group compared to a control.

In order to demonstrate how DESeq2 works, we will be addressing some key issues in RNA-seq read count data, and how DESeq2 accounts for these problems when computing the fold change.

1. Different sequencing depths across samples can create bias in gene expression counts. DESeq2 accounts for this by normalizing the data through sample-specific size factors.
1. RNA-seq data tends to follow a negative binomial distribution, meaning we cannot use a gaussian standard regression. DESeq2 uses a negative binomial generalized linear model instead to better fit this data.
1. This negative binomial model requires a parameter of variance, but its difficult to estimate the variance for each gene since each gene usually has a small number of within-group observations. DESeq2’s solution is to share information across genes to estimate variance through an empirical bayes shrinkage.
1. Fold change estimates become noisy for genes with low read counts. We can clean this up by shrinking the estimates towards zero if read counts are low, which is also done by an empirical bayes shrinkage.
1. Lastly, because multiple hypothesis testing adjustment can lead to loss of power when testing a large number of genes, DESeq2 will automatically filter out lowly expressed genes.

## DESeq2 pipeline overview
![DESeq2_pipeline_overview](./figures/DESeq2_pipeline_overview.png)
In order to identify differentially expressed genes, DESeq2 fits a negative binomial generalized linear model (a GLM with logarithmic link function) to each gene. A negative binomial distribution is applied as opposed to a poisson distribution in order to capture the tendency of RNA-seq data to be overdispersed, meaning that the variance of gene expression exhibits a disproportionate increase for a given increase in the expression level mean. 

Mathematically, for a gene $i$ and sample $j$, DESeq2 models read counts $K_{ij}$ using
$$K_{ij} \sim NB(\text{mean} = \mu_{ij}, \text{dispersion}=\alpha_i)$$
where $NB$ represents the negative binomial distribution.

Broadly, this is accomplished by 
1. normalizing the raw count data by estimating sample-specific size factors $s$,
2. estimating gene-specific dispersion factors $\alpha$,
3. fitting the generalized linear model and obtaining fold changes,
4. shrinking fold-changes,
5. and statistically testing for differential expression, i.e. significant fold changes.
## Sample-specific size factor estimation
Because DESeq2 takes in raw expression data, the data must first be normalized to account for sample-dependent sequencing depth. DESeq2 does this by modelling the mean gene expression $\mu_{ij}$ for gene $i$ of sample $j$ as $$\mu_{ij} = s_j \times q_{ij}$$ where $s_j$ is the size factor for sample $j$ and $q_{ij}$ is the raw gene expression value for gene $i$ of sample $j$. 

![size-factor-estimation](./figures/size-factor-estimation.png)

Visualizing the data in the form of a count matrix indexed by genes with each column representing a different sample, DESeq2 performs the following steps to estimate $s$:
1. Find the pseudo-reference for each gene, defined as the row-wise geometric mean
2. Compute the raw-value to pseudo-reference ratio for each column
3. Define $s_{j}$ as the median ratio of each column
4. Normalize counts by dividing by the corresponding $s_j$
## Gene-specific dispersion estimation
After normalizing for sequencing depth, DESeq2 proceeds to model the variance of the expression distribution for each gene $i$. It does this by estimating the dispersion factor for each gene $\alpha_i$ which is related to its variance of expression level $K$ by $$Var(K_{ij})=\mu_{ij} + \alpha_i\mu_{ij}^2$$ where $\mu_{ij}$ represents the mean gene expression for gene $i$ of sample $j$. 

![MLE_dispersion_estimates.png](./figures/MLE_dispersion_estimates.png)

DESeq2 first estimates each gene's dispersion using maximum-likelihood estimation (MLE) based on the empirical replicates of each gene individually. After obtaining the initial dispersion estimate for every gene, it then plots these estimates (shown as black points in the figure above) on a dispersion-versus-mean plot. 

![dispersion-shrinkage.png](./figures/dispersion-shrinkage.png)

Because there is a tendency for this method to overestimate dispersion, DESeq2 applies a round of empirical bayes shrinkage. To do this, DESeq2 obtains the curve of best fit (shown in red) across every gene's estimate. This function is then used as the prior for the empirical bayes shrinkage, where each gene's dispersion is regressed towards the curve with the magnitude of regression depending on the initial estimate's distance from the curve and the sample size of the original estimation. This is done on the assumption that genes with similar mean expressions should have similar dispersions. Since there may be cases where a gene's dispersion is much higher than the prior due to underlying biological reasons, DESeq2 only uses the shrunken estimation of a gene's dispersion if its original estimate is within two residual two standard deviations from the curve. In either case, the resulting dispersion, also referred to as the maximum a-posteriori (MAP) estimate, is used as the dispersion parameter of a given gene's negative binomial distribution. 

## Obtaining fold changes
Now we will look at how DESeq2 calculates its fold change. Fold change is a measure used in RNA-seq data analysis to compare the expression levels of a gene across different conditions. In bioinformatics, we often use the Log2 fold change, which is the log2 ratio of the expression level of a gene in one condition to the expression level of the same gene in another condition. 
$$\text{Log2 fold change} = \log_2\left(\frac{\text{Counts(Treatment)}}{\text{Counts(Control)}}\right)$$

After normalizing the count data and fitting the negative binomial generalized linear model to each gene, DESeq2 applies a shrinkage method to the log2 fold changes. This is done to reduce the noise in the fold change estimates for genes with low read counts. The shrinkage method is based on the assumption that genes with similar expression levels should have similar fold changes. 

![shrinkage.png](./figures/LFC_shrinkage.jpg)

## Testing for differential expression

Lastly, DESeq2 tests for differential expression by performing a Wald test on the log2 fold changes. The Wald test is a statistical test that tests the null hypothesis that the log2 fold change is equal to zero. The Wald test is a type of generalized linear model (GLM) that uses a normal distribution to model the log2 fold changes. The Wald test is used to test for differential expression because it is a simple and fast test that is appropriate for large sample sizes. 

To maximize the number of genes and keep the false discovery rate (FDR) low, DESeq2 uses a Benjamini-Hochberg adjustment to correct for multiple hypothesis testing. The Benjamini-Hochberg adjustment is a method that controls the FDR by adjusting the p-values of the Wald test. DESeq2 finds a threshold for the adjusted p-values, and genes with adjusted p-values below the threshold are considered to be differentially expressed. 

And that's it! After performing the Wald test, DESeq2 outputs a table of genes that are differentially expressed between the two conditions.	

## References

[1] Love, M.I., Huber, W., & Anders, S. (2014). Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. *Genome Biology, 15*(12), 550. [DOI:10.1186/s13059-014-0550-8](https://doi.org/10.1186/s13059-014-0550-8). 

[2] Harvard Chan Bioinformatics Core. (n.d.). *DESeq2 Analysis*. Retrieved from [https://hbctraining.github.io/DGE_workshop/lessons/04_DGE_DESeq2_analysis.html](https://hbctraining.github.io/DGE_workshop/lessons/04_DGE_DESeq2_analysis.html).

[3] Love, M.I., Anders, S., & Huber, W. (2023). *Analyzing RNA-seq data with DESeq2*. Retrieved from [https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html](https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html).

[4] Harvard Chan Bioinformatics Core. (n.d.). *Count Normalization*. Retrieved from [https://hbctraining.github.io/DGE_workshop/lessons/02_DGE_count_normalization.html](https://hbctraining.github.io/DGE_workshop/lessons/02_DGE_count_normalization.html).

