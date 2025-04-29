---
tags:
  - project
  - buyer_seller_messaging
  - multi-modal_learning
aliases: 
date of note: 2025-04-28
---

## Four Designs

### Concatenation

>[!important]
>**Direct concatenation** of two embeddings
>$$
>f_{\text{fuse}} = W_{\text{fuse}}\left[  W_{\text{text}}x_{\text{text}},  W_{\text{tab}}x_{\text{tab}}  \right]
>$$

- [[Multi-modal BERT Classification Model v2 for BSM]]
- [[Multi-modal BERT for FSDP Model Parallelism]]

| ID  | Network             |                  | Number of Parameters |
| --- | ------------------- | ---------------- | -------------------- |
| 0   | tab_subnetwork      | TabAE            | 1.2 K                |
| 1   | text_subnetwork     | TextBertBase     | 167 M                |
| 2   | final_merge_network | **Sequential**   | **603**              |
| 3   | loss_op             | CrossEntropyLoss | 0                    |

>[!info]
>- 167 M Trainable params
>- 0 Non-trainable params
>- 167 M Total params
>- **669.741** Total estimated model params size (MB)


```mermaid
flowchart TB
  %% Inputs
  A1["dialogue_processed_input_ids & attention_mask\nshape: B x C x T"]
  A2["tabular fields\nshape: B x input_tab_dim"]

  %% Text branch
  subgraph TextBranch["TextBertBase"]
    A1 --> B1["Reshape → (B·C) x T"]
    B1 --> B2["BERT encoder → pooler_output\nshape: (B·C) x H"]
    B2 --> B3["Reshape & mean over C → B x H"]
  end

  %% Tabular branch
  subgraph TabBranch["TabAE"]
    A2 --> C1["combine_tab_data → B x input_tab_dim"]
    C1 --> C2["LayerNorm → Linear(input_tab_dim→H) → ReLU\nshape: B x H"]
  end

  %% Fusion & classification
  B3 --> D1["Concat → B x (2H)"]
  C2 --> D1
  D1 --> D2["ReLU"]
  D2 --> D3["Linear(2H→num_classes)"]
  D3 --> E["logits\nshape: B x num_classes"]
```

### Fusion Gate

>[!important]
>- **Define the fusion gate** as the sigmoid gating mechanism with input as two embeddings
>$$
>g =  \sigma \left(  W_{g}\left[ W_{\text{text}}x_{\text{text}},  W_{\text{tab}}x_{\text{tab}}  \right]\right) 
>$$
>- Use the gate to define the *contribution of each modality* for each sample
>- Merge based on weighted sum $$f_{\text{fuse}} = g\, \odot W_{\text{text}}x_{\text{text}} + (1 - g)\, \odot W_{\text{tab}}x_{\text{tab}}$$

- [[Multi-modal BERT via Fusion Gate]]
- [[Gated Recurrent Units in Neural Network]]

```mermaid
flowchart TB
  %% Inputs
  A1["dialogue_processed_input_ids & attention_mask\nshape: B×C×T"]
  A2["tabular fields\nshape: B×input_tab_dim"]

  %% Text branch
  subgraph TextBranch["TextBertBase"]
    A1 --> T1["Reshape → (B·C)×T"]
    T1 --> T2["BERT encoder → pooler_output\nshape: (B·C)×H"]
    T2 --> T3["Mean over C → B×H"]
  end

  %% Tabular branch
  subgraph TabBranch["TabAE"]
    A2 --> U1["combine_tab_data → B×input_tab_dim"]
    U1 --> U2["LayerNorm → Linear(input_tab_dim→D_tab) → ReLU\nshape: B×D_tab"]
  end

  %% GateFusion
  T3 --> G1["text_proj: Linear(H→F)\n→ B×F"]
  U2 --> G2["tab_proj: Linear(D_tab→F)\n→ B×F"]
  G1 --> G3["Concat → B×2F"]
  G2 --> G3
  G3 --> G4["gate_net:\nLinear(2F→F) → LayerNorm → Sigmoid\n→ g (B×F)"]
  G4 --> G5["Fuse:\nfused = g⊙text_proj + (1–g)⊙tab_proj\n→ B×F"]

  %% Classification
  G5 --> C1["ReLU"]
  C1 --> C2["Linear(F→num_classes)"]
  C2 --> Out["logits\nshape: B×num_classes"]
```

