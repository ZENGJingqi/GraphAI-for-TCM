# Troubleshooting

This document collects the most common setup and execution issues reported by users of **GraphAI-for-TCM**.

## 1. Training files seem to be missing

The public repository now includes:

- `Data/all_graphs_with_labels-train.pt`
- `Data/all_hypergraphs_with_labels-train.pkl`

If these files are not present in your local copy, check the following:

1. You cloned the repository recently enough to include the updated data release.
2. Your Git client completed the download of large files successfully.
3. You are working in the repository root rather than an older unpacked copy of the project.

## 2. `ModuleNotFoundError: No module named 'hypernetx'`

The hypergraph notebook requires `hypernetx`, which is not part of the Python standard library.

Use one of the repository environment options:

```bash
pip install -r requirements.txt
```

or

```bash
conda env create -f environment.yml
conda activate graphai-for-tcm
```

## 3. Notebook cannot find `Test_input.xlsx`

The main public prediction notebook expects:

- `Data/Test_input.xlsx`

If you renamed the file or moved it elsewhere, either restore the original filename or update the file path in the notebook accordingly.

The released `1_Graph Embedding in TCM Formulas.ipynb` is configured to use `Test_input.xlsx`.

## 4. Notebook cannot find data or model files

The notebooks use repository-relative paths such as:

- `../Data`
- `../Model`
- `../Figure`

They are intended to be launched from the `Python` directory. If you start Jupyter from another directory, path resolution may fail.

## 5. `torch-geometric` installation issues

On some systems, `torch-geometric` is the package most likely to require platform-specific installation steps.

If installing from `requirements.txt` fails:

1. install `torch` first using the official PyTorch instructions for your platform
2. install `torch-geometric` using the official PyG instructions for the same PyTorch version
3. install the remaining packages from `requirements.txt`

## 6. Large files download slowly or fail

The released training files are relatively large. GitHub may warn about their size during cloning or pushing.

If your download is interrupted:

1. retry the clone on a stable connection
2. verify the file sizes in the `Data` directory
3. avoid mixing the repository with an older manually copied project folder

## 7. Hypergraph file inspection fails outside the notebook

`Data/all_hypergraphs_with_labels-train.pkl` is loaded by the released notebook through `torch.load(...)` and depends on the Python environment expected by that workflow.

If direct loading fails, first reproduce the notebook environment with `requirements.txt` or `environment.yml`, then load the file again.

## 8. Character display problems for Chinese herb names

If herb names appear garbled:

1. use UTF-8 capable editors and terminals
2. prefer spreadsheet software or modern text editors for viewing `.tsv` files
3. load the files with pandas rather than relying on shell display alone

## 9. Recommended first-run order

If you are unsure where to start, use this order:

1. create the environment
2. open the notebooks in `Python`
3. run `1_Graph Embedding in TCM Formulas.ipynb`
4. run `2_Prediction Using the GAT Model.ipynb`
5. run `3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb`
