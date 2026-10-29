# Single-Cell RNA-seq Analysis: Free, Hands-On Learning Roadmap

> A video-first roadmap for learning **single-cell RNA sequencing (scRNA-seq) analysis** from raw sequencing reads to cell annotation, differential expression, pathway analysis, and advanced single-cell methods.

![Free video resources](https://img.shields.io/badge/learning%20videos-free%20to%20watch-brightgreen)
![Language](https://img.shields.io/badge/language-English-blue)
![Focus](https://img.shields.io/badge/focus-practical%20scRNA--seq-purple)

This repository is a curated learning path for people who want to **analyze real single-cell RNA-seq data**, follow a complete workflow, and understand the decisions behind each step. It focuses on scRNA-seq-specific analysis rather than general programming or introductory bioinformatics.

**All linked instructional videos and public recordings are free to watch at the time of review and are in English.** Supporting links to software, public datasets, and code notebooks are included where they are needed to perform the exercises. Free-to-watch does not mean a video is openly licensed for redistribution; please respect each creator's terms and cite original work when appropriate.

---

## Table of contents

- [Start here](#start-here)
- [Choose a main analysis track](#choose-a-main-analysis-track)
- [Free datasets for practice](#free-datasets-for-practice)
- [Complete workflow: step by step](#complete-workflow-step-by-step)
- [Advanced analysis modules](#advanced-analysis-modules)
- [Practical project checklist](#practical-project-checklist)
- [Common mistakes to avoid](#common-mistakes-to-avoid)
- [Recommended free software](#recommended-free-software)
- [How to contribute](#how-to-contribute)
- [Search keywords](#search-keywords)

---

## Start here

### 1. Introduction to Bioinformatics

Start with the **Lockdown Learning Bioinformatics** playlist on YouTube. This is the general bioinformatics orientation for people who need it; the rest of this repository focuses on single-cell RNA-seq analysis.

- **[Lockdown Learning Bioinformatics — YouTube playlist](https://www.youtube.com/playlist?list=PLzfP3sCXUnxEu5S9oXni1zmc1sjYmT1L9)**

### 2. Watch one complete scRNA-seq analysis before studying each step

Choose one main workflow and follow it from start to finish. Then revisit the individual steps below for deeper practice.

| Track | Main video | Best use |
|---|---|---|
| **Python / Scanpy** | [Sanbomics — Complete single-cell RNA-seq analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE) | Broad, practical workflow including doublet removal, preprocessing, integration, clustering, cell-type identification, differential expression, gene-set enrichment, and scoring. |
| **R / Seurat** | [Bioinformagician — Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk) | Step-by-step standard workflow: loading a 10x dataset, QC, filtering, normalization, variable features, scaling, PCA, clustering, and UMAP. |
| **Python / Scanpy workshop** | [Erikomics — Single-cell RNA-seq analysis with Scanpy](https://www.youtube.com/watch?v=JGktZRG5JKk) | Practical Scanpy workshop covering QC, normalization, PCA, UMAP, clustering, differential expression, and visualization. |
| **Raw FASTQ to count matrix** | [NGS101 — Single-cell RNA-seq: FASTQ to count matrix with 10x and Cell Ranger](https://www.youtube.com/watch?v=yGkQQPgTMpA) | Raw data, barcode/UMI concepts, Cell Ranger count, QC reports, and the count matrix. |

**Recommended route:** complete either the R/Seurat or Python/Scanpy core route first. Avoid trying to learn both frameworks at once. Once one workflow is reproducible, repeat it in the other framework to understand the differences.

---

## Choose a main analysis track

### R track

- **Main framework:** [Seurat](https://satijalab.org/seurat/)
- **Core workflow video:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Normalization with SCTransform:** [Seurat v5 — SCTransform-normalized datasets](https://www.youtube.com/watch?v=AzCrxX4E5rU)
- **Batch correction with Harmony:** [Integrating single-cell RNA-seq data in R using Harmony](https://www.youtube.com/watch?v=zEuqhiu341I)
- **Pseudobulk differential expression:** [Detailed pseudobulk workflow with DESeq2](https://www.youtube.com/watch?v=04gB2owLKus)
- **Trajectory analysis:** [Monocle3 and Seurat — step-by-step tutorial](https://www.youtube.com/watch?v=iq4T_uzMFcY)

### Python track

- **Main framework:** [Scanpy](https://scanpy.readthedocs.io/)
- **Core workflow video:** [Complete single-cell RNA-seq analysis walkthrough using Scanpy and scVI](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Additional workshop:** [Single-cell RNA-seq analysis with Scanpy](https://www.youtube.com/watch?v=JGktZRG5JKk)
- **Cell-type annotation:** [CellTypist explained — annotation with machine learning](https://www.youtube.com/watch?v=kzbILpr8I04)
- **RNA velocity:** [Single-cell RNA velocity with velocyto and scVelo](https://www.youtube.com/watch?v=AUiYxtGJYtg)

---

## Free datasets for practice

Start with a small public dataset, then repeat the workflow on a multi-sample dataset with biological replicates.

| Data source | What to use it for |
|---|---|
| [10x Genomics public datasets](https://www.10xgenomics.com/datasets) | Practice with 10x count matrices and, where available, raw FASTQ files and analysis outputs. |
| [NCBI GEO](https://www.ncbi.nlm.nih.gov/geo/) | Find published studies, sample metadata, processed data, and links to raw sequencing data. |
| [NCBI SRA](https://www.ncbi.nlm.nih.gov/sra) | Retrieve raw sequencing reads when the study provides them. |
| [CELLxGENE Discover](https://cellxgene.cziscience.com/) | Explore and download annotated public single-cell datasets for downstream analysis practice. |
| [Single Cell Expression Atlas](https://www.ebi.ac.uk/gxa/sc/home) | Search public single-cell studies and processed expression data. |
| [Human Cell Atlas data portal](https://data.humancellatlas.org/) | Explore cell atlas datasets and supporting metadata. |

### Video: downloading raw data

- [How to download FASTQ files from NCBI using SRA Toolkit](https://www.youtube.com/watch?v=LWYQZKRIQKk)
- [NGS101 — downloading a public dataset and processing 10x FASTQ files](https://www.youtube.com/watch?v=yGkQQPgTMpA)

**Practice tip:** keep sample metadata with the expression matrix from the beginning. Record sample ID, donor/animal ID, condition, tissue, batch, library chemistry, sequencing run, and relevant biological covariates. Do not treat thousands of cells from one donor as thousands of independent biological replicates.

---

# Complete workflow: step by step

Each step includes a free video or playlist and a practical outcome to produce before moving on. Use the steps in order for a standard droplet-based gene-expression experiment. Some steps are optional or depend on the assay and research question; these are marked accordingly.

## Phase A — Study design and raw data

### 0. Define the scientific question and experimental design

Before running software, write down the biological comparison, the experimental unit, expected cell populations, conditions, and known technical factors. Identify independent biological replicates and potential confounders. Decide whether the goal is cell discovery, condition comparison, trajectory analysis, or another question.

- **Video:** [EMBL-EBI — Experimental design for single-cell RNA-seq](https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=28522811-6cc8-47c5-ac0c-b1e5013858ea&start=0)
- **Core-workflow reference:** [Sanbomics — complete analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)

**Hands-on output:** a written analysis plan and one metadata table with one row per sample. Include donor/sample identifiers and condition labels before merging any count matrices.

### 1. Select a study and understand its assay

Check organism, tissue, chemistry, number of samples, biological replicates, sequencing design, available raw reads, and whether the data are gene-expression-only or include antibody tags, guide captures, V(D)J, or ATAC data. Do not mix assays or species without understanding the implications.

- **Video:** [NGS101 — single-cell RNA-seq from FASTQ to count matrix](https://www.youtube.com/watch?v=yGkQQPgTMpA)
- **Dataset portal:** [10x Genomics public datasets](https://www.10xgenomics.com/datasets)

**Hands-on output:** a small study manifest containing study accession, sample IDs, conditions, data source, assay chemistry, and selected input files.

### 2. Download raw sequencing reads and metadata

When raw reads are available, retrieve the FASTQ files and sample sheet. For studies hosted in GEO, follow links to the SRA run accessions. Confirm that read files belong to the correct sample and sequencing library.

- **Video:** [Download FASTQ files from NCBI with SRA Toolkit](https://www.youtube.com/watch?v=LWYQZKRIQKk)
- **Alternative walk-through:** [NGS101 — raw data download and Cell Ranger workflow](https://www.youtube.com/watch?v=yGkQQPgTMpA)
- **Data sources:** [GEO](https://www.ncbi.nlm.nih.gov/geo/) · [SRA](https://www.ncbi.nlm.nih.gov/sra)

**Hands-on output:** a read-only copy of the original FASTQ files, checksums where practical, and a sample sheet linking every FASTQ pair to its biological sample.

### 3. Inspect raw FASTQ quality

Review read quality, read length, adapter content, overrepresented sequences, and whether read structure matches the library chemistry. For droplet-based scRNA-seq, cell barcodes and UMIs have specific positions in the reads, so do not blindly apply ordinary bulk RNA-seq trimming steps. Trim only when justified by the protocol and the QC report.

- **Video:** [NGS101 — FASTQ preparation, FastQC, and Cell Ranger](https://www.youtube.com/watch?v=yGkQQPgTMpA)
- **Extra video search for FastQC and MultiQC:** [YouTube — FastQC/MultiQC quality-control walkthroughs](https://www.youtube.com/results?search_query=FastQC+MultiQC+FASTQ+quality+control+tutorial+English)

**Hands-on output:** saved raw-read QC reports and a short record of any problems found. Keep original FASTQ files unchanged.

### 4. Process reads into a gene-by-cell count matrix

Choose a processing method compatible with the platform and library chemistry. The workflow must handle barcodes and UMIs, align or pseudoalign reads, assign reads to genes, correct/validate barcodes as appropriate, and generate a count matrix.

- **Video:** [NGS101 — Cell Ranger count from FASTQ to count matrix](https://www.youtube.com/watch?v=yGkQQPgTMpA)
- **Open-source alternative:** [STARsolo](https://github.com/alexdobin/STAR) is part of STAR; [kallisto | bustools](https://www.kallistobus.tools/) provides an alternative workflow.
- **Official Cell Ranger tutorials:** [10x Genomics Cell Ranger tutorial library](https://www.10xgenomics.com/support/software/cell-ranger/latest/tutorials)

**Hands-on output:** a complete processing directory, software/version record, reference genome/annotation version, run summary, and raw/unfiltered plus filtered matrices where available. Cell Ranger is available at no cost for supported workflows, but it is not open-source software; STARsolo and kallisto|bustools are open-source alternatives.

### 5. Understand cell calling and processing reports

Inspect the number of reads, fraction of reads in cells, valid barcode fraction, sequencing saturation, median genes per cell, and number of cells called. These metrics are useful diagnostics, not a guarantee that every retained barcode is a high-quality cell.

- **Video:** [NGS101 — interpreting the Cell Ranger output and QC report](https://www.youtube.com/watch?v=yGkQQPgTMpA)

**Hands-on output:** a one-page summary of processing metrics for every sample. Investigate large differences between samples before combining them.

---

## Phase B — Load data and perform quality control

### 6. Load the matrix and build the analysis object

Create a Seurat object, `AnnData` object, or `SingleCellExperiment` from the count matrix. Ensure the matrix orientation and feature identifiers are correct. Attach sample metadata, keep raw counts intact, and confirm that cell names are unique across samples.

- **R / Seurat video:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Python / Scanpy video:** [Single-cell RNA-seq analysis with Scanpy](https://www.youtube.com/watch?v=JGktZRG5JKk)

**Hands-on output:** a saved initial analysis object plus a metadata table with one row per cell and correct sample/condition labels.

### 7. Calculate and visualize cell-level QC metrics

Examine, at minimum:

- **Detected genes per cell** — very low values may indicate empty droplets or damaged cells; unusually high values may indicate multiplets.
- **UMI counts per cell** — very low or very high counts can flag poor-quality cells or possible multiplets.
- **Mitochondrial transcript percentage** — high values can indicate stressed or damaged cells, but expected ranges differ by tissue and assay.
- **Ribosomal, hemoglobin, or other tissue-specific metrics** — use only when biologically justified.
- **Sample-level distributions** — compare metrics across samples rather than applying one blind global cutoff.

- **R / Seurat video:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Python / Scanpy video:** [Single-cell RNA-seq analysis with Scanpy](https://www.youtube.com/watch?v=JGktZRG5JKk)
- **Full walkthrough with QC and preprocessing:** [Sanbomics — Scanpy/scVI workflow](https://www.youtube.com/watch?v=uvyG9yLuNSE)

**Hands-on output:** violin plots and scatter plots of QC metrics by sample, plus a written explanation of the chosen filtering rules. There are no universal cutoffs that work for every dataset.

### 8. Filter low-quality cells and low-information genes

Choose thresholds after inspecting distributions. Record cells removed by each rule and compare the effects across samples. Avoid setting thresholds so aggressively that they remove real cell types with naturally low RNA content or high mitochondrial expression.

- **Video:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Video:** [Scanpy workshop](https://www.youtube.com/watch?v=JGktZRG5JKk)

**Hands-on output:** a filtered object, a pre/post-filtering table, and QC plots showing that the filtering achieved its intended purpose.

### 9. Detect doublets and multiplets

Doublets are droplets containing more than one cell. High UMI counts or high gene counts can flag candidates, but are not sufficient on their own. Use a method appropriate to the framework and data, such as Scrublet, DoubletFinder, or a scVI-based method, and compare calls with QC metrics and expected loading rates. Do not automatically remove every cell marked by an algorithm without review.

- **Video:** [Sanbomics — complete workflow, including doublet removal](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Topic-specific video search:** [DoubletFinder, Scrublet, and scRNA-seq doublet detection](https://www.youtube.com/results?search_query=DoubletFinder+Scrublet+single+cell+RNA-seq+doublet+detection+tutorial+English)

**Hands-on output:** per-cell doublet scores/calls, the fraction flagged in each sample, and a saved object with the decision documented.

### 10. Assess ambient RNA contamination *(as needed)*

Ambient RNA from lysed cells can add misleading transcripts to droplets. Consider tools such as SoupX or CellBender when the data, tissue, and experimental protocol suggest contamination. Review marker distributions before and after correction. Do not assume all low-level expression is contamination.

- **Topic-specific video search:** [SoupX and CellBender ambient RNA correction](https://www.youtube.com/results?search_query=SoupX+CellBender+ambient+RNA+correction+single+cell+RNA-seq+tutorial+English)
- **Core workflow for context:** [Sanbomics — complete analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)

**Hands-on output:** a reasoned decision to correct or not correct ambient RNA, with sample-level evidence and a record of the tool and parameters if correction is performed.

### 11. Review cell cycle, stress, and other technical effects

Score cell-cycle or stress-related signatures only when relevant. Check whether these variables explain variation in the embedding or clusters. Regressing out a biological signal can damage the result, so compare analyses with and without the adjustment before deciding.

- **Video:** [Sanbomics — preprocessing, scoring, and downstream analysis](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Additional video search:** [Single-cell RNA-seq cell-cycle scoring and regression](https://www.youtube.com/results?search_query=single+cell+RNA-seq+cell+cycle+scoring+Seurat+Scanpy+tutorial+English)

**Hands-on output:** plots of relevant scores across samples and clusters, with an explicit justification for any regression or exclusion step.

---

## Phase C — Normalize, reduce dimensions, and cluster

### 12. Normalize expression and select informative features

Choose an approach compatible with the planned analysis. Common options are log-normalization with highly variable gene selection or SCTransform in Seurat. In Scanpy, use the appropriate normalization and transformation workflow. Preserve raw counts separately for methods that need them later.

- **R / Seurat:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **R / SCTransform:** [Seurat v5 SCTransform workflow](https://www.youtube.com/watch?v=AzCrxX4E5rU)
- **Python / Scanpy:** [Scanpy workshop](https://www.youtube.com/watch?v=JGktZRG5JKk)

**Hands-on output:** a normalized object, a documented list of variable genes, and clear notes on which expression layer/matrix is being used for each downstream operation.

### 13. Perform PCA or another suitable dimensionality reduction

Run PCA on an appropriate scaled or normalized feature matrix. Examine the variance explained, principal component loadings, and patterns in the leading components. Use biological knowledge and QC metrics to help choose dimensions; do not select PCs solely because a particular UMAP looks attractive.

- **R / Seurat video:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Python / Scanpy video:** [Scanpy workshop](https://www.youtube.com/watch?v=JGktZRG5JKk)

**Hands-on output:** PCA diagnostics and a documented rationale for the dimensions used for graph construction.

### 14. Build a cell-neighbor graph and cluster cells

Construct a nearest-neighbor graph using the selected representation, then run graph-based clustering. Test a small range of clustering resolutions and check marker genes, cluster stability, and whether clusters make biological sense. A cluster label is a computational grouping, not a cell identity by itself.

- **R / Seurat:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Python / Scanpy:** [Scanpy workshop](https://www.youtube.com/watch?v=JGktZRG5JKk)
- **Longer Python workflow:** [Sanbomics — complete analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)

**Hands-on output:** a saved clustering result at one or more justified resolutions, with cell counts per cluster and plots of the cluster composition by sample and condition.

### 15. Visualize the data with UMAP or t-SNE

Use UMAP/t-SNE as visual summaries of the chosen representation, not as literal maps of biological distance. Compare embeddings with cluster labels, sample labels, condition, QC metrics, and known marker genes. Do not infer developmental direction from a UMAP alone.

- **R / Seurat:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Python / Scanpy:** [Scanpy workshop](https://www.youtube.com/watch?v=JGktZRG5JKk)

**Hands-on output:** UMAP plots coloured by cluster, sample, condition, and key QC metrics, with the same plotting settings used consistently for comparisons.

### 16. Integrate multiple samples or correct batch effects *(when justified)*

First determine whether there is a batch problem. Samples can separate because of technical variation, real biology, or both. Compare unintegrated and integrated results, check whether shared cell types align, and ensure condition-specific biology has not been erased. Do not integrate simply because the dataset contains multiple samples.

- **R / Harmony:** [Integrate single-cell RNA-seq data using Harmony in Seurat](https://www.youtube.com/watch?v=zEuqhiu341I)
- **Python / scVI and integration:** [Sanbomics — complete Scanpy/scVI workflow](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Additional integration video search:** [Single-cell RNA-seq integration and batch correction](https://www.youtube.com/results?search_query=single+cell+RNA-seq+batch+correction+integration+Harmony+scVI+tutorial+English)

**Hands-on output:** before/after integration plots, a clear description of the batch variables, and a check that known biological differences remain visible. Keep a non-integrated object for analyses that require the original expression counts.

---

## Phase D — Identify and validate cell types

### 17. Find cluster marker genes

Find genes enriched in each cluster and inspect effect sizes, detection fractions, multiple-testing-adjusted results, and whether markers are specific enough to distinguish similar cell populations. Marker testing is useful for cluster interpretation but is not automatically a valid test of differences between experimental conditions.

- **R / Seurat:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Python / Scanpy and downstream analysis:** [Sanbomics — complete analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)

**Hands-on output:** a ranked marker table for every cluster and DotPlot/heatmap/violin plots for a concise panel of candidate markers.

### 18. Annotate cell types using marker genes and reference-based methods

Start with known biological markers and the tissue context. Use automated tools such as SingleR or CellTypist as supporting evidence, not as unquestioned ground truth. Compare manual and automated labels, examine prediction confidence, and resolve disagreements using marker expression and reference suitability.

- **CellTypist video:** [CellTypist explained — ML-based cell-type annotation](https://www.youtube.com/watch?v=kzbILpr8I04)
- **Manual annotation and complete analysis:** [Sanbomics — complete single-cell walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Seurat workflow:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Extra video search:** [SingleR and reference-based scRNA-seq annotation](https://www.youtube.com/results?search_query=SingleR+reference+based+single+cell+RNA-seq+annotation+tutorial+English)

**Hands-on output:** a cell annotation table containing cluster ID, proposed cell type, positive markers, conflicting markers, reference/model used, confidence, and any unresolved label.

### 19. Refine broad cell types and subcluster important populations

Once broad cell types are assigned, subset relevant populations and repeat QC checks, dimensionality reduction, clustering, and marker discovery at a suitable resolution. This can reveal rare cell states or subtypes that were hidden in the full dataset. Avoid over-clustering cells without stable marker support.

- **Video:** [Sanbomics — detailed analysis, cell identification, and downstream interpretation](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Seurat workflow:** [Detailed Seurat workflow tutorial](https://www.youtube.com/watch?v=5HBzgsz8qyk)

**Hands-on output:** a documented hierarchy of cell labels (for example, broad lineage → subtype → state) and a justification for the subpopulations retained for further analysis.

---

## Phase E — Differential expression and biological interpretation

### 20. Compare gene expression between conditions within cell types

Define the comparison before testing. For multi-sample experiments, use biological replicates as the unit of inference. Pseudobulk workflows aggregate counts for each sample within each cell type and then use bulk RNA-seq methods such as DESeq2 or edgeR. Per-cell tests can be useful for exploratory questions but may inflate significance if cells are incorrectly treated as independent replicates.

- **Main video:** [Pseudo-bulk analysis for single-cell RNA-seq — DESeq2 workflow](https://www.youtube.com/watch?v=04gB2owLKus)
- **Context and visualization:** [Sanbomics — complete analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)

**Hands-on output:** a reproducible differential-expression table with log fold changes, adjusted p-values, cell type, condition contrast, biological sample count, filtering settings, and design formula. Add volcano plots and expression plots for selected genes.

### 21. Test for differential cell-type abundance *(when comparing conditions)*

Expression changes and cell-composition changes are different questions. Count cells by type and sample, then use a method appropriate for the experimental design. For more detailed changes along cell-state continua, explore neighbourhood-based methods such as Milo. Be careful with proportions when samples have low cell counts.

- **Topic-specific video search:** [Differential abundance in single-cell RNA-seq, including MiloR](https://www.youtube.com/results?search_query=single+cell+RNA-seq+differential+abundance+MiloR+tutorial+English)
- **General condition-comparison workflow:** [Pseudo-bulk analysis for single-cell RNA-seq](https://www.youtube.com/watch?v=04gB2owLKus)

**Hands-on output:** a sample-level cell-composition table, plots of proportions by condition, and a statistical result that respects the replicate structure.

### 22. Perform pathway enrichment and gene-set analysis

Interpret gene lists using GO, Reactome, or other well-curated gene sets. Distinguish over-representation analysis from ranked-list methods such as GSEA. Record the background gene universe, identifier mapping, database version, direction of the comparison, and multiple-testing method. Pathway terms often overlap and are not independent findings.

- **Video:** [Sanbomics — gene-set enrichment and downstream scRNA-seq analysis](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Additional video search:** [GO enrichment and GSEA for scRNA-seq marker/differential-expression results](https://www.youtube.com/results?search_query=GO+enrichment+GSEA+single+cell+RNA-seq+Scanpy+Seurat+tutorial+English)

**Hands-on output:** enrichment tables with adjusted p-values and gene members, plus dot plots or enrichment plots for a small number of clearly interpreted terms.

### 23. Score gene signatures and inspect biological states

Use gene-set scoring to compare pathways, cell states, or published signatures across cells and samples. Check that genes are present in the dataset, assess expression detection and background effects, and avoid comparing scores across datasets unless the scoring method and normalization make that comparison appropriate.

- **Video:** [Sanbomics — gene signature scoring and downstream analyses](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Additional video search:** [Single-cell gene signature scoring in Seurat and Scanpy](https://www.youtube.com/results?search_query=single+cell+gene+signature+scoring+Seurat+Scanpy+tutorial+English)

**Hands-on output:** a signature-score table and visualizations split by cell type, sample, and condition where relevant, with a short statement of what each score can and cannot establish.

---

## Phase F — Advanced analysis modules

These modules are question-driven extensions, not mandatory steps for every dataset. Complete core QC, annotation, and sample metadata first.

### 24. Trajectory inference and pseudotime

Use trajectory methods only when a biologically plausible continuous process exists, such as differentiation, maturation, or a time course. Select a sensible root using independent evidence and inspect genes that change along the trajectory. Pseudotime is an inferred ordering, not actual elapsed time.

- **R video:** [Trajectory analysis with Monocle3 and Seurat](https://www.youtube.com/watch?v=iq4T_uzMFcY)
- **Additional tutorial video:** [Single-cell trajectory analysis — YouTube results](https://www.youtube.com/results?search_query=single+cell+trajectory+pseudotime+Monocle3+Slingshot+PAGA+tutorial+English)

**Hands-on output:** a trajectory embedding with root/branch decisions documented, genes changing along pseudotime, and an explanation for why a continuum is biologically justified.

### 25. RNA velocity

RNA velocity estimates a cell's likely near-future transcriptional state using spliced and unspliced RNA. The standard filtered gene-count matrix usually is not enough; the processing workflow must retain or generate the spliced/unspliced layers. Velocity estimates are model-based and should be treated as hypotheses.

- **Video:** [How to do single-cell RNA velocity analysis with velocyto and scVelo](https://www.youtube.com/watch?v=AUiYxtGJYtg)
- **Context:** [Trajectory and advanced scRNA-seq analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)

**Hands-on output:** spliced/unspliced matrices, model diagnostics, velocity plots, and a clear note on the method's assumptions and limitations.

### 26. Cell-cell communication and ligand-receptor analysis

Methods such as CellChat, CellPhoneDB, LIANA, and NicheNet infer possible signaling relationships from expression data and curated interaction resources. They do **not** directly measure ligand binding or prove that signaling occurred. Consider spatial context and validate important hypotheses independently.

- **Topic-specific video search:** [CellChat, CellPhoneDB, and ligand-receptor analysis](https://www.youtube.com/results?search_query=CellChat+CellPhoneDB+LIANA+single+cell+RNA-seq+cell+cell+communication+tutorial+English)
- **Trajectory and cell-cell communication lecture/tutorial:** [Single Cell RNA-seq Workshop — Lecture 14](https://wcresko.github.io/scRNAseq_tutorial/Lecture_Folder/Lecture_14_Trajectory_CellCommunication.html)
- **Practical code companion:** [CellChat tutorial repository](https://github.com/jinworks/CellChat)

**Hands-on output:** sender/receiver cell groups, ranked candidate interactions, database/method details, and an explicit distinction between inferred communication and experimentally validated signaling.

### 27. Gene regulatory networks and transcription-factor activity

SCENIC and pySCENIC infer candidate transcription-factor regulons and their activity from expression patterns and motif information. These are advanced analyses that depend on species-specific references and suitable gene coverage.

- **Video:** [SCENIC Video Tutorial 1 — Introduction and Setup](https://www.youtube.com/watch?v=9K6S8BmPJ0A)
- **Additional topic search:** [SCENIC and pySCENIC single-cell gene regulatory network tutorials](https://www.youtube.com/results?search_query=SCENIC+pySCENIC+single+cell+gene+regulatory+network+tutorial+English)
- **Practical code companion:** [SCENIC / pySCENIC resources](https://github.com/aertslab/SCENIC)

**Hands-on output:** regulon activity results, QC/coverage checks, and a short list of well-supported regulatory hypotheses rather than a claim that every inferred edge is causal.

### 28. Multimodal single-cell data: CITE-seq, hashing, V(D)J, and multiome

These workflows apply only when the experiment includes modalities beyond gene expression. Examples include antibody-derived tags (ADT), sample hashtag oligos (HTO), T-cell/B-cell receptor sequences, guide capture, or paired RNA/ATAC data. Use assay-specific quality control and keep modality-specific counts and metadata distinct.

- **Video:** [EMBL-EBI — Multi-omics recording](https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=dc816b23-8148-4051-9195-b3e800d259d1)
- **Additional video search:** [CITE-seq, Cell Hashing, V(D)J and single-cell multiome analysis](https://www.youtube.com/results?search_query=CITE-seq+Cell+Hashing+VDJ+single+cell+multiome+analysis+tutorial+English)
- **10x processing tutorials:** [Cell Ranger tutorials](https://www.10xgenomics.com/support/software/cell-ranger/latest/tutorials)

**Hands-on output:** a separate QC summary for every assay, correctly linked cell/sample barcodes, and a clear explanation of which modalities contribute to each result.

### 29. Spatial transcriptomics integration *(adjacent advanced module)*

Spatial transcriptomics is a related but distinct workflow. If you have a spatial dataset, learn its platform-specific data structure and quality-control metrics before mapping cell types or signatures from scRNA-seq. Do not assume every spatial platform measures individual cells in the same way.

- **Topic-specific video search:** [Single-cell and spatial transcriptomics integration with Seurat](https://www.youtube.com/results?search_query=Seurat+single+cell+spatial+transcriptomics+integration+tutorial+English)
- **Related multi-omics recording:** [EMBL-EBI — Multi-omics](https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=dc816b23-8148-4051-9195-b3e800d259d1)

**Hands-on output:** spatial QC figures, cell-type/signature mapping results, and a note about the resolution and limitations of the platform used.

---

## Phase G — Figures, validation, and reproducible delivery

### 30. Create publication-ready figures

Prepare a coherent set of plots that supports the biological question instead of presenting every possible plot. A typical figure set includes sample/QC summaries, UMAPs, marker plots, annotation support, condition comparisons, differential-expression results, and pathway summaries. Keep plot scales and group labels consistent when figures are compared.

- **Video:** [Sanbomics — visualization and downstream analysis](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Video:** [Bioinformagician — Seurat workflow and plotting](https://www.youtube.com/watch?v=5HBzgsz8qyk)
- **Additional video search:** [Publication-quality plots for single-cell RNA-seq](https://www.youtube.com/results?search_query=publication+quality+single+cell+RNA-seq+plots+Seurat+Scanpy+tutorial+English)

**Hands-on output:** an organized figure directory with editable source code, clear legends, sample sizes, statistical methods, and adjusted p-values where applicable.

### 31. Validate important findings and check robustness

Check important cell annotations against multiple markers or independent references. Repeat key analyses under reasonable QC thresholds, clustering resolutions, and integration choices. Validate high-priority biological findings using independent datasets, orthogonal measurements, or experiments where possible.

- **Core workflow:** [Sanbomics — complete single-cell analysis walkthrough](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Advanced interpretation:** [Single-cell trajectory and cell-cell communication lecture](https://wcresko.github.io/scRNAseq_tutorial/Lecture_Folder/Lecture_14_Trajectory_CellCommunication.html)

**Hands-on output:** a short robustness report explaining which results were stable, which changed with analysis choices, and which remain uncertain.

### 32. Save, document, and share the analysis

Keep raw data separate from derived files. Record software/package versions, reference genome and annotation versions, commands or scripts, parameters, filtering decisions, and data accessions. Save the final analysis object and the minimal code needed to recreate key tables and plots. Check data-sharing and consent restrictions before publishing any human-derived data.

- **General reproducible workflow:** [Sanbomics — notebook-based single-cell analysis](https://www.youtube.com/watch?v=uvyG9yLuNSE)
- **Free video search:** [Reproducible computational biology and data sharing](https://www.youtube.com/results?search_query=reproducible+research+single+cell+RNA-seq+analysis+data+sharing+tutorial+English)

**Hands-on output:** a README for the analysis project, environment/package versions, a metadata dictionary, scripts or notebooks, a record of all input accessions, and a clear description of any manual decisions.

---

## Advanced analysis modules

Use these when your scientific question specifically calls for them. They are extensions of the core workflow, not universal requirements.

| Research question | Methods to explore | Video / practical starting point |
|---|---|---|
| Which genes distinguish clusters? | Seurat `FindAllMarkers`, Scanpy `rank_genes_groups` | [Seurat workflow](https://www.youtube.com/watch?v=5HBzgsz8qyk) · [Scanpy workflow](https://www.youtube.com/watch?v=JGktZRG5JKk) |
| Which genes change between conditions within a cell type? | Pseudobulk + DESeq2/edgeR; design-aware alternatives | [Pseudobulk DESeq2 tutorial](https://www.youtube.com/watch?v=04gB2owLKus) |
| Are cell populations more or less abundant between groups? | Milo, propeller, sample-level composition methods | [Milo/differential abundance video search](https://www.youtube.com/results?search_query=single+cell+RNA-seq+differential+abundance+MiloR+tutorial+English) |
| How do samples align while preserving biology? | Harmony, Seurat integration, scVI | [Harmony](https://www.youtube.com/watch?v=zEuqhiu341I) · [Sanbomics / scVI](https://www.youtube.com/watch?v=uvyG9yLuNSE) |
| What is the inferred order of a cell-state continuum? | Monocle3, Slingshot, PAGA, tradeSeq | [Monocle3 trajectory tutorial](https://www.youtube.com/watch?v=iq4T_uzMFcY) |
| What is the inferred direction of transcriptional change? | velocyto, scVelo | [RNA velocity walkthrough](https://www.youtube.com/watch?v=AUiYxtGJYtg) |
| Which cell groups may signal to one another? | CellChat, LIANA, CellPhoneDB, NicheNet | [Communication analysis video search](https://www.youtube.com/results?search_query=CellChat+CellPhoneDB+LIANA+single+cell+RNA-seq+cell+cell+communication+tutorial+English) |
| Which transcription factors may regulate cell states? | SCENIC, pySCENIC | [SCENIC setup video](https://www.youtube.com/watch?v=9K6S8BmPJ0A) |
| How can RNA be combined with antibody/ATAC/receptor data? | CITE-seq, WNN, multiome, V(D)J | [EMBL-EBI multi-omics recording](https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=dc816b23-8148-4051-9195-b3e800d259d1) |

---

## Practical project checklist

Use this as a final checklist for a portfolio-quality analysis. Adapt it to the study rather than forcing every optional analysis onto every dataset.

- [ ] State the biological question and define the correct biological replicate.
- [ ] Download a public dataset and preserve its source accession and license/usage details.
- [ ] Create a metadata table that matches every sample and barcode to the correct labels.
- [ ] Inspect raw FASTQ QC if raw reads are available.
- [ ] Generate a count matrix with a recorded software, reference, and parameter set.
- [ ] Save processing summaries and compare sequencing/processing metrics by sample.
- [ ] Build an analysis object with intact raw counts and correct metadata.
- [ ] Plot cell-level and sample-level QC metrics before filtering.
- [ ] Record filtering decisions and cell numbers before and after QC.
- [ ] Evaluate doublets and ambient RNA when appropriate.
- [ ] Normalize expression and select features using a documented workflow.
- [ ] Run PCA/dimensionality reduction, build the neighbor graph, and cluster cells.
- [ ] Inspect UMAPs by cluster, sample, condition, and QC metric.
- [ ] Test whether integration is needed; compare results before and after integration.
- [ ] Identify cluster markers and annotate cell types with multiple lines of evidence.
- [ ] Perform subclustering only when the question and evidence support it.
- [ ] Use a replicate-aware design for condition-level differential expression.
- [ ] Evaluate differential abundance if the biology includes changes in cell composition.
- [ ] Perform pathway analysis and signature scoring where relevant.
- [ ] Run trajectory, RNA velocity, communication, or regulatory-network analysis only when justified.
- [ ] Create figures with readable legends, sample sizes, and statistical details.
- [ ] Check robustness and validate the most important biological findings.
- [ ] Save code, environment versions, metadata definitions, and final objects.
- [ ] Write a project README explaining the workflow, results, limitations, and how to reproduce the analysis.

---

## Common mistakes to avoid

1. **Using a single universal QC cutoff.** Thresholds depend on sample type, chemistry, sequencing depth, and biological context.
2. **Treating cells as independent biological replicates.** In multi-sample studies, inference about a condition generally needs the donor/sample structure to be respected.
3. **Integrating before checking individual samples.** Perform sample-level QC first and verify that integration preserves biological differences.
4. **Using integrated expression values for every downstream test.** Use the appropriate original count data and statistical model for differential expression.
5. **Assigning identities from one marker or one automatic label.** Check marker combinations, tissue context, reference suitability, and conflicting evidence.
6. **Reading UMAP distance as a precise measure of biology.** UMAP is a visualization, and apparent distances can be misleading.
7. **Interpreting inferred trajectories or ligand-receptor pairs as proof.** These methods generate hypotheses that need independent evidence.
8. **Ignoring software and reference versions.** Version changes can affect results and syntax; record them and follow the version-specific workflow.

---

## Recommended free software

These tools are commonly used in single-cell analysis and have free-to-use software or open-source options. Always check each project's current license, platform support, and installation requirements.

| Task | Tools to consider |
|---|---|
| FASTQ inspection | FastQC, MultiQC |
| Barcode-aware read processing and count matrix | STARsolo, kallisto-bustools; Cell Ranger is a no-cost but proprietary option for supported assays |
| R-based analysis | Seurat, SingleCellExperiment, scater, scran, Bioconductor |
| Python-based analysis | Scanpy, AnnData, scvi-tools |
| Doublet detection | Scrublet, DoubletFinder, scvi-tools methods |
| Ambient RNA correction | SoupX, CellBender |
| Batch correction / integration | Harmony, Seurat integration methods, scvi-tools |
| Cell annotation | Marker-based annotation, SingleR, CellTypist |
| Pseudobulk differential expression | DESeq2, edgeR, limma |
| Pathway analysis | clusterProfiler, GSEA tools, gseapy |
| Trajectory inference | Monocle3, Slingshot, PAGA |
| RNA velocity | velocyto, scVelo |
| Cell-cell communication | CellChat, LIANA, CellPhoneDB, NicheNet |
| Gene regulatory networks | SCENIC, pySCENIC |

Supporting project links: [Seurat](https://satijalab.org/seurat/) · [Scanpy](https://scanpy.readthedocs.io/) · [Bioconductor](https://bioconductor.org/) · [scvi-tools](https://scvi-tools.org/) · [STARsolo](https://github.com/alexdobin/STAR) · [kallisto | bustools](https://www.kallistobus.tools/) · [CellTypist](https://www.celltypist.org/)

---

## How to contribute

Contributions are welcome, especially for **free English-language video tutorials** that are hands-on, accurate, and still accessible.

Before opening a pull request:

1. Add the direct video or playlist link, not just the creator's channel homepage.
2. Confirm the video is in English and can be watched without paying for a course.
3. Name the workflow step it teaches and summarize the practical outcome.
4. Prefer videos that show real code, data, parameter choices, and interpretation.
5. Note the software version if the video relies on a specific version or older syntax.
6. Do not upload or re-host videos; link to the original creator.

If a direct video cannot be verified, label the link as a YouTube topic search rather than presenting it as an individual video recommendation.

---

## Search keywords

Single-cell RNA-seq analysis, scRNA-seq pipeline, single-cell transcriptomics, Seurat tutorial, Scanpy tutorial, scvi-tools, Cell Ranger, STARsolo, count matrix generation, single-cell quality control, doublet detection, ambient RNA correction, normalization, highly variable genes, PCA, UMAP, clustering, batch correction, data integration, cell-type annotation, SingleR, CellTypist, differential expression, pseudobulk, DESeq2, differential abundance, gene-set enrichment, pathway analysis, gene signature scoring, trajectory inference, pseudotime, Monocle3, Slingshot, RNA velocity, scVelo, cell-cell communication, CellChat, SCENIC, CITE-seq, multiome, spatial transcriptomics, reproducible single-cell analysis.

---

**Resource review date:** 30 October 2026. Videos and software pages can change or be removed; please open links before relying on a tutorial for a current software version.
