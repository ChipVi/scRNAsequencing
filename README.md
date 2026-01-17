# Single-cell RNA sequencing
In this project, I work with human mitochondria RNA counts data.

File 1: 
  * Performing basic data preprocessing: quality control, filtering low quality cells by number of genes and number of counts.
  * Normalization 
  * Select highly variable genes (genes that have high variance across types of cells): choose top 5000 genes
      -> We can use this feature to classify different types of cells later.
  * PCA to reduce dimensions and extract more distinguished features by variance ratio.
  * Clustering:
      1. Use Harmony to minimize the batch differences
      2. Use K-nearest-neighbors build KNN graph from PCA: for each cell, find its k most similar cells (based on PCA)
      3. Draw UMAP clustering diagrams of 3 types: Leiden (similar gene expressions), cell_type, assays (similar batch conditions).
