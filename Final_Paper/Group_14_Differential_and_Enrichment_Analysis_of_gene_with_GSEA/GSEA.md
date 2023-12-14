# Differential and Enrinchment Analysis with GSEA (Gene Set Enrichment Analysis)
1. [Introduction: Why?](#231)<br>
    1.1. [Differential Expression and Differential Analysis of Genes](#2311)<br>
    1.2. [Gene Set Enrichment Analysis](#2312)
2. [Differential Gene Expression Analysis: How?](#232)<br>
    2.1. [General Workflow](#2321)<br>
    2.2. [RNA-Seq Workflow - Preparing for DGE](#2222)<br>
    2.3. [Methods and Methods Comparison](#2322)
3. [Gene Set Enrichment Analysis: How?](#233)



## 1. Introduction<a name="231"></a>
Have you wondered about how different kind of cells in our body are developed despite their similar DNA composition? Have you considered why some patients die from particular disease, while some do not? 
    Differential Development of cell  |  Different phenotypes 
:-------------------------:|:-------------------------:
<img src="different-cell.png" width="500" /> | <img src="different-phenotype.png" width="500" /> 

A foundamental concept underlying those phenomonon is the **Differential Expression of genes**. Genes are expressed differentially under different conditions to allow for different combinations of proteins and activation of certain biological pathway. Analyzing **differential expression of a set of genes** under different conditions can uncover mystery behind development of stem cells and cause of diseases [4]. 

Tools like **GSEA** can help us achieve this goal. However, before we dive deeper, let's start with some *basic concept review*. 

#### 1) Differential Expression and Differential Analysis of Genes<a name="2311"></a>

> **Differential Expression of genes** is *a evident change in read counts or expression level of genes under different conditions* [1]. 

Let's make a analogy here to help to understand this concept better. Let's consider different kinds of genes as different kinds of the lego building block.

<p align="center"><img src="lego-block.png" width="500" /></p>


It's intuitive that you need many white lego blocks to build a cloud lego while some white lego blocks to build the black cat for its eyes. 
Lego cloud           |  Lego Cat
:-------------------------:|:-------------------------:
<img src="lego-cloud.png" width="500" /> |  <img src="lego-cat.png" width="500" />

In different biological conditions, same gene will be expressed in different amount based on needs. This phenomena is the differential expression of the gene. 

> **Differential analysis** is to *analyze significant change in gene expression level of **a gene** under different biological conditions*.[5]
<p align="center"><img src="DGE.png" width="500" /></p> [5]

As its name, differential analysis is computational method used to detect **evident change of gene expression of *a gene* under different conditions**, **or between two phenotype**[2]. It will require inputs like raw counts of gene expression in different condition and conduct statistical analysis (like t-test) to check if difference is statistically significant. 
 
#### 2) Gene Set Enrichment Analysis<a name="2312"></a>

- **Gene Set Enrichment Analysis** is to *analyze evident change in expression level of **a priori sets of gene** in different conditions* [3]. 
<p align="center"><img src="GSEA.gif" width="500" /></p> [3]

Going back to our lego analogy, we know that different kind of lego products is consist of different combination of lego building blocks. Knowing how many blocks we have for certain product can help us forsee the look of it to some degree. 

On a similar note, differential expression of a set of genes can correlate with certain phenotype of organism. That's why we want to use gene set enrichment analysis, which we use statistical method to check if there is **evident change in expression of *a sets of gene* under different biological conditions**. 



## 2. Differential Gene Expression Analysis: How?<a name="232"></a>
From the concept review, you probably can see how differential gene expression analysis is a necessary previous step of GSEA. 

To check if a set of genes is expressed differentially, we need to determine if a gene is expressed differentially first. Because we want to focus on GSEA in this chapter, let's take some time to go through the general workflow of DGE (differential gene expression analysis). 

#### 1) General Workflow <a name="2321"></a>
The procedure of DGE can be generally concluded as follow: 
- 1. Normalization 
- 2. Statistical Test
- 3. P value check (P < 0.05, change is statistically significant; otherwise, it is not)

Let's dive into details one by one. 
1. **Normalization**</a>
   
   In RNA-seq downstream analysis, we will know how many reads are mapped to particular genes (that can be roughly taken as measure of expression level sometimes). 
   <p align="center"><img src="mapping.png" width="500" /></p> 
   
   *However, count of reads does not necessarily reflect the actual expression level of a gene.*

   To be specific, it's much easier for a gene that is *longer* and located in *DNA has higher counts of reads mapping* to have more reads mapped to it. Therefore, we need to take **gene length** and **library size** into consideration. That's why we need to first conduct normalization to make sure we get valid expression level from input counts data. Common strategy and equations used for normalziation are presented below. [BENG183 Lecture]

   <p align="center"><img src="normalization-equations.png" width="500" /></p> 


3. **Statistical Test**</a>

   We only care about **evident** change in expression level under different conditions. Thus, to make sure the difference in value in not caused by chance, we need to conduct statistical test, usually a t-test, to compare and make sure the change in expression level under different condition is significant.

   <p align="center"><img src="DGE.png" width="500" /></p> [5]

4. **P Value Check**</a>

   To check significance, we will use p value generated from t-test and 0.05 as threhold to determine its significance
   
   **If P < 0.05, change is statistically significant; otherwise, it is not significant.**

   <p align="center"><img src="pval.png" width="500" /></p> 


> Based on these general ideas, we'll walk through one of the most popular techniques for Differential Analysis and then briefly introduce other methods, as well as how to choose tools that work best for GSEA.


#### 2) RNA-Seq Workflow - Preparing for DGE<a name="2222"></a>

Before we can use GSEA, we first need to perform our differential gene expression analysis separately. Luckily, DGE is a well established protocol with a plethora of tools available to help us unlock the potential of differential analysis. While we’ll dive deeper into some of these tools later as well as how you can make the seemingly difficult decision on which one to pick, let’s first discuss some vital steps leading up to DGE analysis.

<p align="center"><img src="./de_workflow.png" width="300" /></p> 

From previous chapters, we should already be familiar with the general RNA sequencing analysis pipeline outlined above, but just for the sake of review let’s discuss some of the key steps. We’ll begin with our RNA-seq data as sequence reads and run these through FASTQC for quality control. Next, we’ll map our reads to the reference genome, and often this step will be conducted using STAR. Lastly, before DGE we will do expression quantification, which can be performed in featureCounts. [BENG183 Lecture] If any of these steps are unclear, feel free to take a minute and revisit these earlier topics. At this stage, you’re ready to take the next step with differential gene expression analysis - so let’s dive into the methods that make it all work.

#### 3) Methods and Methods Comparison<a name="2322"></a>

As touched on earlier, there’s a wide range of tools that can be used for DGE analysis. Some of the more common and well-known tools include DESeq2, EdgeR, and limma-voom, but there’s others as well, each with its own functionality. 

 <p align="center"><img src="./dge_tools.png" width="500" /></p> 

While these methods do have some differences in their exact procedure, they all follow a general workflow and can be successfully applied for DGE. Additionally, most DGE tools can be compatible with GSEA, so there’s not really any major restrictions on which one you can select. For now, we’re going to narrow down our focus to just DESeq2 and EdgeR - both are well established tools that are a part of the R programming language.

<p align="center"><img src="./dge_comparison.png" width="500" /></p> 

As for that general workflow, we’re going to begin with count data which tells us the number of sequence reads originating from each gene. Higher counts will mean more expression, and lower counts the opposite. Normalization is next. DESeq2 uses median of ratios for normalization, whereas EdgeR takes trimmed mean of M values (TMM) [6]. These aren’t extremely different, but this does demonstrate some of the minor differences that keep the two tools unique. 

Both DESeq2 and EdgeR will model read counts as a negative binomial distribution, and with our filtered, normalized, and high quality counts will run statistical tests to calculate fold changes, p-values, and other measures to represent the level of significance of expression differences. An example table output from DESeq2 is shown below. As we can see, we have p-values for each gene which will allow us to judge significance. 

<p align="center"><img src="./deseq2output.png" width="500" /></p> 

Once we’ve arrived here, actually understanding the output of our DGE analysis can be a daunting task in itself. Don’t worry! GSEA is an easy to use software that can help you analyze, annotate, and interpret enrichment results.


## 2.3.5 Selected methods comparison<a name="235"></a> 
<table>
 <tbody>
    <tr>
        <th>Method</td>
        <th>Targets</td>
        <th>Resolution</td>
        <th>Notes</td>
    </tr>
    <tr>
        <td>3C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0535">[3]</a></td>
        <td>one-vs-one</td>
        <td>~1–10 kb<br></td>
        <td><ul><li>Sequence of bait locus must be known</li><li>Easy data analysis</li><li>Low throughput</li></ul></td>
    </tr>
    <tr>
    <td>4C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0545">[4]</a></td>
    <td>one-vs-all</td>
    <td>~2 kb</td>
    <td><ul><li>Sequence of bait locus must be known</li><li>Detects novel contacts</li><li>Long-range contacts</li></ul></td>
    </tr>
    <tr>
    <td>5C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0550">[5]</a></td>
    <td>many-vs-many</td>
    <td>~1 kb</td>
    <td><ul><li>High dynamic range</li><li>Complete contact map of a locus</li><li>3C with ligation-mediated amplification (LMA) of a ‘carbon copy’ library of oligos designed across restriction fragment junctions of interest
3C</li></ul></td>
    </tr>
    <tr>
    <td>Hi-C <a href="http://refhub.elsevier.com/S2001-0370(17)30093-4/rf0300">[6]</a></td>
    <td>all-vs-all</td>
    <td>0.1–1 Mb</td>
    <td><ul><li>Genome-wide nucleosome core positioning</li><li>Relative low resolution</li><li>High cost</li></ul></td>
    </tr>
    <tr>
    <td>ChIA-PET <a href="http://refhub.elsevier.com/S0168-9525(15)00063-3/sbref1405">[7]</a></td>
    <td>Interaction of whole genome mediated by protein</td>
    <td>Depends on read depth and the size of the genome region bound by the protein of interest</td>
    <td><ul><li>Lower noise with ChIP</li><li>Biased method since selected protein</li></ul></td>
    </tr>
 </tbody>
</table>

















# Referrence
[1] Anjum A, Jaggi S, Varghese E, Lall S, Bhowmik A, Rai A. Identification of Differentially Expressed Genes in RNA-seq Data of Arabidopsis thaliana: A Compound Distribution Approach. J Comput Biol. 2016 Apr;23(4):239-47. doi: 10.1089/cmb.2015.0205. Epub 2016 Mar 7. PMID: 26949988; PMCID: PMC4827276. <br>

[2] Abbas, M., EL-Manzalawy, Y. Machine learning based refined differential gene expression analysis of pediatric sepsis. BMC Med Genomics 13, 122 (2020). https://doi.org/10.1186/s12920-020-00771-4<br>

[3] Gene Set Enrichment Analysis Website. https://www.gsea-msigdb.org/gsea/doc/GSEAUserGuideFrame.html<br>

[4] Differential Gene Expression | Definition & Analysis. https://study.com/academy/lesson/differential-gene-expression-definition-examples.html#:~:text=Differential%20gene%20expression%20defines%20the,of%20liver%20and%20skin%20cells <br>

[5] Comparing experimental conditions: differential expression analysis. https://biocorecrg.github.io/CRG_Bioinformatics_for_Biologists/differential_gene_expression.html.<br>

[6] Differential gene expression (DGE) analysis. https://hbctraining.github.io/Training-modules/planning_successful_rnaseq/lessons/sample_level_QC.html

[7] Fullwood, M.J. et al. (2009) An oestrogen-receptor-alpha-bound human chromatin interactome. Nature 462, 58–64.<br>

[8] https://github.com/hms-dbmi/hic-data-analysis-bootcamp/blob/master/HiC-Protocol.pptx.



