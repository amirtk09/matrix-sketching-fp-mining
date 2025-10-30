<div align="center">

# 🧩 Matrix Monitoring for Accelerating Frequent Pattern Mining

**Notebook:** `CDM__1_Final.ipynb`  
**Dataset:** [Online Retail Dataset (UCI Machine Learning Repository)](https://archive.ics.uci.edu/dataset/352/online+retail)  
**Author:** AmirHossein Talebi Koohestani  

</div>

---

## 📖 Project Overview

This project investigates how **matrix sketching and monitoring techniques** can accelerate **frequent pattern mining algorithms**, specifically the **FP-Growth** algorithm.  

By applying low-rank approximation and sketching methods such as **Gaussian Random Projection (GRP)**, **Incremental PCA (IPCA)**, and **Sparse Frequent Directions (SpFD)**, we evaluate trade-offs between **runtime**, **memory efficiency**, and **pattern stability** in large-scale transactional data.

---

## 🎯 Objectives

- Compress large transaction matrices efficiently while preserving key structural information.  
- Compare different sketching algorithms for:
  - Reconstruction accuracy  
  - Computational efficiency  
  - Robustness to injected anomalies  
- Evaluate performance of FP-Growth on original vs. sketched matrices.

---

## 🧠 Techniques Implemented

| Technique | Description |
|------------|-------------|
| **GRP (Gaussian Random Projection)** | Projects the matrix onto a lower-dimensional random Gaussian subspace. Simple, fast, and effective for large-scale data. |
| **IPCA (Incremental PCA)** | TensorFlow-based incremental PCA that updates principal components over streaming batches. Useful for memory-constrained settings. |
| **SpEmb (Sparse Embedding)** | Sparse random embedding for efficient linear dimensionality reduction with reduced storage cost. |
| **SpFD (Sparse Frequent Directions)** | Combines sparse embeddings and the Frequent Directions algorithm for low-rank approximation. Highly efficient and stable.<br><br>Reference: <br> D. Teng and D. Chu, *“A Fast Frequent Directions Algorithm for Low Rank Approximation,”* IEEE TPAMI, vol. 41, no. 6, pp. 1279–1293, June 2019. DOI: [10.1109/TPAMI.2018.2839198](https://doi.org/10.1109/TPAMI.2018.2839198). |

---

## 🧩 Methodology

1. **Load** and clean the Online Retail dataset.  
2. **Build** a binary item–transaction matrix (`InvoiceNo × StockCode`).  
3. **Split** transactions chronologically into batches.  
4. **Apply** sketching algorithms (GRP, IPCA, SpFD, SpEmb).  
5. **Evaluate** reconstruction quality:
   - Frobenius norm error
   - Explained variance ratio
   - Execution time  
6. **Run FP-Growth** on both original and sketched matrices to compare mining results.  
7. **Inject anomalies** and assess each model’s stability and sensitivity.

---

## 📊 Evaluation Metrics

| Metric | Meaning |
|---------|----------|
| **Reconstruction Error** | Relative Frobenius norm between original and reconstructed matrices. |
| **Explained Variance Ratio** | Percentage of total variance retained by the sketched data. |
| **Execution Time** | Processing time per cumulative batch. |
| **Pattern Stability** | Similarity between itemsets found in original vs. reduced matrices. |
| **Detection Ratio** | (Average error on anomalous data) ÷ (Average error on normal data). Indicates robustness. |
