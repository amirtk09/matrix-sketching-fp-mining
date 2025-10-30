<div align="center">

# 🧩 Matrix Monitoring for Accelerating Frequent Pattern Mining

**Notebook:** `CDM__1_Final.ipynb`  
**Dataset:** [Online Retail Dataset (UCI Machine Learning Repository)](https://archive.ics.uci.edu/dataset/352/online+retail)  
**Author:** AmirHossein Talebi Koohestani  

</div>

---

## 📖 Project Overview

This project investigates how **matrix sketching and monitoring techniques** can accelerate **frequent pattern mining algorithms**, specifically the **FP-Growth** algorithm.  

By applying low-rank approximation and sketching methods such as **Gaussian Random Projection (GRP)**, **Incremental PCA (IPCA)**, and **Sparse Frequent Directions (SpFD)**, we evaluate trade-offs between reconstruction accuracy, computational efficiency, and robustness.

---

## 🚀 Installation & Setup

### Prerequisites

- **Python 3.8+**
- **pip** (Python package manager)
- **Jupyter Notebook** or **JupyterLab**

### Installation Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/amirtk09/matrix-sketching-fp-mining.git
   cd matrix-sketching-fp-mining
   ```

2. **Install required dependencies:**
   ```bash
   pip install numpy pandas scikit-learn scipy mlxtend tensorflow jupyter
   ```

   Or if you have a `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```
3. **Download the TensorFlow Incremental PCA module (tfpca.py):**

   ```bash
   wget https://raw.githubusercontent.com/lukassnoek/tf-incremental-pca/master/tfpca.py
   ```

   Alternatively, manually download the file from <a href="https://github.com/lukassnoek/tf-incremental-pca">lukassnoek/tf-incremental-pca</a> and place it in the project root directory.

4. **Download the dataset:**
   - Download the [Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail) from UCI Machine Learning Repository
   - Place the `Online Retail.xlsx` file in the project root directory

4. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

5. **Open and run:**
   - Navigate to `CDM__1_Final.ipynb`
   - Run all cells sequentially

### Recommended Environment

For optimal performance, consider using a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

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
| **IPCA (Incremental PCA)** | TensorFlow-based incremental PCA that updates principal components over streaming batches. Useful for memory-constrained settings.<br><br>Reference: <br> [lukassnoek/tf-incremental-pca](https://github.com/lukassnoek/tf-incremental-pca) |
| **SpFD (Sparse Frequent Directions)** | Combines sparse embeddings and the Frequent Directions algorithm for low-rank approximation. Highly efficient and stable. <br><br>Reference: <br> D. Teng and D. Chu, "A Fast Frequent Directions Algorithm for Low Rank Approximation," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 41, no. 6, pp. 1279-1293, 1 June 2019, doi: 10.1109/TPAMI.2018.2839198|

---

## 🧩 Methodology

1. **Load** and clean the Online Retail dataset.  
2. **Build** a binary item–transaction matrix (`InvoiceNo × StockCode`).  
3. **Split** transactions chronologically into batches.  
4. **Apply** sketching algorithms (GRP, IPCA, SpFD).  
5. **Evaluate** reconstruction quality:
   - Frobenius norm error
   - Explained variance ratio
   - Execution time  
6. **Run FP-Growth** on both original and sketched matrices to compare mining results.  
7. **Inject anomalies** and assess each model's stability and sensitivity.

---

## 📊 Evaluation Metrics

| Metric | Meaning |
|---------|----------|
| **Reconstruction Error** | Frobenius norm between original and reconstructed matrices. |
| **Explained Variance Ratio** | Percentage of total variance retained by the sketched data. |
| **Execution Time** | Processing time per cumulative batch. |
| **Pattern Stability** | Similarity between itemsets found in original vs. reduced matrices. |
| **Detection Ratio** | (Average error on anomalous data) ÷ (Average error on normal data). Indicates robustness. |
