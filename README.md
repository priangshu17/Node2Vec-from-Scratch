# Node2Vec-from-Scratch

This repository contains a Jupyter Notebook that implements the **Node2Vec** algorithm from scratch. The project is an educational guide for learning feature representations (embeddings) for nodes in a graph, highlighting its signature **biased random walk** strategy.

## 📝 Overview

Node2Vec is a powerful algorithm for node embedding that generates node sequences via biased random walks. These walks can be tuned to explore graph neighborhoods in different ways, allowing the model to learn richer structural features than uniform random walks. A Skip-Gram-like model is then trained on these walks to produce the final node embeddings.

This notebook implements the entire pipeline:
1.  **Graph Creation**: Building a graph structure using a library like `networkx`.
2.  **Biased Random Walk Generation**: Calculating transition probabilities based on the `p` & `q` parameters and generating a corpus of walks.
3.  **Embedding Learning**: Training a model on the walks to generate node vectors.
4.  **Evaluation & Visualization**: Using the learned embeddings for a downstream node classification task and visualizing them with t-SNE.

## 🔑 Key Concepts: Biased Random Walks

The core of Node2Vec is its flexible random walk strategy, which is controlled by two parameters:

* **Return Parameter (`p`):** Controls the likelihood of immediately revisiting a node in the walk. A high `p` value encourages the walk to explore new nodes.
* **In-out Parameter (`q`):** Controls the balance between exploring "inward" (local) and "outward" (distant) nodes. A high `q` biases the walk towards local nodes (BFS-like), while a low `q` encourages exploring further nodes (DFS-like).

This strategy allows Node2Vec to capture a nuanced understanding of node similarity, balancing between community structure (**homophily**) and functional roles (**structural equivalence**).


The quality of the learned embeddings is demonstrated through:
1.  **t-SNE Visualization**: The high-dimensional embeddings are projected into a 2D space, which visually confirms that the algorithm successfully clusters nodes with similar properties.
