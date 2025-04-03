# Final Project

!!!warning "*'I heard the jury is still out on science'* --GOB from Arrested Development"

    Now is your chance to flex your single cell analysis muscles. You are a beast. Show us what you can do! In the final project, you will develop a new analysis method, benchmark it, and then you will use it to address an open question in stem cell biology. Teams should only do the project listed under their section number. In other words, students registered for section 647 should follow the instructions in [Section 647](#section-647) and students registered for 447 should follow the instructions in [Section 447](#section-447). 

    **Deadline: TBA**

![GOB](img/GOB.png){ align=right width=450 }

### Section 447

DNA copy number alterations (CNA) have been detected in embryonic stem cells (ESC) and induced pluripotent stem cells (iPSC). CNAs that are specific to iPSC/ESC versus the germline can be problematic. The lesions may be tumorigenic, they may hinder derivation of selected lineages, or they may obscure disease-specific phenotypes that the lines were derrived to explore. There are lots of ways to detecte CNAs, including karyotyping, FISH, array comparative genomic hybridization, single nucleotide polymorphism (SNP) arrays[^1], and genome sequencing. In 2010, a method called e-karyotyping was published that attempted to infer CNAs based on expression of genes co-located in the genome[^2]. The overall goal of this project ou will use a method called e- Karyotyping that was developed by Nissim Benevisty's lab (see paper linked on syllabus). The idea behind e-Karyotpying is that a cell line with a gain in copy will have increased expression of genes encompassed by the gain as compared to cell lines that do not harbor that CNA. Similarly, cell lines with a loss in copy number will have decreased expression of genes encompassed by the lost region as compared to lines that do not harbor the deletion (or loss). One of the benefits of this approach is the gene expression profiling (by arrays or RNA-Seq) is common, and so one does not have to perform additional molecular profiling (e.g. DNA-sequencing) to detect large scale CNA.




sd
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


### Section 647

Signaling pathways in development:


Goal is to develop a method + resources that will allow a user to infer signaling pathways that are likely to have influenced the transition from cell type A to cell type B. Optimize and test the method on in vitro experiments with defined signaling pathway controls. Apply the method to infer:

sequence of signaling events that govern: epi to 
A: primordial germ cell
B: neural crest melanocyte
C: paraxial mesoderm sub-type derivatives (muscle etc)
D: hindgut forgut


Apply to gastruloids (or some other in vitro model). do the signaling conditions applied have the same transcriptional response as their in vivo analogs?


1. identify effectors of these pathways
2. identify publicly available sources of data that measure binding of effectors to the genome (TFBS -> motifs)
3. Invent a method that pairs a query cell type with data that is most potentially relevant to infer
4. Expand 4 by allowing for the user to supply chromatin accessibility data







[^1]: Laurent LC, Ulitsky I, Slavin I, Tran H, Schork A, Morey R, Lynch C, Harness
JV, Lee S, Barrero MJ, Ku S, Martynova M, Semechkin R, Galat V, Gottesfeld J,
Izpisua Belmonte JC, Murry C, Keirstead HS, Park HS, Schmidt U, Laslett AL,
Muller FJ, Nievergelt CM, Shamir R, Loring JF. Dynamic changes in the copy
number of pluripotency and cell proliferation genes in human ESCs and iPSCs
during reprogramming and time in culture. Cell Stem Cell. 2011 Jan
7;8(1):106-18. doi: 10.1016/j.stem.2010.12.003. [PMID: 21211785; PMCID:
PMC3043464.](https://pubmed.ncbi.nlm.nih.gov/21211785/)

[^2]: Mayshar Y, Ben-David U, Lavon N, Biancotti JC, Yakir B, Clark AT, Plath K,
Lowry WE, Benvenisty N. Identification and classification of chromosomal
aberrations in human induced pluripotent stem cells. Cell Stem Cell. 2010 Oct
8;7(4):521-31. doi: 10.1016/j.stem.2010.07.017. [PMID: 20887957.](https://pubmed.ncbi.nlm.nih.gov/20887957/)


