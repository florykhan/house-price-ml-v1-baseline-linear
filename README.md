# 🏠 House Price Prediction — v1 Baseline Linear Model

This repository implements a **baseline machine learning pipeline** for predicting median house prices in California.  
It forms the **first version (v1)** of a multi-stage project focused on improving model performance through iterative experimentation.

---

## 🎯 Project Overview

The goal of this version is to:
- Build a **clean, reproducible baseline model** using Linear Regression.
- Establish a **solid workflow** for loading, exploring, and modeling structured tabular data.
- Evaluate baseline performance to guide improvements in future versions.

This version uses the **Normal Equation** (closed-form solution) for Linear Regression as implemented in `scikit-learn`.

---

## 🧱 Repository Structure
```
house-price-ml-v1-baseline-linear/
│
├── data/ # Dataset directory (kept empty intentionally for privacy / size)
│ └── housing.csv # Place your dataset here
│
├── notebooks/
│ ├── 01_exploration.ipynb # Exploratory Data Analysis (EDA)
│ └── 02_training.ipynb # Model training & evaluation
│
├── src/ # Placeholder for reusable helper scripts (empty in v1)
│
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt
```
> 🗒️ **Note:**  
> The `data/` and `src/` folders are intentionally left empty in this version.  
> - `data/` — add your own copy of `housing.csv` if running locally.  
> - `src/` — will contain helper functions in later versions.

---

## 📊 Dataset

- **Source:** California Housing dataset (available via `sklearn.datasets.fetch_california_housing` or [`Kaggle`](https://www.kaggle.com/datasets/camnugent/california-housing-prices))
- **Size:** ~20,000 samples, 8 numerical + 1 categorical feature  
- **Target:** `median_house_value`

| Feature | Description |
|----------|--------------|
| `longitude`, `latitude` | geographic coordinates |
| `housing_median_age` | median age of houses in the block |
| `total_rooms`, `total_bedrooms` | housing stock features |
| `population`, `households` | demographic context |
| `median_income` | median income (in tens of thousands of USD) |
| `ocean_proximity` | categorical location label |
| `median_house_value` | target (house price, in USD) |
  
---

## 🧭 Workflow Summary

### **1️⃣ Exploratory Data Analysis (01_exploration.ipynb)**
- Inspected schema, data types, and null values  
- Visualized distributions using histograms  
- Computed **correlation matrix** to identify strong predictors of price  
- Examined categorical feature `ocean_proximity` and its impact on target variable  

Key insight: **`median_income`** shows the strongest positive correlation with house value.

---

### **2️⃣ Model Training (02_training.ipynb)**
- Selected baseline features:
["median_income", "housing_median_age", "latitude", "longitude", "ocean_proximity"]

- Preprocessed data using:
  - `ColumnTransformer` for handling numeric & categorical columns
  - `OneHotEncoder` for `ocean_proximity`
- Trained a **Linear Regression** model using the **Normal Equation**
- Evaluated on test set using:
  - **RMSE** (Root Mean Squared Error)
  - **R² Score**

---

## 📈 Results

<table>
<tr>
<td>
  
| Metric | Value |
|---------|--------|
| **RMSE** | ≈ \$73,000 |
| **R²** | ≈ 0.6 |

</td>
<td style="vertical-align: top; padding-left: 25px;">

- The model explains ~60 % of variance in housing prices.
- Captures strong linear trends (e.g., income vs. price) but misses nonlinear and interaction effects.
  
</td>
</tr>
</table>

---

## 🧩 Key Takeaways

- A **clean baseline** provides a solid reference point for further experimentation.  
- **Median income** is the most informative predictor in this dataset.  
- Performance can be improved through:
  - Feature transformations  
  - Nonlinear terms  
  - Regularization and scaling

---

## 🧰 Run Locally

You can run this project on your machine using **Python 3.11** and `venv`.

### 1️⃣ Clone the repository
```bash
git clone git@github.com:florykhan/house-price-ml-v1-baseline-linear.git
cd house-price-ml-v1-baseline-linear
```

### 2️⃣ Create and activate a virtual environment
```bash
python3 -m venv venv
source venv/bin/activate   # (on macOS/Linux)
venv\Scripts\activate      # (on Windows)
```

### 3️⃣ Install dependencies
```bash
pip install -r requirements.txt
```

### 4️⃣ Add the dataset
Place `housing.csv` inside the `data/` folder:
```bash
house-price-ml-v1-baseline-linear/data/housing.csv
```

### 5️⃣ Run the notebooks
Launch Jupyter and open the notebooks:
```bash
jupyter notebook
```

Then run:
- `01_exploration.ipynb` — data exploration
- `02_training.ipynb` — model training & evaluation

---

## 🚀 Next Steps — Version 2

Future development will continue in [`house-price-ml-v2-feature-engineering`](https://github.com/florykhan/house-price-ml-v2-feature-engineering)

Planned enhancements:
- Implement **Gradient Descent** for Linear Regression (custom training loop)  
- Add **Feature Engineering** (derived ratios, log transformations)  
- Apply **Normalization / Standardization** for stable optimization  
- Experiment with **Polynomial Regression** for nonlinear patterns  
- Integrate **Regularization** (Ridge & Lasso)  
- Introduce **Cross-Validation** for robust evaluation  
- **Save trained model** for future use or deployment  

---

## 🧠 Tech Stack

- **Language:** Python 3.11  
- **Core Libraries:**  
  - `pandas`, `numpy`, `matplotlib`  
  - `scikit-learn`  
- **Environment:** Jupyter Notebook / VS Code  
- **Version Control:** Git + GitHub (SSH configured)

---

## 🧾 License
MIT License — feel free to use and modify with attribution.
See the [`LICENSE`](./LICENSE) file for full details.

---

## 👤 Author
**Ilian Khankhalaev**  
_BSc Computing Science, Simon Fraser University_  
📍 Vancouver, BC  |  [florykhan@gmail.com](mailto:florykhan@gmail.com)  |  [GitHub](https://github.com/florykhan)  |  [LinkedIn](https://www.linkedin.com/in/ilian-khankhalaev/)
