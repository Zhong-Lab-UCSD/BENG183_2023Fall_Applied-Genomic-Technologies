# Normalization of RNA-seq read counts

Faith Okamoto, Camille Phares, Jeremy Tu

1. Why normalize?
2. Types of normalization methods
3. Selecting Proper Methods

## Why normalize?

### RNA-seq input data

Recall that RNA sequencing outputs [exonic](https://www.genome.gov/genetics-glossary/Exon) reads, i.e. DNA sequences replicated using mRNA as templates. These reads are then distilled into a [**count matrix**](https://kasperdanielhansen.github.io/genbioconductor/html/Count_Based_RNAseq.html) (Hansen 2016). Given *n* genes, the input to normalization is (for each sample) a vector of *n* values, where each value is the number of reads mapping to a given gene.

### Raw counts are not "fair"

Comparing raw counts between genes or between samples may not be "fair":

- Consider two samples where, for some technical reason (e.g. different amounts of reagent), **one sample produced double the reads of the other**. If the number of reads mapping to a given gene also doubles, that gene is not differentially expressed; its share of the transcriptome is the same.
- Consider two genes, from the same sample/sequencing run, where **one gene is double the length of the other**. ("Length" refers to exonic DNA sequence.) If the longer gene has double the number of mapped reads, it doesn't have higher expression; an equal number of copies of its mRNA has double the length, thus double the chance for reads to map.
- Consider two samples where **one sample has massive overexpression of a highly-expressed gene** (e.g. a mitochondrial gene). Since RNA-seq quantifies *relative* shares of the transcriptome, all other genes would get less reads. If the number of reads mapping to a different gene is less in the overexpression sample, that may not be differential expression; the same level of expression would still result in a smaller share of the mRNA available for sequencing.

### Normalization ideas

These are some examples of how to address specific problems:

- To control for sequencing volume, **divide by total number of reads**. This makes **inter-sample comparison** more "fair".
- To control for different gene sizes, **divide by exon length**. This makes **intra-sample comparison** more "fair".
- To control for a few over-expressed genes "hogging" the available reads, **use a controlled/unbiased factor**. For example, dividing by the expression of **"housekeeping genes"** which have known amount of necessarily constant expression, or using a **"spike-in"** (Jiang et al. 2011) of a measured amount of artificially added RNA. This makes **inter-sample comparison** more "fair".

## Types of Normalization Methods ##

There are many ways to normalize RNA-sequencing reads, each making different assumptions about the data and compensating for different potential sources of error. Some of the most common methods for normalization fall under three categories: normalization by library size, by distribution, and by controls.

### Normalization by Library Size ##

Normalization by library size accounts for sequencing depth by finding the proportion of mRNA each gene takes up. Total count normalization divides the read counts by the total number of reads in the sample. Similarly, RPKM (reads per kilobase million) and its relative FPKM (fragments per kilobase million) normalize by finding the reads per million of each gene, and then dividing by the length of the gene. TPM (transcripts per kilobase million) is similar to FPKM and RPKM, but it goes in reverse order, dividing the read counts by the gene length and then dividing this by the per million scaling factor. 
<p align="center">
<img width="382" alt="image" src="https://github.com/flowerwallpaper/BENG183/assets/103080777/a3057ea4-2598-4601-8346-464a48b59dcf">
</p>

### Normalization by distribution ###

Normalization by distribution aims to account for variability of sequencing data. Quantile normalization makes the distribution of the normalized data the same by replacing each quantile with the average of that quantile across all samples. DESeq scales each factor by a size factor, which is the ratio of each read count to the mean of all read counts for that gene across samples. TMM (trimmed mean of the m-values) picks a reference sample, removes differentially expressed genes, and then compares this to the non-DE genes in other samples. If it's too far off, this method gives us a correction factor for that sample. 

<p align="center">
<img width="356" alt="image" src="https://github.com/flowerwallpaper/BENG183/assets/103080777/49327b9a-7e46-42f5-a91a-72c37e991c01">
</p>

### Normalization by Controls ###

Using controls is another method to analyze RNA-seq data. Normalizing using a control that isn't affected by biological conditions is useful for finding the shares of gene expression. 
Genes necessary for a cell's function, called housekeeping genes, are assumed to not be differentially expressed as they are necessary for a cell's function. A spike-in is another control option. It's a synthetic RNA transcript with a controlled read count, which makes it another good option. RUV (remove unwanted variation) uses negative control genes or samples, which can be spike-ins or housekeeping genes, to find how known and unknown factors affect the sample variation, and normalize it. 

<p align="center">
<img width="334" alt="image" src="https://github.com/flowerwallpaper/BENG183/assets/103080777/bded4e32-2cda-49a3-a25e-91fba412c28e">
</p>


## Selecting Proper Methods

### Why does the method selected matter?

The methods described above are very powerful tools that help us view our data in a meaningful way. However, not all methods are created equal when taking into context the objective of the experiment taking place and the characteristics and logistics of your data. Each method has its specific uses, as well as concessions, making it very important to choose the right methods catered towards the experiment at hand, as these methods all normalize in different ways, possibly leading to different results.

### RPKM, FPKM, and TPM

For RPKM, FPKM, and TPM, the objective is very similar, in that these methods all aim to compare gene expression. RPKM and FPKM achieve this through first dividing each gene’s reads or fragments by the total number of reads of fragments, then correcting for transcript length through dividing the library-adjusted counts by the transcript length (Cockrum et al., 2020). This, however, presents clear problems, specifically when trying to compare gene expression across multiple samples. TPM, as the most widely used method of these three in the present, addresses these issues through essentially reversing the steps of normalization, ensuring that red coverage is properly represented equally between samples, regardless of gene length. Overall, out of these three methods, TPM is the most applicable in a general context. It does still, however, have its own issues in terms of its biases. One pitfall that is important to look out for is the existence of extreme outliers, especially in smaller samples, as TPM has no mechanism to deal with them, due to the nature of the method taking into account every read. This, in general, makes it bad for dealing with samples or higher variation, something often found in small samples, that other methods may be preferable in addressing, or possibly implementing alongside TPM.

## DESeq2

DESeq2 serves as a method with the objective of identifying differentially expressed genes, and thus is very useful and the often preferred method for hypothesis testing. As a method, DESeq2 is very computationally intensive, which serves as its main drawback, however, it accounts for a lot of biases that make it worthwhile. An example of this would be in its ability to handle outliers significantly better than other methods, through one of two possibilities: removing the whole gene from subsequent analysis in the case of 6 or less replicates or replacing the outliers with imputed trimmed mean values in cases that there are 7 or more replicates (Love et. al., 2014). Beyond just this, DESeq2 has a lot of micro adjustment estimations in place to account for variability quite well, making it decent at handling smaller samples. It is also important to note that DESeq2 accounts for differential expression in its model, whereas other methods, such as TMM, do not have such a luxury.

##TMM

TMM, or trimmed mean of M-values, acts as a very robust way of calculating and normalizing gene expression levels. As stated above, it is very simple, and serves as an easy way to normalize data (Robinson and Oshlack, 2010). While it does have some merit in identifying differential expression, it falls short compared to those such as DESeq2 when directly compared. Unlike, DESeq2, it assumes most genes are not differentially expressed. Despite some of these issues surrounding its use as a standalone method for differential expression, its simple implementation and flexibility gives it many uses in multistep exploratory analysis.

##Control Strategies

Control strategies are very useful in addressing biases that overarching methods may not account for properly. Though they are able to artificially account for biases, it is important to know when they are able to be used. Housekeeping genes, genes that are expected to be stable across all samples, are a strong example of this importance, in that knowing and choosing the proper genes to compare against for the specific experiment at hand. Housekeeping genes often differ significantly from one experiment to another based on what is being analyzed, and thus, it is not a one-size fits all implementation. Spike-ins also require knowledge of the source of bias or variability. Similarly, but with a little more flexibility, RUV also works best with a known or suspected source of variability. Because of the specificity of each of these control strategies, some may be preferable to others in specific scenarios based on where the biases are coming from.

## Works cited

Hansen K. GitHub. 2016 May. https://kasperdanielhansen.github.io/genbioconductor/html/Count_Based_RNAseq.html

Jiang L, Schlesinger F, Davis CA, Zhang Y, Li R, Salit M, Gingeras TR, Oliver B. Synthetic spike-in standards for RNA-seq experiments. Genome Res. 2011 Sep;21(9):1543-51. doi: 10.1101/gr.121095.111. Epub 2011 Aug 4. PMID: 21816910; PMCID: PMC3166838.

Cockrum, Chad, et al. “A primer for generating and using transcriptome data and gene sets.” Development, vol. 147, no. 24, 2020, https://doi.org/10.1242/dev.193854. 
Love, M.I., Huber, W. & Anders, S. Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. Genome Biol 15, 550 (2014). https://doi.org/10.1186/s13059-014-0550-8
Robinson, M.D., Oshlack, A. A scaling normalization method for differential expression analysis of RNA-seq data. Genome Biol 11, R25 (2010). https://doi.org/10.1186/gb-2010-11-3-r25





