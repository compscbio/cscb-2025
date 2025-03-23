# Homework 5

!!!warning No jokes this time

    The goal of this homework is for you to gain experience in using gene regulatory network inference methods and to apply them to simulate cell state dynamics.

    **Deadline: Thurs, April 3rd 2025 11:59pm**

### Background

We have discussed why groups are attempting to engineer cell fate, and we have discussed various experimental approaches, namely directed differentiation of pluripotent stem cells and direct conversion from one somatic cell type into another. We have also seen how time-consuming and resource-intensive it is to try to empirically devise experimental protocols to produce a given cell type. Several computational tools have been invented to amerliorate this problem. In general, these methods tend to leverage expression data and regulatory networks in an attempt to prioritize targeting the most impactful nodes. The overall goal of this homework is for you to gain some experience with computational methods for cell fate engineering. This will entail reversen engineering gene regulatory networks, and using them to simulate the effect of over-expressing and knocking down transcription factors on fate outcomes. You will also build on what you have learned about trajectory inference and cell typing to complete this homework.

Your mission is to predict a minimal set of perturbations to apply to mouse embryonic stem cells so that they will differentiate to a) nascent mesoderm, and to b) anterior primitive streak/nascent endoderm. To achieve this, you will be asked to reverse engineer the GRN that underpins the differentiation of epiblast to mesoderm or APS/endoderm, and then use this GRN to simulate the fate outcome from perturbing TFs that you select. We have provied a scRNA-seq data set (specifications in [Data](#Data) section) that you are now familar with: it is the mouse embryo data set of epiblast cells, nascent mesoderm, and anterior primitive streak cells. This is the data set that you should use to infer the GRN. Note that we have excluded visceral endoderm cells from this data set. We have also provided a scRNA-seq data set of mouse embryonic stem cells in an undifferentiated state, which should be used to set the initial state of the cells for your simulations.

### Task 1: trajectory inference

After loading the gastrulation data, use **scFates** to reconstruct a trajectory tree that connects epiblast to APS, and epiblast to mesoderm, and also use scFates to predict a pseudotime for each cell. If you did well on HW4 part 2, this part should be super easy for you.

### Task 2: TF selection

Select 10-15 TFs to use for GRN reconstruction. You can choose to use functions in scFates to identify these TFs, or another approach such as differential gene expression, or another method of your choicee. Describe how you identified these TFs and justify why your choice is a good one.

### Task 3: Reconstruct gene regulatory network

Use [oneSC](https://onesc.readthedocs.io/en/latest/index.html) to infer the GRN assoicated with the gastrulation data set. You need to limit your analysis to TFs identified in [Task 2](#Task 2), and ensure that the state graph is consistent with what you know about development. If oneSC's state graph conflicts with this, then you should manually define this.


### Task 4: Find minimal TF set

Devise a strategy to predict a minimal set of TFs that, when perturbed in mouse embryonic stem cells, will yield the highest proportion of APS cells. Your method should be based on the GRN you inferred in Task 3, and optionally on the scRNA-seq data provided below. Use the method to generate a set of candidate TFs and then check how your prediction performs by simulating the impact of the perturbation using oneSC. You should compare the performance of your method to a judiciously chosen baseline method.

Now apply your method to predict TFs to perturb in mESCs to yield the highest proportion of nascent mesoderm cells. Evaluate your predictions as above (i.e. perform simulations with your perturbations, qunatify cell type numbers, and compare to results using a baseline method). 

Did your method outperform the baseline method? Discuss why or why not.


### Data

#### List of mouse transcription factors:
- [allTFs_mm_aertslab_011924.txt](https://jhu.instructure.com/files/13616012/download?download_frd=1)


#### scRNA-seq data of mouse gastrulation embryonic cells
- [h5ad: adHW5_EpiMesoAPS_n500.h5ad](https://jhu.instructure.com/files/13759151/download?download_frd=1)
- Includes only APS, nascent mesoderm, and epiblast cells
- We have already performed cell quality control. You will want to perform gene quality control and standard downstream processing.

#### scRNA-seq data of pluripotent mouse embryonic stem cells
- [h5ad: adHW5_mESC.h5ad](https://jhu.instructure.com/files/13758759/download?download_frd=1)



