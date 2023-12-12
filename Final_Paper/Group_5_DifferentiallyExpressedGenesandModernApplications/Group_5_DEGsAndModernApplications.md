# Differentially Expressed Genes: General Overview and Modern-Day Applications
### Team 5: Andre Chu, Camryn Morey, Emily Zhang

This project was completed for BENG 183, Fall 2023 :)

 ## Introduction
Gene expression is a fundamental process in which genetic information is converted into a functional product, typically a protein. The patterns of gene expression define the identity and function of a cell. However, when these patterns are altered, they can indicate disease processes or distinctive traits. Differentially expressed genes (DEGs) show a significant difference in expression levels between distinct conditions, such as healthy versus diseased tissue, or between samples of an experiment, such as before and after experimental treatment. DEGs are pivotal in biomedical research by offering a molecular snapshot of differences in cellular functions resulting from various physiological states.

The study of DEGs has become an essential aspect of genomic research, providing insights into the complex mechanisms of diseases, aiding in developing diagnostic tools, and enhancing the efficacy of therapeutic interventions. Advances in genomic and computational technologies have revolutionized the identification and analysis of DEGs, enabling researchers to dissect the intricacies of gene regulation and expression in unprecedented detail (Liang).

## The Science of Gene Expression
Understanding the mechanisms behind variation in gene expression is paramount to unraveling the complexities of cellular function and organismal diversity. This process is crucial for any cellular processes within our bodies and the maintenance of life, dictating everything from the color of one's eyes to the ability of a cell to repair damaged DNA (Liang).

### Genetic Information and Transcription
The journey of gene expression begins in the cell nucleus, where genetic information is stored within the double helix of DNA. A gene comprises a sequence of nucleotides that carry the instructions for synthesizing proteins—molecules that perform a myriad of functions within the cell, including providing structural support or regulating biochemical processes. Transcription is the initial step where messenger RNA (mRNA) is synthesized from a DNA template. This mRNA serves as a transient, working copy of the gene, which is then transported out of the nucleus into the cytoplasm.

### mRNA Translation and Protein Synthesis
Once in the cytoplasm, the mRNA is translated into a protein. Ribosomes and tRNA (transfer RNA) read the sequence of mRNA nucleotides and build polypeptide chains in the order specified by their corresponding mRNA. These polypeptide chains fold into functional proteins that can act as enzymes, structural components of cells, or signaling molecules.

### Regulation of Gene Expression
Various mechanisms tightly regulate gene expression that ensures proteins are produced at the right time, place, and quantity. Regulatory regions in DNA, known as promoters and enhancers, are vital to controlling the expression of genes. Transcription factors, themselves proteins, bind to these regions to either promote or inhibit the transcription of the associated gene. 
Epigenetic regulation is how gene expression is controlled by chromatin structure. Chromatin is the structure in which DNA is densely packed, which has space-conserving benefits within the cell. Additionally, chromatin modifications such as methylation and acetylation affect how "open" certain genes are, which can prohibit or allow transcription factors and transcriptional machinery to access binding sites, affecting expression (Scitable by Nature Education).

<img src="https://ib.bioninja.com.au/_Media/gene-expression_med.jpeg" alt="TFs" width="450"/>

*Effects of transciption factor binding (BioNinja, n.d.).*

### Differential Gene Expression and Cellular Diversity
Differential gene expression refers to the variation in the expression level of genes between different cell types, developmental stages, or environmental conditions. The differential expression of genes leads to diverse cell types in a multicellular organism. For example, although a neuron and a muscle cell contain the same DNA, they express different subsets of genes, resulting in their distinct functions.

### The Role of Gene Expression in Health and Disease
Changes in gene expression can have profound implications for health and disease. In many diseases, such as cancer, certain genes display expression levels that differ significantly from their expression in normal tissue. These differentially expressed genes can provide insights into the molecular basis of diseases, elucidating the differences in activated molecular pathways between healthy and diseased states as well as revealing potential targets for therapeutic intervention.

## Genomic and Computational Technologies in the Study of Differentially Expressed Genes
The comprehensive study of gene expression and the identification of DEGs are predicated on advanced genomic and computational technologies. Most gene expression data are derived from quantifying RNA, as the transcriptome represents the dynamic aspect of genomics.

