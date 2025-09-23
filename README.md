# Online Hierarchical Clustering for Data Streams

This repository contains the implementations of **hierarchical clustering algorithms** and their online/streaming adaptations.  
The work was developed as part of my Master's thesis on **data stream clustering**.  

---

## 📌 Overview

Traditional hierarchical clustering algorithms (such as HAC) are offline and require the entire dataset to be available beforehand.  
In this project, I have implemented their **online/streaming versions (OHAC and OTD)** that can incrementally update the cluster structure as new data points arrive.  

---

## ⚙️ Implemented Algorithms

### Offline Algorithms
- **HAC (Hierarchical Agglomerative Clustering)**  
  Standard bottom-up clustering applied in batch mode.  

- **TD (Tree Divisive Clustering)**  
  Standard top-down hierarchical clustering, applied to the whole dataset.  

### Online / Streaming Algorithms
- **OHAC (Online Hierarchical Agglomerative Clustering)**  
  Online adaptation of HAC for streaming data.  
  Based on: *Fisher & Salzberg (1989), "Online Hierarchical Clustering Approximations"*  

- **OTD (Online Tree Divisive Clustering)**  
  Online version of Tree Divisive clustering for streaming environments.  
  Based on: *Fisher & Salzberg (1989), "Online Hierarchical Clustering Approximations"*  
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
