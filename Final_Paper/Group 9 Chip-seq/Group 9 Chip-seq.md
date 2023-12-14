# Chromatin Immunoprecipitation Sequencing (ChIP-SEQ) & Analysis
###### BENG183 Final Paper date:12-13-2023 
###### Group 9 
###### Hanson Hoang A16872363
###### Kathy Yu Xuan Gu A16362055
###### Maria Pinyi Wang A16423014

1. [Introduction](#1)
2. [Purpose of CHIP-Sequencing](#2)
3. [ChIP-Seq Workflow](#3)<br>
    3.1. [Crosslinking](#31)<br>
    3.2. [Cell Lysis](#32)<br>
    3.3. [Chromatin Shearing](#33)<br>
    3.4. [Immunoprecipitation (IP)](#34)<br>
    3.5. [Reversal of Cross-linking](#35)<br>
    3.6. [DNA Purification](#36)<br>
    3.7. [Library prep and indexing](#37)<br>
4. [ChIP-Seq Analysis Pipline](#4)<br>
    4.1. [Quality Control & Pre-processing](#41)<br>
    4.2. [Read Alignment to Reference Genome](#42)<br>
    4.3. [Peak Calling and Identification](#43)<br>
    4.4. [Annotation and Functional Analysis](#44)<br>
    4.5. [Motif Analysis for DNA Binding Sequences](#45)<br>
    4.6. [Visualization and Interpretation](#46)<br>
5. [Advantages of ChIP-Seq](#5)<br>
    5.1. [Unbiased Genome Exploration](#51)<br>
    5.2. [Extensive Genome-Wide Profiling](#52)<br>
    5.3. [Efficient DNA Target Capture](#53)<br>
    5.4. [Adaptable Sample Compatibility](#54)<br>
    5.5. [Enhanced Resolution and Sensitivity](#55)<br>
    5.6. [Predictive Power for Tissue-Specific Enhancer Activities](#56)<br>
6. [Applications of ChIP-Seq](#6)<br>
    6.1. [Profiling DNA-Binding Proteins](#61)<br>
    6.2. [Gene Regulation Insights](#62)<br>
    6.3. [Identifying Transcription Factor Binding Sites](#63)<br>
    6.4. [Wide-Ranging Applications Beyond Histone-DNA Interactions](#64)<br>
    6.5. [Detecting Variations in Transcription Factor Binding](#65)<br>



## 1. Introduction<a name="1"></a>

ChIP-seq, short for Chromatin Immunoprecipitation Sequencing, is a sequencing technique used to study genome-wide DNA-protein interactions.
By identifying regions where proteins, like transcription factors or histones, that bind to DNA, ChIP-seq allows us to understand how gene regulation works along with learning the structure of the chromatin and epigenetic modifications.

## 2. Purpose of CHIP-Sequencing<a name="2"></a>

The purpose of ChIP-seq is to map and study genome-wide interactions between DNA and proteins. By identifying binding sites, regulatory elements, and chromatin modifications, ChIP-seq enables us to study epigenetic modifications that affect gene regulation to ultimately understand our bodies cellular responses and mechanisms.


## 3. ChIP-Seq Workflow<a name="3"></a>

#### 1) Crosslinking<a name="31"></a>

Cells are treated with a cross-linking agent, often formaldehyde to covalently link interacting proteins to DNA. As there is constant movement of proteins and DNA, ChIP captures a snapshot of the protein–DNA complexes that exist at a specific time. In vivo crosslinking covalently stabilizes protein–DNA complexes. 

#### 2) Cell Lysis<a name="32"></a>

Cells are lysed to break open the cell membrane and release the chromatin. Because protein–DNA interactions occur primarily in the nuclear compartment, removing cytosolic proteins can help reduce background signal and increase sensitivity. Successful cell lysis can be visualized under a microscope. Take a 10 µL sample before and after lysis, and using a hemocytometer, examine the whole cells versus the nuclei.

#### 3) Chromatin Shearing<a name="33"></a>

The chromatin is fragmented or “sheared” to mononucleosome sized fragments (150-300 bp) through processes like sonication and enzymatic digestion. By shearing the long strands, the resulted DNA fragments can be more easily and quickly processed, which is important for obtaining high resolution sequencing data.

#### 4) Immunoprecipitation (IP)<a name="34"></a>

To isolate a specifically modified histone, transcription factor, or cofactor of interest, ChIP-validated antibodies are used to immunoprecipitate and isolate the target from other nuclear components. The antibody is coupled to magnetic beads coated with protein-A and/or G (depending on the antibody isotype) to facilitate immunoprecipitation, and the antibody-bound chromatin is isolated from bulk chromatin using a magnet. The advantages of magnetic beads are easy separation and easy visibility of the beads in the tube, leading to less loss of material and highly reproducible results. All components other than the target should be washed off using wash buffers with progressively higher salt and detergent concentrations, in order to reduce background signal in the data.

#### 5) Reversal of Cross-linking<a name="35"></a>

The target-enriched chromatin is treated with Proteinase K to digest proteins, RNase A to degrade RNA, and high salt with heat environment to reverse cross-links. This separates the protein from the DNA, allowing for downstream processing.

#### 6) DNA Purification<a name="36"></a>

DNA fragments are purified from the immunoprecipitated sample. This step removes proteins and other cellular components, leaving only the DNA associated with the protein of interest.

#### 7) Library prep and indexing<a name="37"></a>

Just like with RNAseq, prepare a sequence library by adding sequencing adapters to both ends of the DNA fragments. When the library is prepared, perform PCR to the strands to amplify the library. For quality check, check the library concentration and confirm size distribution by capillary electrophresis. When it is considered a qualified library, the strands are sequenced, and the garbage reads are filtered out. Finally, align the high quality reads to the reference genome and the data is ready for analysis.   



## 4. ChIP-Seq Analysis Pipline<a name="4"></a>

#### 1) Quality Control & Pre-processing<a name="41"></a>

The first step is to ensure that the raw sequencing data is of high quality and suitable for downstream analysis. This involves checking the quality metrics of the reads, such as base quality scores, GC content, sequence length, duplication rate, and adapter contamination.

Quality control and pre-processing are essential steps in ChIP-seq data analysis, as they can reduce the technical variation and noise that can affect the biological signal and interpretation. ChIP-seq data can be influenced by various factors, such as chromatin fragmentation, antibody specificity, and sequencing depth. These factors can introduce unwanted variation, bias, or artifacts that can influence the results and lead to false positives/negatives. By performing quality control and pre-processing, the data can be normalized, filtered, and corrected to minimize these effects and improve the reliability and reproducibility of the analysis. 

One of the tools that can perform this quality assessment is FastQC, which generates a quality report for each sample. The report includes various plots and statistics that can help identify potential problems or biases in the data.

Another tool that can help with the pre-processing of the data is Trim Galore, which can remove the low quality reads and adapters from the fastq files. This can improve the accuracy and efficiency of the subsequent alignment step.


#### 2) Read Alignment to Reference Genome<a name="42"></a>

The second step is to map the reads to a reference genome, which allows for the identification of the genomic regions that interact with the protein of interest. This involves using an alignment tool that can handle the short and high-throughput reads generated by chip-seq.

Two tools that can perform this alignment are STAR and HISAT2, which are both spliced aligners. They can handle both single-end and paired-end reads, and can account for splice junctions, indels, and mismatches. They also support multiple output formats, such as SAM and BAM, which store the information about the mapped reads and their alignment to the reference genome.

The quality and accuracy of the read alignment can affect the results and interpretation of the downstream analysis, such as:

- **Peak detection: The peak calling tool relies on the alignment information to identify the regions of the genome that are enriched for the protein of interest. The number, shape, and significance of the peaks depend on the distribution and intensity of the reads along the genome. Poor or inaccurate alignment can lead to false positives/negatives in peak detection.**
- **Peak location: The peak location indicates the genomic position and range of the protein-DNA binding site. The accuracy and resolution of the peak location depend on the alignment of the reads to the reference genome. Misalignment/shift of the reads can result in inaccurate and/or imprecise peak location.**
- **Peak intensity: The peak intensity indicates the strength and frequency of the protein-DNA binding event. The quantification and comparison of the peak intensity depend on the alignment of the reads to the reference genome. Uneven or biased alignment can result in overestimation/underestimation of the peak intensity.**

#### 3) Peak Calling and Identification<a name="43"></a>

The third step is to locate the regions where the protein of interest interacts with the DNA, which are called peaks or enriched regions. This involves using a peak calling tool that can detect the significant signal peaks from the background noise, and estimate their boundaries and significance.

Two of the tools that can perform this peak calling are MACS2 and HOMER. They can assign peaks to the closest genes and perform functional analysis of the peak-associated genes, such as gene ontology enrichment, pathway analysis, and motif discovery. They can also compare the peaks or enriched regions between different samples or conditions, and identify the differential binding sites.
- **MACS2 is a tool for ChIP-seq peak calling that uses a dynamic Poisson distribution to model the local background noise and a sliding window approach to scan the genome for peaks. MACS2 can also adjust the peak boundaries by shifting the read positions according to the estimated fragment size, and estimate the false discovery rate (FDR) for each peak based on a negative binomial distribution.**
- **HOMER is another popular tool for ChIP-seq peak calling that uses a binomial test to compare the read counts in a given region to a local background mode, and a fixed or variable window size to define the peak regions. HOMER can also perform peak annotation, motif analysis, and differential binding analysis using various statistical methods.**


#### 4) Annotation and Functional Analysis<a name="44"></a>

The fourth step is to link the enriched regions to the known genomic features, such as genes, promoters, enhancers, or regulatory elements. This involves using an annotation tool that can assign the peaks to the closest or most relevant genomic features, and provide information about their function and expression.

One of the tools that can perform this annotation is DAVID, which is a web-based tool that can annotate and associate the peaks with various biological databases and resources. It can also perform functional enrichment analysis, which can identify the over-represented biological functions or pathways among the peaks, and provide statistical evidence for their significance.

Another tool that can perform annotation and functional analysis is GREAT, which is a web-based tool that can assign the peaks to the genes that are most likely to be regulated by them, based on the genomic distance and the regulatory potential of each region. It can also perform ontology enrichment analysis, which can identify the over-represented biological terms or concepts among the peaks, and provide statistical evidence for their relevance.

#### 5) Motif Analysis for DNA Binding Sequences<a name="45"></a>

The fifth step is to discover the conserved DNA motifs within the enriched regions, which can represent the binding sites for specific transcription factors or other DNA-binding proteins. This involves using a motif discovery tool that can scan the sequences of the peaks and identify the common patterns or motifs that are enriched in the data.

One of the tools that can perform this motif discovery is HOMER, which is a suite of tools that can perform various tasks related to chip-seq analysis. It can identify both known and novel motifs, and compare them with the existing motif databases, such as JASPAR or TRANSFAC. It can also perform motif enrichment analysis, which can determine the significance and specificity of the motifs among the peaks.

#### 6) Visualization and Interpretation<a name="46"></a>

The final step is to visualize and manually interpret the chip-seq data, which can help to gain insights into the biological meaning and implications of the results. This involves using a visualization tool that can display the aligned reads, the identified peaks, the genomic annotations, and the motifs in a graphical and interactive way.

Two of the tools that can perform this visualization are IGV and UCSC Genome Browser, which are both popular and user-friendly tools that can load and display various types of genomic data. They can also provide various features and options to customize the view, such as zooming, panning, filtering, highlighting, and exporting. 


## 5. Advantages of ChIP-Seq<a name="5"></a>

#### 1) Unbiased Genome Exploration<a name="51"></a>

ChIP-Seq's ability to explore the genome without prior sequence information revolutionizes genetic analysis, offering a new horizon in genomic discovery. This technique bypasses the limitations of array-based methods, providing a more comprehensive and inclusive genomic view. It's especially valuable in exploratory studies, allowing researchers to uncover previously unknown genomic elements and interactions. ChIP-Seq's role in such exploratory research has become indispensable, opening up new avenues for understanding genomic complexity.

#### 2) Extensive Genome-Wide Profiling<a name="52"></a>

ChIP-Seq is celebrated for its capability to generate extensive data across the entire genome. Its massively parallel sequencing technology facilitates high-throughput data acquisition, making it a formidable tool for comprehensive epigenomic profiling. This technique allows simultaneous investigation of multiple genomic regions, shedding light on complex genomic landscapes. The cost-effectiveness combined with the high data yield positions ChIP-Seq as a practical and efficient choice for large-scale genomic studies.

#### 3) Efficient DNA Target Capture<a name="53"></a>

The technique’s efficacy in isolating DNA targets, especially those linked to transcription factors and histone modifications, is unparalleled. ChIP-Seq can survey the entire genome, capturing a wide array of DNA-protein interactions. This capability allows for a detailed understanding of chromatin dynamics and gene regulation. The comprehensive data obtained through ChIP-Seq are invaluable for mapping genomic interactions and understanding cellular processes.

#### 4) Adaptable Sample Compatibility<a name="54"></a>

ChIP-Seq's versatility with a range of DNA samples makes it exceptionally adaptable. It can be applied to diverse study designs, including those involving limited or challenging sample types. This adaptability extends the technique's applicability across various research contexts, including studies on rare cell types or precious clinical samples. Consequently, ChIP-Seq is a valuable tool in both basic and translational research.

#### 5) Enhanced Resolution and Sensitivity<a name="55"></a>

ChIP-Seq's increased sensitivity and specificity for mapping transcription factor binding sites across the genome mark a significant advancement over earlier techniques. This heightened resolution allows for the identification of subtle and complex patterns of DNA-protein interactions. The ability to detect low-abundance transcription factors and discern their binding affinities provides deeper insights into gene regulatory networks. ChIP-Seq's precision is crucial for understanding the nuances of chromatin architecture and function.

#### 6) Predictive Power for Tissue-Specific Enhancer Activities<a name="56"></a>

ChIP-Seq has demonstrated remarkable accuracy in predicting tissue-specific activities of enhancers. The technique's high-resolution profiling of chromatin marks facilitates the identification of typical and super-enhancers. This predictive capability is essential for understanding gene expression regulation and cellular differentiation processes. ChIP-Seq has thus become a key tool in deciphering the complex regulatory landscapes of eukaryotic genomes.

## 6. Applications of ChIP-Seq<a name="6"></a>

#### 1) Profiling DNA-Binding Proteins<a name="61"></a>

ChIP-Seq has substantially enhanced our understanding of DNA-binding proteins and their genomic localization. By enabling genome-wide profiling, this technique provides detailed maps of protein-DNA interactions. These maps are crucial for understanding transcriptional regulation and chromatin organization. ChIP-Seq's ability to identify binding sites of transcription factors and other DNA-associated proteins has been instrumental in revealing the complexity of gene regulation.

#### 2) Gene Regulation Insights<a name="62"></a>

ChIP-Seq offers unparalleled insights into gene regulation, particularly in the context of transcriptionally inactive DNA sequences. By studying interactions between these sequences and histones, ChIP-Seq helps unravel the mechanisms of epigenetic regulation. This understanding is key to deciphering how genes are turned on and off in different cellular contexts. Such insights have profound implications for understanding diseases linked to gene regulatory dysfunction.

#### 3) name<a name="63"></a>

ChIP-Seq is vital for identifying transcription factor binding sites, often used in conjunction with RNA sequencing and methylation analysis. This combination of techniques allows for a comprehensive understanding of gene regulatory networks. ChIP-Seq data can reveal how transcription factors interact with the genome, influencing gene expression patterns. Such insights are crucial for understanding cellular responses to environmental stimuli and developmental cues.

#### 4) Wide-Ranging Applications Beyond Histone-DNA Interactions<a name="64"></a>

The scope of ChIP-Seq extends well beyond studying Histone-DNA interactions. Its applications in areas like DNA methylation, nucleosome positioning, and chromatin remodeling highlight its versatility. ChIP-Seq is instrumental in mapping various chromatin states and understanding their role in gene regulation. This versatility makes ChIP-Seq an indispensable tool in fields ranging from basic biology to medical research.

#### 5) Detecting Variations in Transcription Factor Binding<a name="65"></a>

ChIP-Seq is adept at uncovering functional variations in transcription factor binding due to genetic differences. This ability to detect individual-specific and allele-specific chromatin signatures is crucial for personalized medicine. It reveals how genetic variations influence gene expression and disease susceptibility.

## Reference

[1]https://nbisweden.github.io/workshop-archive/workshop-ChIP-seq/2018-11-07/labs/lab-processing.html

[2]https://en.wikipedia.org/wiki/ChIP_sequencing

[3]https://www.illumina.com/techniques/sequencing/dna-sequencing/chip-seq.html

[4]https://www.nature.com/articles/nrg2641

[5]https://www.youtube.com/watch?v=nkWGmaYRues

[6]https://www.epicypher.com/resources/blogchromatin-mapping-basics-chipseq/