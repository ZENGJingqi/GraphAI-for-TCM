# Example Workflow

This page describes the released end-to-end example workflow bundled with **GraphAI-for-TCM**.

## Released example input

The repository includes `Data/Test_input.xlsx` as a ready-to-run prediction input set.

Observed summary of the released example input:

- total rows: 1,912
- total formulae: 215
- example formula IDs: `COVID00001`, `COVID00002`, `COVID00003`, ...

Each row corresponds to one herb entry within a formula, and rows with the same `CPM_ID` belong to the same formula graph.

## What happens when you run the three main notebooks

### Step 1. Graph construction

Notebook:

- `Python/1_Graph Embedding in TCM Formulas.ipynb`

Input files:

- `Data/Test_input.xlsx`
- `Data/CHP_Encoder.tsv`
- `Data/CHP_Medicinal_properties.tsv`

Generated file:

- `Data/all_graphs_to_be_predicted.pt`

This file contains PyTorch Geometric graph objects used for downstream inference.

### Step 2. Pretrained GAT prediction

Notebook:

- `Python/2_Prediction Using the GAT Model.ipynb`

Input files:

- `Data/all_graphs_to_be_predicted.pt`
- `Model/gat_model.pth`

Generated files:

- `Data/prediction_outputs.tsv`
- `Data/attention_weights.tsv`

In the current released example run, `prediction_outputs.tsv` contains one row per formula and 215 unique formula IDs. The leading columns are:

- `cpm_id`
- `Class_1`
- `Class_2`
- `Class_3`
- `Class_4`
- `Class_5`

followed by latent graph representation dimensions `hg_1` to `hg_64`.

### Step 3. Quantitative interpretation

Notebook:

- `Python/3_Quantitative Evaluation of Compatibility Mechanisms Using the GAT Model.ipynb`

Generated files:

- `Data/attention_averages.tsv`
- `Data/calculated_attention_weights.tsv`
- example figure outputs in `Figure`

In the current released example run:

- `attention_weights.tsv` contains 15,231 rows
- `attention_averages.tsv` contains 15,231 rows
- `calculated_attention_weights.tsv` contains 33,923 rows

These files correspond to the same 215 example formula IDs.

## Interpreting the bundled outputs

### `prediction_outputs.tsv`

This file is the formula-level output table. Each row represents one formula graph, and the `Class_1` to `Class_5` columns are the primary model output dimensions from the released inference notebook.

### `attention_weights.tsv`

This file is the edge-level attention export. It allows users to inspect how the model weights relationships between herb nodes and semantic nodes such as medicinal flavor or meridian tropism.

### `calculated_attention_weights.tsv`

This file is a simplified interpretation-oriented export with four columns:

- `cpm_id`
- `Source`
- `Target`
- `attention`

It is useful for downstream ranking, interpretation, and figure generation.

## Important note on bundled example outputs

The repository's current bundled output TSV files were regenerated from the released `Data/Test_input.xlsx` example set so that the example input and output assets are internally consistent.

If you replace `Test_input.xlsx` with your own input file and rerun the notebooks, the output TSV files will be overwritten with results corresponding to your custom formula set.
