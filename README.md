# Malware Classification Model - Documentation

## About the Dataset
The dataset used for developing this model consists of three CSV files:
- **API_Functions.csv**
  - 28,017 samples
  - 21,920 features
  - Contains data on malware that has invoked API function calls
- **DLLs_Imported.csv**
  - 28,016 samples
  - 631 features
  - Contains data about function calls invoked from malware that attacks via DLLs
- **PortableExecutables.csv**
  - (Details not provided, assumed similar structure)

## Algorithm Used
- **Random Forest** for feature selection
- **K-Fold Cross-Validation** for model validation

## Procedure
Our workflow follows a structured approach to processing and modeling the dataset:
1. **Data Preprocessing**
   - The dataset contains 28,014 samples and 22,693 features.
   - Standardization is applied using a Standard Scaler to normalize feature values.
2. **Feature Selection**
   - A Random Forest (RF) model with 100 trees is used.
   - Features are selected based on an importance threshold of 0.75, reducing dimensionality while preserving critical information.
3. **Data Splitting**
   - The dataset is stratified into training and testing sets to maintain class balance.
   - Class weights are adjusted to improve generalization across different malware types.
4. **Hyperparameter Tuning**
   - Grid Search Cross-Validation (CV) is applied to optimize model parameters.
   - K-Fold Cross-Validation ensures robustness by testing on multiple subsets.
5. **Model Evaluation**
   - The trained model is validated on unseen data to assess its real-world performance.

## Dependencies
Ensure the following Python libraries are installed:

```bash
pip install tensorflow sklearn pandas numpy joblib
```

## Installation & Usage

### Step 1: Download Required Files
Download the dataset and code files before proceeding.

### Step 2: Merge CSV Files (If Needed)
- If you have three separate CSV files (`API_Functions.csv`, `DLLs_Imported.csv`, `PortableExecutables.csv`), run `merger.ipynb` to combine them into a single dataset.
- The merged dataset will be used for training and testing.
- Ensure the final file is named `merged.csv`, or provide its path manually in the scripts.

### Step 3: Train the Model (Optional)
- If you want to train the model using your own dataset, ensure you have a single merged CSV file (follow Step 2 if necessary).
- Run `train.ipynb` to train the model.
- **Recommended:** Use Google Colab's TPU v2.8 for better training efficiency.
- A sample merged csv `merged.csv` is given for training purposes.

### Step 4: Test the Model
- If you want to predict the malware type using the pre-trained model, ensure you have a single CSV file (merge if necessary).
- Run `test.ipynb` to classify malware samples.
- The predictions will be saved in `output.csv`.
- A sample test csv `test.csv` is given for testing purposes.
