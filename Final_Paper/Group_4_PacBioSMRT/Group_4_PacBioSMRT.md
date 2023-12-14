![logo-pacbio](https://hackmd.io/_uploads/S1xZ2c54p.svg)
# **SMRT Sequencing**

Team #4
By: Ruchi Kamboj, Varsha Mani, Jessica Fong

Here's a [short video](https://youtu.be/_lD8JyAbwEo) about how SMRT sequencing works.
## Background

DNA Sequencing is essential to bioinformatics and research as it allows scientists to understand the nucleotide sequence of genes. DNA sequencing has allowed scientists to assemble genomes of different species and understand and develop new remedies for diseases. The more reliable and efficient sequencing technologies are, the more breakthroughs can be made. A new type of next-generation sequencing called SMRT (Single Molecule Real-Time) is revolutionizing DNA sequencing. It was commercialized in 2011.


## What is a ZMW?

SMRT or Single Molecule Real-Time sequencing utilizes a zero-mode waveguide (ZMW) in order to sequence molecules. 

A ZMW is an optical waveguide. It is a glass-supported, cylindrical, metallic chamber that is 70 nanometers wide, has lighting coming through the bottom, and has an extremely small detection volume of 20 * 10<sup>-21</sup> liters. It directs light energy into a volume that is tiny in relation to the light's wavelength in all dimensions. A ZMW is made of optical nanostructures in a thin metallic film. 

The ZMW allows individual molecules that are tagged with a fluorescent biomarker to be isolated and identified. The ZMW records one nucleotide at a time being incorporated by DNA polymerase.

![zmw](https://hackmd.io/_uploads/H1gedJNS6.jpg) 
Above shows a diagram of a ZMW.

![A-single-SMRT-cell-Each-SMRT-cell-contains-150-000-ZMWs-Approximately-35-000-75-000-of](https://hackmd.io/_uploads/SJKQuy4Bp.jpg)


Above shows a Pac Bio SMRT Cell, which contains around 150,000 ZMWs.

## How does SMRT Work?

First, one DNA polymerase enzyme is affixed to the bottom of a ZMW with a DNA template.

![dna in zmw](https://hackmd.io/_uploads/Skc45yEHa.png)

The figure above shows one molecule of DNA in a ZMW chamber. 

![nuc colored](https://hackmd.io/_uploads/ryKAcyESa.png)

Each DNA nucleotide is fluorescently labeled with a different colored dye, like in the figure above.

Upon incorporation of a nucleotide by DNA polymerase, the nucleotide gives off a fluorescent light which is detected by the ZMW. The nucleotides are recorded according to their dye color. As the polymerase synthesizes, each nucleotide it adds is being recorded so real-time DNA sequencing is recorded.

![first pulse](https://hackmd.io/_uploads/Bk-ncyEHT.png)

![second pulse](https://hackmd.io/_uploads/rkraq1EBp.png)


The figures above illustrate this process. It shows a ZMW with a DNA polymerase attached to the bottom, and how when a nucleotide is added, the nucleotide will give off a light upon incorporation. That color light is recorded and using those colors, the molecule will be sequenced by reading all the pulses.


## Different SMRT Modes


There are two main modes of SMRT: CCS and CLR. 

CCS is circular consensus sequencing. The DNA polymerase will transcribe the same molecule many times and the consensus sequence will be used. This results in a very high quality accurate sequencing of 99% known as HiFi reads.

![ccs](https://hackmd.io/_uploads/HJO731NS6.png)

The figure above illustrates CCS sequencing, with the DNA polymerase looping around the template many times. 


CLR is Continuous Long Read sequencing. In CLR the DNA polymerase transcribes sequences greater than 50kb sequences as it continuously adds nucleotides and the ZMW records the light pulses. 

![clr](https://hackmd.io/_uploads/SkHU2yNrT.png)

The figure above illustrates CLR.

## SMRT Pipeline

1. DNA/RNA is isolated.
    A. This isolation needs to be of a high molecular weight. The Nanobind Kit is recommended.
2. Library Prep
    A. DNA will be fragmented. The ends will be repaired. Then the quality and size of the fragments will be checked. Purify the DNA.
    B. Double stranded DNA fragments are capped on both sides with ligated hairpin adapters making a circular template. 
    C. DNA purification will be used on the templates. 
    D. To the adapters, the primers and the DNA polymerase will attach.

![LIB prep](https://hackmd.io/_uploads/r1Kr6yNrT.png)

The figure above shows a diagram of the steps of library preparation.

![fin lib](https://hackmd.io/_uploads/H1bDayVHa.png)

Finally, before sequencing the DNA molecule will look like the above figure. 

3) Sequencing 
    A) The PacBio sequencing system (Sequel II system) will be used. The PacBio SMRT Cell has millions of ZMWs. In the ZMWs, DNA molecules are immobilized.
    B) One DNA polymerase enzyme is affixed to the bottom of a ZMW with a DNA template. 
    C) Nucleotide incorporation is measured in real time through the emission and recording of light. Each nucleotide gives off a different color light when incorporated by the polymerase. 
    D) The polymerase can sequence the same DNA many times which produces very accurate consensus HiFi reads.


![pipeline](https://hackmd.io/_uploads/rJNXAJ4S6.png)

The figure above shows the steps of SMRT illustrated.

## Advantages and Disadvantages

### Advantages
![coverage_longVSshort](https://hackmd.io/_uploads/SkyQSTcVT.png)
There are several advantages to using SMRT sequencing. Firstly, it eliminates the need for DNA amplification. Secondly, it produces long read lengths, with averages ranging from 10kb to 15kb. In the picture above, short read lengths can result in gaps when mapped back to the genome. In contrast, long read lengths eliminate these gaps. Thirdly, the uniform coverage ensures few areas with either few reads or an excessive number of reads in one region of the genome, as depicted in the picture below.
![coverage](https://hackmd.io/_uploads/Sy8qCh9ET.png) 
Fourthly, SMRT sequencing exhibits minimal GC bias. This means that in regions with high GC content, there is no significant increase or decrease in the number of reads compared to other regions. Lastly, SMRT sequencing has the capability to differentiate certain common DNA modifications, such as methylation.
  * How can SMRT tell when DNA modification has occurred?
    * `SMRT Sequencing allows the observation of single DNA polymerases reading individual molecules of DNA in real time. Therefore, the kinetic characteristics of DNA polymerization are observable on a single-molecule basis.` ([source](https://www.pacb.com/wp-content/uploads/2015/09/WP_Detecting_DNA_Base_Modifications_Using_SMRT_Sequencing.pdf))
  * ![DNAmythylation](https://hackmd.io/_uploads/SkeFxa5E6.png)


  Read [this research article](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2013-14-7-405) for more knowledge on the advantages of SMRT sequencing.

### Disadvantages
![disadvantages_SMRT](https://hackmd.io/_uploads/H1UGzR54p.png)
While SMRT sequencing offers numerous advantages, there are also a couple of disadvantages. Firstly, it demands higher DNA input amounts. Secondly, cost limitations arise because SMRT is more expensive to use compared to short-read sequencing technology. Lastly, it exhibits lower throughput, resulting in a reduced number of sequenced bases per hour compared to high-throughput methods.
 
![SMRT_cell](https://hackmd.io/_uploads/BkaYyAc4a.svg)

There is also the possibility of SMRT sequencing not performing as intended. According to [this article](https://bitesizebio.com/28911/single-molecule-real-time-sequencing/#:~:text=The%20PACBIO%20SMRT%20system%20seems,carry%20out%20successful%20sequencing%20reactions), certain issues may arise during the use of SMRT. 
  * Not all of the zero-mode waveguides (a nanophotonic device for confining light to a small observation volume) will carry out successful sequencing reactions
  * Some of the wells simply do not have the DNA template
  * Sequencing error rate produced using PACBIO SMRT is still high compared to the Illumina platform
    * Can need at least 15 passes (15 times passage over) to generate 99% accurate data


## Tools
There are many sequencing tools that allow processing and interpretation of data to handle different stages of the sequencing workflow. Some of the following tools are not necessarily specific to PacBio SMRT, but they help in sequencing PacBio SMRT data.

### SMRT Link Software
SMRT Link Software is a tool that PacBio SMRT utilizes for data analysis to visualize sequencing data while providing access to tasks such as variant detection and De Novo Assembly. This tool processes data and encompasses tools for De Novo Assembly as well as identifies insertions, deletions, and DNA/RNA base modifications to enhance user experience. With SMRT Link Software, researchers can identify variants and visualize the variance across the whole genome.
![SMRT Link Software](https://hackmd.io/_uploads/B1imLfILa.png)

### Canu
Canu is a genome assembly software that reduces sequencing errors in long-read data, handles large and complex genomes efficiently, and produces accurate high-quality assemblies. Canu is also used by the De Novo Assembly for assembly of long-read data.

### Quiver
Quiver is a software used for improving base calling accuracy to determine the correct base at each sequence position. It is part of SMRT Link Software and is no longer its individual tool. The software is used for consensus calling to analyze reads that overlap with each other.

### Racon
Racon is a tool used for error correction in long-read sequencing data, as PacBio SMRT produces. Racon uses alignment and consensus techniques to improve read accuracy. Racon helps with reducing errors in the long-read data.

### HGAP
Hierarchical Genome Assembly Process (HGAP) is used for De Novo Assembly for long-read data, involving processing raw SMRT sequencing data, generating an initial assembly, performing error correction, and abiding by quality assessment of the genome.
![HGAP Tool](https://hackmd.io/_uploads/rJE4If88T.png)

### Pilon
Pilon is used for refining genome assemblies through base error correction and improving data accuracy. Pilon is typically used for short-read data, but it can be utilized for PacBio SMRT as well. It is used to have a combination of long-read and short-read data from PacBio and Illumina to determine accuracy.


## Comparisons to Different Sequencing Technologies
One way to analyze the usefulness of PacBio SMRT is by analyzing the year of production, length of read length, error rate, cost, and applications as well as compare this sequencing technology to other technologies.

### PacBio
PacBio SMRT was developed in the early 2000s and produces longer read lengths that are up to several kb of length. This sequencing tool also has higher per-base error rate and is more costly and time consuming per base. Some applications of PacBio SMRT include De Novo Assembly and identifying genomic variations.

### Illumina
Illumina Sequencing was developed in the early 2000s and produces shorter read lengths that are approximately a few hundred base pairs. This sequencing tool also has a lower per-base error rate and is cost-effective. Some applications of Illumina Sequencing include Whole Genome Sequencing and Transcriptome Analysis.

### Single-Cell
Single-Cell Sequencing was developed in the mid 2010s, although the concept has been studied for many decades. This sequencing tool produces shorter read lengths and has a higher per-base error rate. It is more costly per-base and applications of Single-Cell Sequencing include tumor heterogeneity and aiding immune responses.

### Nanopore
Nanopore Sequencing has also been studied for many decades, but the first sequencing technology was developed in the mid 2010s. This sequencing technique can produce long reads to enable better analysis of repetitive sequences and structural variations. It also has a higher per-base error rate and it is also more costly per-base. Some applications of Nanopore Sequencing include genome assembly, RNA-Sequencing, detecting DNA modifications and pathogens.

### Sanger
Sanger Sequencing is the oldest of all the sequencing techniques mentioned, as it was developed in the 1970s. Sanger Sequencing produces shorter read lengths and has a lower per-base error rate. It is more costly per-base and applications of Sanger Sequencing include fragment analysis and validation of specific regions of interest such as SNPs, insertions, and deletions.

The following shows a comparison between the development, cost, time-consumption, read length production, accuracy, and reads produced of the five sequencing techniques mentioned above.

![Development_Cost.png](https://hackmd.io/_uploads/Hy7TwfIL6.jpg)
![TIme_ReadLength.png](https://hackmd.io/_uploads/ryjyuMILp.jpg)
![Accuracy_ReadsProduced.png](https://hackmd.io/_uploads/BklWdzLUa.jpg)

There are trade-offs in each of the five sequencing techniques. For instance, while Sanger Sequencing is the most accurate, it has a long time consumption and a heavy cost. On the other hand, PacBio SMRT is not very accurate, but it produces the longest reads for data analysis.


## Applications & Significance
One application of PacBio SMRT includes De Novo Genome Assembly, where the long reads generated by PacBio SMRT allow researchers to construct accurate genomes with repetitive sequences. This technology allows the sequencing of complex regions like telomeres and centromeres as well. 

Another application of PacBio SMRT includes Genome Sequencing, where the production of long reads is useful for assembling complex genomes as well as allows the detection of genetic variations like insertions, deletions, and SNPs. 

PacBio SMRT also allows the identification of different variants that can cause diseases and can relate genomic regions that are linked to diseases. PacBio SMRT generates long reads, which are useful in identifying variants since they can span repetitive regions. There are also other tools like SMRT Link Software and Canu that analyze PacBio data to detect variants.

Additionally, PacBio SMRT is useful in analyzing long non-coding RNA to analyze gene expression regulation and disease implications. PacBio SMRT produces long reads that enable the identification of splice variants in long non-coding RNAs; combining PacBio SMRT with DNA methylation or Chromatin Immunoprecipitation Sequencing (ChIP-Seq) data can provide more information about long non-coding RNAs.


## Citations
0.2 Sequencing technologies. 2019, https://zhonglab.gitbook.io/3dgenome/chap0-preparation/0.2-sequencing-technologies

“Advantages of Nanopore Sequencing.” Oxford Nanopore Technologies, 5 Apr. 2023, nanoporetech.com/how-it-works/advantages-nanopore-sequencing. 

Casey, Richard. “What Is de Novo Assembly?” The Sequencing Center, Richard Casey https://thesequencingcenter.com/wp-content/uploads/2019/01/TSC_wide_logo_blue-e1546560904499.png, 26 Sept. 2022, thesequencingcenter.com/knowledge-base/de-novo-assembly/.

“Computational Tools.” PacBio, 21 Nov. 2023, www.pacb.com/computational-tools/. 

“Getting Started with Next Generation Sequencing.” Illumina, www.illumina.com/destination/ngs-getting-started.html?scid=2023-270PAS4074&amp;gclid=CjwKCAiApuCrBhAuEiwA8VJ6Jt5PgR4x8v_jzLs7ITf55Fhf8xJ_ym9Rb9WuszvtizbnmUC1ScB_ShoCWy4QAvD_BwE.

“Overview of Pacbio SMRT Sequencing: Principles, Workflow, and Applications.” Overview of PacBio SMRT Sequencing: Principles, Workflow, and Applications - CD Genomics, www.cd-genomics.com/pacbio-smrt-system-single-molecule-real-time-sequencing.html. Accessed 13 Dec. 2023. 

Pacbio sequencing – how it works. 4 Feb. 2020, https://www.youtube.com/watch?v=_lD8JyAbwEo

PacBio. “Sequencing 101: From DNA to Discovery - the Steps of SMRT Sequencing.” PacBio, 11 Apr. 2022, www.pacb.com/blog/steps-of-smrt-sequencing/. 

Pavlovic, S., Klaassen, K., Stankovic, B., Stojiljkovic, M., & Zukic, B. (2020). Chapter 9 - next-generation sequencing: The enabler and the way ahead. In M. E. Kambouris & A. Velegraki (Eds.), Microbiomics (pp. 175–200). Academic Press. https://doi.org/10.1016/B978-0-12-816664-2.00009-8

Rhoads, Anthony, and Kin Fai Au. “PacBio Sequencing and Its Applications.” Genomics, Proteomics &amp; Bioinformatics, U.S. National Library of Medicine, Oct. 2015, www.ncbi.nlm.nih.gov/pmc/articles/PMC4678779/. 

Roberts, R. J., Carneiro, M. O., & Schatz, M. C. 2013, The advantages of SMRT sequencing. Genome Biology, 14(7), 405. https://doi.org/10.1186/gb-2013-14-7-405

“Sanger Sequencing.” NHS Choices, NHS, www.genomicseducation.hee.nhs.uk/genotes/knowledge-hub/sanger-sequencing/.

Single molecule real-time sequencing. 9 Jul. 2016, https://bitesizebio.com/28911/single-molecule-real-time-sequencing/

“SMRT Analysis Software.” PacBio, 30 Nov. 2023, www.pacb.com/products-and-services/analytical-software/smrt-analysis/.

