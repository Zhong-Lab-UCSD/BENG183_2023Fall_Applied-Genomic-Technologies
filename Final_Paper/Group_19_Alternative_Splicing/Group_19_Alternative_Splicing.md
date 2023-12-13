# Alternative Splicing

## Done by: Anthony Vasquez, Omar Halawa, Yasmin Jaber

# Table of Contents 
- [Overview](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/omar-part/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#overview)
- [Alternative Splicing in RNA-Seq Alignment](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/omar-part/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Alternative-Splicing-in-RNA-Seq-Alignment)
  - [Paired-End Alignment](https://github.com/kaiakamatsu/BENG183-Classification/blob/main/Classification.md#Paired-End-Alignment)
  - [Splice-Aware Alignment](https://github.com/kaiakamatsu/BENG183-Classification/blob/main/Classification.md#Splice-Aware-Alignment)
  - [Popular Tools](https://github.com/kaiakamatsu/BENG183-Classification/blob/main/Classification.md#Popular-Tools)
- [Alternative Splicing in Disease and Therapy](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/omar-part/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Alternative-Splicing-in-Disease-and-Therapy)
- [Future Directions](https://github.com/pavasquez1/BENG183_2023Fall_Applied-Genomic-Technologies/blob/omar-part/Final_Paper/Group_19_Alternative_Splicing/Group_19_Alternative_Splicing.md#Future-Directions)

# Overview

Alternative splicing is a mechanism that produces multiple mRNA isoforms from the same gene. These isoforms are then translated into functionally different proteins. 

![altsplice](https://upload.wikimedia.org/wikipedia/commons/0/0a/DNA_alternative_splicing.gif)

Outside of constitutive splicing (normal splicing) there are five types of alternative splicing: 
1. Exon skipping
2. Intron retention
3. Alternative 3' splice site
4. Alternative 5' splice site
5. Mutually exclusive exons

![altsplicetypes](https://www.mdpi.com/ijms/ijms-22-04468/article_deploy/html/images/ijms-22-04468-g001.png)


# Alternative Splicing in RNA-Seq Alignment
As discussed in the previous section, RNA-seq is arguably the most important technology when it comes to identifying (and helping quantify the rates of) protein isoforms present in our samples. This is simply due to the fact that:
<ol>
  <li>Obtaining the mature mRNA transcripts via RNA-seq exposes all of the transcriptomic diversity of alternative splicing.</li>
  <li>These resulting transcripts eventually get translated into the various protein isoforms.</li>
</ol>
Therefore, performing RNA-seq and analyzing the resulting transcriptome and the variation that exists in it provides a comprehensive overview of the presence and effects of alternative splicing.


## Paired-End Alignment
Before we get into the specifics of post-sequencing alignment with regards to alternative splicing, and in order for us to better understand the upcoming figures, we need to first examine one aspect of the design of our RNA-seq experiment. As per [Illumina's recommendation](https://www.illumina.com/science/technology/next-generation-sequencing/plan-experiments/paired-end-vs-single-read.html), **paired-end sequencing** (as shown below) is the preferred choice over single-end sequencing as it provides higher quality alignment through being better-suited to identify relative positions of reads with the paired ends of fragments. This is also why, for many sequencing experiments that revolve around studying structural rearrangements, paired-end sequencing is used.  

![altsplicetypes](https://www.ebi.ac.uk/training/online/courses/functional-genomics-ii-common-technologies-and-data-analysis-methods/wp-content/uploads/sites/70/2020/05/Figure17.png)

## Splice-Aware Alignment

## Popular Tools

# Alternative Splicing in Disease and Therapy

# Future Directions
