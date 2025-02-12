# Homework 2


!!!warning "**Homework 2: Parameter Parcheesi**"

    Deadline: Tuesday, Feb 18th 2025 11:59pm

### Background
This homework will ask you to to explore the impact of varying steps in the scRNA-seq analysis pipeline (as applied in HW1) on your estimate of cell type composition.

!!!attention "**Data**"

    We are using data from HW1 as well as a few more PBMC samples.

### Data
#### Sample 1
This is the same Sample 1 as we used in Lecture 4. Here are some more details:

- 10k PBMCs from a Healthy Donor (v3 chemistry) Single Cell Gene Expression Dataset by Cell Ranger 3.0.0
- Peripheral blood mononuclear cells (PBMCs) from a healthy donor (the same cells were used to generate pbmc\_1k\_v2, pbmc\_10k\_v3). PBMCs are primary cells with relatively small amounts of RNA (~1pg RNA/cell).
- 11,769 cells detected by CellRanger
- Sequenced on Illumina NovaSeq with approximately 54,000 reads per cell
- [10X Genomics web page for this data](https://www.10xgenomics.com/resources/datasets/10-k-pbm-cs-from-a-healthy-donor-v-3-chemistry-3-standard-3-0-0)
- [pbmc\_10k\_v3\_filtered\_feature\_bc\_matrix.h5](https://cf.10xgenomics.com/samples/cell-exp/3.0.0/pbmc_10k_v3/pbmc_10k_v3_filtered_feature_bc_matrix.h5)

#### Sample 2
Here are some more details:

- 20k Human PBMCs, 3’ HT v3.1, Chromium X
- Sourced from a healthy female donor
- 23,837 cells
- 35,000 reads per cell
- [link to downlad](https://cf.10xgenomics.com/samples/cell-exp/6.1.0/20k_PBMC_3p_HT_nextgem_Chromium_X/20k_PBMC_3p_HT_nextgem_Chromium_X_filtered_feature_bc_matrix.h5)

#### Sample 3
This sample was not included in Lecture 4. 

- Single Cell 3' v2
- 2,909 cells
- 115,061 reads per cell
- healthy donor
- [download](https://jhu.instructure.com/files/13362961/download?download_frd=1)

### Your mission

Analyze the provided data to address the following questions:

1. You are curious about some of the steps in the processing pipeline. While some seem reasonable, others seem highly arbitrary. **How does altering the pipeline impact cell composition estimates? If so, in what ways?**
	- Specifically, determine how each of the following changes (independently) impacts the estimated cell composition (as applied to Sample 1 data):
		- Don't filter cells based on MT content
		- Don't filter cells based on total counts
		- Don't normalize expression (so skip both `sc.pp.normalize_total()` and `sc.pp.log1p()`
		- Don't use PCs for kNN graph
		- Test extreme values of n_pcs (e.g. n_pcs = 3, n_pcs = 50) when computing kNN graph
		- Test extreme values of n_neighbors when computing kNN graph
		- ***How do each pipeline variant above alter the cell type gene signatures that you defined?*** 
	- Deliverables:
		- Efficient visualisation of the cell type proportions across pipeline variant. Ideally the students will use their barplot function and pass it the adatas that result from annotation each of the outcomes of each variation to the pipeline.
		- Written summary detailing effect of each change to the pipeline and an explanation (or speculation) for this result.
2. **To what extent do cell type compositions (as estimated by scRNA-seq) vary between samples?** From your work on qustion 1 above, you have arrived at an opinion as to the best pipeline. Apply that to pipeline the additional two PBMC samples (i.e. Sample 2 and Sample 3). Compare all three to the proportion estimates from the literature (see HW1). Do you think that the variation that you observe in the scRNAseq-based estimates primarily reflect real biological variation, or do they reflect technical variation due to the vicissitudes of scRNAseq data generation and analysis?
	- Deliverables:
		- stacked barplots showing cell type compositions across samples and literature
		- Written answer to questions about source of variation plus justification.
3. Adult stem cells are not as numerous as their downstream progeny and so you wonder about the factors that impact scRNA-seq's sensitivty for detecting such rare populations. Some factors include read depth (the number of UMIs per cell), size of the 'rare' population, the degree of distinctness of its transcriptome, and the analysis pipeline steps and parameters (among many other factors). **Use existing Scanpy functions to explore the impact of read depth, population size, and analysis pipeline steps/parameters on the power to detect rare populations.**
	- Deliverables:
		- Written report including the strategy (including what cell type(s) treated as 'rare' population'), rationale, and general lessons derived from the analyses with relevant figures. What is the most important factor? What is the minimum population size (expressed as fraction of total number of cells in sample) that yields a detectable distinct cluster? How does this vary with read depth? Do variations in the pipeline alter the chance of detecting the rare population?







!!!success "**ALL SUBMISSIONS MUST...**"

	... include _all_ code necessary to replicate the results, and must adhere to posted guidelines for code documentation, cogent written reports, and meaningful figures.










