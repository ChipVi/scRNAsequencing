# Single-cell RNA sequencing
In this project, I work with human mitochondria RNA counts data.

## Preprocessing dataset
  * Quality control, filtering low quality cells by number of genes and number of counts.
  * Normalization 
  * Select highly variable genes (genes that have high variance across types of cells): choose top 5000 genes
      -> We can use this feature to classify different types of cells later.
  * PCA to reduce dimensions and extract more distinguished features by variance ratio.
  * Clustering:
      1. Use Harmony to minimize the batch differences
      2. Use K-nearest-neighbors build KNN graph from PCA: for each cell, find its k most similar cells (based on PCA)
      3. Draw UMAP clustering diagrams of 3 types: Leiden (similar gene expressions), cell_type, assays (similar batch conditions).

## Classification Cell types

 * Use Geneformer to turn gene expressions - counts of RNA sequences into embeddings, by letting the model learn and infer on the train and test set correspondingly. This helps extract compact features of the dataset based on a model (BERT) that has been trained to learn correct representations of genes, thus helps reducing 28k expression counts into 768 embeddings.
 * Use a classic Machine Learning classifier which is Random Forest to classify cell types based on 768 embeddings from the previous step.
