GraphAI-for-TCM

Author: Zeng Jingqi

Contact: zjingqi@163.com

Date: November 10, 2024

Overview

This repository, GraphAI-for-TCM, complements the Traditional Chinese Medicine Multi-dimensional Knowledge Graph (TCM-MKG) project, forming a cohesive system designed to facilitate the quantitative evaluation of compatibility mechanisms within Traditional Chinese Medicine (TCM). The code and models provided here are part of my study titled:

"Graph Artificial Intelligence for the Quantitative Evaluation of Compatibility Mechanisms in Traditional Chinese Medicine"

In this study, I explored graph-based artificial intelligence techniques, specifically focusing on the application of graph attention mechanisms to analyze and interpret the intricate compatibility relationships within TCM formulations. The repository includes pre-trained models, data processing scripts, and example workflows that together enable users to conduct advanced TCM compatibility studies.

For additional data, please refer to the TCM-MKG dataset:

Zeng, Jingqi (2024). Traditional Chinese Medicine Multidimensional Knowledge Graph (V1.0) [Data set].
Available at: https://doi.org/10.5281/zenodo.13763953

Repository Structure

This repository is organized into three main sections:

1. Data

The Data folder includes essential datasets required for model operation. This includes encoded representations of TCM components, medicinal properties, and test input datasets:

CHP_Encoder and CHP_Medicinal_properties provide encoded information about TCM components, supporting the model’s analysis capabilities.
Test_input serves as an example input file where users can substitute their data for prediction tasks.
Intermediate files generated during model operations, such as prediction_outputs and attention_weights, record the model’s output and attention mechanisms, aiding interpretation.
For a comprehensive TCM dataset, please refer to the TCM-MKG data link.

2. Model

The Model folder contains a pretrained model weight file:

gat_model.pth: A pretrained Graph Attention Network (GAT) model optimized for TCM compatibility analysis. This model leverages attention mechanisms to evaluate and quantify compatibility relationships, allowing the model to prioritize relevant features within TCM formulations. This pretrained model serves as a flexible tool for both direct predictions and further fine-tuning.

3. Python

The Python folder provides several Jupyter notebooks essential for performing compatibility analysis. The core notebooks include:

1_Graph Embedding in TCM Formulas.ipynb: Embeds TCM formulations as graph structures, preparing them for analysis.
2_Prediction Using the GAT Model.ipynb: Utilizes the pretrained GAT model to perform compatibility predictions.
3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb: Quantitatively evaluates the model’s predictions, providing insights into TCM compatibility.
Additionally, this folder includes experimental notebooks that document the exploration of alternative models, such as Graph Transformer Networks and Hypergraph Neural Networks, which were investigated during the study. While these experimental models are not the primary focus, they offer valuable insights into various graph-based approaches for TCM data analysis.

Citation

If you find this repository or the TCM-MKG dataset useful for your research, please cite:

Zeng, Jingqi (2024). Traditional Chinese Medicine Multidimensional Knowledge Graph (V1.0) [Data set].
https://doi.org/10.5281/zenodo.13763953

Contact

For questions or further information, please feel free to reach out to me:

Zeng Jingqi
Email: zjingqi@163.com
