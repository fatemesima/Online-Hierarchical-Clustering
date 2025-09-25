# Online Hierarchical Clustering for Data Streams

This repository contains the implementations of **hierarchical clustering algorithms** and their online/streaming adaptations.  
The work was developed as part of my Master's thesis on **data stream clustering**.  

---

## 📌 Overview

Traditional hierarchical clustering algorithms (such as HAC) are **offline** and require the entire dataset to be available beforehand.  
To address this limitation, we explore and implement several **online/streaming hierarchical clustering algorithms** that can incrementally update the cluster structure as new data points arrive.  

In particular, this repository includes:  
- **Offline algorithms:** RCT and PRC  
- **Online/streaming algorithms:** OHAC, OTD, and our proposed method **OPRC**  


---

## ⚙️ Implemented Algorithms

### Offline Algorithms
- **HAC (Hierarchical Agglomerative Clustering)**  
  Standard bottom-up clustering applied in batch mode.  

- **TD (Tree Divisive Clustering)**  
  Standard top-down hierarchical clustering, applied to the whole dataset.  
- **RCT (Random Cut Tree):**  
  Constructs a binary partitioning of the dataset by recursively cutting intervals using uniformly random splits.  

- **PRC (Projected Random Cut):**  
  - A multidimensional extension of RCT.  
  - Projects the data into 1D using a Gaussian random vector, then applies the Random Cut procedure.  
  - Offline by design since it requires all data points to be available in advance.  
### Online / Streaming Algorithms
- **OHAC (Online Hierarchical Agglomerative Clustering)**  
  Online adaptation of HAC for streaming data.  
  Based on: *Fisher & Salzberg (1989), "Online Hierarchical Clustering Approximations"*  
- **OTD (Online Tree Divisive Clustering)**  
  Online version of Tree Divisive clustering for streaming environments.  
  Based on: *Fisher & Salzberg (1989), "Online Hierarchical Clustering Approximations"*

- **OPRC (Online Projected Random Cut) → *Proposed Method***  
  - Designed to extend PRC into an **online setting**.  
  - Works by projecting high-dimensional data into 1D and then applying a dynamic version of RCT (ORC).  
  - Algorithm dynamically inserts new points into the existing tree structure without recomputing from scratch.  
  - ⚠️ While in theory OPRC may seem inefficient in worst-case scenarios, our **empirical results demonstrate strong performance and fast runtime in practice**.  

---

## Proposed Algorithm Steps  

1. **Base Case:**  
   If \( x_{n+1} = x_1 \), then set it as the root of the tree.  

2. **Case 1 – Outside Interval:**  
   Otherwise, if \( x_{n+1} \) is **not** in the interval \((x_1, x_n)\):  
   - Apply the **offline random cut algorithm** on the points  
     \[ x_1 \leq x_2 \leq \dots \leq x_n \leq x_{n+1} \].  
   - This is done by selecting a uniform random point \( r \) in the range \((x_1, x_n)\), and splitting this interval into left and right sub-intervals using \( r \) as the divider.  
   - Recursively repeat this process until reaching the leaves.  
   - The resulting tree is returned as the output.  

3. **Case 2 – Inside Interval:**  
   Otherwise, if \( x_{n+1} \) **is** in the interval \((x_1, x_n)\):  
   - Let \( r \) be the value that splits the root’s points into two subtrees:  
     - Left subtree: \( T^{-} \)  
     - Right subtree: \( T^{+} \)  
   - Compare the new point \( x_{n+1} \) with \( r \):  
     - If \( x_{n+1} < r \), recursively apply the algorithm on the **left subtree** with \( x_{n+1} \).  
       - The output tree is: \(\text{ORC}(T^{-}, x_{n+1}), T^{+}\).  
     - If \( x_{n+1} > r \), recursively apply the algorithm on the **right subtree** with \( x_{n+1} \).  
       - The output tree is: \(T^{-}, \text{ORC}(T^{+}, x_{n+1})\).
       
## 📊 Results Comparison  

In the `results/` folder, we provide the experimental runtime plots for the datasets **Glass, Iris, Zoo, R15, Aggregation, and Pathbased**.  
Additionally, the folder contains a **comparison table** of the accuracy/performance metrics for these algorithms across the mentioned datasets.  

The results show that in most cases, the proposed online algorithm achieves **competitive runtime performance** and maintains **good clustering accuracy** compared to baseline methods.  

---
## 📖 References
- Menon, Aditya Krishna, Anand Rajagopalan, Baris Sumengen, Gui Citovsky, Qin
Cao, and Sanjiv Kumar. ”Online hierarchical clustering approximations.” arXiv preprint
arXiv:1909.09667 (2019).  
  [🔗 Paper link](https://arxiv.org/abs/1909.09667)