### RNA Quantification and Sequencing Technologies
RNA sequencing (RNA-seq) using next-generation sequencing technology has allowed for the quantification of RNA expression at an unprecedented scale and resolution. RNA-seq involves the direct sequencing of cDNA libraries, which are generated from RNA samples, to produce millions of short sequence reads. The output reads are mapped to a reference genome, providing a digital readout of the presence and quantity of RNA in a sample (Costa-Silva).
Single-cell RNA sequencing (scRNA-seq) extends the capabilities of RNA-seq to the level of individual cells, offering a high-resolution view of cellular heterogeneity and the differential expression of genes within distinct cell populations. This technology has been instrumental in uncovering tissue complexity and understanding cells' functional diversity within a complex biological system.

With technologies such as Visium and Xenium, spatial transcriptomics adds another dimension by preserving the spatial context of gene expression. By combining gene expression data with the location of the RNA within the tissue, researchers can relate the transcriptomic profile to the histological architecture, enabling a deeper understanding of tissue organization and function (Yue).
Microarrays, one of the earlier technologies for studying gene expression, involve hybridizing cDNA to predefined probes on a solid surface. This is a more limited approach as it depends on the probes designed for specific genes of interest, whereas modern RNA-seq technologies allow us to capture the whole transcriptome. While less informative than sequencing-based approaches, microarrays are still used due to their cost-effectiveness and utility in certain research contexts (Wilson).

### Computational Analysis of Gene Expression Data
The vast amount of data generated by genomic technologies necessitates sophisticated computational tools for analysis. Tools such as DESeq2, edgeR, and baySeq are at the forefront of computational technologies for analyzing RNA-seq data. These software packages employ statistical models to determine if differences in levels of gene expression between samples are statistically significant (Costa).

DESeq2 utilizes a model based on the negative binomial distribution to test for differential expression, accounting for variability within and between samples. EdgeR also uses a negative binomial model but includes Empirical Bayes methods to handle overdispersion and biological variability in the data. BaySeq takes a Bayesian approach, estimating the posterior probabilities of models that include differential expression and those that do not.

### Integrating Data for Enhanced Insights
Integrating the data generated by these technologies provides a comprehensive view of the transcriptome. By combining RNA-seq, scRNA-seq, and spatial transcriptomics data, researchers gain further insight into the gene expression profiles of individual cell types within their native tissue context. Microarray data can complement this by providing broad expression profiles across many conditions or time points.

Together, these genomic and computational technologies provide a powerful arsenal for deciphering the complexities of gene expression. They enable researchers to accurately identify and quantify DEGs, facilitating a deeper understanding of their role in health and disease.

## Quantifying Differential Gene Expression:
The quest to understand the transcriptomic intricacies of cells under varying conditions hinges on the ability to accurately quantify differential gene expression. This section explores the methodologies and statistical frameworks employed to discern and quantify these variations, laying a foundation for subsequent biological interpretation.

### Raw Data Processing and Expression Matrix Construction
Initial raw data from high-throughput technologies like RNA-seq are composed of read counts corresponding to the number of times a fragment from a specific gene is sequenced. This raw data undergoes a preprocessing pipeline that includes quality control steps, alignment to a reference genome or transcriptome, and assembly into an expression matrix. The expression matrix is the cornerstone for subsequent analyses, encapsulating the gene expression levels across all samples in the study. Typically, the rows of the expression matrix represent each gene, and the columns represent each sample.

<img src="https://www.people.vcu.edu/~mreimers/OGMDA/gene_expression_matrix.gif" alt="ExpressionMatrix" width="300"/>

*Expression matrix structure (Balamurugan, Natarajan, & Premalatha, 2016).*

### Normalization
Normalization methods strive to render the expression levels from disparate samples comparable. This is essential because various technical factors unrelated to biological differences can influence the raw expression measurements, such as differences in the overall number of reads in a sample. For RNA-seq, normalization procedures such as TPM, RPKM, and FPKM adjust the data to account for sequencing depth and gene length. These scaled values facilitate a more reliable comparison between genes within and across samples. For microarray data, robust multi-array average (RMA) and quantile normalization are routinely applied to mitigate technical variability across arrays.

| Normalization method | Description | Accounted factors | Recommendations for use |
| :------------------ | :--------- | :----------------:| :--------------------- |
|TPM (transcripts per kilobase million) | counts per length of transcript (kb) per million reads mapped | sequencing depth and gene length | gene count comparisons within a sample or between samples of the same sample group; NOT for DE analysis |
|RPKM/FPKM (reads/fragments per kilobase of exon per million reads/fragments mapped) | similar to TPM | sequencing depth and gene length | gene count comparisons between genes within a sample; NOT for between sample comparisons or DE analysis |
|DESeq2’s median of ratios | counts divided by sample-specific size factors determined by median ratio of gene counts relative to geometric mean per gene | sequencing depth and RNA composition | gene count comparisons between samples and for DE analysis; NOT for within sample comparisons |
|EdgeR’s trimmed mean of M values (TMM) | uses a weighted trimmed mean of the log expression ratios between samples | sequencing depth, RNA composition, and gene length | gene count comparisons between and within samples and for DE analysis |

