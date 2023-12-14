# MAPPING RNA INTERACTOME IN VIVO (MARIO)

## 1.1 RNA-RNA INTERACTOME

### Background
The RNA-RNA interactome, as uncovered by Mapping RNA Interactome In Vivo (MARIO), plays a crucial role in unveiling the mysteries of non-coding sequences within the human genome. To this day, despite constituting the majority of our genetic material, non-coding sequences are still largely unexplored while certain elements like promoters and enhancers are contrastingly better understood.

### Different Types of RNA
To fully grasp the significance of the RNA-RNA interactome, it's essential to first understand ourselves the diverse landscape of RNA molecules.

One crucial RNA is tRNA. It holds a pivotal role in the process of translation. tRNA ensures the conversion of genetic information encoded in mRNA into functional proteins. By recognizing specific codons on mRNA, it can ferry the corresponding amino acids to the ribosome allowing protein synthesis to occur. The precision of tRNA-mRNA interactions is fundamental for the accurate translation of the genetic code.

Another crucial RNA is mRNA. It serves as the messenger that carries the genetic instructions that guide the synthesis of proteins during translation from the DNA in the nucleus to the ribosomes in the cytoplasm. Understanding the interactions involving mRNA, especially when tRNA is also involved, is important as it can unveil the mechanisms governing protein synthesis, a fundamental process for cellular function.

MicroRNAs, or miRNAs, constitute another class of small non-coding RNAs that play a crucial role in the post-transcriptional regulation of gene expression. Unlike the previous two RNAs, miRNAs do not code for proteins themselves but rather function as molecular regulators in the sense that they bind to specific mRNA targets and influence their stability and translation efficiency. The miRNA-mRNA interactions are crucial regulatory steps that impact cellular functions and responses.

### Significance of RNA-RNA interactome
This tool provides a systematic approach to decoding the functions embedded in non-coding sequences with a primary focus on two key interactions. These interactions are tRNA-mRNA and miRNA-mRNA. The former interaction (tRNA-mRNA) ensures the accurate translation of genetic instructions into proteins. This interaction is a fundamental process in protein synthesis. The latter interaction (miRNA-mRNA) involves microRNAs regulating gene expression by essentially acting as molecular regulators in the intricate dance of genetic processes and expression.

The RNA-RNA interactome essentially serves as a valuable means to understand the functional significance of often overlooked non-coding sequences. MARIO is crucial in this regard in the sense that it facilitates this exploration, offering researchers insights into the roles of these genomic regions in cellular processes. This tool effectively acts as a bridge by helping connect the gaps in our knowledge and enabling researchers to gain a more comprehensive understanding of the non-coding genome.

Moreover, the RNA-RNA interactome has implications beyond basic biological understanding. With the ability to identify and characterize specific RNA interactions, it opens avenues for researchers to potentially target key players in disease pathways. This knowledge could eventually pave the way for developing RNA-based therapeutics that modulate gene expression, offering a potential avenue for precision medicine.

## 1.2 MAPPING PROCEDURE

### Mapping Strategy
Due to the difficulties of studying the complexities of the RNA-RNA interactome, a new technology is required to gain useful data. Mapping RNA Interactome in Vivo (MARIO) is an innovative strategy that aims to convert RNA-RNA interactions into cDNA, which is much easier to qualitatively and quantitatively sequence and analyze.

### Overall Procedure
While the individual steps of MARIO can become rather complex, the overall procedure of the technology can be summarized into eight steps (Nguyen et al. 2016):
1. Cross-linking RNAs to proteins
2. RNA fragmentation, protein denaturing, and biotinylation
3. Immobilization of RNA-binding proteins at low density
4. Ligation of a biotinylated RNA linker
5. Proximity ligation under a dilute condition
6. RNA purification and reverse transcription
7. Biotin pull-down
8. Construction of the sequencing library


Figure 1. MARIO technology diagram depicting the key experimental steps in the overall procedure (Nguyen et al. 2016)

