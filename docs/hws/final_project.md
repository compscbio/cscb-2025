# Example homework assignment

!!! warning
    This is **not** a real assignment for CSCB! It's just a realistic example to demonstrate the style guide.

### Goal

*The goal of this assignment is to give you some experience in data wrangling and quality control of scRNA-seq data.*

### Due date: Jan 1st, 2001.

### Data

In this assignment, you will perform a few initial steps in the analysis of a dataset from a tech-dev paper showing off an unusual combination of cababilities. The paper includes several large experiments with genetic perturbations followed by a scRNA-seq readout ([Replogle et al 2020](https://www.nature.com/articles/s41587-020-0470-y)). These assays are applied to mostly the K562 leukemia cell line.  We'll focus on just the CRISPRa multiplexing experiment, which does gene overexpression followed by scRNA. 

### Your mission

#### Task 1
- Tidy the dataset so that it fits in an AnnData object.
- For each overexpressed gene, how many cells are measured?

#### Task 2
- Compute typical scRNA quality metrics and filter out genes and cells as discussed in class.
- As you apply each filter, print the number of cells remaining so that anyone following your code can see which filtering steps are most impactful.

#### Task 3
- Write code to visualize the data using scanpy.
- Run the code and describe the results.

### Resources

You may use the provided code (`ingestion.py`) to convert gene names from Ensembl gene id's (example: `ENSG00000109101`) to more readable Entrez gene symbols (example: `Foxn1`).

### Deliverables

A Jupyter notebook that contains documented code achieving Tasks 1, 2, and 3. For an example submission, [['HWEX Done']].