### Mixture of Expert

>[!important]
>- Define the **router network** as a *classifier* to choose which expert $$p_{\text{router}} = [p_{0}, p_{1}] =  \text{softmax} \left(  W_{r}\left[ W_{\text{text}}x_{\text{text}},  W_{\text{tab}}x_{\text{tab}}  \right]\right)$$ 
>	- where $$p_{i} = P\left( \text{router choose }i\text{-th expert} \right)$$
>- Use the router network to choose which expert to use per sample
>- Merge based on weighted sum $$f_{\text{fuse}} = p_{0}\, W_{\text{text}}x_{\text{text}} + p_{1}\, W_{\text{tab}}x_{\text{tab}}$$

- [[Multi-modal BERT via Mixture of Experts]]
- [[Mixture of Experts or MoE as Deep Ensemble Learning]]
- [[Switch Transformer via Mixture of Expert Layer]]

| ID  | Network         |                      | Name of Parameters |
| --- | --------------- | -------------------- | ------------------ |
| 0   | tab_subnetwork  | TabAE                | 1.2 K              |
| 1   | text_subnetwork | TextBertBase         | 167 M              |
| 2   | moe_fusion      | **MixtureOfExperts** | **402**            |
| 3   | classifier      | **Sequential**       | **303**            |
| 4   | loss_op         | CrossEntropyLoss     | 0                  |


>[!info]
>- 167 M Trainable params
>- 0 Non-trainable params
>- 167 M Total params
>- **669.741** Total estimated model params size (MB)



```mermaid
flowchart TB
  %% Inputs
  A1["dialogue_processed_input_ids & attention_mask\nshape: B×C×T"]
  A2["tabular fields\nshape: B×input_tab_dim"]

  %% Text branch
  subgraph TextBranch["TextBertBase"]
    A1 --> T1["Reshape → (B·C)×T"]
    T1 --> T2["BERT encoder → pooler_output\nshape: (B·C)×H"]
    T2 --> T3["Reshape & mean over C → B×H"]
  end

  %% Tabular branch
  subgraph TabBranch["TabAE"]
    A2 --> U1["combine_tab_data → B×input_tab_dim"]
    U1 --> U2["LayerNorm → Linear(input_tab_dim→H) → ReLU\nshape: B×H"]
  end

  %% Expert projections
  T3 --> M1["text_proj: Linear(H→F)\n→ B×F"]
  U2 --> M2["tab_proj: Linear(H→F)\n→ B×F"]

  %% Mixture of Experts
  M1 --> M3["Concat → B×2F"]
  M2 --> M3
  M3 --> M4["router: Linear(2F→2) + Softmax\n→ weights [B×2]"]
  M4 --> M5["Split to w_txt [B×1], w_tab [B×1]"]
  M5 --> M6["Fuse: w_txt·txt_feat + w_tab·tab_feat\n→ B×F"]

  %% Classification
  M6 --> C1["ReLU"]
  C1 --> C2["Linear(F→num_classes)"]
  C2 --> Out["logits\nshape: B×num_classes"]
```


### Cross Attention

