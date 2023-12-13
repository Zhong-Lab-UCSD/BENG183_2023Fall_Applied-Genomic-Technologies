# BENG 183 Final Paper

### Contents
  - **[scRNA-sequencing and Imaging Spatial transcriptomics](#231)**
  - **[Pros and Cons](#2)**
  - **[Similarities and differences](#3)**
  - **[Real-world Uses](#4)**
  - **[Sources](#5)**


### scRNA-sequencing and Spatial Transcriptomics<a name="231"></a>
* **scRNA**:
  * **Background**:
    Single cell RNA sequencing (scRNA-seq) is a recent development in genomic analysis introduced by Tang et al. in 2009. Single cell RNA sequecing allows scientists to analyze the genomes/transcriptomes of individual cells at a high-resolution which opens doors in understanding more about cellular function and heterogeneity, cell population and subpopulation identification, etc. Being a highly sensitive ultra-low-input method, scRNA-seq is able to capture more information when other methods would consider it as "noise." Tools that are most commonly used for scRNA-seq analysis would be Scanpy (Python) and Seurat (R) both offer similar functions in preprocessing, clustering, quality control, visualization, identification of cell types, and many more.
  * **Method**: scRNA-seq follows the workflow as shown below. First tissue preparation followed by the isolation of the cells capturing the single cells. Each cell is then wrapped with unique molecular identifiers inside a nanoscale droplet to be then reverse transcribed into cDNA. This newly transcribed cDNA is then amplified to be sequenced and then analyzed using tools like scanpy and seurat. Illumina's video explains this workflow very clearly [Single-cell Sequencing and Analysis Workflow](https://www.youtube.com/watch?v=CVaSHbQg-P8&ab_channel=Illumina)
  * ![image](https://github.com/JungTzen/beng183_final_paper/assets/83424119/8094f912-87eb-479c-81a7-4dbd39dcb82e)
  * **Tools**: Scanpy (Python Library) and Seurat (R Package) and work interchangeably but using either Python or R can provide access to different workflows and libraries/packages that can enhance your scRNA-seq analysis. For example, using Scanpy can open doors for machine learning integration due to the Python programming language while Seurat is often used in most labs due to its statistical tools and many scientists' familiarity with the R programming language. Both give access to scientists to computionally analyze their samples after being sequenced through visualizing (t-SNE and UMAP plots), clustering, preprocessing, and interpretation of the single cellular data.

* **Imaging Spatial Transcriptomics**: 
  * **Background**:
    Spatial transcriptomics is a molecular profiling method used to help scientists measure gene activity in tissue and map where the activity occurs at. The tool we will be focusing on will be MERFISH (Multiplexed error-robust fluorescence in situ hybridization) which is a very popular tool for handling spatial transcriptomics. MERFISH (Multiplexed Error-Robust Fluorescence In Situ Hybridization) is a spatially resolved single-cell transcriptome profiling technology that enables the visualization and counting of a large number of RNA transcripts from hundreds to tens of thousands of genes across tissue slices with single-cell resolution. 
  * **Method**:
    ![image](https://cdn-jcodf.nitrocdn.com/YbAKvIzVYiimMHgpqGPSKkpjKgpcVgmj/assets/images/optimized/rev-feddd4c/vizgen.com/wp-content/uploads/2022/10/MERFISH-Technology-OverView.png.webp)
     MERFISH is based on single-molecule FISH (Fluorescence In Situ Hybridization), where fluorescently labeled probes bind to the desired RNA targets with high specificity, allowing the direct counting of the number of fluorescent spots under a high-resolution microscope to quantify RNA expression. Combinatorial labeling, sequential imaging, and error-robust barcoding are added to single-molecule FISH by MERFISH, which significantly boosts multiplexing capacity and makes spatially resolved, single-cell gene expression profiling possible.
   ![image](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41467-023-39447-9/MediaObjects/41467_2023_39447_Fig1_HTML.png) The multiplexing capability is significantly increased by creating a distinct binary barcode for each targeted gene through successive imaging rounds. Furthermore, the barcoding system is built with error resilience to guarantee precise and reliable outcomes.[Video Explanation](https://youtu.be/O0QekKSscjA)
  * **Tools**:
    MERFISH data generated on the MERSCOPE is compatible with third-party software such as Scanpy/Squidpy, Seurat, Voyager, and Giotto, which are already integrated into many existing single-cell analysis workstreams. Plotting packages such as matplotlib can also be used to plot the spatial data.


### Pros and Cons<a name="2"></a>
* **scRNA-seq** <br>
  * **Pros**:
    * **Widely-Used**: scRNA-seq is widely-used technique in the field of biology and due to this there is a plenthora of resources, forums, and extensive databases/tools to support single cell research.
    * **Versatility**: scRNA-seq can be used in a multitude of research which we discussed some fields of research here: **[Real-world Uses](#4)**. Aside from that, this technology is applicable to a range of cells from tissue, cultured cells, blood, etc. 
    * **Efficiency (More genes per sequence)**: When compared to spatial transcriptomics, scRNA-seq can sequence thousands of genes per cell and provide information on cells that can missed by bulk RNA sequencing or spatial transcriptomics which are limited due to its sampling size (either too much or too little)
    * **Higher Resolution Compared to Bulk-RNA Sequencing**: Due to scRNA-seq's high sensitivity, it offers higher resolution on samples that are usually disregarded by bulk sampling methods as "noise".
  * **Cons**:
    * **Lack of Spatial Information**: Due to the limitation of single cell analysis, it doesn't capture the spatial context of cells within tissue samples which is used to understand cellular functions and interactions. This is why scRNA-seq and spatial transcriptomics can work hand and hand.
    * **Data Integration challenges**: Analyzing single cell RNA-sequenced data usually requires a comprehensive understanding on bioinformatic tools and data structures as it is more complex than bulk RNA-seq data including the reads, unique molecular identifiers (UMIs), quality scores, cell barcodes, etc. 
    * **Gene dropout due to technical limitations**: There are many reasons as to what can lead to gene dropout rates increases in scRNA-seq. Due to its workflow, the dropout could occur because of the low RNA content, amplification bias, and sequencing depth. The poor gene detection could later complicate data analysis and interpretation.
    * **Lower resolution**: When comparing resolution with technologies like spatial transcriptomics and ATAC-seq, scRNA-seq yields lower resolution which impacts interpretation of other aspects of the cell. 

* **Spatial Transcriptomics** <br>
  * **Pros**:
    * **High Spatial Resolution**: MERFISH offers high spatial resolution, allowing the visualization and counting of a large number of RNA transcripts from hundreds to tens of thousands of genes across tissue slices with single-cell resolution
      
    * **High Throughput**: The technology enables the simultaneous measurement of the copy number and spatial distribution of hundreds to tens of thousands of RNA species in individual cells, offering high throughput capabilities
      
    * **High Sensitivity**: MERFISH provides high sensitivity, allowing for the accurate measurement of the copy number and spatial distribution of RNA species in single cells
      
    * **High Multiplexing Power**: It offers high multiplexing power, allowing for the visualization and counting of a large number of RNA transcripts from hundreds to tens of thousands of genes across tissue slices with single-cell resolution

  * **Cons**:
    * **Specialized Equipment & High Cost**: MERFISH requires special imaging and amplification setups, making it relatively expensive and potentially inaccessible to some researchers
      
    * **Imaging Time**: The technique's imaging time is a significant portion of the total time required to perform a MERFISH measurement

### Similarities and Differences<a name="3"></a>
* **Similarities**
  * **Gene expression analysis**:Both single-cell RNA sequencing (scRNA-seq) and MERFISH are used for gene expression analysis at the single-cell level, providing insights into the transcriptional profiles of individual cells

  * **Single-cell resolution**: Both technologies offer single-cell resolution, allowing the study of gene expression at the individual cell level, which is essential for understanding cellular heterogeneity and function within complex tissues

  * **quantitative gene expression measurement**:  Both scRNA-seq and MERFISH enable the quantitative measurement of gene expression at the single-cell level, providing valuable information about the abundance of specific RNA transcripts within individual cells.

* **Differences**
  * **Methodologies**
    * scRNA-seq: Involves isolating RNA from single cells, converting it to cDNA, sequencing 
    * MERFISH: Uses spatially barcoded oligos/probes to capture spatial information by imaging tissue sections or samples 
  * **MERFISH has additional Spatial Data**: Unlike scRNA-seq, MERFISH provides spatially resolved gene expression data, allowing the visualization and counting of RNA transcripts with spatial information, which is crucial for understanding the spatial organization of gene expression within tissues
  * **Use cases**: scRNA-seq and MERFISH have different use cases and are often chosen based on the specific research questions and the need for spatial information in gene expression analysis
  * **Gene Dropout Rates**: MERFISH has been shown to have improvements in overall gene dropout rates and sensitivity compared to scRNA-seq, which is an important consideration when choosing the appropriate technology for specific research applications


### Real World Uses <a name="4"></a>
By integrating scRNA-seq and spatial transcriptomics, researchers can gain a more holistic understanding of biological systems, combining the depth of single-cell analysis with the critical context of spatial distribution.

**Advanced Cancer Research:**
![image](https://github.com/JungTzen/beng183_final_paper/assets/114448991/3e8ac81f-f979-47ba-ab77-34832189ad6d)

Spatial Transcriptomics has been incredibly helpful in understanding the spatial heterogeneity of tumors. It has helped us characterize tertiary lymphoid structures, also known as TLSs which are formations at sites with persistent inflamatory stimiluation (like tumors). By using ST scientists have able to understand the spatial organization of immune cells and thier role in anti-tumor responses. On the flip side of the coin, RNA-seq helps us understand the gene expression profiles of cancel cells which further helps us in our understanding of molecular mechanisms driving cancer progression. 

**Developmental biology:**
![image](https://github.com/JungTzen/beng183_final_paper/assets/114448991/469f47b3-d714-472a-93a6-bcc33d651b9d)

Development biology spans many different specific subfields of biology (both from an anatomical view or a disease-centric view). Spatial transcriptomics serves as a valuable tool in furthering our understanding of this field as  it provides a visual/spatial view of how tissues and cells change over the course of development. ST helps in understanding how different cells contribute to the growth and formation of comlplex biological structures. This is an incredible tool which enhances the prelimainary genetic compository information that RNA-seq provides. 

**Drug Development and Response Monitoring:**
![image](https://github.com/JungTzen/beng183_final_paper/assets/114448991/b7cca785-769b-4604-9b14-c050ae7efa2f)

Regarding drug development and responnse monitoring, spatial transcriptomics has played a vital role in understand the spatial heterogenity of dru responses at the cellular level. An example of ths is the graph-based domain adoption model called SpaRx. This model uses pharmacogenomics profiles to interpret single-cell spatial transcriptomics data. Ultimately, the model allows scientists to identify spatially localized cellular resistance and hence optimize treatment for individual patients. SpaRx has demonstrated high accuracy in characterizing spatial therapeutic variability, uncovering the molecular mechanisms underpinning drug resistance, and identifying personalized drug targets and effective drug combinations​. RNA sequencing also plays a crucial role in identifiyign drug targets and understnad the molecular mechanisms behind the interactions of drugs.

**Immunological Research:**
![image](https://github.com/JungTzen/beng183_final_paper/assets/114448991/36242078-4d0e-4f95-a23f-388119cb9877)

Spatial transcriptomics helps us map the spatial distribution of immune cells in tissues and understand thier interactions relating to immune responses. Interestingly, many of ST's contributions to immunological research can be connected to cancer biology. An example of this is how ST was used to understand melanoma in a zebrafish model. The researchers focused on BRAF V600E-driven melanomas, utilizing ST to capture the complex spatial patterns within the tumor and its interaction with various surrounding tissues. The study highlighted the transcriptional distinctiveness of the tumor-microenvironment interface, a crucial area for understanding tumor invasion and growth. 

### Sources <a name="5"></a>
* Hunter, M.V., Moncada, R., Weiss, J.M. et al. Spatially resolved transcriptomics reveals the architecture of the tumor-microenvironment interface. Nat Commun 12, 6278 (2021). https://doi.org/10.1038/s41467-021-26614-z
* Jovic D, Liang X, Zeng H, Lin L, Xu F, Luo Y. Single-cell RNA sequencing technologies and applications: A brief overview. Clin Transl Med. 2022 Mar;12(3):e694. doi: 10.1002/ctm2.694. PMID: 35352511; PMCID: PMC8964935.
* Chen G, Ning B, Shi T. Single-Cell RNA-Seq Technologies and Related Computational Data Analysis. Front Genet. 2019 Apr 5;10:317. doi: 10.3389/fgene.2019.00317. PMID: 31024627; PMCID: PMC6460256.
* https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8964935/figure/ctm2694-fig-0002/
* https://learn.gencore.bio.nyu.edu/single-cell-rnaseq/
* https://encyclopedia.pub/entry/24618
* https://www.illumina.com/techniques/sequencing/rna-sequencing/ultra-low-input-single-cell-rna-seq.html
* Jeffrey R. Moffitt et al.,Molecular, spatial, and functional single-cell profiling of the hypothalamic preoptic region.Science362,eaau5324(2018).DOI:10.1126/science.aau5324
* https://www.hhmi.org/news/new-method-allows-precise-measurement-transcriptome-single-cells
* Mantri, Madhav & Scuderi, Gaetano & Abedini-Nassab, Roozbeh & Wang, Michael & McKellar, David & Shi, Hao & Grodner, Benjamin & Butcher, Jonathan & de vlaminck, Iwijn. (2021). Spatiotemporal single-cell RNA sequencing of developing chicken hearts identifies interplay between cellular differentiation and morphogenesis. Nature Communications. 12. 10.1038/s41467-021-21892-z.
* Park, Y.M., Lin, DC. Moving closer towards a comprehensive view of tumor biology and microarchitecture using spatial transcriptomics. Nat Commun 14, 7017 (2023). https://doi.org/10.1038/s41467-023-42960-6
* https://www.genengnews.com/sponsored/getting-hooked-on-merfish-a-core-labs-journey-into-spatial-genomics/
* Tang Z, Liu X, Li Z, Zhang T, Yang B, Su J, Song Q. SpaRx: Elucidate single-cell spatial heterogeneity of drug responses for personalized treatment. bioRxiv [Preprint]. 2023 Aug 6:2023.08.03.551911. doi: 10.1101/2023.08.03.551911. Update in: Brief Bioinform. 2023 Sep 22;24(6): PMID: 37577665; PMCID: PMC10418183.
* Xiaoyu Wei et al.,Single-cell Stereo-seq reveals induced progenitor cells involved in axolotl brain regeneration.Science377,eabp9444(2022).DOI:10.1126/science.abp9444
* https://genomemedicine.biomedcentral.com/articles/10.1186/s13073-022-01075-1
* https://vizgen.com/technology/
* https://www.illumina.com/techniques/sequencing/rna-sequencing/ultra-low-input-single-cell-rna-seq.html
* IMAGE: https://www.google.com/url?sa=i&url=https%3A%2F%2Fphys.org%2Fnews%2F2023-11-exploring-spatial-transcriptomics-biomedical.html&psig=AOvVaw16kzYM56r_CDc_bL-ezgm3&ust=1702250420533000&source=images&cd=vfe&opi=89978449&ved=0CBIQjRxqFwoTCOCCoI-_g4MDFQAAAAAdAAAAABAD
* https://vizgen.com/resources/how-merfish-technology-works/
* https://vizgen.com/technology/
* IMAGE: https://cdn-jcodf.nitrocdn.com/YbAKvIzVYiimMHgpqGPSKkpjKgpcVgmj/assets/images/optimized/rev-feddd4c/vizgen.com/wp-content/uploads/2022/10/MERFISH-Technology-OverView.png.webp
* https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.nature.com%2Farticles%2Fs41467-023-39447-9&psig=AOvVaw3ygZBpSsTPcIcdX3FF6yWq&ust=1702352938070000&source=images&cd=vfe&opi=89978449&ved=0CBIQjRxqFwoTCPi87IO9hoMDFQAAAAAdAAAAABAJ
* https://vizgen.com/developing-spatial-transcriptomics-data-analysis-solutions-to-empower-researchers/
* https://www.sciencedirect.com/science/article/pii/S0888754323001155
* https://www.nature.com/articles/s41598-019-43943-8
* https://www.life-science-alliance.org/content/6/1/e202201701
