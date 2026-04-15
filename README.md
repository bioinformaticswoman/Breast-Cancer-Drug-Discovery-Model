
# Predicting Drug Potency for Breast Cancer Target (ESR1) using Machine Learning

## Overview
This project explores how machine learning can be applied to drug discovery by predicting the potency of small molecules targeting the Estrogen Receptor Alpha (ESR1), a well-known protein involved in breast cancer.

The goal was to build a model that can estimate **pIC50 values** (a measure of drug effectiveness) directly from molecular structure, using publicly available bioactivity data from ChEMBL.

---

## Why this project?
Drug discovery is traditionally expensive and time-consuming. Computational approaches like this aim to **prioritize promising compounds early**, reducing experimental cost and effort.

Through this project, I wanted to understand how chemical structure translates into biological activity, and how well machine learning can capture that relationship.

---

## Dataset
- Source: ChEMBL database  
- Target: Estrogen Receptor Alpha (ESR1)  
- Bioactivity type: IC50 (converted to pIC50)  
- Organism: Homo sapiens  

Each data point represents a molecule (SMILES format) and its experimentally measured activity.

---

## Approach

### 1. Data Collection
Bioactivity data was retrieved programmatically using the ChEMBL API and filtered to include only IC50 measurements for ESR1.

### 2. Data Cleaning & Transformation
- Removed missing and inconsistent entries  
- Converted IC50 values (nM) to pIC50 for better numerical stability and interpretability  

### 3. Feature Engineering
Two types of features were used:

**Molecular Descriptors (RDKit):**
- Molecular Weight  
- LogP (lipophilicity)  
- Hydrogen Bond Donors/Acceptors  

**Molecular Fingerprints:**
- Morgan fingerprints (1024-bit vectors)  
- Capture structural patterns and substructures within molecules  

These fingerprints significantly improved model performance by providing richer chemical information.

---

## Model
- Algorithm: Random Forest Regressor  
- Train/Test Split: 80/20  

The model learns to map molecular features → drug potency (pIC50).

---

## Results

### Distribution of pIC50


![pIC50 Distribution](<img width="640" height="480" alt="pic50_distribution" src="https://github.com/user-attachments/assets/4c8a56d9-02d6-4737-a7fe-e44798aa2520" />
)

This shows how drug potency is distributed across the dataset.

---

### Model Performance


![Model Performance](<img width="574" height="463" alt="actual_vs_predicted_plot" src="https://github.com/user-attachments/assets/e94ce103-d631-4ba4-b825-726e787464c4" />
)

The scatter plot compares predicted vs experimental pIC50 values.  

---

### Feature Importance


![Feature Importance](<img width="676" height="440" alt="feature_importance" src="https://github.com/user-attachments/assets/8f85439d-0cda-4c3d-a7d0-f8e7dd2be8a4" />
)

This highlights which molecular properties contribute most to predictions.

---

## Key Takeaways
- Basic descriptors alone were insufficient for good predictions  
- Molecular fingerprints significantly improved performance  
- The model captures **some structure–activity relationship**, but not perfectly  
- Drug activity is influenced by complex factors beyond simple descriptors  

---

## Limitations
- Model performance is moderate and can be improved further  
- Only a subset of molecular features was used  
- No hyperparameter tuning or cross-validation was performed  

---

## Future Work
- Try advanced models (XGBoost, neural networks)  
- Perform hyperparameter optimization  
- Include additional descriptors (TPSA, rotatable bonds, etc.)  
- Explore deep learning-based molecular representations  

---

## Tools & Libraries
- Python  
- RDKit  
- Pandas, NumPy  
- Scikit-learn  
- Matplotlib, Seaborn  
- Google Colab  

---

## Project Structure
├── notebooks/
│ └── breast_cancer_drug_discovery.ipynb
├── data/
│ └── processed_dataset.csv
├── images/
│ ├── pic50_distribution.png
│ ├── predicted_vs_actual.png
│ └── feature_importance.png
└── README.md

---

## Final Thoughts
This project was a practical introduction to how machine learning can be applied in cheminformatics. It reinforced the importance of feature engineering and highlighted both the potential and limitations of predictive models in drug discovery.

---

## Author
Shagun Srivastava
