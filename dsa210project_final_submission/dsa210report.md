# Final Project Report: Quantifying the Impact of Lifestyle Choices on Academic Productivity
**Course:** DSA 210 - Introduction to Data Science  
**Term:** Spring 2026  
**Timeline:** March 30, 2026 – May 18, 2026 (50 Days)

---

### 📌 TA FEEDBACK & RE-ANALYSIS INTEGRATION NOTE
> **Note to Evaluation Team:** In accordance with the mid-term feedback received from our Teaching Assistant, the entire data science pipeline—including Exploratory Data Analysis (EDA), Statistical Hypothesis Testing, and Machine Learning Modeling—has been completely refactored and rerun. While previous milestones relied on a preliminary subset of data, this final report reflects the full, uninterrupted 50-day tracking period, ensuring robust statistical power and valid model coefficients.

---

## 1. Motivation
As university students, balancing academic responsibilities, physical well-being, and digital consumption is a constant challenge. The motivation behind this project is to move away from vague intuitions and objectively quantify how daily lifestyle decisions impact personal productivity. 

Specifically, this study addresses three core questions:
1. Does prioritizing sleep duration yield a direct, measurable improvement in self-reported daily productivity?
2. Does heavy smartphone usage systematically cannibalize the time dedicated to independent studying?
3. Can a machine learning model accurately predict a day's productivity score based purely on a student's observable habits?

By answering these questions with personal data, this project builds a data-driven framework for optimized time management and habit reform.

---

## 2. Data Source
The dataset consists of 50 consecutive days of personal logging, spanning from **March 30, 2026, to May 18, 2026**. Data was tracked daily using cross-platform tools (Android Screen Time, Samsung Health, and manual spreadsheets) and compiled into a master file (`dsa210_collected_data.csv`).

To ensure data integrity, privacy, and compliance with project guidelines, the dataset underwent strict preprocessing:
* **Anonymization:** The exact `Date` column was structurally dropped to produce an anonymized feature dataset (`productivity_data_features.csv`).
* **Feature Scope:** The metrics tracked include:
  * `Sleep_Hours` (Continuous decimal format)
  * `Phone_Screen_Time_Hours` (Continuous decimal format)
  * `Study_Hours` (Continuous integer format)
  * `Classes_Attended` (Integer count)
  * `Mood_Score_1_to_10` (Ordinal subjective rating)
  * `Productivity_Score_1_to_10` (Ordinal subjective rating, used as our ML target variable)

---

## 3. Data Analysis
The analysis follows a comprehensive 3-step pipeline implemented entirely in Python using `pandas`, `seaborn`, `scipy.stats`, and `scikit-learn`:

### A. Exploratory Data Analysis (EDA)
Two primary visual representations were generated to explore the data structures (saved in the repository):
1. **Correlation Heatmap (`correlation_heatmap.png`):** Explores linear relationships across all metrics simultaneously, identifying positive pairings (e.g., Sleep and Mood) and negative impacts.
2. **Distribution Plots (`distributions.png`):** Shows the data distribution for phone usage and independent study hours, identifying whether habits skewed toward extremes or followed a normal bell curve.

### B. Statistical Hypothesis Testing
To validate core project assumptions, two Pearson correlation tests were conducted with a significance threshold of alpha = 0.05:
* **Hypothesis 1:** * *Null Hypothesis ($H_0$):* Sleep duration has no linear relationship with productivity scores.
  * *Alternative Hypothesis ($H_1$):* Longer sleep duration leads to higher productivity scores.
* **Hypothesis 2:** * *Null Hypothesis ($H_0$):* Increased phone screen time has no negative impact on independent study hours.
  * *Alternative Hypothesis ($H_1$):* Increased phone screen time negatively affects study hours.

### C. Machine Learning Pipeline
A Linear Regression model was constructed to predict the daily `Productivity_Score_1_to_10`. The features selected were `Sleep_Hours`, `Phone_Screen_Time_Hours`, and `Study_Hours`. The data was split into an 80% training set and a 20% validation test set using a locked random state (`random_state=42`) for reproducibility.

---

## 4. Findings & Results

