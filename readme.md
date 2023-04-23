# 1 - Analysis of the Heart Disease Dataset 
Load the data from
[here](https://raw.githubusercontent.com/jpinero/DMI_2021/main/datasets/heart_disease_dataset.csv), and the description is [here](https://raw.githubusercontent.com/jpinero/DMI_2021/main/datasets/heart_disease_description.txt). 
The original dataset comes from [here](https://archive.ics.uci.edu/ml/datasets/Heart+Disease) and corresponds to the [processed cleveland data](https://archive.ics.uci.edu/ml/machine-learning-databases/heart-disease/processed.cleveland.data)

## Perform an EDA on the dataset
Create visualizations in order to show which variables seem to be more associated with heart disease


## Difference in mortality rates in hospitalized COVID-19 patients 
Using the supplementary material from the [Difference in mortality rates in hospitalized COVID-19 patients identified by cytokine profile clustering using a machine learning approach: An outcome prediction alternative](https://www.frontiersin.org/articles/10.3389/fmed.2022.987182/full), perform the following tasks

## Reproduce Figure 1 from the publication
## Reproduce Figure 2 from the publication
but instead of representing the clusters in the annotation, represent the groups (G1 to G4)

## Improve figure 2 of the publication
Add a second annotation with information of deathm and a third one with information of gender


# 2 - Clustering and Dimensionality reduction

## Clustering gene expression data in healthy tissues

Download the [data](https://www.ebi.ac.uk/biostudies/arrayexpress/studies/E-MTAB-6081) (design and tpm files) corresponding to the publication [An RNASeq normal tissue atlas for mouse and rat](https://www.nature.com/articles/sdata2017185). 
Download the [gene expression data](https://storage.googleapis.com/gtex_analysis_v8/rna_seq_data/GTEx_Analysis_2017-06-05_v8_RNASeQCv1.1.9_gene_median_tpm.gct.gz) corresponding to the publication  [The Genotype-Tissue Expression (GTEx) pilot analysis: multitissue gene regulation in humans](https://www.science.org/doi/10.1126/science.1262110) from  the [GTEX portal](https://gtexportal.org/home/datasets)

From GTEX data, keep only tissues belonging to the following categories:  


```
gtex_tissues = ["colon", "ileum", "duodenum", "jejunum", "small intestine"  , "muscle", "pancreas", "liver", "stomach",  "kidney",  "quadriceps", "thymus", "heart" ,    "esophagus", "brain" ]
```

Cluster tissues using gene expression data. Run k-means and hierarchical clustering. For each algorithm, determine the optimal number of clusters. 

Compare the clustering results using both methodologies, and with the tissues/species. Show the results of the final partitions as a table. 


Plot a heatmap of the 50 genes with top variance over all samples. Add the information about tissue groups and model (human, rat and mouse) as annotations in the heatmap*. 

## PCA 
With the gene expression for different tissues and models, perform a PCA on the data and visualize the results (PC1 and PC2, and also, PC3 ). Label the points in the plot with their respective tissues/models. 

Visualize the data using the PC1 and PC2 again, but this time, color the observations by cluster, using the k means clusters, with k of your choice. Produce a caption for the plot


What are the top 50 genes that contribute to the PC1? Are they the same genes that are more variable according to the exercise 1?

## tSNE 

Perform t-SNE on the dataset and visualize the results. Test at least 2 perplexity values.


# 3 - Machine Learning 
KNN, decision trees, random forest, logistic regression, linear discriminant analysis 

## part 1

[Stamey et al. 1989](https://www.auajournals.org/doi/10.1016/S0022-5347%2817%2941175-X) examined the correlation between the level of prostate-specific antigen (PSA) and a number of clinical measures in men who were about to receive a radical prostatectomy. PSA is a protein that is produced by the prostate gland. The higher a man’s PSA level, the more likely it is that he has prostate cancer.  
Use the [prostate cancer dataset](data/prostate_data.txt), described [here](data/prostate_description.txt),  to train a model that predicts log of prostate-specific antigen. 
The variables are    

- log cancer volume (lcavol)  
- log prostate weight (lweight)  
- age  
- log of the amount of benign prostatic hyperplasia (lbph)   
- seminal vesicle invasion (svi)  
- log of capsular penetration (lcp)  
- Gleason score (gleason)    
- percent of Gleason scores 4 or 5 (pgg45)  

You can ignore column named "train" and do your own data splitting.  
Do not forget to perform feature selection!   
You can use as examples the [Linear Regression Lab](https://hastie.su.domains/ISLR2/Labs/Rmarkdown_Notebooks/Ch3-linreg-lab.html) and the section related to feature selection from  [Lab: Linear Models and Regularization Methods
](https://hastie.su.domains/ISLR2/Labs/Rmarkdown_Notebooks/Ch6-varselect-lab.html) from the book [An Introduction to Statistical Learning](https://www.statlearning.com/).


## part 2

Use the [breast cancer dataset](data/breat_cancer_data.csv) to train a model that predicts whether a future tumor image (with unknown diagnosis) is a benign or malignant tumor. Try different machine learning algorithms such as:   
- KNNs  
- Decision trees  
- Random forest  
- Logistic Regression  

The breast cancer dataset contains digitized breast cancer image features, and was created by [Dr. William H. Wolberg, W. Nick Street, and Olvi L. Mangasarian](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29). Each row in the data set represents an image of a tumor sample, including the diagnosis (benign or malignant) and several other measurements (nucleus texture, perimeter, area, and more). Diagnosis for each image was conducted by physicians.

Do not forget to perform hyperparameter tuning!   
Which of all models performs better for this data? Discuss.  

Generate a ROC curve for all the models. 

You can use as a guide the analysis of this dataset included in the [chapter 5](https://datasciencebook.ca/classification1.html) of the Data Science, A First Introduction Book.
Additionally, for further information and ideas, you can check [this post](https://www.rebeccabarter.com/blog/2020-03-25_machine_learning/)


## part 3  

Use [The Cancer Genome Atlas (TCGA)](https://www.genome.gov/Funded-Programs-Projects/Cancer-Genome-Atlas) gene expression data of two different cancer types to build a machine learning model that identifies whether one unknown sample belongs to one or the other. The TCGA is a comprehensive and coordinated effort to accelerate our understanding of the molecular basis of cancer through the application of genome analysis technologies, including large-scale genome sequencing. The program has generated, analyzed, and made available genomic sequence, expression, methylation, and copy number variation data on over 11,000 individuals who represent over 30 different types of cancer. 
After building your model, you should predict the cancer types for [10 unkwnon samples](data/unknwown_samples.tsv).  

For this task, you should retrieve the TCGA data from the [Genomic Data Commons Data Portal](https://portal.gdc.cancer.gov/). If necessary you can watch the video uploaded in the Campus Global. The video assumes that you have previously installed the [GDC data transfer tool](https://gdc.cancer.gov/access-data/gdc-data-transfer-tool). 

Each team will work with two specific cancer types, that will be assigned in class.

Important notice: if you do not have a lot of hard drive space in your laptop, you can modify the manifest file to download only 50 samples per cancer types. 
As part of the assignment, you should provide the input data fed to the machine learning algorithm as a tsv file. 
