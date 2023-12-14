# Introduction
ChIP-Seq (chromatin immunoprecipitation sequencing) is a powerful tool that has revolutionized the field of molecular biology. ChIP-Seq enables the identification of genome-wide DNA binding activity for transcription factors, histone modifications, nucleosomes, and many other insights into the genome. As suggested in the name, it can achieve this through chromatin immunoprecipitation, followed by sequencing. Renowned biotechnology companies such as Illumina have already begun to integrate ChIP-Seq with existing technology such as next-generation sequencing allowing them to research [cancer development and progression](https://www.illumina.com/techniques/sequencing/dna-sequencing/chip-seq.html). In short, ChIP-Seq is an incredibly useful tool and has quickly become essential to understanding the complexities of the genome. This write-up will provide a basic overview of the chromatin immunoprecipitation to sequencing pipeline, followed by the bioinformatics pipeline, some of the recent applications of ChIP-Seq, and why ChiP-Seq should be more prominent. 
# Chromatin Immunoprecipitation Pipeline<a name="1"></a>

![Experimental Sequencing Pipeline](https://media.cellsignal.com/www/images/resources/applications/chip-educational/chip-protocol-steps.png)

*Image source: [Cell Signaling Technology](https://media.cellsignal.com/www/images/resources/applications/chip-educational/chip-protocol-steps.png)*

### 1. Cross-linking of Protein and DNA:
**Objective:** Stabilization of DNA-Protein Complexes

The first step in chromatin immunoprecipitation is for the cross-linking of cells to occur. In order to achieve this, Formaldehyde is used to cross-link proteins to DNA, this will create covalent bonds between them. This captures the interactions between proteins and DNA at a specific moment and locks them in place for analysis. Furthermore, using formaldehyde for cross-linking stabilizes the complexes, preventing their dissociation during later steps. 

### 2. Cell Lysis and Chromatin Shearing:
**Objective:** Solubilization of DNA-Protein Complexes

**Cell Lysis:**
Cells are treated with lysis solutions, which will dissolve cell membranes, allowing easier access to cellular contents. This process will also solubilize the DNA-protein complexes, making them accessible for further analysis.

**Chromatin Shearing:**
To further analyze the samples, the DNA-protein complexes need to be broken into smaller fragments. This can be done using ultrasonic waves to physically fragment the chromatin (sonication) or using specific enzymes to cleave the DNA at targeted sites (enzyme digestion).

### 3. Immunoprecipitation of DNA-Protein Complexes:
**Objective:** Isolation and Purification of DNA Fragments

For this step, protein-specific antibodies are introduced to the solution. They are designed to recognize and bind to specific proteins of interest within the DNA-protein complexes. The antibody-protein-DNA complexes are then treated with immunoprecipitation. This step enriches the sample for DNA fragments associated with the targeted protein, allowing for their isolation and further analysis.

### 4. Reverse Cross-linking and DNA Purification:
**Objective:** Separation of DNA from Proteins and Reversal of Cross-links

After immunoprecipitation, the cross-links between proteins and DNA are then reversed to separate the DNA. This can be done by heating the sample which will break the formaldehyde bonds. In addition, the resulting DNA will be purified from proteins and other cellular debris, which can then be used for sequencing.




# Bioinformatics Pipeline<a name="2"></a>

After performing ChIP-Seq experiments, the raw data obtained need to be processed through a series of computational steps. Below is a typical pipeline for ChIP-Seq data processing.

### 1. Quality Control of Raw Data<a name="2.1"></a>
Quality control is a crucial part of processing any raw sequencing data, regardless of what type of sequencing data you are working with.
- **Run FastQC**: Run [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/) to assess the quality of the data. FastQC is widely used in other sequencing methods as well. There is a lot of FastQC data to assess, so most importantly, check for the adapter content, per base sequence quality, and sequence duplication levels for good results.
- **Trimming**: If your quality scores are low, consider trimming your data using tools like [fastp](https://github.com/OpenGene/fastp) or [Cutadapt](https://cutadapt.readthedocs.io/en/stable/). Trimming tools are able to remove adapter and low quality sequences from your reads, improving quality scores and reliability of your downstream analyses. 
![image](https://github.com/hbcheng7/BENG183/assets/133923635/80bb6ba8-d960-4306-9626-a42bae78b855)
<br>FASTQC Example Output of Quality Scores
	- In this example, we see a considerable dropoff in quality score toward the end of reads. This tells us that using a trimming tool would be necessary to ensure data quality.

### 2. Alignment to a Reference Genome<a name="2.2"></a>
Alignment is a big step in knowing where all of your raw reads fall. Without it, you won't know where in position these reads are and will have no idea how to piece together the pieces of it. Tools used in this case will give you data on where each read lies in the genome, as well as information about the alignment quality and details. 

- **Alignment Tools**: Map the reads to a reference genome. This can be done with tools such as [Bowtie](https://bowtie-bio.sourceforge.net/manual.shtml), [STAR](https://github.com/alexdobin/STAR), or [BWA](https://bio-bwa.sourceforge.net/bwa.shtml). Your input would be your fastq files, and you will recieve a BAM/SAM file output.
  ![image](https://github.com/hbcheng7/BENG183/assets/133923635/2f8763ed-9b3f-4d0e-96ab-f00274542cb1)
<br>Bowtie Read Alignment Process
  	- In this image, gaps are represented by a red '-' and mismatches are represented with the mismatched nucleotide of the read bolded adn in red. The more mismatches and gaps in the final alignment, the lower the alignment quality tends to be.

- **SAM Format**: It is important to be able to understand your alignment and its details for each read. Thus, you should run SAMtools to generate a SAM format output from a binary BAM format if your aligner returned a BAM file. SAM formats are able to be read and give statistics needed for each read.
![image](https://github.com/hbcheng7/BENG183/assets/130010866/01632628-5b43-4435-a702-0aede747c5cd)
<br>SAM File Format Guide (Read more [here](https://en.wikipedia.org/wiki/SAM_(file_format)))
  
### 3. Post-alignment Processing<a name="2.3"></a>
After alignments, you should run some more quality control filtering. This is mainly to clean up any bad alignments and unneccesary reads. SAMtools can already perform this quality control.

- **Removing Duplicates and Poorly Aligned Reads**: Discard duplicate reads to avoid biases, and throw away poorly aligned reads that will not be useful for the data. SAMtools, SAM Bamba, or Picard Tools are packages that can do this.

### 4. Peak Calling<a name="2.4"></a>
Peak calling is an important step in this process. You want to find where peaks are going to be, and are of a significant higher signal than the background. These will be your areas for where transcription factor binding will be happening. Make sure you normalize your data for neccesary comparisons without bias.
![image](https://github.com/hbcheng7/BENG183/assets/133923635/884969c5-fd2c-46af-b65d-d0e115938c0d)
<br>MACS2 Model For Finding Peaks via Tag Data (Read more [here](https://pypi.org/project/MACS2/))
  
- **Identify Enriched Peak Regions**: Peak calling can be done with tools such as MACS2 or HOMER.
- **Peak Annotation**: Annotating peaks is important to see which features are most likely to be found at your identified region. This can be done with HOMER or BEDTools. Your results should be genomic signal profiles, distributions of different regulatory elements, and nearest introns/exons/ genic regions.

### 5. Differential Binding Analysis<a name="2.5"></a>
Differential binding analysis is important to visualize the differences in gene regulation that result in different gene expression levels. This will help identify just how different transcription factors bind differently to regions, and how they do so in different scenarios.

- **Comparative Analysis**: Compare different conditions or time points to identify how the binding complex interacts differently. Tools that could be used for this could be DiffBind or MAnorm.
![image](https://github.com/hbcheng7/BENG183/assets/133923635/9d0123cf-ee94-4360-acc1-b09570c98149)
<br>Diffbind binding affinities visualized for each factor (Read more [here](https://bioconductor.org/packages/release/bioc/vignettes/DiffBind/inst/doc/DiffBind.pdf))

### 6. Visualization<a name="2.6"></a>
It is important to see where in the genome your peaks are being called. This can be done using a genome browser.

- **Genome Browser**: You can visualize the binding sites as peaks compared to the background using tools like the UCSC Genome Browser or IGV.
<img width="663" alt="image" src="https://github.com/hbcheng7/BENG183/assets/133923635/49eae0d5-0f94-4047-a5de-896af21f109c">
<br>IGV Visualization (enriched peaks are circled)

### 7. Motif Analysis<a name="2.7"></a>
Lastly, you can utilize techniques to find enriched motifs. This allows for us to understand binding preferences and regulatory roles of protein-DNA binding complexes

- **Motif Annotation**: Utilize a tool to discover any motifs and compare them to known background motifs. Usually a list of the most similarly represented motifs will show up, including all the statistics needed such as nucleotide frequencies at each position or probabilities. Tools such as MEME-suite or HOMER can be used.

This pipeline is crucial for transforming raw ChIP-Seq data into meaningful insights about protein-DNA interactions and their impact on gene regulation and cellular processes.

<img width="676" alt="image" src="https://github.com/hbcheng7/BENG183/assets/133923635/a96b9f2c-a98e-41cb-b59d-6cf32b17ef09">
<br>Top Known Motifs Found with their Statistics  

# Advantages and Applications<a name="3"></a>

### Why should I use ChIP-seq?<a name="3.1"></a>

- **High-Resolution Mapping**
  - Targets precise DNA binding sites, providing clarity on regulatory regions.
  - Reveaks motif occurrence within binding regions to understand protein binding specificity.

- **Genome-wide Profiling**
  -  Allows for the investigation of all potential binding sites across the whole genome in a single experiment, avoiding the biases of pre-selected regions.
  -  Very broad scope across various genomic elements, including enhancers, silencers, and insulators.

- **Multiplexing Capabilities**
  -  High throughput with multiple targets in a single experiment.
  -  Reduces time and cost by consolidating multiple assays into a single sequencing run.

- **Adaptability**
  -  Applicable to any protein of interest, provided a known antibody is available.
  -  Can be tailored for various modifications, expanding its use beyond just histones or transcription factors.

- **Studying non-coding RNA genes**
  -  Enhances the current understanding of gene regulatory networks by mapping unknown regulatory elements.
  -  Contributes to the annotation of non-coding RNA genes and their associated proteins.

- **Compatibility with Low-Quantity Samples**
  -  Enables epigenetic studies on rare cell types, such as stem cells or specific cancer cells.
  -  Particularly useful for clinical samples where the available material is often limited or costly.
 
### When should I use ChIP-seq?<a name="3.2">
If your research project entails any of these, you would want to strongly consider ChIP-seq technology:
1. Exploring Gene Regulation Mechanisms
   - Use ChIP-seq to study select transcription factors or histone modifications on your gene or genes of interest.
   - Integrate this data with RNA-seq data, to identify which proteins are associated with your gene of interest, then to determine the nature of regulation those proteins have on your gene, seen as RNA transcripts. You can integrate this data with any data that displays post-transcriptional expression data, even phenotypic data if you know the ontology associated with your gene or genes of interest.
2. Studying Protein-DNA interactions
   - Use ChIP-seq if you have a certain protein or proteins you'd like to study, to reveal which regions of the genome it is associated with. One way to visualize results of this would be Gene Ontology analysis of regions of DNA associated with your protein(s), to see what exactly your protein is involved in.
3. Epigenetic Research
   - ChIP-seq is very useful for epigenetic purposes, especially studying chromatin and epigenetic modifications. It is the go-to method for examining how histone modifications and chromatin remodelers influence chromatin structure and gene expression
4. Disease Research
   - ChIP-seq can be used to determine differences in moecular mechanisms for underlying diseases, revealing changes in protein-DNA interactions on the epigenetic level. These are crucial for revealing the whole story of diseases.

In general, ChIP-seq is a powerful tool, and it can be even more powerful with accompanying tools such as RNA-seq to further explore revealed protein-DNA interactions. Much of these research directions would benefit greatly from additional assays to further explore the complexities of the human genome. Whenever your project is studying protein-DNA interactions, think ChIP-seq.

Lastly, here is one real-world example of ChIP-seq being used:
- **The ENCODE Project**
  - The Encyclopedia of DNA Elements ([ENCODE](https://www.encodeproject.org/help/project-overview/)) Project  utilizes ChIP-seq to map DNA-binding sites of various transcription factors and histone modifications across the whole human genome.
  - This project aims to catalog all functional elements in the human genome, offering a comprehensive atlas for understanding gene regulation and its implications in health and disease.

# References
1. https://www.illumina.com/techniques/sequencing/dna-sequencing/chip-seq.html
2. https://media.cellsignal.com/www/images/resources/applications/chip-educational/chip-protocol-steps.png
3. https://www.thermofisher.com/us/en/home/life-science/antibodies/antibodies-learning-center/antibodies-resource-library/antibody-application-notes/step-by-step-guide-successful-chip-assays.html
4. https://www.epicypher.com/resources/blogchromatin-mapping-basics-chipseq/
5. https://www.cd-genomics.com/pipeline-and-tools-comparison-for-chip-seq-analysis.html
6. https://hbctraining.github.io/Intro-to-rnaseq-hpc-salmon/lessons/qc_fastqc_assessment.html
7. https://www.basepairtech.com/blog/basepairs-chip-seq-analysis-pipelines-pathway-enrichment/
8. https://www.encodeproject.org/help/project-overview/


