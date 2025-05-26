# Calorie Estimation & Category Classification of McDonald's Menu Items
## 1. Project Overview
This repository contains a two-part machine learning pipeline that tackles calorie estimation and menu-item classification for McDonald’s menu. The initial goals were:

- Calorie Estimation: Use regression techniques to predict calories based on nutrition features (fat, carbs, protein, saturated fat, sugars).

- Category Classification: Use classification algorithms to assign each menu item to a predefined category (Beef & Pork, Beverages, Breakfast, Chicken & Fish, Coffee & Tea, Desserts & Shakes, Snacks & Sides).

## 2. RAW_DATA

All raw data used in this project is sourced from the official McDonald’s Nutrition Facts dataset on Kaggle:

Dataset: [McDonald’s Nutrition Facts](https://www.kaggle.com/datasets/mcdonalds/nutrition-facts/data)

menu.csv: Original data file with 260 menu items and nutrition features (Calories, Protein, Total Fat, Saturated Fat, Carbohydrates, Sugars).

## 3. DATA

In this section, we explore and preprocess the data:

Exploration: See initial_exploration.ipynb for summary statistics, missing-value analysis, and distribution plots of each nutrition feature.

Transformations: 
- Dropped missing values and duplicate records.

- Converted string values to numeric types.

- Standardized features using StandardScaler for downstream modeling.

Visualizations: Link to histograms, boxplots, and pairplots generated in the exploration notebook.

Regression: Calorie Estimation

## 4.ANALYSIS

Here, we present the technical results of our regression and classification pipelines.

Regression: Calorie Estimation

Pipeline: Split data into 80% train / 20% test, applied 5-fold cross-validation on training data.

Model: Linear Regression to estimate calories as a function of nutrition features.

Key Findings:

- Each gram of Total Fat adds approximately +130 calories.

- Each gram of Carbohydrates adds approximately +120 calories.

- Each gram of Protein adds approximately +48 calories.

- Each gram of Saturated Fat adds approximately +3 calories.

- Each gram of Sugars contributes approximately –3 calories.

Metrics: See notebooks/regression_analysis.ipynb for MSE, RMSE, MAE, and R² on the test set.

Classification & Clustering: Menu-Item Tagging

Models Evaluated:

|Model          |Accuracy|Macro F1|Weighted F1|
|---------------|--------|--------|-----------|
|Decision Tree  |75%     |0.55    |  0.74     |
|SVM            |73%     |0.54    |  0.74     |
|Random Forest  |99%     |0.99    |  0.99     |
|Neural Network |67%     |0.60    |  0.67     |

Best Model: Random Forest achieved the highest accuracy and F1-scores on the test set.

Clustering: Applied PCA (first two components capture ~92% variance) and k‑means clustering to group items by calorie 

profile:

- Low Calorie: Beverages & light snacks

- Moderate Calorie: Balanced meals (burgers, sandwiches)

- High Calorie: Hearty entrées (breakfast platters)

Details & Tuning: See classification.ipynb for model hyperparameter tuning, confusion matrices, and cluster visualizations.

Challenges & Limitations

Imbalanced category distribution required stratification and careful metric selection.

Linear assumptions in the regression model may not fully capture non-linear effects of saturated fat and sugars.

Further improvements could include regularization techniques (Ridge, Lasso), ensemble methods, and deeper neural networks.

## 5.CONCLUSIONS

This project demonstrates how straightforward machine learning pipelines can provide actionable insights for menu analysis:

- Calorie Estimation: We learned that macronutrient contributions to calories are not equally weighted—fat and carbohydrates dominate calorie counts.

- Category Tagging: Ensemble methods like Random Forest excel at capturing complex nutritional patterns for accurate menu classification.

- Business Impact: Such pipelines can fuel dynamic calorie-estimation tools, personalized menu recommendations, and nutritional compliance dashboards.
