# 📊 GNN Weight Matrix Effect

## 🔍 Project Overview

In recent years, **Graph Neural Networks (GNNs)** have become powerful tools for learning on graph-structured data. Among these, the use of **learnable weight matrices** and **non-linear transformations** has been a central architectural component — present in popular models like **GCN** and **GAT**.

However, recent studies such as **LightGCN** question the necessity of these components. LightGCN removes weight matrices and non-linearities entirely, relying solely on **structural message passing**, which results in simpler models with fewer parameters and lower computational cost.

This project evaluates and compares three representative GNN architectures:
- **GCN** – uses weight matrices and nonlinearities.
- **GAT** – includes attention mechanisms for weighted neighbor aggregation.
- **LightGCN** – removes both transformations and nonlinearities.

We perform a systematic comparison of these models on two core tasks:
- **Node Classification** (on Cora, Amazon Photo)
- **Link Prediction** (on PubMed, Citeseer)

---

## 🎯 Problem Statement

Most GNNs assume that transformation of features via weight matrices is necessary for good performance. This project investigates whether:
- Complex transformations (as in GCN and GAT) significantly improve performance
- Simpler models (like LightGCN) can be competitive or even superior on some tasks
- The attention mechanism in GAT truly yields gains in performance, or if simpler alternatives are sufficient

By isolating the role of weight matrices and attention, we aim to understand **what really matters** in GNN design, and whether simplification can be done without major loss of accuracy.

---

## 📂 Datasets

We use four real-world graph datasets covering citation networks and co-purchase networks:

| Dataset       | Task               | Nodes  | Edges   | Features | Classes | Notes                                  |
|---------------|--------------------|--------|---------|----------|---------|----------------------------------------|
| Cora          | Node Classification | 2,708  | 5,429   | 1,433    | 7       | High homophily citation network        |
| Citeseer      | Link Prediction     | 3,312  | 4,732   | 3,703    | 6       | Sparse features, less homophily        |
| PubMed        | Link Prediction     | 19,717 | 44,338  | 500      | 3       | Dense TF-IDF features                  |
| Amazon Photo  | Node Classification | 7,650  | 119,043 | 745      | 8       | Dense product co-purchase network      |

---

## 🧠 Models Compared

| Model     | Weight Matrices | Non-linear Activations | Attention | Description |
|-----------|------------------|-------------------------|-----------|-------------|
| GCN       | ✅ Yes           | ✅ Yes                  | ❌ No      | Convolution over graph features with transformation and averaging |
| GAT       | ✅ Yes           | ✅ Yes                  | ✅ Yes     | Applies attention over neighbors for adaptive aggregation |
| LightGCN  | ❌ No            | ❌ No                   | ❌ No      | Propagates node embeddings through structure without transformation |

---

## 📈 Evaluation Metrics

We assess model performance using:

- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**
- **AUC-ROC**

Metrics are selected based on task type:
- For **node classification**, accuracy is the main metric.
- For **link prediction**, F1 and AUC are emphasized due to class imbalance.

---

## 📊 Results

### 🔹 Node Classification

| Dataset       | Model     | Accuracy (%) |
|---------------|-----------|--------------|
| Cora          | GCN       | 88.68        |
| Cora          | GAT       | **88.81**    |
| Cora          | LightGCN  | 87.95        |
| Amazon Photo  | GCN       | 96.41        |
| Amazon Photo  | GAT       | **96.47**    |
| Amazon Photo  | LightGCN  | 96.01        |

- GAT slightly outperformed others due to attention mechanism.
- GCN delivered reliable results.
- LightGCN performed competitively despite architectural simplicity.

---

### 🔹 Link Prediction

| Dataset   | Metric    | GCN     | GAT     | LightGCN |
|-----------|-----------|---------|---------|----------|
| PubMed    | F1 Score  | 74.62   | 77.67   | **79.11** |
| PubMed    | AUC       | **90.77** | 86.29   | 87.89    |
| Citeseer  | F1 Score  | 75.74   | 75.56   | **77.64** |
| Citeseer  | AUC       | 81.16   | 81.55   | **84.93** |

- LightGCN achieved best F1 in both datasets.
- GCN had highest AUC on PubMed but lower F1.
- GAT remained balanced but did not outperform LightGCN.

---

## ✅ Final Takeaways

No single model is universally best — the choice depends on the task:

- Use **GAT** for node classification when precision matters or graphs are noisy.
- Use **LightGCN** for link prediction when scalability and recall are priorities.
- Use **GCN** as a balanced baseline for most graph learning problems.
- In large systems, combining models (e.g., **GAT** for classification and **LightGCN** for prediction) can yield optimal results.
- Understanding graph properties (e.g., homophily, density, node feature richness) is critical when choosing a GNN.

> ⚠️ This project confirms that **simpler models can match or outperform complex architectures** in many real-world scenarios, and thoughtful model selection often beats brute architectural complexity.