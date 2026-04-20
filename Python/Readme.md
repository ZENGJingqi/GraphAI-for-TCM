# Python Folder Overview

The **Python** directory contains the notebook-based workflow for graph construction, pretrained inference, interpretation, and training experiments in **GraphAI-for-TCM**.

## Recommended notebook order

For most users, the intended sequence is:

1. **`1_Graph Embedding in TCM Formulas.ipynb`**  
   Reads `../Data/Test_input.xlsx`, `../Data/CHP_Encoder.tsv`, and `../Data/CHP_Medicinal_properties.tsv`, then exports `../Data/all_graphs_to_be_predicted.pt`.

2. **`2_Prediction Using the GAT Model.ipynb`**  
   Loads `../Data/all_graphs_to_be_predicted.pt` and `../Model/gat_model.pth`, then exports:
   - `../Data/prediction_outputs.tsv`
   - `../Data/attention_weights.tsv`

3. **`3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb`**  
   Consumes the attention outputs and produces:
   - `../Data/attention_averages.tsv`
   - `../Data/calculated_attention_weights.tsv`
   - formula-specific figures in `../Figure`

These three notebooks form the main public inference workflow for custom formula analysis.

## Training and comparison notebooks

The remaining notebooks are primarily for model development, benchmarking, or representation experiments:

- **`Graph Attention Network.ipynb`**  
  Uses `../Data/all_graphs_with_labels-train.pt` for graph-based model training and evaluation.

- **`Graph Transformer Network.ipynb`**  
  Uses `../Data/all_graphs_with_labels-train.pt` for transformer-style graph experiments.

- **`Hypergraph Neural Network.ipynb`**  
  Uses `../Data/all_hypergraphs_with_labels-train.pkl` for hypergraph neural network experiments.

- **`Transforming Graph Encoding to Hypergraph Encoding.ipynb`**  
  Converts graph-formatted prediction inputs into hypergraph-formatted objects for downstream hypergraph workflows.

## Input and output expectations

Users preparing custom prediction input should keep the schema of `../Data/Test_input.xlsx` unchanged:

- `CPM_ID`
- `CHP_ID`
- `Dosage_ratio`
- `Chinese_herbal_pieces`

The notebooks assume repository-relative paths and are intended to be run from inside the `Python` directory.

## Practical notes

- The released graph training data are PyTorch Geometric graph objects.
- The released hypergraph training workflow uses serialized hypergraph objects loaded through PyTorch and may require additional hypergraph-related dependencies in the Python environment.
- The pretrained inference path is centered on the GAT model because it offers an interpretable attention mechanism that aligns well with the compatibility-analysis goal of the project.
- The repository root provides `requirements.txt` for environment setup before running the notebooks.
- Conda users can use `environment.yml` from the repository root.
- Common execution issues are summarized in `TROUBLESHOOTING.md`.
