# Personalized Cancer Diagnosis

Classifies genetic mutations into 9 classes using the gene, the variation and the clinical text (multi-class classification).

## Data
- Kaggle competition "Personalized Medicine: Redefining Cancer Treatment" (Memorial Sloan Kettering Cancer Center)
- 3,321 rows: gene, variation, clinical text and class (1 to 9)
- Split 80/20, stratified: 2,656 train rows, 665 test rows
- The data is for non-commercial use, so the data files are not included here. Download them from Kaggle and put them in a Google Drive folder named cancer_project.

## Method
- Cleaning: lowercase, removed symbols and extra spaces, empty texts replaced by gene and variation
- Features: TF-IDF of the text (20,000 features, single words and word pairs) plus one-hot encoding of gene and variation (22,644 features in total)
- Models: baseline (class shares), Logistic Regression (C chosen by 3-fold cross-validation), XGBoost
- Metrics: log loss (main score), accuracy, confusion table

## Results

| Method | Log loss | Accuracy |
|---|---|---|
| Baseline (class shares) | 1.8306 | 28.7% |
| Logistic Regression | 1.0115 | 67.9% |
| XGBoost | 1.1431 | 62.6% |

Best model: Logistic Regression, about 45% lower log loss than the baseline.

## Limitations
- About 90% of the test variations never appear in the training data
- Small data, and classes 8 and 9 have very few rows (class 8 was never predicted)
- Best model chosen using the test set, from only three models
- No deep learning or word embeddings, XGBoost not tuned

## Tools
Python, pandas, scikit-learn, scipy, XGBoost, Google Colab, Google Drive
