# Alternative Splicing

Anthony Vasquez, Omar Halawa, Yasmin Jaber

# Introduction

Alternative splicing is a powerful post-transcriptional mechanism that produces multiple mRNA isoforms from the same gene. The isoforms are then translated into functionally different, sometimes inactive, proteins. Alternative splicing is a major contributor to genetic diversity and gene regulation. As a result, there are numerous tools in the RNA-sequencing pipeline designed to analyze the transcriptome. 


---

### Historical Background and Discovery

Alternative Splicing was first defined in 1977 when researchers discovered that not only were introns spliced out of the mRNA of an adenovirus, but also a single mRNA could be spliced "at different junctions [resulting] in a variety of mature mRNA molecules, each containing different combinations of exons." [1]

<div align="center">
<img src="https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/DNA_alternative_splicing.gif" width="850" height="500" />

Image credit [omiics](https://omiics.com/Services/bioinformatic-analysis/alternative-splicing.html)
<div align="left">
  
### Importance in Cellular Biology (maybe remove)


# Mechanics of Alternative Splicing

### Basic Mechanisms

In addition to constitutive splicing (normal splicing), there are five main types of alternative splicing:
1. **Exon skipping**: an exon is not included in the mature mRNA product.
2. **Intron retention**: an intron from the coding sequence is included in the mature mRNA product.
3. **Alternative 3' splice site**: an exon is spliced at a location other than the normal 3' splice site.
4. **Alternative 5' splice site**: an exon is spliced at a location other than the normal 5' splice site.
5. **Mutually exclusive exons**: only one exon from a neighboring group of exons is included in the mature mRNA product. [2]

<div align="center">
<img src="https://www.mdpi.com/ijms/ijms-22-04468/article_deploy/html/images/ijms-22-04468-g001.png" width="500" height="350" />

Image credit [2]
<div align="left">


### Regulatory Proteins and Factors

There are two main elemental factors that facilitate alternative splicing: trans-acting elements facilitate the splicing of introns and exons, and cis-regulatory elements facilitate the binding of trans-acting factors to different introns and exons. 

Trans-acting factors include SR proteins, which are rich in serine and arginine, heterogeneous nuclear ribonucleoproteins (hnRNPs), various ribonucleoproteins, and proteins. Cis-regulatory elements include: exonic splice enhancer (ESE), exonic splice silencer (ESS), intronic splice enhancer (ISE), and intronic splice silencer (ISS). Exonic splice enhancers promote the binding of SR protein's which contribute to the splicing of exons or introns. Exonic splice silencers promote the binding of hnRNPs which can prevent the splicing of an exon. [3]

<div align="center">
<img src="https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Altsplicingelements.png" width="600" height="300" />

Image credit [3] 
<div align="left">


### Role of the Spliceosome in Alternative Splicing

The spliceosome is a ribonucleoprotein complex that contains the basal splicing machinery responsible for splicing an exon [4]. SR proteins recruit the spliceosome to the splice site while hnRNPs minimize the SR protein's ability to recruit the spliceosome [5]. Various other proteins facilitate the removal of the exon and rejoining of the mRNA. 

# Alternative Splicing and Genomic Diversity

### Contribution to Protein Diversity

Alternative splicing occurs in over 90 percent of human genes and in over 95 percent of human multi-exonic genes [4,6]. In a study on alternative splicing titled, _Alternative Splicing: Human Disease and Quantitative Analysis from High-Throughput sequencing_, authors Wei Jian and Liang Chen claim "There are around 20,000 human protein-coding genes, but almost 150,000 transcript isoforms" [6]. In humans, alternative splicing increases protein diversity by a magnitude of around seven and a half. 


#### Contribution to Gene Regulation
> Alternative splicing also contributes to gene regulation by producing non-functional proteins that occupy translational machinery without contributing to genetic expression. 

### Examples of Alternative Splicing in Different Genes

In the human insulin receptor (INSR) gene, exon skipping of exon 11 produces mRNA isoforms IR-A (exon 11 excluded) and IR-B (exon 11 included). Quantitative reverse transcription polymerase chain reaction (qRT-PCR) sequencing showed that low levels of IR-B compared to IR-A is associated with the presence of non-small cell lung cancer (NSCLC) [8].  

<div align="center">
<img src="https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/INSRAltSplice.png" width="850" height="500" />

Image credit [Wildonger BIMM 100 - UCSD]
<div align="left">

> In the Drosophila genus (also known as fruit flies), a single gene, Down syndrome cell adhesion molecule (DSCAM), can be alternatively spliced to produce **38,016** different mature mRNA products [7].

### Evolutionary Perspective







References


[1] Clancy, Suzanne. _RNA Splicing: Introns, Exons, and Spliceosome_. https://www.nature.com/scitable/topicpage/rna-splicing-introns-exons-and-spliceosome-12375/#:~:text=The%20first%20example%20of%20alternative,containing%20different%20combinations%20of%20exons.

[2] Fahmi, Naima et al. _AS-Quant: Detection and Visualization of Alternative Splicing Events with RNA-seq Data_. https://www.mdpi.com/1422-0067/22/9/4468

[3] Human-transcriptome DataBase for Alternative Splicing. http://www.h-invitational.jp/h-dbas/as_mechanism.jsp

[4] Chen, Kenian et al. _Alternative Splicing: An Important Mechanism in Stem Cell Biology_. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4300919/

[5] Jeong, Sunjoo. _SR Proteins: Binders, Regulators, and Connectors of RNA_. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5303883/

[6] Jiang, Wei and Chen, Liang. _Alternative Splicing: Human Disease and Quantitative Analysis from High-Throughput sequencing_. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7772363/

[7] Celotto, A M and Gravely, B R. _Alternative splicing of the Drosophila Dscam pre-mRNA is both temporally and spatially regulated_. https://pubmed.ncbi.nlm.nih.gov/11606537/

[8] Jiang, Liyan et al. _Increased IR-A/IR-B ratio in non-small cell lung cancers associates with lower epithelial-mesenchymal transition signature and longer survival in squamous cell lung carcinoma_. https://bmccancer.biomedcentral.com/articles/10.1186/1471-2407-14-131
