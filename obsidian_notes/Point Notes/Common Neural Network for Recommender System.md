---
tags:
  - chatgpt
  - recommender_system/architecture
aliases: 
date of note: 2025-04-07
---

>[!question]
>what are commonly encountered neural network based model for recommender system

## 🔥 **1. Neural Collaborative Filtering (NCF)**

**Paper:** _He et al., 2017_

- Replaces dot product in matrix factorization with a neural network.
    
- Combines:
    
    - **GMF (Generalized Matrix Factorization)**
        
    - **MLP (Multi-Layer Perceptron)**
        
- Final model: **NeuMF**
    

📌 **Use case:** User-item interaction modeling  
📚 Libraries: TensorFlow Recommenders, RecBole

---

## 🧠 **2. Wide & Deep Learning (Google)**

**Paper:** _Cheng et al., 2016_

- Two-tower structure:
    
    - **Wide**: memorization (linear model)
        
    - **Deep**: generalization (neural network)
        
- Scales well and works great for large, feature-rich datasets.
    

📌 **Use case:** Apps like Google Play recommendations

---

## 🧮 **3. DeepFM (Deep Factorization Machines)**

**Paper:** _Guo et al., 2017_

- Combines the strengths of:
    
    - **Factorization Machines (FM)**: for sparse feature interactions
        
    - **DNNs**: for high-order interactions
        
- Works well with tabular data (click-through, conversion rates)
    

📌 **Use case:** Ad click prediction, e-commerce

---

## 🌀 **4. Autoencoders / Variational Autoencoders (VAE)**

- Used for collaborative filtering via reconstruction.
    
- **Mult-VAE** is a popular variant for user-item implicit feedback.
    
- Learns compressed latent space → used to recommend items
    

📌 **Use case:** Implicit feedback (e.g., likes, views)

---

## ⏱️ **5. Sequence-Based Models (RNN, GRU, LSTM)**

### ▶️ GRU4Rec

**Paper:** _Hidasi et al., 2015_

- Uses GRU for **session-based recommendations**.
    
- Learns the sequence of user actions.
    

📌 **Use case:** E-commerce sessions, playlist generation

---

## 🧬 **6. Transformer-Based Models**

### SASRec (Self-Attentive Sequential Recommender)

**Paper:** _Kang & McAuley, 2018_

- Applies Transformers to model user behavior sequences.
    
- Handles long-term dependencies better than RNNs.
    

### BERT4Rec

**Paper:** _Sun et al., 2019_

- Adapts BERT-style masked language modeling to predict items.
    

📌 **Use case:** Next-item prediction, content streaming (Netflix/Spotify)

---

## 🧱 **7. Two-Tower Models**

- User and item representations are learned separately using DNNs.
    
- Combined via similarity (dot product or cosine).
    
- Extremely scalable, used in:
    
    - **YouTube DNN**
        
    - **Facebook DLRM**
        

📌 **Use case:** Large-scale retrieval (millions of users/items)

---

## 🌐 **8. Graph Neural Networks for Recommendations**

### LightGCN, NGCF, PinSage

- Models the **user-item graph**.
    
- Learns better embeddings via message passing.
    

📌 **Use case:** Pinterest, social recommendations, implicit feedback

---

### 🔧 Bonus: Tools & Frameworks to Explore These Models

- 🔷 **[RecBole](https://recbole.io/)** – Unified framework for deep recommenders
    
- 🔶 **TensorFlow Recommenders** – Production-friendly TF-based models
    
- 🔵 **[Microsoft Recommenders GitHub](https://github.com/microsoft/recommenders)** – Huge collection of models + tutorials
    

---








-----------
##  Recommended Notes

- [[Recommender System]]