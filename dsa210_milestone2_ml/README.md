# DSA210 Project - Milestone 2 (Machine Learning)

## Updates from Milestone 1
Based on the TA feedback received for Milestone 1 ("Sample Size is small; you should rerun the whole explanatory and hypothesis testing part again after having all your data"), I have updated the dataset from 15 days to 37 days. 

As a result, this folder includes the **updated EDA and Hypothesis Testing** run on the larger dataset to provide more statistically significant results. 

## Milestone 2: Machine Learning
This milestone applies a **Linear Regression** model to predict `Productivity_Score` based on three features:
- `Sleep_Hours`
- `Phone_Screen_Time_Hours`
- `Study_Hours`

### Files Included:
- `Milestone2_ML.ipynb`: Contains the full pipeline (Data Loading -> Updated EDA -> Updated Hypothesis Testing -> Machine Learning Model).
- `dsa210_collected_data.csv`: The updated 37-day dataset.
- `correlation_heatmap.png` & `distributions.png`: Updated visuals from the larger dataset.
- `ml_prediction_scatter.png`: A scatter plot showing the Actual vs. Predicted Productivity scores from the ML model.

### ML Results Summary
The Linear Regression coefficients demonstrated how each hour of sleep and studying positively impacted productivity, while excessive phone screen time negatively impacted the score.