*Common normalization methods. Adapted from (Harvard Chan Bioinformatics Core Training, n.d.).*

### Statistical Inference for Detecting DEGs
The heart of differential expression analysis lies in statistical testing. Various statistical tests are employed to evaluate whether the observed differences in expression levels are due to biological variation or merely random chance. Parametric tests such as the t-tests and ANOVA are applied when data distributions meet certain assumptions, typically in microarray analyses. Conversely, RNA-seq data often require non-parametric approaches or distribution-specific models due to count data's discrete and overdispersed nature. Negative binomial distribution-based methods, such as those implemented in DESeq2 and edgeR, have become the gold standard, as they are tailored to the properties of RNA-seq data and account for biological variability (Abrams).

### Multiple Testing Conundrum
When thousands of genes are tested simultaneously for differential expression, the probability of false-positive results increases. This multiple-testing problem is tackled by adjusting the p-values to reduce the chances of false discoveries. The Bonferroni correction, while stringent, can be overly conservative and lead to false negatives. Alternatively, the Benjamini-Hochberg procedure controls the FDR, striking a balance between discovering true positives and limiting false positives, and is widely adopted in transcriptomic studies.

### Log Fold Change
The statistical significance alone does not paint the full picture; the magnitude of change is equally crucial. Log fold change, typically in base 2, conveys the change in expression levels between conditions. This metric offers an intuitive interpretation: a log2 fold change of 1 indicates a doubling, while -1 indicates a halving expression. The choice of fold change threshold for biological significance is context-dependent, influenced by factors such as the variability of the data, the reproducibility of results, and prior biological knowledge.

### Validation and Biological Interpretation
The computational identification of DEGs is merely a precursor to biological validation. Techniques such as quantitative PCR (qPCR), which are highly sensitive and specific, are often employed to validate a subset of differentially expressed genes. Furthermore, integrating differential expression results with other biological data, such as protein expression levels or phenotypic outcomes, is vital to understanding the biological implications of the observed transcriptional changes (Corchete).


### Visualization and Data Presentation
Effective visualization of differential expression results is key to conveying findings. Volcano plots, which juxtapose fold change and statistical significance, and heatmaps, which illustrate expression patterns across multiple genes and samples, are indispensable tools for data presentation. These visualizations not only facilitate the identification of key genes but also enable the exploration of broader expression trends across the dataset.


<img src="https://www.bioinformatics.com.cn/static/img/onlineplots_img/086_basic_3_color_volcano_plot.png" alt="VolcanoPlot" width="300"/>

*Volcano plot showing differentially expressed genes of interest (SRplot, n.d.).*


## Biological Significance of DEGs:
Identifying DEGs lies in unraveling their biological significance, which allows us to gain insights into the molecular mechanisms underpinning physiological and pathological processes. This section will explore the functional implications of DEGs and their role in elucidating biological pathways and disease mechanisms.

### Functional Annotation of DEGs
Functional annotation is the first step toward understanding the biological significance of DEGs. It involves linking gene expression data to known information about gene functions, such as protein-coding sequences, regulatory elements, or non-coding RNAs. Databases such as Gene Ontology (GO), Kyoto Encyclopedia of Genes and Genomes (KEGG), and ENSEMBL provide frameworks for annotating genes with their biological processes, molecular functions, and cellular components. This enables researchers to categorize DEGs into functional groups and identify enriched biological themes.

<img src="https://yulab-smu.top/biomedical-knowledge-mining-book/biomedicalKnowledge_files/figure-html/Barplot-1.png" alt="FEA" width="500"/>

*Example results of GO enrichment analysis (Yu, n.d.).*

### Pathway Analysis and Gene Set Enrichment
Pathway analysis goes beyond individual genes, examining the coordinated expression of genes within known biological pathways. It is instrumental in determining how DEGs interact in networks that contribute to specific biological functions or disease states. Gene Set Enrichment Analysis (GSEA) is a powerful statistical method used to determine if predefined sets of genes between two biological states show statistically significant differences. GSEA can reveal overrepresented 
or enriched pathways among DEGs, providing insights into the underlying biological mechanisms that dictate varying biological profiles.

