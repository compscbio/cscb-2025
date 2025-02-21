# Homework 3

!!!warning "**The Mandocellorian**: *This is the way (to cell typing)*"

    The overall goal of this homework is for you to gain a sophisticated understanding of these 'cell-typing' techniques and their relative merits in the context of cell fate engineering.

    **Deadline: Monday, March 3rd 2025 11:59pm**


### Background

![mando](img/mandocellorian.jpg){ align=right width=300 }

We have discussed different approaches for determining the identity of cells in scRNAseq data, including:

1. <u>Manual annotation</u> by identifying known marker occurrence in clusters. Sometimes referred to as 'cluster-then-annotate'[^1]
2. <u>Integration</u> with a reference data set for which cell annotations have been determined[^2]
3. Applying a <u>classifier</u> that has been trained on a reference data set[^3]

We have provided three scRNAseq data sets as described in the 'Data' section below. You will use these data and the 3 cell-typing approaches (i.e. 'cluster-then-annotate', BKKNN, and PySingleCellNet) to address the questions listed below. 

A bit of important background: Cell fate engineering (e.g. directed differentiation, direct conversion, etc) frequently generates populations of cells that exhibit mixed identities. Let's call these <u>hybrids</u>. Unlike the Tooth Fairy, Easter Bunny, or Santa Claus, hybrids are real (sorry if that was a spoiler). Hybrids are not doublets. And hybrids are not frequently observed in physiological contexts. In other words, we do not see them in scRNA-seq atlases from nominally normal tissues. 

##### Question 1
How do manual annotation, classification, and integration compare in terms of accurately and sensitively predicting cell type identity? You should answer this by using each method to predict cell identities of the validation data. Select the best metric(s), compute these metrics for each method, and compare the results to answer the question.

##### Question 2
How do you think an ideal cell-typing method should handle hybrids? Discuss strategies for distinguishing true hybrids from doublets. The answer to this part does not require code or analysis. You just need to cogently describe your viewpoint. Keep in mind various <u>use cases</u>, such as application to cells from 'normal tissues', to cells from pathological contexts, and to cells derived via cell fate engineering.

##### Question 3
How well do the three cell-typing methods above perform when analyzing populations that include hybrids? To answer this question, you should

- Generate synthetic hybrids by summing or averaging the expression profiles of cells of different identities from the validation data. You should generate various hybrid populations based on the cell types mixed, and the proportion of each. You could even explore which genes to use rather than randomly sampling from all genes.

- Combine your new synthetic data that includes hybrids with the validation data to make a new validation data set

- Predict cell identity of the new validation data using all three cell-typing methods

- Compute prediction metrics of all three cell-typing methods

- Please characterize the types of failures that are common and unique to each method and discuss how these failures could impact the analysis of real engineered cell


##### Question 4
How does transplantation affect engineered pancreatic-like cells? More specifically:

- Does the proportion of cells of uncertain identity change?

- Do the proportion of cell types differ between transplanted and non-transplanted cells? If so, do you think that these differences reflect real biology or could they just reflect sampling variation?

- How does transplantation affect transcriptional state of the cell types? To answer this ...
	
	- Use the cell-type predictions of the query data from your preferred cell-typing method

	- For each cell type, perform differential gene expression analysis comparing transplanted vs non-transplanted cells of that cell type

		- What are the top 10 genes differentially expressed? Select a maximally informative and efficient visualization to show these genes and their expression patterns in the transplanted vs non-transplanted cells.

		- What biological processes or pathways distinguish the transplanted and non-transplanted cells? You should answer this by performing enrichment analysis. As above, select a maximally informative and efficient visualization to illustrate these pathways.

	- Are there shared genes across pancreatic cell types that are commonly dysregulated in un-transplanted versus transplanted cells? 


##### Extra-credit
Implement a function that computes a 'hybrid identity' score. Use this function to evaluate my assertion above that hybrid cells are not typically seen in normal contexts but are observed in engineered populations.

#### Data
The training and validation data sets are of human cadaver-derived pancreatic islet cells. The query data set is derived from pluripotent stem cells that have been engineered with the intention of producing insulin-producing beta cells. Some of the engineered cells were transplanted into mice and subsequently recovered to see how the in vivo environment impacted their identity. All scRNAseq data here was produced using the 10x platform. We have performed some data cleaning and trimming.

