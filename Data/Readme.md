This section contains the essential data files required for model application, as well as intermediary outputs generated during the operational processes. These resources facilitate user-driven prediction analysis and result interpretation. Detailed descriptions are as follows:

1. **Application Layer Data**  
   The following data files support the model's application layer:

   - **CHP_Encoder**: Encodes Traditional Chinese Medicine (TCM) components, providing structured input for model processing.
   - **CHP_Medicinal_properties**: Contains medicinal property data for TCM, informing model-based analysis and prediction.
   - **Chinese_herbal_pieces**: This file records essential information about Chinese herbal pieces, with a focus on the `CHP_ID` codes associated with each herbal piece. This coding system is particularly valuable for users constructing and interpreting custom prescription data, enabling precise identification and analysis of specific herbs within TCM formulations.
   - **Test_input**: This file serves as an example input dataset. Users may modify this data to suit their own prediction and analysis needs.

   **Note**: Training data files are not provided in this repository. The following files are therefore not included:
   - `all_hypergraphs_with_labels-train.pkl`
   - `all_graphs_with_labels-train.pt`

2. **Operational Layer Data**  
   Intermediary files generated during the model's operation document the output and relevant attention mechanisms, assisting users in analyzing and interpreting prediction processes:

   - **prediction_outputs**: Logs the model’s prediction outputs for further analysis.
   - **attention_weights**: Contains the distribution of attention weights, allowing insights into which features are emphasized by the model.
   - **attention_averages**: Records averaged attention weights, simplifying feature analysis.
   - **calculated_attention_weights**: Contains processed attention weight data to quantify the interactions and relationships among medicinal herbs within a prescription.

3. **Additional Data Resources**  
   For more comprehensive details on the dataset, please refer to the complete Traditional Chinese Medicine Multidimensional Knowledge Graph (TCM-MKG) dataset available at:

   **Zeng, J., & Jia, X. (2024). Traditional Chinese Medicine Multidimensional Knowledge Graph (V1.0) [Data set]. **  
   China Pharmaceutical University.  
   [https://doi.org/10.5281/zenodo.13763953](https://doi.org/10.5281/zenodo.13763953)

