# Machine Learning Practical Course — ML_Course

This project contains notebooks for the regression algorithms in the practical assignment.

## Project structure

```text
ML_Course/
├── data/
│   └── Practical_Dataset for ML.xlsx
├── notebooks/
│   ├── 01_simple_linear_regression.ipynb
│   ├── 02_multiple_linear_regression.ipynb
│   ├── 03_polynomial_regression.ipynb
│   ├── 04_support_vector_regression.ipynb
│   ├── 05_decision_tree_regression.ipynb
│   ├── 06_random_forest_regression.ipynb
│   ├── 07_ridge_regression.ipynb
│   ├── 08_neural_network_regression.ipynb
│   └── 09_model_comparison.ipynb
├── outputs/
│   └── metrics/
├── README.md
└── requirements.txt
```

Notebook filenames can differ slightly depending on the version you downloaded; keep your actual filenames consistent.

## Setup

Recommended: Python 3.11 or 3.12 for broad scientific Python package compatibility.

### Windows PowerShell

```powershell
cd path	o\ML_Course
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter lab
```

If Python 3.12 is not installed, use a supported Python version already installed on your machine and adjust the `py` command accordingly.

## Dataset

Place `Practical_Dataset for ML.xlsx` inside `data/`. The notebooks expect:
- Excel worksheet: `Data`
- Regression target: `price_etb`
- Notebook 01 feature: `size_sqm`

If the workbook uses different column names or sheet names, update the constants in the notebooks.

## Recommended run order

Run notebooks in numerical order from 01 through 09. Notebook 09 also trains a common comparison suite using one shared split so that its table is internally consistent.

## Fair-comparison rules

- Keep the target, rows, feature eligibility, and split consistent across algorithms.
- Use a fixed split (`test_size=0.20`, `random_state=42`) for this assignment unless your instructor specifies otherwise.
- Fit imputers, scalers, feature transformations, and other preprocessing on training data only; use pipelines where possible.
- Tune hyperparameters with cross-validation on the training set only.
- Keep the test set for final evaluation, not repeated model selection.
- Compare MAE, RMSE, and R² together; consider training/test gaps and practical complexity.
- For a true real-world prediction, exclude variables that would not be known at prediction time. `days_on_market` may leak future information if predicting the initial listing price.
- For time-dependent data, use a time-aware split instead of a random split.

## Output

Notebooks save metrics under `outputs/metrics/`. Create this directory automatically by running the relevant notebook. Output metrics are generated from your own run; do not copy unverified example numbers.

## Troubleshooting

- **Workbook not found:** check the file path and `DATA_PATH` cell.
- **Worksheet not found:** confirm the sheet is named `Data`.
- **Missing columns:** check `price_etb` and, for notebook 01, `size_sqm`.
- **MLP/SVR slow:** reduce the parameter grid or run fewer CV configurations for a first experiment.
- **PowerShell activation blocked:** run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` in that terminal, then activate the environment.
