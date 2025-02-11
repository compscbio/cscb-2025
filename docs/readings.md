# Readings

Please try to read the first paper for each week. Other papers listed will be discussed in class and/or will be helpful for the homeworks. In cases where the Pubmed of the paper does not have links to OpenAccess versions of the paper, we will provide a pdf (requires being logged in to Hopkins SSO).

### Week 1: scRNA-seq data generation

1. [Macosko EZ, Basu A, Satija R, et al. Highly Parallel Genome-wide Expression Profiling of Individual Cells Using Nanoliter Droplets. Cell. 2015;161(5):1202-1214. doi:10.1016/j.cell.2015.05.002](https://pubmed.ncbi.nlm.nih.gov/26000488/)

2. [Zheng GX, Terry JM, Belgrader P, et al. Massively parallel digital transcriptional profiling of single cells. Nat Commun. 2017;8:14049. Published 2017 Jan 16. doi:10.1038/ncomms14049](https://pubmed.ncbi.nlm.nih.gov/28091601/)

### Week 2: scRNA-seq analysis

1. [Quality control](https://www.sc-best-practices.org/preprocessing_visualization/quality_control.html) sections: 6.0 - 6.3
2. [Normalization](https://www.sc-best-practices.org/preprocessing_visualization/normalization.html) section 7.0 - 7.1
3. [PCA](https://www.sc-best-practices.org/preprocessing_visualization/dimensionality_reduction.html) 9.0 - 9.1
4. [Clustering](https://www.sc-best-practices.org/cellular_structure/clustering.html) Whole chapter
5. [Manual cell typing](https://www.sc-best-practices.org/cellular_structure/annotation.html) 11.0 - 11.4
 

### Week 3: Integration and cell typing

#### Typing and integration methods
1. [Kiselev VY, Yiu A, Hemberg M. scmap: projection of single-cell RNA-seq data across data sets. Nat Methods. 2018 May;15(5):359-362. doi: 10.1038/nmeth.4644](https://pubmed.ncbi.nlm.nih.gov/29608555/)
2. [Polański K, Young MD, Miao Z, Meyer KB, Teichmann SA, Park JE. BBKNN: fast batch alignment of single cell transcriptomes. Bioinformatics. 2020 Feb 1;36(3):964-965. doi: 10.1093/bioinformatics/btz625](https://pubmed.ncbi.nlm.nih.gov/31400197/)
3. [Tan Y, Cahan P. SingleCellNet: A Computational Tool to Classify Single Cell RNA-Seq Data Across Platforms and Across Species. Cell Syst. 2019 Aug 28;9(2):207-213.e2. doi: 10.1016/j.cels.2019.06.004. Epub 2019 Jul 31](https://pubmed.ncbi.nlm.nih.gov/31377170/)
3. [Korsunsky I, Millard N, Fan J, Slowikowski K, Zhang F, Wei K, Baglaenko Y, Brenner M, Loh PR, Raychaudhuri S. Fast, sensitive and accurate integration of single-cell data with Harmony. Nat Methods. 2019 Dec;16(12):1289-1296. doi: 10.1038/s41592-019-0619-0](https://pubmed.ncbi.nlm.nih.gov/31740819/)

#### Benchmarking studes
1. [Tran HTN, Ang KS, Chevrier M, Zhang X, Lee NYS, Goh M, Chen J. A benchmark of batch-effect correction methods for single-cell RNA sequencing data. Genome Biol. 2020 Jan 16;21(1):12. doi: 10.1186/s13059-019-1850-9](https://pubmed.ncbi.nlm.nih.gov/31948481/)
2. [Kang JB, Nathan A, Weinand K, Zhang F, Millard N, Rumker L, Moody DB, Korsunsky I, Raychaudhuri S. Efficient and precise single-cell reference atlas mapping with Symphony. Nat Commun. 2021 Oct 7;12(1):5890. doi: 10.1038/s41467-021-25957-x](https://pubmed.ncbi.nlm.nih.gov/34620862/)
3. [Open problems in Single-cell analysis](https://openproblems.bio/results/)


### Week 4: Trajectory inference

!!! tip "Read the Monocle paper"
    
    Be sure to read the Monocle paper (#1 below) as it introduces all of the major concepts related to TI and pseudotime.

#### Methods
1. [Trapnell C, Cacchiarelli D, Grimsby J, Pokharel P, Li S, Morse M, Lennon NJ, Livak KJ, Mikkelsen TS, Rinn JL. The dynamics and regulators of cell fate decisions are revealed by pseudotemporal ordering of single cells. Nat Biotechnol. 2014 Apr;32(4):381-386. doi: 10.1038/nbt.2859. Epub 2014 Mar 23.](https://pubmed.ncbi.nlm.nih.gov/24658644/)
2. [Faure L, Soldatov R, Kharchenko PV, Adameyko I. scFates: a scalable python package for advanced pseudotime and bifurcation analysis from single-cell data. Bioinformatics. 2023 Jan 1;39(1):btac746. doi: 10.1093/bioinformatics/btac746.](https://pubmed.ncbi.nlm.nih.gov/36394263/)
3. [Street K, Risso D, Fletcher RB, Das D, Ngai J, Yosef N, Purdom E, Dudoit S. Slingshot: cell lineage and pseudotime inference for single-cell transcriptomics. BMC Genomics. 2018 Jun 19;19(1):477. doi:10.1186/s12864-018-4772-0.](https://pubmed.ncbi.nlm.nih.gov/29914354/)

#### Benchmarking
1. [Saelens W, Cannoodt R, Todorov H, Saeys Y. A comparison of single-cell trajectory inference methods. Nat Biotechnol. 2019 May;37(5):547-554. doi: 10.1038/s41587-019-0071-9. Epub 2019 Apr 1. PMID: 30936559.](https://pubmed.ncbi.nlm.nih.gov/30936559/)


#### Week 5: Cell fate potency and 'stemness' (Feb 25th/27th)

Paper #1 is describes CytoTRACE. Prioritize this paper.

1. [Gulati GS, Sikandar SS, Wesche DJ, Manjunath A, Bharadwaj A, Berger MJ,
Ilagan F, Kuo AH, Hsieh RW, Cai S, Zabala M, Scheeren FA, Lobo NA, Qian D, Yu
FB, Dirbas FM, Clarke MF, Newman AM. Single-cell transcriptional diversity is a
hallmark of developmental potential. Science. 2020 Jan 24;367(6476):405-411.
doi: 10.1126/science.aax0249. PMID: 31974247; PMCID: PMC7694873.](https://pubmed.ncbi.nlm.nih.gov/31974247/)
2. [Teschendorff AE, Maity AK, Hu X, Weiyan C, Lechner M. Ultra-fast scalable
estimation of single-cell differentiation potency from scRNA-Seq data.
Bioinformatics. 2021 Jul 12;37(11):1528-1534. doi:
10.1093/bioinformatics/btaa987. PMID: 33244588; PMCID: PMC8275983.](https://pubmed.ncbi.nlm.nih.gov/33244588/)
3. [Noller K, Cahan P. Cell cycle expression heterogeneity predicts degree of
differentiation. Brief Bioinform. 2024 Sep 23;25(6):bbae536. doi:
10.1093/bib/bbae536. PMID: 39446193; PMCID: PMC11500603.](https://pubmed.ncbi.nlm.nih.gov/39446193/)


#### Week 6: 
