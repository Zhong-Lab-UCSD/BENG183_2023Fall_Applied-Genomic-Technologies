# Alternative Splicing

Anthony Vasquez, Omar Halawa, Yasmin Jaber

# Table of Contents 
- [Introduction](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#introduction)
  - [Historical Background and Discovery](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Historical-Background-and-Discovery)
- [Mechanics of Alternative Splicing](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Mechanics-of-Alternative-Splicing)
  - [Basic Mechanisms](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Basic-Mechanisms)
  - [Regulatory Proteins and Factors](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Regulatory-Proteins-and-Factors)
  - [Role of the Spliceosome in Alternative Splicing](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Role-of-the-Spliceosome-in-Alternative-Splicing)
- [Alternative Splicing and Genomic Diversity](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Alternative-Splicing-and-Genomic-Diversity)
  - [Contribution to Protein Diversity](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Contribution-to-Protein-Diversity)
  - [Contribution to Gene Regulation](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Contribution-to-Gene-Regulation)
  - [Examples of Alternative Splicing in Genes](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Examples-of-Alternative-Splicing-in-Genes)
  - [Evolutionary Perspective](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Evolutionary-Perspective)
- [Alternative Splicing in RNA-Seq Alignment](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Alternative-Splicing-in-RNA-Seq-Alignment)
  - [Paired-End Alignment](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Paired-End-Alignment)
  - [Splice-Aware Alignment](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Splice-Aware-Alignment)
  - [Popular Tools](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Popular-Tools)
- [Alternative Splicing in Disease and Therapy](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Alternative-Splicing-in-Disease-and-Therapy)
- [Future Directions](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Future-Directions)
- [References](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#References)


# Introduction

Alternative splicing is a powerful, post-transcriptional mechanism that produces multiple mRNA isoforms from the same gene. The isoforms are then translated into functionally different, sometimes inactive, proteins. Alternative splicing is a major contributor to genetic diversity and a minor contributor to gene regulation. As a result, there are numerous tools in the RNA-sequencing pipeline designed to analyze alternative splicing in the transcriptome. 


---

### Historical Background and Discovery

Alternative Splicing was first defined in 1977 when researchers discovered that not only were introns spliced out of the mRNA of an adenovirus, but also a single mRNA could be spliced "at different junctions [resulting] in a variety of mature mRNA molecules, each containing different combinations of exons" [1].

<div align="center">
<img src="https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/DNA_alternative_splicing.gif" width="850" height="500" />

Image credit [omiics](https://omiics.com/Services/bioinformatic-analysis/alternative-splicing.html)
<div align="left">
  
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

Trans-acting factors include SR proteins, which are rich in serine and arginine, heterogeneous nuclear ribonucleoproteins (hnRNPs), various ribonucleoproteins, and various proteins. Cis-regulatory elements include exonic splice enhancers (ESE), exonic splice silencers (ESS), intronic splice enhancers (ISE), and intronic splice silencers (ISS). Exonic splice enhancers promote the binding of SR proteins which contribute to the splicing of exons [3]. Exonic splice silencers promote the binding of hnRNPs which can prevent the splicing of an exon [3]. Intronic splice enhancers, and silencers, utilize other trans-acting factors to facilite retention, or removal, of introns.

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

### Examples of Alternative Splicing in Genes

In the human insulin receptor (INSR) gene, exon skipping of exon 11 produces mRNA isoforms IR-A (exon 11 excluded) and IR-B (exon 11 included). Quantitative reverse transcription polymerase chain reaction (qRT-PCR) sequencing showed that low levels of IR-B compared to IR-A is associated with the presence of non-small cell lung cancer (NSCLC) [8].  

<div align="center">
<img src="https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/INSRAltSplice.png" width="850" height="500" />

Image credit [Wildonger BIMM 100 - UCSD]
<div align="left">

> In the Drosophila genus (also known as fruit flies), a single gene, Down syndrome cell adhesion molecule (DSCAM), can be alternatively spliced to produce **38,016** different mature mRNA products [7].

### Evolutionary Perspective

Alternative splicing allows for the possibility of producing a novel protein with a new function while still maintaining the original protein function. The production of novel proteins can lead to "phenotypic innovation" [9].

> The speciation of human body lice from human head lice is believed to have been caused by alternative splicing [9].


# Alternative Splicing in RNA-Seq Alignment
As discussed in the previous section, RNA-seq is arguably the most important technology when it comes to identifying (and helping quantify the rates of) protein isoforms present in our samples. This is simply due to the fact that:
<ol>
  <li>Obtaining the mature mRNA transcripts via RNA-seq exposes all of the transcriptomic diversity of alternative splicing.</li>
  <li>These resulting transcripts eventually get translated into the various protein isoforms.</li>
</ol>
Therefore, performing RNA-seq and analyzing the resulting transcriptome and the variation that exists in it provides a comprehensive overview of the presence and effects of alternative splicing.


## Paired-End Alignment
Before we get into the specifics of post-sequencing alignment with regards to alternative splicing, and in order for us to better understand the upcoming figures, we need to first examine one aspect of the design of our RNA-seq experiment. As per [Illumina's recommendation](https://www.illumina.com/science/technology/next-generation-sequencing/plan-experiments/paired-end-vs-single-read.html), **paired-end sequencing** (as shown below) is the preferred choice over single-end sequencing as it provides higher quality alignment through being better-suited to identify relative positions of reads with the paired ends of fragments. This is also why, for many sequencing experiments that revolve around studying structural rearrangements, paired-end sequencing is used. See [here](https://systemsbiology.columbia.edu/genome-sequencing-defining-your-experiment) for more details.

![pairedend](https://www.ebi.ac.uk/training/online/courses/functional-genomics-ii-common-technologies-and-data-analysis-methods/wp-content/uploads/sites/70/2020/05/Figure17.png)

## Splice-Aware Alignment
Many modern sequence aligners take into account the various possibilities that alternative splicing can give rise to; these are known as **splice-aware aligners**. Unlike their splice-unaware counterparts which also use a reference genome to aid their alignment, these tools account for alternative splicing in two main ways. First, they can take into consideration known gene annotations as well as canonical splice sites. This allows for careful evaluation of existent alternative splicing data we have to aid in the alignment of the transcriptomic fragments. Secondly, in somewhat of a _de novo_ fashion, splice-aware aligners can also consider the possibilities of new splice junctions based on just the provided reference genome. The combination of these two techniques, coupled with traditional alignment methods, allow these splice-aware aligners to, with high confidence, perform alignment of RNA-seq data in organisms that undergo alternative splicing. See [here](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6192213/) for more information about the techniques employed to make splice-aware alignment possible.

## Popular Tools
### STAR:
[STAR](https://github.com/alexdobin/STAR) stands for Spliced Transcripts Alignment to a Reference. It is one of the fastest and most accurate splice-aware alingers currently available. It utilizes seed indexing (step 1) and seed extension (step 2) which enhances its speed greatly compared to many older splice-aware alingers.

Indexing Reference Genome:   
```STAR --runMode genomeGenerate --genomeDir /path/to/genome/index --genomeFastaFiles /path/to/reference/genome.fa```

Aligning Reads:   
```STAR --runThreadN <num_threads> --genomeDir /path/to/genome/index --readFilesIn /path/to/reads/reads1.fq /path/to/reads/reads2.fq --outFileNamePrefix /path/to/output/prefix```

### HISAT2:
[HISAT2](https://daehwankimlab.github.io/hisat2/) stands for Hierarchical Indexing for Spliced Alignment of Transcripts. Like STAR, there is an initial indexing step, but, as the name suggests, it utilizes a hierarchical indexing-based approach, unlike STAR. It is also one of the fastest and most accurate splice-aware aligners out there. In addition, HISAT2 is praised for being very memory-efficient.

Indexing Reference Genome:   
```hisat2-build /path/to/reference/genome.fa /path/to/genome/index```

Aligning Reads:   
```hisat2 -x /path/to/genome/index -1 /path/to/reads/reads1.fq -2 /path/to/reads/reads2.fq -S /path/to/output/alignment.sam```

# Alternative Splicing in Disease and Therapy
With the discovery of the existence of protein isoforms, alternative splicing has quickly become a research frontier in medical genomics, and particularly cancer genomics. This is due to the fact that the differences brought about by the changes in the final mature mRNA transcript often translate (no pun intended) into structural 3D-conformational changes which ultimately affect functionality. One of the most prominent examples of disease-associated isoforms is **[Δ40p53](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7352174/)**, an N-terminally truncated isoform of the p53 tumor suppressor gene where it not have the first 39 amino acids as the constitutive splicing (original) sequence. This isoform gives rise to an increased rate of cell proliferation, a characteristic trait of cancer development in cells. 

Likewise, due to cases like that of Δ40p53, targeted therapies that aim at either directly editing the disease-associated isoform to correct it or compensating for the, typically, loss-of-function exhibited have been a hot topic of research. 

# Future Directions
On the topic of potential therapeutics, many new advances such as CRISPR/Cas9-related technologies are currently being applied to try and correct these disease-associated isoforms. However, as is the case with any such technology, particularly one that could potentially be as detrimental as gene-editing, though certain experiments on model organsims show promise, clinical trials on humans are very few and far in between due the sheer potential of unintended consequences. This is natural as we do not yet fully comprehend the direct correlation between sequence edits and protein functionality (think of things like the [protein 3D-modeling problem](https://frazer.uq.edu.au/files/2176/3d-modeling-handout-converted.pdf)), at least not the extent where we are confident in carrying larger-scale clinical trials on humans. However, as we learn more and advance these technologies, we get one step closer to fully understanding this natural transcriptomic variation that exists in our genetic code that is alternative splicing and how, through targeted therapies, we can correct any potentially disease-inducing isoforms.


# References

[1] Clancy, Suzanne. _RNA Splicing: Introns, Exons, and Spliceosome_. https://www.nature.com/scitable/topicpage/rna-splicing-introns-exons-and-spliceosome-12375/

[2] Fahmi, Naima et al. _AS-Quant: Detection and Visualization of Alternative Splicing Events with RNA-seq Data_. https://www.mdpi.com/1422-0067/22/9/4468

[3] Human-transcriptome DataBase for Alternative Splicing. http://www.h-invitational.jp/h-dbas/as_mechanism.jsp

[4] Chen, Kenian et al. _Alternative Splicing: An Important Mechanism in Stem Cell Biology_. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4300919/

[5] Jeong, Sunjoo. _SR Proteins: Binders, Regulators, and Connectors of RNA_. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5303883/

[6] Jiang, Wei and Chen, Liang. _Alternative Splicing: Human Disease and Quantitative Analysis from High-Throughput sequencing_. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7772363/

[7] Celotto, A M and Gravely, B R. _Alternative splicing of the Drosophila Dscam pre-mRNA is both temporally and spatially regulated_. https://pubmed.ncbi.nlm.nih.gov/11606537/

[8] Jiang, Liyan et al. _Increased IR-A/IR-B ratio in non-small cell lung cancers associates with lower epithelial-mesenchymal transition signature and longer survival in squamous cell lung carcinoma_. https://bmccancer.biomedcentral.com/articles/10.1186/1471-2407-14-131

[9] Bush, Stephen et al. _Alternative Splicing and the Evolution of Phenotypic Novelty_. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5182408/
