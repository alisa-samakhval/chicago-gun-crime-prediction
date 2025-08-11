#  Predicting Gun Involvement in Chicago Crimes

##  Overview
This project builds and evaluates machine learning models to predict whether an **ongoing crime in Chicago** will involve a firearm.  
Using **temporal**, **geographic**, and **location-based** features from the [Chicago Crime Dataset](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2/about_data), we compare a **Random Forest** and a **Linear Support Vector Machine** classifier.

---

##  Dataset
- **Source:** Chicago Crime Dataset (2001–Present)  
- **Subset Used:** 2016–2025 (~500k crimes)  
- **Balanced:** 50% firearm, 50% non-firearm via random undersampling  
- **Features:**  
  - Temporal: Hour of day, day of week  
  - Geographic: Latitude, Longitude  
  - Categorical: Primary Type, Location Description  
- **Target:** Firearm present (derived with regex on `Description` field)

---

##  Methodology
1. Extracted time, location, and categorical features  
2. One-hot encoding for categorical features  
3. Standard scaling for numeric features (SVM only)  
4. Random undersampling to balance classes  
5. Models:  
   - **Random Forest:** 100 trees, seed=42  
   - **Linear SVM:** `C=1.0`, `class_weight='balanced'`, `max_iter=10000`  
6. Evaluation: Balanced Accuracy, Precision, Recall, F1-Score

---

##  Results

| Metric              | Random Forest | Linear SVM |
|---------------------|--------------|------------|
| Balanced Accuracy   | 0.88         | **0.89**   |
| Precision (Pos/Neg) | 0.87 / 0.90  | **0.87 / 0.91** |
| Recall (Pos/Neg)    | 0.86 / 0.90  | **0.86 / 0.91** |

**Best Model:** Linear SVM (slightly higher across all metrics)