### DEGs and Disease Mechanisms
DEGs often serve as molecular signatures for diseases, especially in complex conditions like cancer, autoimmune disorders, and neurodegenerative diseases. For instance, the overexpression of oncogenes or the silencing of tumor suppressor genes are hallmark DEGs in various cancers. By studying these genes, researchers can uncover critical steps in disease progression and identify potential targets for therapeutic intervention.

### The Impact of DEGs on Cellular and Developmental Processes
The differential expression of genes is a driving force behind cellular differentiation and development. DEGs are pivotal in defining the specific functions of cell types within an organism and are essential for the proper development of tissues and organs. Disruptions in the expression of these genes can lead to developmental abnormalities and congenital disorders.


### Translational Implications of DEGs
Understanding the biological significance of DEGs also has translational implications. DEGs can serve as biomarkers for the diagnosis or prognosis of diseases and can inform the development of targeted therapies. For example, the expression levels of certain genes may correlate with patient response to a treatment, allowing for personalized medicine approaches.

### Systems Biology and Integrative Approaches
Systems biology approaches integrate DEG data with other omics data, such as proteomics and metabolomics, to provide a more comprehensive view of the biological state of an organism. This integrative approach is essential for constructing a holistic model of cellular behavior and can lead to a more profound understanding of complex biological systems.

### Challenges in Interpreting the Biological Relevance of DEGs
While identifying DEGs provides valuable insights, interpreting their biological relevance comes with challenges. The complexity of gene regulation and the context-dependent nature of gene function means that not all DEGs are equally important in every setting. Furthermore, the interplay between genes and the environment complicates the interpretation of their expression patterns. Rigorous experimental validation and cautious interpretation are imperative in studying DEGs.




## Applications Today
Identifying differentially expressed genes is important in modern scientific practices as well. From precision medicine to oncology and disease comparison, DEGs are pivotal in advancing our understanding and treatment of complex diseases.

### Precision Medicine: Customizing Treatment Plans
Precision medicine is reshaping healthcare by customizing treatments to individual genetic profiles. This approach is particularly transformative in conditions where genetic variability significantly influences treatment response. Two interesting applications are pharmacogenomics and genetic risk stratification.

Pharmacogenomics uses DEG profiles to predict individual responses to drugs. For instance, in certain cancers, the expression of genes related to drug metabolism can indicate how a patient will respond to chemotherapy. Based on these profiles, tailoring drug choices and dosages can significantly improve treatment efficacy and reduce adverse effects.

In genetic risk stratification, DEGs are used to classify patients based on their risk for developing specific diseases, enabling early interventions. For example, the expression levels of certain genes may indicate a predisposition to cardiovascular diseases, guiding preventative strategies (Hockings).



### Oncology: Advancements in Cancer Treatment
In oncology, DEGs are instrumental in understanding and treating cancer more effectively.

Studying DEGs helps understand tumor heterogeneity, essential for developing personalized cancer therapies. For instance, gene expression analysis can reveal subpopulations of cancer cells resistant to standard treatments, contributing to the development of novel personalized therapies for the individual. It can also provide insight into the evolution and progression of each individual's tumor, as evidenced by the Differential Variation Analysis (EVA), which enables the detection of tumor heterogeneity using single-cell RNA-sequencing data (Davis-Marcisak).

DEGs are also important in tumor microenvironment analysis. The tumor microenvironment, consisting of immune cells, fibroblasts, and other cell types, is crucial in cancer progression. DEGs provide insights into how these cells interact with tumor cells and influence treatment response. For instance, the expression of immune checkpoint genes can guide the use of immunotherapies.

As for studies focused on mitigating treatment side effects, DEGs can identify potential targets for treatment, with the main purposes of using novel targets less prominent in normal cells to reduce cell cytotoxicity in treatments. Recent advancements in gene therapy underscore its potential to reduce treatment side effects by targeting cancer cells more precisely. The focus has shifted towards identifying therapeutic genes differentially expressed in cancer cells, potentially regulating their transformation. Advances in genomic data analysis, including whole-genome sequencing and gene expression profiling, are instrumental in identifying novel targets for intervention. These developments aim to enhance treatment specificity, thereby minimizing cytotoxic effects on healthy cells and improving therapeutic efficacy in cancer treatments (Das).

<img src="https://genxpro.net/wp-content/uploads/2015/07/precision_medicine1.jpg" alt="VolcanoPlot" width="400"/>

*Personlized treatment for cancer patients (GenXPro, n.d.).*

### Disease Comparison: Modernizing Treatment Approaches
Comparing gene expression profiles across different disease states allows for more specific and effective treatments. DEGs are especially useful for subtype identification and progression monitoring.

