# Homework 4

!!!warning "*Do you believe in fate, Neo?*"

    The overall goal of this homework is for you to gain experience in using trajectory inference (TI) and cell fate potency methods. 

    **Deadline: Tues, March 25th 2025 11:59pm**

### Background

![fate](img/fate.png){ align=right width=600 }

**Gastrulation** marks the point during embryonic development at which some pluripotent epiblast cells commit to endoderm or mesoderm fates. Gastrulation initiates with posterior epiblast cells undergoing an **epithelial-to-mesenchymal transition** (EMT). These cells delaminate, ingress through, and ultimately migrate away from, the **primitive streak**.  The fate of many embryonic cells and their progeny are determined by where and when they undergo this process. In general, cells located anteriorly and that delaminte early during gastrulation (i.e. **anterior primitive streak** or APS) are fated to become **definitive endoderm** (DE) cells. Cells that delaminate later and are located more posteriorly are generally fated to become mesoderm lineages cells. 

We have provided a scRNA-seq data set from mouse embryos at the gastrula-stage as described in the [Data section](#Data). In brief, it consists of epiblast cells, nascent mesoderm, anterior primitive streak, and visceral endoderm cells from E6.5 to E8.5 stage mouse embryos. Starting at E6.5, some epiblast cells will undergo the processes described above, and they will ultimately give rise to definitive endoderm or mesoderm cells. However, visceral endoderm cells are specified earlier in development and are not derived from the epiblast cells present in this data set. 

!!!danger "TI pitfalls"

	1. TI analysis typically assumes that the input cells _are_ developmentally interlinked. Even when data violate this assumption, most TI methods will still try to link them purely on the basis of transcriptional similarity. This is bad. 
	2. TI analysis also typically requires the user to input a start point or 'root' of a trajectory. 

### Task 1: Perform cell-typing

Before you can reliably appy TI to this data, you must perform cell-typing to (A) identify and exclude VE cells, and (B) to identify the epiblast, mesoderm, and anterior primitive streak cells. This will allow you to suggest a root for the TI analysis. To help you with this part, here are some well-established marker genes:

- Epiblast: Utf1, Slc7a3, Pou3f1
- Mesoderm: Mesp1, Fgf3, Snai1
- Anterior primitive streak: Foxa2, Gsc, Sox17
- Visceral endoderm: Use your highly refined literature-mining skills to find these. Please select 3-5 genes that are reported to be VE-specific from the literature. You must cite the primary papers in which each gene has been demonstrated to be a marker of murine VE. 

You will know that you are done with Task 1 when you have clearly annotated each cell and have excluded the VE cells from the input data.

### Task 2: Infer trajectory and pseudotime

Use scFates to reconstruct a trajectory that connects epiblast to APS, and epiblast to mesoderm. Then predict the pseudotime for each cell. To receive full credit for Part 2, you must infer the tree, justify your parameter selections, and visualize the resulting tree with labeled branches and milestones, and visualize pseudotime.


### Task 3: Discover regulators of differentiation

What transcription factors might promote the transition from epiblast to mesoderm or to endoderm? Develop a critiera for ranking transcription factors (TFs) accoring to their predicted importance or influence on differentiation. This could be simply the p-value from scFates's association test, or you might conceive of other criteria. Use this criteria to select the top X TFs (where X >4) that specifically promotes mesoderm or endoderm differentiation from the epiblast. Mine the literature around each of your candidate TFs to assess the extent to which your criteria and application of scFates recovered bona fide regulators of gastrulation. Your answer should cite the primary papers that you use here. You must have two sets of X candidates TFs, one for mesoderm differentiation, and one for endoderm differentiation.

### Task 4: Discover regulators of pluripotency

What transcription factors potentially oppose epiblast cells from differentiation, and thus promote pluripotency? Perform the same kind of analysis as you did for Task 3 here, but now apply it to find TFs that inhibit epiblast differentaition.

### Task 5: Compare Cytotrace to pseudotime

To what extent do Cytotrace and scFtes pseudotime agree? Compute Cytotrace's cell potency on this data and compute its correlation with scFates pseudotime. Do they agree? If not, perform further analyses to explore why this might be the case. 

### Data
#### scRNA-seq data of mouse gastrulation embryonic cells
- [h5ad: adHW3_2024.h5ad](https://jhu.instructure.com/files/13615999/download?download_frd=1)
- Includes only VE, APS, nascent mesoderm, and epiblast cells
- We have already performed cell quality control. You will want to perform gene quality control and standard downstream processing.
- There should be roughly equivalent numbers of cells per population.

#### List of mouse transcription factors:
- [allTFs_mm_aertslab_011924.txt](https://jhu.instructure.com/files/13616012/download?download_frd=1)


