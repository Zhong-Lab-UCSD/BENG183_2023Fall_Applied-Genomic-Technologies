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


### Contribution to Gene Regulation
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

# What Genomic Technologies are Used to Study Alternative Splicing?

As we have seen through this chapter, alternative splicing is a crucial mechanism in gene expression an diversity, which allows a single gene to produce multiple protein isoforms. Understanding alternative splicing is vital for insights into gene regulation, protein function, and the study of many different diseases. This chapter focuses on the genomic technologies we can use to study alternative splicing, these include: RNA Sequencing (RNA-Seq), Microarrays, Single-Cell RNA Sequencing (scRNA-Seq), and Long Read Sequencing. 


## RNA Sequencing (RNA-seq)

RNA Sequencing, or RNA-Seq, is a powerful tool for studying alternative splicing. This tool is by far the most commonly used tool to study alternative splicing as researchers can use RNA-Seq data to identify and quantify different splice isoforms, as well as detect novel splicing events.  

This tool involves involves the sequencing of RNA transcripts in order to provide insights into the transcriptome of an organism. Below is an overview of the steps of RNA sequencing, so that you can familiarize yourself with the process before diving into the role that RNA-seq plays in alternative splicing research.

### Steps of RNA Sequencing (RNA-Seq):

1. Collecting the sample and Isolating the RNA:

The first step in RNA-Seq is to collect the biological sample from which RNA will be extracted. This could be a tissue sample, a blood sample, or cells from a culture.
RNA is then isolated from the sample. This involves the use of various reagents and techniques to separate RNA from DNA, proteins, and other cellular components.

2. Purify RNA and perform a quality check:

Purfiy the extracted RNA  so that all contaminants can be removed. This step is crucial to ensure the accuracy of subsequent analyses.

After purification, we can move onto assessing the quality and quantity of the RNA. This can be done using methods like gel electrophoresis, spectrophotometry, or more advanced techniques.

3. Fragment RNA and synthesize cDNA:

Because of the fact RNA molecules, especially mRNA, are often too long for efficient sequencing, they are fragmented into smaller pieces.

The fragmented RNA is then reverse-transcribed into complementary DNA (cDNA). This is done using reverse transcriptase enzymes and primers.

4. Prepare the library:

The cDNA fragments are processed to create a sequencing library. This involves several steps, including the ligation of adaptors to the ends of the cDNA fragments and amplification of the cDNA.

The adaptors are crucial for the sequencing process, as they provide a binding site for the sequencing primers and allow the fragments to be immobilized onto the sequencing platform.

5. Sequencing:

The prepared library is loaded onto a sequencer. High-throughput sequencing technologies, such as Illumina's sequencing by synthesis is most often used.

During sequencing, each cDNA fragment is sequenced to determine its nucleotide sequence. This generates massive amounts of data, often requiring robust computational resources for analysis.

6. Data analysis using bioinformatics techniques:

The raw sequencing data is first processed to remove low-quality reads and adapter sequences.

The remaining high-quality reads are aligned to a reference genome or transcriptome, allowing for the identification and quantification of RNA species present in the original sample.

Advanced bioinformatics techniques are applied to analyze the data, which may include differential gene expression analysis, splice variant identification, and functional annotation.

7. Interpretation and validation of data:

The results are interpreted in the context of the biological question being studied. This might involve comparing gene expression profiles between different samples or conditions.

Validation of the findings, often using techniques like qRT-PCR, is crucial to confirm the RNA-Seq results.


### Below is a graphic that sums up the main steps of RNA-seq:

