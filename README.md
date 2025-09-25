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
  Based on: *Fisher & Salzberg (1989), "Online Hierarchical Clustering Approximations"*  - **OPRC (Online Projected Random Cut) → *Proposed Method***  
  - Designed to extend PRC into an **online setting**.  
  - Works by projecting high-dimensional data into 1D and then applying a dynamic version of RCT (ORC).  
  - Algorithm dynamically inserts new points into the existing tree structure without recomputing from scratch.  
  - ⚠️ While in theory OPRC may seem inefficient in worst-case scenarios, our **empirical results demonstrate strong performance and fast runtime in practice**.  
---
## ⏱️ Runtime Comparison

![Runtime Comparison] ## ⏱️ Runtime Comparison

![Runtime Comparison](Online-Hierarchical-Clustering/download.png))

---
## 📖 References
- Menon, Aditya Krishna, Anand Rajagopalan, Baris Sumengen, Gui Citovsky, Qin
Cao, and Sanjiv Kumar. ”Online hierarchical clustering approximations.” arXiv preprint
arXiv:1909.09667 (2019).  
  [🔗 Paper link](https://arxiv.org/abs/1909.09667)
