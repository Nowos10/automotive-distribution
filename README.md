
# Part Number Classification using XGBoost

This project leverages machine learning (specifically XGBoost) to automate the labeling of product inventory descriptions using historical data. It addresses challenges in inventory management by classifying unlabeled part numbers based on their attributes and textual descriptions.

## Objective
Automate the labeling of 60,000+ unlabeled inventory items using machine learning, improving classification, forecasting, and cost estimation.

## Dataset
- Input: `Test.xlsx` (Contains over 80,000 inventory items)
- Features: `Item Description`, `UM`, `Product Line`, `Product Group`, `Type`, `Net Weight`
- Label: `Label from SKU Hierarchy3` (target variable)

## Workflow

1. **Data Cleaning and Feature Selection**
   - Removed unnecessary columns and cleaned item descriptions using regex.
   - Extracted keywords from descriptions to improve model interpretability.

2. **Data Preprocessing**
   - Encoded categorical variables using `OrdinalEncoder` and `LabelEncoder`.
   - Filtered out classes with fewer than 8 samples.
   - Split data into training/testing sets (80/20) using stratified sampling.

3. **Modeling**
   - Used `XGBClassifier` for multi-class classification.
   - Applied SMOTE (commented out) for class imbalance.
   - Evaluated using confusion matrix and classification report.

4. **Final Prediction**
   - Trained on the full labeled dataset.
   - Predicted labels for the full inventory, including initially unlabeled items.
   - Saved predictions to `Final_prediction_updated.xlsx`.

## Key Libraries
```python
pandas, numpy, matplotlib, seaborn, re
scikit-learn: LabelEncoder, OrdinalEncoder, train_test_split
imblearn: SMOTE
xgboost: XGBClassifier
```

## Evaluation Metrics
- Accuracy: ~95%
- Macro and weighted F1-scores reported per class
- Multi-class confusion matrix for visual diagnostics

## Output
Final output includes predicted labels for each part number saved in Excel for further business analysis.

## File
- `Final_prediction_updated.xlsx`: Contains predictions with relevant features
- `XGB Model - product_classification.pdf`: Full code with steps and visualizations
