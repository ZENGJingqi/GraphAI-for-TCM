# GraphAI-for-TCM

**Author**: Zeng Jingqi  
**Contact**: [zjingqi@163.com](mailto:zjingqi@163.com)  
**Project update**: April 2026

---

## Overview

**GraphAI-for-TCM** is a graph artificial intelligence framework for studying compatibility mechanisms in Traditional Chinese Medicine (TCM) formulae. The repository is designed as the model and workflow companion to the **Traditional Chinese Medicine Multidimensional Knowledge Graph (TCM-MKG)** resource and supports graph construction, model inference, mechanism interpretation, and reproducible training experiments.

This project is associated with the following article:

Zeng, J., & Jia, X. (2025). *Quantifying compatibility mechanisms in traditional Chinese medicine with interpretable graph neural networks*. **Journal of Pharmaceutical Analysis, 15**(8), 101342.  
Paper: [https://doi.org/10.1016/j.jpha.2025.101342](https://doi.org/10.1016/j.jpha.2025.101342)

The underlying multidimensional knowledge resource is available as:

Zeng, J., & Jia, X. (2024). *Traditional Chinese Medicine Multidimensional Knowledge Graph (TCM-MKG) (V1.0)* [Data set]. China Pharmaceutical University.  
Dataset: [https://doi.org/10.5281/zenodo.13763953](https://doi.org/10.5281/zenodo.13763953)

Based on the published study and dataset record, the framework integrates standardized TCM terminology, Chinese patent medicines, Chinese herbal pieces, pharmacognostic origins, chemical compounds, biological targets, and diseases into a unified analytical pipeline. In the paper, graph neural networks with attention mechanisms are used to represent Chinese herbal formulae and to quantify herb-herb compatibility patterns in an interpretable way.

---

## Scientific Scope

This repository focuses on three connected tasks:

1. **Knowledge-guided representation of TCM formulae**  
   Formulae are encoded as graph-structured or hypergraph-structured samples built from Chinese herbal pieces and their medicinal-property semantics.

2. **Interpretable graph learning for compatibility analysis**  
   Attention-based graph models are used to capture interactions among herbal components, with medicinal properties such as therapeutic nature, flavor, and meridian tropism incorporated as structured prior knowledge.

3. **Quantitative mechanism interpretation**  
   The workflow exposes attention-derived outputs that support downstream interpretation of compatibility strength, herb pair relationships, and formula-level mechanistic patterns.

The associated publication reports that the broader TCM-MKG-driven framework was built from seven standardized modules and used to analyze 6,080 Chinese herbal formulae. It also describes a neighbor-diffusion strategy for improving compound-target coverage in the knowledge graph, providing the biomedical context that supports the downstream graph learning workflow in this repository.

![Research Framework for TCM Compatibility Mechanisms](Figure/Graphic_abstract.png)

---

## Repository Structure

- **Data**  
  Core input data, reproducibility assets, and generated outputs used by the notebooks and pretrained model.
  - `CHP_Encoder.tsv`: encoded descriptors for Chinese herbal pieces
  - `CHP_Medicinal_properties.tsv`: medicinal-property annotations used in graph encoding
  - `Chinese_herbal_pieces.tsv`: reference table for CHP identifiers and herb names
  - `Test_input.xlsx`: example input for prediction workflows
  - `all_graphs_with_labels-train.pt`: training set for graph-based experiments
  - `all_hypergraphs_with_labels-train.pkl`: training set for hypergraph-based experiments
  - `prediction_outputs.tsv`, `attention_weights.tsv`, `attention_averages.tsv`, `calculated_attention_weights.tsv`: example result and interpretation outputs

- **Model**  
  Contains the pretrained graph attention model `gat_model.pth` for compatibility prediction and interpretation workflows.

- **Python**  
  Jupyter notebooks covering graph construction, model prediction, interpretability analysis, and alternative graph-learning settings:
  - `1_Graph Embedding in TCM Formulas.ipynb`
  - `2_Prediction Using the GAT Model.ipynb`
  - `3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb`
  - `Graph Attention Network.ipynb`
  - `Graph Transformer Network.ipynb`
  - `Hypergraph Neural Network.ipynb`
  - `Transforming Graph Encoding to Hypergraph Encoding.ipynb`

Detailed data descriptions are provided in `Data/Readme.md` and `Data/Data_dictionary.md`. Setup and runtime troubleshooting notes are collected in `TROUBLESHOOTING.md`.

---

## Quick Start

### 0. Create the environment

The repository is notebook-driven. A typical setup sequence is:

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

On Windows PowerShell, activate the environment with:

```powershell
.venv\Scripts\Activate.ps1
```

For Conda users, an alternative setup file is also provided:

```bash
conda env create -f environment.yml
conda activate graphai-for-tcm
```

Then launch Jupyter from the repository root and open the notebooks in the `Python` directory:

```bash
jupyter notebook
```

For most users, the recommended inference workflow is the three-notebook GAT pipeline in the `Python` directory:

1. **Prepare formula input**  
   Edit `Data/Test_input.xlsx` or replace it with a file of the same schema containing the columns:
   - `CPM_ID`
   - `CHP_ID`
   - `Dosage_ratio`
   - `Chinese_herbal_pieces`

2. **Build graph representations**  
   Run `Python/1_Graph Embedding in TCM Formulas.ipynb` to convert formula records into `Data/all_graphs_to_be_predicted.pt`.

3. **Run the pretrained GAT model**  
   Run `Python/2_Prediction Using the GAT Model.ipynb` to load `Model/gat_model.pth` and export:
   - `Data/prediction_outputs.tsv`
   - `Data/attention_weights.tsv`

4. **Interpret compatibility mechanisms**  
   Run `Python/3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb` to generate:
   - `Data/attention_averages.tsv`
   - `Data/calculated_attention_weights.tsv`
   - formula-specific heatmap figures in `Figure`

For users interested in model development rather than inference only, the training-oriented notebooks use:

- `Data/all_graphs_with_labels-train.pt` for graph-based experiments
- `Data/all_hypergraphs_with_labels-train.pkl` for hypergraph-based experiments

---

## Data at a Glance

The repository contains three data layers:

1. **Reference tables**  
   `CHP_Encoder.tsv`, `CHP_Medicinal_properties.tsv`, and `Chinese_herbal_pieces.tsv` provide encoded herb features, medicinal-property annotations, and herb identifier mappings.

2. **User-facing input and generated inference files**  
   `Test_input.xlsx` is the editable entry point for custom formula prediction, while `all_graphs_to_be_predicted.pt`, `prediction_outputs.tsv`, and the attention TSV files capture downstream machine-learning results.

3. **Reproducibility assets**  
   `all_graphs_with_labels-train.pt` and `all_hypergraphs_with_labels-train.pkl` support graph and hypergraph training workflows corresponding to the public project release.

The graph training file contains 6,080 labeled graph samples. Each sample is a `torch_geometric.data.Data` object with node features (`x`), edge indices (`edge_index`), edge attributes (`edge_attr`), a 5-dimensional label vector (`y`), and metadata such as `cpm_id` and node names. The graph node feature matrix uses 91 features per node in the released training set.

---

## Data Availability and Reproducibility

This repository now includes the two training assets that were previously absent from the public project snapshot:

- `Data/all_graphs_with_labels-train.pt`
- `Data/all_hypergraphs_with_labels-train.pkl`

Their inclusion improves reproducibility for users who want to inspect or extend the training workflow rather than only run pretrained inference. The broader biomedical knowledge resource used to support this work remains available through the public TCM-MKG Zenodo record linked above.

The hypergraph training file is consumed by `Python/Hypergraph Neural Network.ipynb` through `torch.load(...)`. Users working with this file outside the notebook should ensure that the required hypergraph-related Python dependencies used by that notebook are available in their environment.

For common installation and notebook execution issues, see `TROUBLESHOOTING.md`.

---

## Recommended Environment

- Python 3.10+
- PyTorch 2.7.1
- Torch Geometric 2.6.1
- scikit-learn 1.7.0
- NumPy 2.3.0
- pandas 2.3.0
- SciPy 1.15.3
- matplotlib 3.10.3
- tqdm 4.67.1
- networkx 3.x
- hypernetx 2.x
- openpyxl 3.x
- notebook 7.x

CPU execution has been tested for the current workflow; a compatible GPU-enabled PyTorch environment can also be used.

If your local platform requires a custom PyTorch or PyTorch Geometric installation route, install those packages first according to the official instructions for your platform, then install the remaining packages from `requirements.txt`.

---

## Citation

If you use this repository, please cite the article and dataset:

1. Zeng, J., & Jia, X. (2025). *Quantifying compatibility mechanisms in traditional Chinese medicine with interpretable graph neural networks*. **Journal of Pharmaceutical Analysis, 15**(8), 101342. [https://doi.org/10.1016/j.jpha.2025.101342](https://doi.org/10.1016/j.jpha.2025.101342)
2. Zeng, J., & Jia, X. (2024). *Traditional Chinese Medicine Multidimensional Knowledge Graph (TCM-MKG) (V1.0)* [Data set]. China Pharmaceutical University. [https://doi.org/10.5281/zenodo.13763953](https://doi.org/10.5281/zenodo.13763953)

---

## Contact

For questions regarding the repository, data organization, or model workflow:

**Zeng Jingqi**  
Email: [zjingqi@163.com](mailto:zjingqi@163.com)

---