>[!important]
>- Define the **cross attention layer** 
>	- **Text attend Tab**: output modified tabular embedding but *highlighted by* text query information
>		- *query: text*
>		- key: tab 
>		- value: tab
>	- **Tab attend Text**: output modified text embedding but *highlighted by* tabular query information
>		- *query: tab*
>		- key: text
>		- value: text
>- Let $h^t, h^a \in \mathbb{R}^H$ be the text and tabular embeddings, respectively
>- 
>$$
>\begin{aligned} 
>&X = \bigl[h^t\bigr] \in \mathbb{R}^{1\times H},  \qquad A = \bigl[h^a\bigr] \in \mathbb{R}^{1\times H}.\\[6pt]\end{aligned} 
>$$
>- Define Multi‐Head Attention:  $$\mathrm{MHA}(Q,K,V)\;:\;\mathbb{R}^{\ell_Q\times H}\times\mathbb{R}^{\ell_K\times H}\times\mathbb{R}^{\ell_V\times H} \to \mathbb{R}^{\ell_Q\times H}.$$
>- **Text attends to Tab** $$U^t \;=\;\mathrm{MHA}\bigl(Q = X,\;K = A,\;V = A\bigr)$$ and 
>	- **Residual connection** $$\widetilde X \;=\;\mathrm{LayerNorm}\bigl(X + U^t\bigr)$$
>- **Tab attends to Text** $$U^a \;=\;\mathrm{MHA}\bigl(Q = A,\;K = \widetilde X,\;V = \widetilde X\bigr),$$ and 
>	- **Residual connection** $$\widetilde A \;=\;\mathrm{LayerNorm}\bigl(A + U^a\bigr)$$

- [[Multi-modal BERT via Cross-Attention]]
- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]

| ID  | Network             |                          | Number of Parameters |
| --- | ------------------- | ------------------------ | -------------------- |
| 0   | tab_subnetwork      | TabAE                    | 1.2 K                |
| 1   | text_subnetwork     | TextBertBase             | 167 M                |
| 2   | cross_att           | **CrossAttentionFusion** | **81.2 K**           |
| 3   | final_merge_network | **Sequential**           | **20.4 K**           |
| 4   | loss_op             | CrossEntropyLoss         | 0                    |

>[!info]
>- 167 M Trainable params
>- 0 Non-trainable params
>- 167 M Total params
>- **670.145** Total estimated model params size (MB)


```mermaid
flowchart TB
  %% Inputs
  A1["dialogue_processed_input_ids & attention_mask\nshape: B×C×T"]
  A2["tabular fields\nshape: B×input_tab_dim"]

  %% Text branch
  subgraph TextBranch["TextBertBase"]
    A1 --> B1["Reshape → (B·C)×T"]
    B1 --> B2["BERT encoder → pooler_output\nshape: (B·C)×H"]
    B2 --> B3["Reshape & mean over C → B×H"]
  end

  %% Tabular branch
  subgraph TabBranch["TabAE"]
    A2 --> C1["combine_tab_data → B×input_tab_dim"]
    C1 --> C2["LayerNorm → Linear(input_tab_dim→H) → ReLU\nshape: B×H"]
  end

  %% Prepare sequences for cross‐attention
  B3 --> D1["Unsqueeze → B×1×H"]
  C2 --> D2["Unsqueeze → B×1×H"]

  %% Cross‐attention fusion
  subgraph Fusion["CrossAttentionFusion"]
    D1 --> F1["text2tab MHA\n(query=text, key=tab, value=tab)"]
    D2 --> F2["tab2text MHA\n(query=tab, key=text, value=text)"]
    F1 --> F3["Add & LayerNorm → B×1×H"]
    F2 --> F4["Add & LayerNorm → B×1×H"]
  end

  %% Back to vectors
  F3 --> E1["Squeeze → B×H"]
  F4 --> E2["Squeeze → B×H"]

  %% Classification
  E1 --> G1["Concat → B×2H"]
  E2 --> G1
  G1 --> G2["Linear(2H→H) → ReLU"]
  G2 --> G3["Linear(H→num_classes)"]
  G3 --> Out["logits\nshape: B×num_classes"]
```






-----------
##  Recommended Notes