![altsplicetypes](https://microbenotes.com/wp-content/uploads/2022/07/RNA-Sequencing.jpg)


According to a paper by Anna Conesa et al. about the best practicesfor RNA-seq data:
### A survey of best practices for RNA-seq data analysis - Conesa et al.

"The most common application of RNA-seq is to estimate gene and transcript expression" [11].

This paper discussed the major steps involved in RNA analysis, specifically the steps in RNA-seq as well as how it can be used to identify and study different isoforms. One of the points that the researchers focused on was transcript-level differential expression analysis, which is specifically suited to help aid the discovery different isoforms of different genes. Conesa and her collegues proposed RNA-seq as the specific method that should be employed for raw data analysis because of its accuracy and efficiency.

Papers like these really highlight the importance of RNA-seq when it comes to studying alternative splicing, as it is clearly one of the the most commonly used and the preferred method for this type of research. 


## Microarrays

While RNA-Seq has largely replaced microarrays for transcriptome profiling, microarrays were instrumental in the early stages of alternative splicing research. This is because microarrays provide high-throughput and cost-effective means to analyze the expression of thousands of genes simultaneously. 

Below is a very brief overview of how microarrays can be used for research like this, so that you can familiarize yourself with the process before diving into the role that microarrays still play in alternative splicing research.

1. Prepare sample: Isolate RNA, convert RNA to cDNA, add flourescent dyes for labelling purposes.

2. Set up the microarray: prepare probes and decide on size and overall organization.

3. Hybridization: Place cDNA into microarray slide, wait for cDNA to bind to probe, wash off unbound cDNA to reduce noise. 

4. Detection and analysis: Use a scanner to read flourscent labels, process data. 

5. Data interpretation: Analyse differential gene expression. 




There are many different types of microarrays that are used to study differential gene expression. When it comes to alternative splicing we can use splice specific microarrays that designed with probes in order to target exon-exon junctions, specific exons, or introns. The fact that we can customize the specific probe used in microarrays gives researchers alot of flexibility when it comes to the specific differences that we want to capture and study. Usually,these microarrays are designed with probes that target the splice junction and exon of interest.


![altsplicetypes2](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/main/Final_Paper/Group_19_Alternative_Splicing/Microarray-analysis-of-alternative-splicing-Probe-topog-raphies-for-different-array.png)

<br>

Below is a diagram of the ways that different isoforms show up on microarrays. This highlights the potential for specificity that microarrays can detect based on the different probes that can be designed:

<br>

![altsplicetypes1](https://ars.els-cdn.com/content/image/1-s2.0-S1046202305001751-gr4.jpg)

### Microarrays vs RNA-seq:

Although RNA-seq is considered the go-to technology when it comes to studying alternative aplicing, microarrays are useful because of their affordability and effectiveness in some applications, even if RNA-Seq provides more depth and the capacity to identify novel transcripts. The decision between RNA-Seq and microarrays is frequently influenced by the particular objectives of the investigation, the degree of information needed, and financial constraints.


## Single-Cell RNA Sequencing (scRNA-Seq)

Ever since its discover in 2009, scRNA-Seq has grown to become of the the most advanced method for understanding the complexity of RNA transcripts within individual cells, as well as helping us understand the makeup of various cell types and functions. scRNA-seq research allows us to produce a vast amount of information in a variety of domains, leading to new findings in our understanding of alternative splicing and its affect on a single cell level. This technology is particularly powerful for studying alternative splicing, as it allows researchers to observe splicing events and gene expression patterns that may vary from cell to cell within a heterogeneous tissue or population.

### How does it work?

scRNA-Seq involves isolating individual cells, extracting their RNA, and then sequencing the RNA to understand the gene expression profile of each cell. This approach differs from traditional RNA-Seq, which provides an averaged view of gene expression from a bulk population of cells.

Cells are isolated using techniques like fluorescence-activated cell sorting (FACS) or microfluidics-based systems. Each cell is separated into its own reaction vessel or droplet.

RNA from each cell is then reverse-transcribed into cDNA. Because the amount of RNA per cell is limited, methods like PCR amplification are often used to increase the quantity of cDNA for sequencing [12].

Below is a graphic that depicts an overview of the main steps of scRNA-Seq:

![altsplicetypes](https://encyclopedia.pub/media/item_content/202206/62bc1112b6b12biosensors-12-00450-g001.png)

### How does it help us study alternative splicing?

1. scRNA-seq allows us to detect cell-specific splicing events:

scRNA-Seq can reveal how splicing varies across different cell types within a tissue, or even between similar cell types under different physiological conditions.

This is crucial for tissues with high cellular heterogeneity, such as the brain or tumors, where cell-to-cell variation in splicing might have significant implications.

2. scRNA-Seq allows us access to high-resolution splicing data:

The technique allows for the examination of splicing at a much finer scale. Researchers can identify specific isoforms expressed in individual cells, providing insights into the functional diversity and complexity at the single-cell level.

### How does scRNA-Seq compare to RNA-Seq?

While bulk RNA-Seq averages gene expression across thousands or millions of cells, scRNA-Seq provides a detailed view of expression in individual cells. This distinction is particularly important in the study of alternative splicing, as it allows for the detection of splicing variants that might be diluted or missed entirely in bulk analyses.

However, its important to note that scRNA-Seq also has some diadvantages because it is a techniques that is quite new and challengeingto performn. Additionally, it is significantly mopre expensive compared to RNA-Seq. According to Jovic et al., One of the main challenges in scRNA-Seq is the handling of technical noise and ensuring sufficient coverage to accurately detect splicing events. Another difficulty arises when we start to look at amplification bias during the cDNA synthesis and amplification steps. This bias has the potential to affect the accurate quantification of splice variants.  [12]


### Below is an example of how sequenced, analysed and graphed scRNA-seq data can look. The graph below shows single cell RNA-seq of the bleomycin lung injury model for mice. over 28 cell types were sequences [13].

<br>

![altsplicetypes](https://ngdc.cncb.ac.cn/regeneration/images/single-cell/landscape_Mouse_Lung_Bleomycin.jpg)



## Long Read Sequencing

Long read sequencing, which is also known as third-generation sequencing, allows us to approach sequnecing in a different way. This approach to studying the transcriptome is particularly beneficial for investigating complex phenomena like alternative splicing. Unlike short read sequencing technologies, long read sequencing can generate much longer reads, sometimes spanning entire transcripts. This capability is very useful for the cause of identifying and characterizing full-length splice variants. This gives reseaches alot of flexibility when it comes to studying alternative splicing because it helps with more accurate alignment process as well as making it easier to identify isofoms. 


### How does it work?

Long read sequencing technologies, such as those developed by Pacific Biosciences (PacBio) and Oxford Nanopore Technologies, can sequence single DNA or RNA molecules without the need for amplification. This results in reads that can be several kilobases long, often enough to cover entire mRNA transcripts from end to end.

The preparation of samples for long read sequencing involves extracting RNA and converting it into cDNA. Unlike short read sequencing, there is no need for fragmentation, allowing the preservation of full-length transcripts.

Below is a graphic depicting an overview of the process of long read sequencing and comparing to short read sequencing: 

![altsplicetypes](https://hudsonalpha.org/wp-content/uploads/2021/02/short-read-2.png)

### How does it help us study alternative splicing?

1. Ability to view and analyse a full-length transcript: 

Long read sequencing enables the direct sequencing of full-length transcripts. This is particularly advantageous for studying alternative splicing, as it allows researchers to observe complete splice variants without the need for computational reconstruction of transcripts from short reads (which can oftentimes be very difficult and even innacurate).

2. Isoform identification and quantification:

The technology excels in identifying and quantifying different splice isoforms, especially ones that are rare or complex. This is very important in understanding the full diversity of transcriptomes in different cells and tissues [14].

3. Complex splicing events are more easly identified:

Long read sequencing can be employed to investigate complex splicing events in genes with multiple exons and extensive alternative splicing. long read sequencing can help provide for us a clearer picture of the splicing landscape, which might be difficult to resolve with short read sequencing [14].

### What is Iso-Seq?

![altsplicetypes](https://isoseq.how/img/isoseq_card.png)

Iso-Seq (by PacBio), short for Isoform Sequencing, is a method that used long read sequencing to specifically analyse and better understand complexity of gene expression, specifically different isoforms.

Traditional RNA sequencing methods often generate short reads that need to be assembled to infer the full transcript, which can be challenging, especially in regions with complex alternative splicing. Iso-Seq overcomes this limitation by sequencing single molecules of RNA, allowing for the direct determination of full-length transcripts without the need for assembly. This results in a more accurate and comprehensive view of transcript diversity, including the identification of novel isoforms, alternative splicing events, and fusion transcripts [10].

### Below is a graphic showing how Iso-Seq is able to help tackle the issue of transcript assembly due to its ability to sequence much longer reads: 

![altsplicetypes](https://pbs.twimg.com/media/DdY3cIRXcAAObmQ.jpg)

<br>



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
Image credit [EMBL EBI]

## Splice-Aware Alignment
Many modern sequence aligners take into account the various possibilities that alternative splicing can give rise to; these are known as **splice-aware aligners**. Unlike their splice-unaware counterparts which also use a reference genome to aid their alignment, these tools account for alternative splicing in two main ways. First, they can take into consideration known gene annotations as well as canonical splice sites. This allows for careful evaluation of existent alternative splicing data we have to aid in the alignment of the transcriptomic fragments. Secondly, in somewhat of a _de novo_ fashion, splice-aware aligners can also consider the possibilities of new splice junctions based on just the provided reference genome. The combination of these two techniques, coupled with traditional alignment methods, allow these splice-aware aligners to, with high confidence, perform alignment of RNA-seq data in organisms that undergo alternative splicing. See [here](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6192213/) for more information about the techniques employed to make splice-aware alignment possible.

## Popular Tools
### STAR:
[STAR](https://github.com/alexdobin/STAR) stands for Spliced Transcripts Alignment to a Reference. It is one of the fastest and most accurate splice-aware alingers currently available. It utilizes seed indexing (step 1) and seed extension (step 2) which enhances its speed greatly compared to many older splice-aware alingers. See the STAR attached GitHub link for how to download.

Indexing Reference Genome:   
```STAR --runMode genomeGenerate --genomeDir /path/to/genome/index --genomeFastaFiles /path/to/reference/genome.fa```

Aligning Reads:   
```STAR --runThreadN <num_threads> --genomeDir /path/to/genome/index --readFilesIn /path/to/reads/reads1.fq /path/to/reads/reads2.fq --outFileNamePrefix /path/to/output/prefix```

### HISAT2:
[HISAT2](https://daehwankimlab.github.io/hisat2/) stands for Hierarchical Indexing for Spliced Alignment of Transcripts. Like STAR, there is an initial indexing step, but, as the name suggests, it utilizes a hierarchical indexing-based approach, unlike STAR. It is also one of the fastest and most accurate splice-aware aligners out there. In addition, HISAT2 is praised for being very memory-efficient. See the HISAT2 attached manual link for how to download.

Indexing Reference Genome:   
```hisat2-build /path/to/reference/genome.fa /path/to/genome/index```

Aligning Reads:   
```hisat2 -x /path/to/genome/index -1 /path/to/reads/reads1.fq -2 /path/to/reads/reads2.fq -S /path/to/output/alignment.sam```

# Alternative Splicing in Disease and Therapy
With the discovery of the existence of protein isoforms, alternative splicing has quickly become a research frontier in medical genomics, and particularly cancer genomics. This is due to the fact that the differences brought about by the changes in the final mature mRNA transcript often translate (no pun intended) into structural 3D-conformational changes which ultimately affect functionality. One of the most prominent examples of disease-associated isoforms is **[Δ40p53](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7352174/)**, an N-terminally truncated isoform of the p53 tumor suppressor gene where it not have the first 39 amino acids as the constitutive splicing (original) sequence. This isoform gives rise to an increased rate of cell proliferation, a characteristic trait of cancer development in cells. 

Likewise, due to cases like that of Δ40p53, targeted therapies that aim at either directly editing the disease-associated isoform to correct it or compensating for the, typically, loss-of-function exhibited have been a hot topic of research. 

# Future Directions
On the topic of potential therapeutics, many new advances such as CRISPR/Cas9-related technologies are currently being applied to try and correct these disease-associated isoforms. However, as is the case with any such technology, particularly one that could potentially be as detrimental as gene-editing, though certain experiments on model organsims show promise, clinical trials on humans are very few and far in between due the sheer potential of unintended consequences. This is natural as we do not yet fully comprehend the direct correlation between sequence edits and protein functionality (think of things like the [protein 3D-modeling problem](https://frazer.uq.edu.au/files/2176/3d-modeling-handout-converted.pdf)), at least not the extent where we are confident in carrying larger-scale clinical trials on humans. However, as we learn more and advance these technologies, we get one step closer to fully understanding this natural transcriptomic variation that exists in our genetic code that is alternative splicing and how, through targeted therapies, we can correct any potentially disease-inducing isoforms.


# Summary and Conclusions:

In this chapter, we were able to explore the depths of alternative splicing, and we have delved into its intricate mechanisms, many of its far-reaching implications, and some emerging technologies that aid in shaping its study and application. Alternative splicing, is a huge emerging field of study in biology as it is the basis of so much genetic diversity within all organisms. It is not only fundamental to understanding biological complexity, but also pivotal in addressing numerous diseases and therapeutic interventions.

From the basic mechanisms like exon skipping and intron retention to the complex interactions of many different proteins, we have been able to discuss how alternative splicing comes about and the vast potential for an exponential amount of diversity and evolution. The historical background provides a foundation for appreciating its discovery and evolution, while the technical aspects of studying alternative splicing through RNA sequencing, microarrays, and other genomic technologies highlight the advancements in this field.

Furthermore, the integration of alternative splicing in RNA-Seq alignments and the challenges that we can face through this process demonstrate the complexity and the need for sophisticated computational tools and software. The potential of predictive modeling and artificial intelligence in splicing research has the potential to bring about a new era of possibilities in genomic studies.

In conclusion, while this field has made remarkable strides, numerous unresolved questions remain. The future of alternative splicing research holds great promise, especially in the realms of splicing modification, personalized medicine, and the harnessing of artificial intelligence. As we move forward, it is crucial to continue exploring, questioning, and innovating, with the ultimate goal of fully unraveling the mysteries of alternative splicing and harnessing its potential for the betterment of human health and understanding of life's complexity.



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

[10] Shen F, Hu C, Huang X, He H, Yang D, Zhao J, Yang X. Advances in alternative splicing identification: deep learning and pantranscriptome. Front Plant Sci. 2023 Sep 18;14:1232466. doi: 10.3389/fpls.2023.1232466. PMID: 37790793; PMCID: PMC10544900.

[11] Conesa, A., Madrigal, P., Tarazona, S. et al. A survey of best practices for RNA-seq data analysis. Genome Biol 17, 13 (2016). https://doi.org/10.1186/s13059-016-0881-8

[12] Jovic D, Liang X, Zeng H, Lin L, Xu F, Luo Y. Single-cell RNA sequencing technologies and applications: A brief overview. Clin Transl Med. 2022 Mar;12(3):e694. doi: 10.1002/ctm2.694. PMID: 35352511; PMCID: PMC8964935.

[13] Strunz, M., Simon, L.M., Ansari, M. et al. Alveolar regeneration through a Krt8+ transitional stem cell state that persists in human lung fibrosis. Nat Commun 11, 3559 (2020). https://doi.org/10.1038/s41467-020-17358-3

[14] Wright, D.J., Hall, N.A.L., Irish, N. et al. Long read sequencing reveals novel isoforms and insights into splicing regulation during cell state changes. BMC Genomics 23, 42 (2022). https://doi.org/10.1186/s12864-021-08261-2

