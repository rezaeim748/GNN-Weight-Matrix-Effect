
# GNN Weight Matrix Effect

## Project Overview

This project explores the impact of learnable weight matrices in Graph Neural Networks (GNNs) by comparing two models: 
- **Graph Convolutional Network (GCN)**, which uses learnable weight matrices.
- **Light Graph Convolutional Network (LightGCN)**, which does not use learnable weight matrices.

We perform these comparisons on two tasks:
1. **Node Classification**: Predicting the class of nodes in a graph.
2. **Link Prediction**: Predicting the existence of an edge between two nodes in a graph.

The project involves multiple datasets, including Cora, DBLP, and Karate Club, and compares the performance of GCN and LightGCN on each dataset in terms of accuracy.

## Datasets

The project uses the following datasets:
- **Cora (Node Classification)**: A citation network dataset for node classification.
- **DBLP (Node Classification)**: A collaboration network dataset for node classification.
- **Karate Club (Link Prediction)**: A social network dataset for link prediction.

The datasets are stored in the `/data` folder and loaded within the corresponding notebooks.

## How to Run the Project

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/GNN-weight-matrix-effect.git
   cd GNN-weight-matrix-effect
   ```

2. **Install Required Dependencies**:
   Ensure you have the necessary libraries installed. You can install them using the `requirements.txt` file (if provided) or manually install key libraries such as `torch`, `numpy`, and `networkx`:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the Jupyter Notebooks**:
   - Navigate to the folder of the dataset you're interested in (e.g., `/cora`, `/dblp`, `/karate club`).
   - Open the Jupyter notebooks (`git_cora_GCN.ipynb`, `git_cora_LightGCN.ipynb`, etc.).
   - Run the notebooks to compare the accuracy of GCN and LightGCN for that dataset.

   ```bash
   jupyter notebook
   ```

4. **Compare the Results**:
   The notebooks will output accuracy metrics for both models, allowing you to see how learnable weight matrices affect the performance of GNNs on each task.

## Results

The project compared the performance of **GCN** (with learnable weight matrices) and **LightGCN** (without learnable weight matrices) across multiple datasets. The following table summarizes the accuracy achieved by each model:

| **Dataset**  | **GCN Accuracy** | **LightGCN Accuracy** |
|--------------|------------------|-----------------------|
| **Cora (Node Classification)**     | 82.3%            | 81.0%                 |
| **DBLP (Node Classification)**     | 83.4%            | 93.8%                 |
| **Karate Club (Link Prediction)**  | 88.1%            | 70.3%                 |

These results highlight the differences in performance between GCN and LightGCN models on node classification and link prediction tasks. GCN generally performs better on link prediction tasks, whereas LightGCN demonstrates higher accuracy on the DBLP node classification task.

## Conclusion

This project provides a detailed comparison between GCN and LightGCN models, highlighting the effects of using learnable weight matrices in GNNs on tasks such as node classification and link prediction.

## License

This project is licensed under the MIT License.