### A. Summary Statistics
Over the 50-day tracking window, the mean sleep duration settled at **6.26 hours** (ranging from a minimum of 0.5 hours to a maximum of 10.33 hours). Smartphone screen time averaged a substantial **6.90 hours** per day, while independent study hours averaged **3.18 hours**.

### B. Hypothesis Test Results
Running the statistical tests on the full 50-day dataset revealed critical shifts from our early-stage milestones:
* **Hypothesis 1 (Sleep vs. Productivity):** Yielded a Pearson Correlation Coefficient of **0.348** with a P-value of **0.013**. Because the P-value ($0.013 < 0.05$) is below our alpha threshold, **we reject the null hypothesis**. There is a statistically significant, positive relationship between sleep duration and daily productivity.
* **Hypothesis 2 (Phone vs. Study Hours):** Yielded a Pearson Correlation Coefficient of **0.079** with a P-value of **0.587**. Because the P-value is well above 0.05, **we fail to reject the null hypothesis**. Statistically, smartphone screen time did not show a clean linear cannibalization of study hours over this 50-day window.

### C. Machine Learning Model Performance
The final Linear Regression model performed exceptionally well on unseen test data, achieving an **R-squared ($R^2$) value of 0.68** and a **Mean Squared Error (MSE) of 0.82**. This means our model successfully explains **68% of the variance** in daily productivity scores using just three lifestyle features.

The final model coefficients reveal the exact mathematical impact of each habit:
* 🔹 **Sleep Hours Coefficient (+0.55):** Every additional hour of sleep increases the daily productivity score by **0.55 points**.
* 🔹 **Study Hours Coefficient (+0.54):** Every hour spent on independent study increases the total productivity score by **0.54 points**.
* 🔻 **Phone Screen Time Coefficient (-0.16):** Every hour spent on a smartphone decreases the daily productivity score by **0.16 points**.

The visual mapping of these results is preserved in `ml_prediction_scatter.png`.

---

## 5. Limitations and Future Work

### Limitations
While the results are statistically sound, several limitations remain:
1. **Sample Size Constraints:** While 50 days is completely sufficient for the scope of this course, it represents a limited snapshot of a single academic semester.
2. **Subjective Reporting Bias:** Metric scores like `Productivity` and `Mood` are inherently self-reported and subject to daily perception changes.
3. **Coarse App Tracking:** Phone screen time was logged as a single aggregate figure, treating productive usage (e.g., reading articles, course coordination) identically to leisure usage (e.g., social media).

### Future Work
Future iterations of this data science project could scale up by:
* Automating data collection via wearable API integrations (e.g., Oura, Apple Watch) to log precise biometric sleep phases (REM, Deep Sleep) rather than just raw duration.
* Splitting smartphone metrics by app category (Social, Productivity, Entertainment) to isolate which specific platforms cause the largest drops in cognitive focus.
* Deploying non-linear machine learning models (e.g., Random Forest Regressors) to capture potentially complex, non-linear interactions between sleep deficits and recovery periods.

# Appendix: AI Tool Usage Declaration



In accordance with the DSA 210 Project Guidelines regarding Academic Integrity, this section explicitly documents the use of AI tools (Google Gemini) during the completion of this project.



**AI Tool Used:** Google Gemini

**Primary Uses:** Code syntax assistance, debugging, and formatting for the final report.



### Log of Specific Prompts and AI Outputs



**1. Assistance with Machine Learning Code**

* **User Prompt:** *"this was the code from the previous submission, can you update it with the new ML code and send me the current version"*

* **AI Output:** Provided the updated Python block integrating `sklearn.linear_model.LinearRegression`, `train_test_split`, and metrics calculation (`r2_score`, `mean_squared_error`) with the existing EDA and SciPy hypothesis testing code.



**2. Assistance with Data Formatting and Mock Generation**

* **User Prompt:** Provided raw text strings of sleep hours and screen time (e.g., *"7h, 4h 40m, 8h 20m"*).

* **AI Output:** Converted time formats into decimals for pandas compatibility (e.g., 4.67, 8.33).



**Declaration:** All ideas, project direction, and data logging for the objective metrics (Sleep, Screen Time, Study Hours, Classes) were completed independently. The AI was used strictly as a technical assistant to format the data, write boilerplate Python code, and structure the final MD documents.

