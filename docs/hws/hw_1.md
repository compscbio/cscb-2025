# Homework 1


!!!warning "**Homework 1: Fundamentals of scRNA-seq analysis in Python**"

    Deadline: Friday, Feb 7th 2025 11:59pm


### Background
We discussed hematopoiesis and the types of cells found in peripheral blood mononuclear cells (PBMCs) during Lectures 3-4. We also walked through the analysis of a human PBMC scRNA-seq data set, from CellRanger output to a cleaned anndata object decorated with cell type annotations for each cell. In this homework, you are going to explore what scRNA-seq tells us about PBMC cell type composition, and you are going to explore the impact of varying steps in the analysis pipeline on your estimate of cell type composition.

!!!example "Cell type composition"

    You should think about and compute _Cell type composition_ relative to the total number of cells sampled. For example, after you perform QC on Sample 1, maybe your anndata object has 10,000 cells. Downstream analysis (i.e. all the steps from filtering to annotation) results in 7500 cells labeled as 'T cell'. In this case, the T cell fraction of the cell composition is 75%.

#### Cell types in PBMCs and their distinctive genes
##### Composition, as claimed in [literature](https://www.frontiersin.org/articles/10.3389/fmolb.2017.00096/)
- T cell: 70%
- B cell: 15%
- Natural killer (NK) cells: 10%
- Monocyte: 5%
- Dendritic cells: 1%
##### Marker genes
###### Monocytes
- LYZ (Lysozyme), CD14, CD68
- sub-types:
	- Classical:  CD14, LYZ, S100A8/S100A9, CCR2
	- Intermediate: FCGR3A (CD16), CD163, IL1B
	- non-classical: CX3CR1, FCGR3A (CD16), CCR5
###### NK cell
- NCAM1 , KIR2DL1, KIR2DL3, KIR2DL4, KIR3DL1, KIR3DL2, NKG2A/C/E (KLRC1/KLRC2/KLRC3), NKG2D (KLRK1), GNLY, GZMB
- Note that some are also expressed by subsets of T cell
###### B cell
- CD19, CD79A, CD79B, CD20
- Will leave sub-type exploration to student
###### T cell
- CD3D, CD3E, CD3G
- Will leave sub-type exploration to student
###### Dendritic cell
- FLT3, CD11C CD1C
- CD123 & CLEC4C  (plasmacytoid dendritic cell)
###### Granulocytes and Megakaryocytes
- were not widely recognized as occupying PBMC
- If student suspects they may then they should identify and include makers thereof in their analysis.
### Data
#### Sample 1
This is the same Sample 1 as we used in Lecture 4. Here are some more details:
- 10k PBMCs from a Healthy Donor (v3 chemistry) Single Cell Gene Expression Dataset by Cell Ranger 3.0.0
- Peripheral blood mononuclear cells (PBMCs) from a healthy donor (the same cells were used to generate pbmc\_1k\_v2, pbmc\_10k\_v3). PBMCs are primary cells with relatively small amounts of RNA (~1pg RNA/cell).
- 11,769 cells detected by CellRanger
- Sequenced on Illumina NovaSeq with approximately 54,000 reads per cell
- [10X Genomics web page for this data](https://www.10xgenomics.com/resources/datasets/10-k-pbm-cs-from-a-healthy-donor-v-3-chemistry-3-standard-3-0-0)
- URL to h5 file: https://cf.10xgenomics.com/samples/cell-exp/3.0.0/pbmc_10k_v3/pbmc_10k_v3_filtered_feature_bc_matrix.h5
- file name: pbmc\_10k\_v3\_filtered\_feature\_bc\_matrix.h5

!!!info "Your mission"

	Analyze the provided data to address the questions listed below


1. **What is the cell type composition of PBMCs of Sample 1?**

	Deliverables:

	- [ ] new .obs column indicating cell type
	- [ ] appropriate visualization (i.e. UMAP with clusters labeled, supported by dotplot that shows exwpression of marker genes)

2. **How does this estimate of cell composition compare to prior literature?**
	To evaluate this rapidly and efficiently, write a function that will take a list of anndata objects that have cell annotations, and produces stacked barplot figure, one bar for scRNAseq, one for proportions from literature. each rectangle in a bar reflects % of sample annotated as cell type X.

	Deliverables:

	- [ ] The function definition
	- [ ] Use of the function to produce the stacked boxplot that shows the cell type proportions from scRNAseq and from literature

3. **What are the transcriptional signatures of each of the PBMC cell types?** We know about some genes that are preferentially expressed in each PBMC cell type (in fact, you used some of these to perform cluster annotation). But one of the benefits of performing genome-wide analyses is that it can identify genes previously unlinked to the phenomenon under study. Your task here is to identify all genes that are preferentially expressed in each PBMC cell type. 

	Deliverables:

	- [ ] One list per cell type containing genes defined by the student as 'preferentially  expressed' in the corresponding cell type.
	- [ ] Visualization: dot plot showing expression and % cells expressed of the top X genes per cell type

!!!success "**ALL SUBMISSIONS MUST...**"

	... include _all_ code necessary to replicate the results, and must adhere to posted guidelines for code documentation, cogent written reports, and meaningful figures.


