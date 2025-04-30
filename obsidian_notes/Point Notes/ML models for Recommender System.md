---
tags:
  - chatgpt
  - recommender_system/architecture
aliases: 
date of note: 2025-04-07
---


>[!question]
>can you recommend popular ML models in content recommendation and recommender system?


### 🧱 **Classical & Matrix Factorization Models**

#### 1. **Collaborative Filtering**

- **User-Item Matrix**, often using **Cosine Similarity** or **Pearson Correlation**
    
- Simple, interpretable, but doesn't scale well or handle cold-start users/items
    

#### 2. **Matrix Factorization Models**

- **SVD (Singular Value Decomposition)**
    
    - Decomposes the user-item interaction matrix
        
- **FunkSVD** (used in Netflix Prize)
    
- **NMF (Non-negative Matrix Factorization)**
    

#### 3. **k-Nearest Neighbors (kNN)**

- `KNNBasic`, `KNNWithZScore` (available in [Surprise](http://surpriselib.com/) library)
    
- Good for small datasets or as baselines
    

---

### 📦 **Tree-Based Models**

#### 4. **Gradient Boosting (XGBoost, LightGBM, CatBoost)**

- Used in **learning-to-rank** setups
    
- Great for combining features (user behavior, content metadata)
    
- Often paired with **feature engineering pipelines**
    

#### 5. **Random Forests**

- Less common now, but sometimes used for hybrid recommenders
    

---

### 🧠 **Deep Learning-Based Models**

#### 6. **Neural Collaborative Filtering (NCF)**

- Combines matrix factorization and deep neural networks
    
- Paper: _"Neural Collaborative Filtering" (He et al., 2017)_
    

#### 7. **Wide & Deep Learning (Google)**

- Combines memorization (wide) and generalization (deep)
    
- Ideal for recommender systems with many categorical features
    

#### 8. **DeepFM**

- Combines **Factorization Machines (FM)** and DNNs
    
- Good for sparse + dense feature interactions
    

#### 9. **Autoencoders**

- Used for collaborative filtering (e.g., **Variational Autoencoders** for CF)
    
- Learns user/item embeddings via reconstruction
    

---

### 🔄 **Sequential/Session-Based Models**

#### 10. **RNNs / GRUs**

- Used for **session-based recommendations**
    
- Models like **GRU4Rec** are designed for sequence-based predictions
    

#### 11. **Transformers**

- Like **SASRec**, **BERT4Rec**, **RecBole** framework
    
- Handles long user behavior sequences, trending in modern RS
    

---

### 🌐 **Graph-Based Models**

#### 12. **Graph Neural Networks (GNNs)**

- Models like **PinSage (Pinterest)**, **LightGCN**, **NGCF**
    
- Leverages user-item interaction as a bipartite graph
    

---

### 🧪 **Other Specialized Models**

#### 13. **Reinforcement Learning (RL)**

- Ex: **Bandits**, **Deep Q-Learning**, **SlateQ**
    
- Used in dynamic/adaptive recommenders (exploration vs exploitation)
    

#### 14. **Hybrid Recommenders**

- Combine collaborative + content-based
    
- Ensemble models (e.g., LightGBM on top of NCF + content + metadata)
    

---

### 🧰 Useful Libraries/Frameworks:

- [Surprise](http://surpriselib.com/) (for classical CF, matrix factorization)
    
- LightFM (hybrid models)
    
- [RecBole](https://recbole.io/) (deep learning recommender models)
    
- TensorFlow Recommenders (TFRS)
    
- [Microsoft Recommenders GitHub](https://github.com/microsoft/recommenders) – ⭐️ tons of models



-----------
##  Recommended Notes