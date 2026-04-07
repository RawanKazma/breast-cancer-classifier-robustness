# breast Cancer Classifier Robustness
Evaluation of machine learning classifiers on a clinically relevant breast cancer dataset.

---

## Project Overview

This project investigates the robustness and generalization of machine learning models on a **medical classification problem**. Real-world clinical datasets often contain **overlapping classes, complex decision boundaries and noisy features**, making model performance challenging to evaluate.  

The Breast Cancer Wisconsin dataset (biopsy-derived features labeled as Benign or Malignant) was used to test how classifiers handle these realistic conditions.

- **Clinical Relevance:** Accurate classification of benign and malignant cases is critical in medical diagnostics, even under feature ambiguity 
- **Objective:** Assess which machine learning algorithms perform best under overlapping, noisy and complex data conditions.

---

## Dataset

- **Source:** Kaggle – Breast Cancer Wisconsin (Diagnostic) dataset  
- **Samples:** 569  
- **Features:** 30 numerical biopsy-derived attributes  
- **Labels:** Benign (B) or Malignant (M)  
- **Class Balance:** B: 63%, M: 37%  
- **Notes:** No missing values; moderate class imbalance  

---

## Methods

### Data Preprocessing

- Stratified split: 60% training, 20% validation, 20% testing  
- Feature scaling applied **after splitting** to prevent data leakage  
- PCA applied for 2D and 3D visualization to inspect class overlap  

### Models Evaluated

1. **Logistic Regression**  
   - Linear, interpretable classifier  
   - Grid search + 5-fold cross-validation (penalty='l2', C=0.1, solver='liblinear')  

2. **Support Vector Machine (SVM)**  
   - Non-linear classification with RBF kernel  
   - Maximizes margin to improve generalization and handle overlap  
   - Grid search + 5-fold cross-validation (C=10, gamma=0.001)  

---

## Results

| Model | Accuracy | Precision | Recall | F1-Score | Training Error | Test Error |
|-------|---------|----------|--------|----------|----------------|------------|
| Logistic Regression | 0.982 | 0.99 | 0.97 | 0.986 | 0.01 | 0.0175 |
| SVM | 0.98 | 0.99 | 0.97 | 0.98 | 0.01 | 0.009 |

- PCA plots confirmed **overlapping classes** near decision boundaries  
- Logistic Regression is robust and interpretable; threshold tuning allows prioritization of sensitivity or specificity  
- SVM captures **non-linear boundaries**, improving separation of complex patterns  
- Both models show **low train-test gaps**, indicating strong generalization  

---

## Key Observations

- Small, noisy medical datasets challenge classifier robustness  
- SVM performs slightly better in handling overlap due to flexible boundaries  
- Logistic Regression is effective for interpretable and reliable clinical prediction  
- Limited dataset size restricts strong conclusions; larger datasets are needed for robust evaluation  