### Cross-Linking RNAs To Proteins
In the first step, RNAs are cross-linked to the proteins they interact with using ultraviolet radiation. Using ultraviolet radiation helps induce the formation of covalent bonds between the nucleotides in the RNAs and the amino acids in the proteins. The cross-linked complexes are also used to generate a MARIO library to further record RNA-protein interactions.

### RNA Fragmentation, Protein Denaturing, And Biotinylation
In the second step, three processes must occur. The first step, RNA fragmentation, is the process of digesting the RNA into smaller fragments. For MARIO, researchers used a ribonuclease called RNase I to digest the RNA. The second step, protein denaturing, is the process of using chemical agents like to remove the unbound proteins. The third step, biotinylation, is the process of adding biotin to the cysteine residues in the cross-linked RNAs, which aids in the purification process later on in the procedure.

### Immobilization Of RNA-Binding Proteins At Low Density
In the third step, the cross-linked protein-RNA complexes are immobilized on streptavidin-coated beads at a low bead surface density. Streptavidin is used to immobilize the complexes that have been successfully tagged via biotinylation of cysteine residues. The remaining mobile complexes can then be flushed out using a washing buffer to result in a product of isolated, biotinylated protein-RNA complexes.

### Ligation Of A Biotinylated RNA Linker
In the fourth step, a biotin-tagged RNA linker is attached to the 5’ end of the RNA. This linker (with sequence 5′- rCrUrArG/iBiodT/rArGrCrCrCrArUrGrCrArArUrG rCrGrArGrGrA -3′) serves as a selection marker to help purify the ligated RNAs. Similar to the process of biotinylation, the unmarked RNA-protein complexes can then be flushed using washing buffers to isolate the remaining complexes with successful RNA linker ligation.

### Proximity Ligation Under A Dilute Condition
In the fifth step, the biotinylated RNA linker helps guide interacting RNA molecules towards one another. This process (known as proximity ligation) helps bind and stabilize proximity-based RNA interactions, which are essential for studying the RNA-RNA interactome.

### RNA Purification And Reverse Transcription
In the sixth step, the process of purifying the RNA and converting the interactions to DNA can occur. To purify the protein-RNA complexes, an elution buffer is used to remove the complexes from the low density streptavidin beads. The RNA is then extracted using centrifugation and precipitation, resulting in an RNA pellet containing a mixture of RNA molecules with and without linkers. The RNA is then treated with a variety of agents to remove biotin, genomic DNA, rRNAs, and other contaminants to finish the purification process. From the purified RNA, reverse transcription is used to synthesize cDNA, which stores information from the RNA-RNA interactome.

### Biotin Pull-Down
In the seventh step, a process called streptavidin-biotin affinity purification is used to select for the target RNA-DNA hybrids. This pull-down ensures that a majority of the sequencing read pairs contain the RNA-linker targets for analysis.

### Construction Of The Sequencing Library
In the eighth step, the sequencing library is generated from the cDNA representing the RNA-RNA interactions. First, the cDNA is circularized to avoid dealing with reverse transcription stalls, a common strategy for constructing sequencing libraries from cDNA. Next, the cDNA is relinearized and amplified using PCR. The now single-stranded cDNA is selected based on size using gel electrophoresis. After this step, the cDNA has been purified and can be amplified again using PCR to generate the final sequencing library.

### Computational Pipeline
After the sequencing library has been generated, the data can be analyzed using the MARIO tools package, which can be used with Python or R (full documentation available at https://mariotools.ucsd.edu/). The computational pipeline uses sequencing reads as an input, and outputs the cDNA library, genomic locations of the cDNA’s respective RNAs, and the inferred RNA interactions from the cDNA. The various tools in the package help provide a variety of computational functions to analyze the MARIO data:
* RNA interaction site binding energy calculation
* RNA interaction site conservation level calculation
* Read pair detection
* RNA folding and secondary structure prediction