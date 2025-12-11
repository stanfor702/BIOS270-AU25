Project 2 Writeup
Alex Stanford


Primary Objective: The primary objective of this project is to assess differences in Malaria specific B cells in terms of phenotype, gene expression, and BCR characteristics.

Rationale: This project is important because it will interrogate unknown differences in various immune states enriched in Plasmodium falciparum infection, providing insights for vaccine design. 

Aim 1: Determine how antigen specificity impacts the phenotype of memory B cells.
Expected outcomes: We expect B cell phenotypes to vary based on antigen specificity with blood stage specific cells to have a greater proportion of cells with an atypical phenotype. 
Potential Challenges: Potential challenges with this aim are the antigenic probes having non-specific binding, to address this, we will test each probe and treat cells with blocking antibodies or neuraminidase if non-specific binding occurs.

Aim 2: Determine how antigen specificity impacts the functionality of the BCRs
Expected outcomes: We expect B cells specific for blood stage antigens to have higher affinities and greater parasite neutralization capacity.
Potential Challenges: Potential challenges with this aim would be expressing IgM switched specific cells in this isotype to assess the affects of avidity. To address this we may express the transcripts first in an IgG backbone, assessing affinity and neutralization before attempting to express the BCR in its pentameric form. 

Data
Source: Lab generated ssRNA and BCRseq data 
Size: 3 sample libraries; 1 for gene expression, 1 for VDJ, and  1 for feature barcodes
Format: FASTQ

Data Suitability: The current format is not optimal for downstream processing and multiple transformations and preprocessing steps will be necessary including aligning the reads to the human genome and assembling BCR clone contigs. To do this and outport in a hierarchal HDF5 format, I will install and utilize the package cellranger on our labs servers.  

Storage and data management
	- The original dataset will be stored on my lab's servers 
	- The backup for the data set will be uploaded to cloud service providers such as Box.
	- To share the processed data with collaborators I will upload matrices to a Github repo and share this with them.

Environment 
Coding environment
	- To process and QC my FASTQ files and get them into an HDF5 format, I will code on my server, establishing a conda environment which will contain programs of necessity such as cellranger, bcl2fastq, basespace authentication, MiXCR, etc. 
	- After cell ranger outputs are achieved, my coding environment will be on my local machine for the beginning of the project. Upon looking at larger data sets I will move the environment to my labs servers and establish a port connection to my IDE of choice. Pipelines will be test and written in an R notebook. 
	- Dependencies 
		○ Preprocessing tools: cellranger, bcl2fastq, basespace authentication, MiXCR
		○ Post-processing Tools (R libraries):  Tidyverse(9 different packages), hdf5r, Seurat, patchwork, Matrix, tibble, ggridges, ggally, corrplot, MASS, pheatmap
Reproducibility
	- My code and scripts will be uploaded to a Github repository to easy acesss. 
	- I will have my conda environment and all the dependencies and packages neatly saved in a yaml file to allow people to use the exact versions of packages I used in analyzing the data. This will hopefully prevent version control issues if new versions of packages come out that may not be compatible with the established pipeline. 
	- Additionally, I will use a Dockerfile to document the different versions of R/python, system-dependencies, and packages installed, to ensure people can run this regardless of the type of machine they are on. 
Pipeline 
	- Computational steps  following cellranger processing will be done in R utilizng the seurat pipeline. The steps of this pipeline include reading and QCing the cell outputs from cellranger before normalizing and modeling by PCA.
	- To ensure the pipeline runs efficiently on my dataset size, format, and number of samples, I will build out the pipeline in chunked batches of the data, in hopes of using the memory more efficiently. 

Machine Learning
Task: a potential supervised machine learning task would be to take the BCR sequences of known specificity and use them in a model to predict the specificities of BCRs of unknown specificity.

Feature presentation:  I am not completely sure how I would convert the raw data into a numerical form for the model.  I would potentially have a method that maps the AA sequence into some integer.

Model selection: I might choose a Deep sequence machine learning model because the order of the nucleotide and amino acid sequences are an essential pattern that impacts binding specificity. 

Generalization strategy: To ensure my model performs well on unseen data I would split clonotypes between training and test sets 

Evaluation metrics: I think tracking precision-recall AUC might be appropriate for the task at hand due to specific B cell specificities being rare making it not the most balance data set. 
