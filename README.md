# **GraphAI-for-TCM**

**Author**: Zeng Jingqi  
**Contact**: zjingqi@163.com  
**Date**: November 10, 2024  

---

## **Overview**

This repository, **GraphAI-for-TCM**, complements the **Traditional Chinese Medicine Multi-dimensional Knowledge Graph (TCM-MKG)** project, forming a cohesive system designed to facilitate the quantitative evaluation of compatibility mechanisms within Traditional Chinese Medicine (TCM). The code and models provided here are part of my study titled:

> **"Graph Artificial Intelligence for the Quantitative Evaluation of Compatibility Mechanisms in Traditional Chinese Medicine"**

In this study, I explored graph-based artificial intelligence techniques, specifically focusing on the application of graph attention mechanisms to analyze and interpret the intricate compatibility relationships within TCM formulations. The repository includes pre-trained models, data processing scripts, and example workflows that together enable users to conduct advanced TCM compatibility studies.

For additional data, please refer to the TCM-MKG dataset:

**Zeng, Jingqi (2024). Traditional Chinese Medicine Multidimensional Knowledge Graph (V1.0) [Data set].**  
Available at: [https://doi.org/10.5281/zenodo.13763953](https://doi.org/10.5281/zenodo.13763953)

---

## **Repository Structure**

- **Data**: Contains essential datasets required for model operation, including:
  - **CHP_Encoder** and **CHP_Medicinal_properties**: Encoded information about TCM components, supporting the model’s analysis capabilities.
  - **Test_input**: Example input file where users can substitute their data for prediction tasks.
  - **Intermediate files**: Files generated during model operations, such as `prediction_outputs` and `attention_weights`, which record the model’s output and attention mechanisms for interpretation.

- **Model**: Houses the pretrained Graph Attention Network model, `gat_model.pth`, optimized for TCM compatibility analysis. This model leverages attention mechanisms to evaluate and quantify compatibility relationships, allowing for both direct predictions and further fine-tuning.

- **Python**: Includes several Jupyter notebooks essential for performing compatibility analysis:
  - **1_Graph Embedding in TCM Formulas.ipynb**: Embeds TCM formulations as graph structures, preparing them for analysis.
  - **2_Prediction Using the GAT Model.ipynb**: Utilizes the pretrained GAT model to perform compatibility predictions.
  - **3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb**: Quantitatively evaluates the model’s predictions, providing insights into TCM compatibility.

  Additional notebooks explore alternative models, such as Graph Transformer Networks and Hypergraph Neural Networks, which offer further insights into various graph-based approaches for TCM data analysis.

---

## **Citation**

If you find this repository or the TCM-MKG dataset useful for your research, please cite:

**Zeng, Jingqi (2024). Traditional Chinese Medicine Multidimensional Knowledge Graph (V1.0) [Data set].**  
[https://doi.org/10.5281/zenodo.13763953](https://doi.org/10.5281/zenodo.13763953)

---

## **Contact**  

For questions or further information, please feel free to reach out:

**Zeng Jingqi**  
Email: [zjingqi@163.com](mailto:zjingqi@163.com)

--- 
