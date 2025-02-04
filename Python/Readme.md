# Python Folder Overview

The **Python** folder contains a collection of Jupyter notebooks with code implementations essential for executing model predictions and exploring different approaches for Traditional Chinese Medicine (TCM) compatibility analysis. This directory allows users to directly interact with data from the **Data** folder and model weights from the **Model** folder. Below is a detailed description of the contents and their usage.

## Key Notebooks for Prediction

The following notebooks are optimized for making compatibility predictions using the preselected **Graph Attention Network (GAT)** model. Users primarily need to interact with these three notebooks for prediction tasks:

- **1_Graph Embedding in TCM Formulas.ipynb**: Handles the embedding of TCM formulas into graph structures, transforming traditional data into a format suitable for graph-based analysis.

- **2_Prediction Using the GAT Model.ipynb**: Enables users to perform predictions using the pretrained GAT model, leveraging its attention-based architecture to analyze and interpret compatibility within TCM formulations.

- **3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb**: Focuses on the quantitative evaluation of compatibility mechanisms identified by the GAT model, providing insights into the model's predictions and the inferred compatibility relationships among TCM ingredients.

These three notebooks form the core prediction workflow, allowing users to effectively utilize the GAT model for compatibility analysis without needing to explore additional configurations or models.

## Additional Exploration Notebooks

The remaining notebooks showcase alternative approaches and experimental methods for compatibility analysis, highlighting the development and evaluation of various model architectures. While these notebooks are supplementary to the primary prediction process, they offer valuable insights into model experimentation and comparative analysis:

- **Graph Attention Network.ipynb**: A detailed implementation of the GAT architecture, focusing on its construction and parameter tuning for compatibility prediction.

- **Graph Transformer Network.ipynb**: Explores the application of a Graph Transformer Network, an alternative graph-based model that emphasizes different aspects of node and edge interactions within TCM data.

- **Hypergraph Neural Network.ipynb**: Investigates the use of a Hypergraph Neural Network, which represents multi-node relationships in a hypergraph structure, capturing more complex interactions between TCM components.

- **Transforming Graph Encoding to Hypergraph Encoding.ipynb**: Demonstrates the process of transforming graph-structured data into a hypergraph format, exploring the potential benefits of hypergraph representation for TCM compatibility analysis.

## Model Selection Rationale

While the **Python** folder includes various model implementations, the **Graph Attention Network (GAT)** model has been selected as the optimal choice based on performance metrics and interpretability for TCM compatibility tasks. The GAT model’s attention mechanism aligns well with the goal of identifying key component interactions in TCM formulas, providing both quantitative and qualitative insights.

This structure allows users to leverage the GAT model efficiently for compatibility predictions while also providing a foundation for exploring and developing alternative approaches.