##### Training data[^4]
- Sorted human pancreatic islet cells from 3 donors
- raw counts
- cells QC-ed
- cell type annotation in .obs\['cell\_type'\]
- [h5ad: adTrain\_n110\_CSCB\_HW3.h5ad](https://jhu.instructure.com/files/13455166/download?download_frd=1)
##### Validation data[^5]
- pancreatic islets from 4 donors
- raw counts
- cells QC-ed
- cell type annotation in .obs\['cell\_type'\]
- [h5ad: adValidation\_n300\_CSCB\_HW3.h5ad](https://jhu.instructure.com/files/13455167/download?download_frd=1)
##### Query data[^6]
- Directed differentiation of hESCs and iPSCs towards beta-like cells (6 stage differentiation)
- transplanted into mouse kidney capsule, then cells subsequently recovered
- cells QC-ed and contaminating mouse cells removed
- raw counts
- [h5ad: adQuery\_n2000\_CSCB\_HW3.h5ad](https://jhu.instructure.com/files/13455164/download?download_frd=1)

##### Marker genes
Here are solid marker genes of the major cell types that you can expect to encounter in this HW:

``` py
marker_genes_dict = {
    'Acinar': ['PRSS2', 'REG1A'],
    'Ductal': ['MMP7', 'KRT19'],
    'Alpha': ['GCG', 'TTR', 'HIGD1A'],
    'Beta': ['INS', 'IAPP', "G6PC2"],
    'Delta': ['SST', 'RBP4', 'LEPR'],
    'Gamma': ['PPY', 'ID2', "GCNT3"],
    'Episilon': ["GHRL", "NNMT", "APOH"],
    'Macrophage': ['IFI30', 'LAPTM5'],
    'Mast': ['TPSB2', "PTPRC"],
    'Stellate': ['COL1A2', 'COL6A2'],
}
```




[^1]: Challenges in unsupervised clustering of single-cell RNA-seq data. Kiselev VY, Andrews TS, Hemberg M. Nat Rev Genet. 2019 May;20(5):273-282. doi: 10.1038/s41576-018-0088-9. [PMID: 30617341](https://pubmed.ncbi.nlm.nih.gov/30617341/)
[^2]: Benchmarking atlas-level data integration in single-cell genomics. Luecken MD, Büttner M, Chaichoompu K, Danese A, Interlandi M, Mueller MF, Strobl DC, Zappia L, Dugas M, Colomé-Tatché M, Theis FJ. Nat Methods. 2022 Jan;19(1):41-50. doi: 10.1038/s41592-021-01336-8. Epub 2021 Dec 23. [PMID: 34949812](https://pubmed.ncbi.nlm.nih.gov/34949812/)
[^3]: SingleCellNet: A Computational Tool to Classify Single Cell RNA-Seq Data Across Platforms and Across Species.Tan Y, Cahan P. Cell Syst. 2019 Aug 28;9(2):207-213.e2. doi: 10.1016/j.cels.2019.06.004. Epub 2019 Jul 31. [PMID: 31377170](https://pubmed.ncbi.nlm.nih.gov/31377170/)
[^4]: van Gurp L, Fodoulian L, Oropeza D, Furuyama K, Bru-Tari E, Vu AN, Kaddis JS, Rodríguez I, Thorel F, Herrera PL. Generation of human islet cell type-specific identity genesets. Nat Commun. 2022 Apr 19;13(1):2020. doi: 10.1038/s41467-022-29588-8. [PMID: 35440614](https://pubmed.ncbi.nlm.nih.gov/35440614/)
[^5]: Xin Y, Dominguez Gutierrez G, Okamoto H, Kim J, Lee AH, Adler C, Ni M, Yancopoulos GD, Murphy AJ, Gromada J. Pseudotime Ordering of Single Human β-Cells Reveals States of Insulin Production and Unfolded Protein Response. Diabetes. 2018 Sep;67(9):1783-1794. doi: 10.2337/db18-0365. Epub 2018 Jun 27. [PMID: 29950394](https://pubmed.ncbi.nlm.nih.gov/29950394/)
[^6]: Augsornworawat P, Maxwell KG, Velazco-Cruz L, Millman JR. Single-Cell Transcriptome Profiling Reveals β Cell Maturation in Stem Cell-Derived Islets after Transplantation. Cell Rep. 2020 Aug 25;32(8):108067. doi: 10.1016/j.celrep.2020.108067. Erratum in: Cell Rep. 2021 Mar 9;34(10):108850. [PMID: 32846125](https://pubmed.ncbi.nlm.nih.gov/32846125/)