DEGs can also be used to monitor disease progression. In diseases like diabetes, where subtypes may respond differently to treatments, DEGs help distinguish these subtypes, resulting in targeted and effective management strategies. DEGs can also be used to monitor disease progression. For example, traits like BMI and lipid levels significantly affect gene expression, indicating the potential of DEGs to reveal the complex interactions between diseases and the transcriptome (Porcu).

### Future Challenges and Developments
While the applications of DEGs are promising, challenges such as the complexity of gene-environment interactions and the need for robust computational tools for DEG analysis must be addressed. As research continues to evolve, integrating DEGs with other omics data is likely to uncover new pathways for disease treatment and prevention, further solidifying their role in the future of medicine.


## References
1. Abrams, Zachary B., et al. “A Protocol to Evaluate RNA Sequencing Normalization Methods - BMC Bioinformatics.” BioMed Central, BioMed Central, 20 Dec. 2019, bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-019-3247-x.

2. Balamurugan, R., Natarajan, A. M., & Premalatha, K. (2016). Biclustering microarray gene expression data using modified Nelder-Mead method. International Journal of Information and Communication Technology, 9(1), 43. https://doi.org/10.1504/IJICT.2016.077686

3. BioNinja (n.d.). Gene Expression. BioNinja. https://ib.bioninja.com.au/higher-level/topic-7-nucleic-acids/72-transcription-and-gene/gene-expression.html

4. Corchete, Luis A., et al. “Systematic Comparison and Assessment of RNA-Seq Procedures for Gene Expression Quantitative Analysis.” Nature News, Nature Publishing Group, 12 Nov. 2020, www.nature.com/articles/s41598-020-76881-x.

5. Costa-Silva, J., Domingues, D., & Lopes, F. M. (2017). RNA-Seq differential expression analysis: An extended review and a software tool. PLoS ONE, 12(12), e0190152. https://doi.org/10.1371/journal.pone.0190152

6. Das, Swadesh K., et al. "Gene Therapies for Cancer: Strategies, Challenges and Successes." Journal of Molecular Medicine, vol. 93, no. 5, May 2015, pp. 493-506. PubMed Central, doi:10.1007/s00109-015-1266-4.

7. Davis-Marcisak, Emily F., et al. "Differential Variation Analysis Enables Detection of Tumor Heterogeneity Using Single-Cell RNA-Sequencing Data." Cancer Research, vol. 79, no. 19, 2019, pp. 5102–5112, https://doi.org/10.1158/0008-5472.CAN-18-3882

8. GenXPro. (n.d.). Precision Medicine - Applications. https://genxpro.net/applications/precision_medicine/

9. Harvard Chan Bioinformatics Core Training. (n.d.). Count normalization and analysis of differential gene expression. https://hbctraining.github.io/DGE_workshop/lessons/02_DGE_count_normalization.html

10. Hockings, Jennifer K., et al. "Pharmacogenomics: An evolving clinical tool for precision medicine." Cleveland Clinic Journal of Medicine, vol. 87, no. 2, Feb. 2020, pp. 91–99, doi:10.3949/ccjm.87a.19073.

11. Liang, Peng, and Arthur B. Pardee. "Analysing Differential Gene Expression in Cancer." Nature Reviews Cancer, vol. 3, 2003, pp. 869–876.
Porcu, Eleonora, et al. “Differentially Expressed Genes Reflect Disease-Induced Rather Than Disease-Causing Changes in the Transcriptome.” 

12. Nature Communications, vol. 12, no. 1, Sept. 2021, Article number 5647. Nature, https://www.nature.com/articles/s41467-021-25805-y.
Scitable by Nature Education. "Gene Expression." Nature, 9 Dec. 2023, https://www.nature.com/scitable/topicpage/gene-expression-14121669/.

13. SRplot (n.d.). Volcano plot. https://www.bioinformatics.com.cn/plot_basic_3_color_volcano_plot_086_en

14. Wilson, Claire H., et al. “Experimental Design and Analysis of Microarray Data.” Applied Mycology and Biotechnology, Elsevier B.V., 2 Sept. 2007, www.ncbi.nlm.nih.gov/pmc/articles/PMC7148956/.

15. Yu, G. (n.d.). ClusterProfiler: an R package for comparing biological themes among gene clusters. https://yulab-smu.top/biomedical-knowledge-mining-book/clusterprofiler-go.html

16. Yue, Liangchen, et al. “A Guidebook of Spatial Transcriptomic Technologies, Data Resources and Analysis Approaches.” Computational and Structural Biotechnology Journal, Elsevier, 16 Jan. 2023, www.sciencedirect.com/science/article/pii/S2001037023000156.
