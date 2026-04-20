This directory contains the core data assets required for model execution, result interpretation, and reproducible experimentation in **GraphAI-for-TCM**.

For column-level descriptions and workflow-specific details, see `Data/Data_dictionary.md`.

## 1. Core input resources

- `CHP_Encoder.tsv`  
  Encoded descriptors for Chinese herbal pieces used as structured model inputs.

- `CHP_Medicinal_properties.tsv`  
  Medicinal-property annotations, including TCM semantic information used during graph encoding.

- `Chinese_herbal_pieces.tsv`  
  Reference table for Chinese herbal piece identifiers (`CHP_ID`) and herb names. This file is useful when constructing custom formula inputs and mapping model outputs back to interpretable herb entities.

- `Test_input.xlsx`  
  Example input file for prediction-oriented workflows.

## 2. Training assets

The repository now includes the training data files required for graph- and hypergraph-based experiments:

- `all_graphs_with_labels-train.pt`  
  Training set used for graph-based learning workflows.

- `all_hypergraphs_with_labels-train.pkl`  
  Training set used for hypergraph-based learning workflows.

These files were added to improve the reproducibility of the published workflow and to support users who want to inspect or extend model training.

Because these files are substantially larger than the lightweight example outputs, users should make sure their local clone finished downloading correctly before running training-oriented notebooks.

## 3. Generated outputs for interpretation

- `prediction_outputs.tsv`  
  Example model prediction outputs regenerated from the released `Test_input.xlsx` workflow.

- `attention_weights.tsv`  
  Attention-weight results for detailed inspection of model emphasis patterns.

- `attention_averages.tsv`  
  Averaged attention summaries for simplified interpretation.

- `calculated_attention_weights.tsv`  
  Processed attention-weight results used to quantify herb-herb interaction patterns within formulae.

The repository also includes a released example figure generated from the interpretation workflow:

- `Figure/MPX_Attention_Heatmap.pdf`

## 4. Related data resource

For the broader biomedical knowledge resource that supports this repository, please refer to the public **Traditional Chinese Medicine Multidimensional Knowledge Graph (TCM-MKG)** dataset:

Zeng, J., & Jia, X. (2024). *Traditional Chinese Medicine Multidimensional Knowledge Graph (TCM-MKG) (V1.0)* [Data set]. China Pharmaceutical University.  
[https://doi.org/10.5281/zenodo.13763953](https://doi.org/10.5281/zenodo.13763953)
