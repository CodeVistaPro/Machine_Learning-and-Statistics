# 📌 A/B Testing Analysis 

## **📝 Project Overview**

A/B testing is a fundamental methodology used to compare two versions of a webpage to determine which one performs better in terms of conversions. This project aims to analyze whether a new webpage design improves conversion rates compared to the existing page. The goal is to leverage **statistical hypothesis testing** and **machine learning** to validate the findings and support business decision-making.

## **📂 Dataset Description**

We worked with two datasets that provided insights into user behavior and demographics:

### **1. A/B Test Data (********`ab_test.csv`********)**

This dataset records user interactions with either the control group (old page) or the treatment group (new page). It contains the following key columns:

- `id`: A unique identifier assigned to each user.
- `time`: Timestamp indicating when the user interacted with the page.
- `con_treat`: Group assignment (either `control` for users who saw the old page or `treatment` for users who saw the new page).
- `page`: Specifies whether the user viewed the `old_page` or the `new_page`.
- `converted`: A binary indicator (1 = User converted, 0 = User did not convert).

### **2. Country Data (********`countries_ab.csv`********)**

This dataset provides location-based information about users.

- `id`: Unique identifier to match with `ab_test.csv`.
- `country`: The country from which the user accessed the website.

### **🔧 Data Preprocessing & Merging**

To prepare the dataset for analysis, we followed these steps:

1. **Merging the datasets**: The country data was merged into the main A/B test dataset on the `id` column to add user location information.
2. **Checking for missing values**: Missing values were assessed and handled appropriately.
3. **Creating time-based features**: Extracted `hour` from the `time` column to analyze conversion trends over time.
4. **Ensuring data consistency**: Checked for duplicate records and data integrity before moving to the analysis phase.

---

## **📊 Exploratory Data Analysis (EDA)**

Before performing statistical tests, exploratory analysis was conducted to gain insights into user behavior:

- **Conversion Rate Analysis**:

  - Calculated overall conversion rates for control and treatment groups.
  - Analyzed conversion rates by country to observe regional trends.
  - Compared conversion rates across old and new pages to identify any patterns.

- **User Distribution**:

  - Bar chart visualization of the  countries with the most users.
  - Analyzed time-based conversion trends by plotting hourly conversion rates.

- **Summary Statistics**:

  - Generated descriptive statistics to understand the distribution of numerical and categorical variables.

---

## **📊 Statistical Hypothesis Testing**

### **✔️ Hypothesis Formulation**

To determine if the new page leads to a statistically significant increase in conversions, we formulated the following hypotheses:

- **Null Hypothesis (H₀)**: There is **no significant difference** in conversion rates between users who visited the old page and those who visited the new page.
- **Alternative Hypothesis (H₁)**: There is **a significant difference** in conversion rates, implying that the new page impacts user behavior.

### **📌 Statistical Tests Used**

1. **Chi-Square Test**:

   - A contingency table was created for conversion rates between the two groups.
   - The **Chi-Square test** was performed to check whether the observed difference in conversion rates was statistically significant.
   - **Result:** The p-value was **greater than 0.05**, indicating no significant difference.

2. **Independent T-Test**:

   - A t-test was conducted to compare the mean conversion rates between the control and treatment groups.
   - **Result:** The p-value was **greater than 0.05**, supporting the conclusion that there is no significant improvement in conversions.

🚀 **Conclusion from Statistical Tests:**

- There is **no strong statistical evidence** that the new page leads to better conversions.

---

## **🤖 Machine Learning with AutoML (PyCaret)**

To validate our statistical findings, we leveraged **PyCaret’s AutoML** framework to build machine learning models for conversion prediction.

### **Models Evaluated & Performance Metrics**

| Model                | Accuracy   | AUC        | Recall     | Precision  | F1 Score   |
| -------------------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| **Dummy Classifier** | **88.03%** | **0.500**  | **0.0000** | **0.0000** | **0.0000** |
| **LightGBM**         | **87.99%** | **0.5017** | **0.0001** | **0.0245** | **0.0002** |

### **🚀 Interpretation of AutoML Results**

✅ **High Accuracy (\~88%) but Low AUC (\~0.50)**

- AUC \~0.50 suggests that the models perform no better than random guessing.\
  ✅ **Dummy Classifier Performs Just as Well**
- Since the baseline model achieves similar accuracy, **no strong predictive pattern exists** in the dataset.
  ✅ **LightGBM Does Not Show Any Significant Improvement**
- This aligns with our statistical tests, confirming that the new page does not drive significant changes in user conversions.

---

## **🚀 Final Business Decision**

📌 **Statistical tests and machine learning models show no significant impact from the new page.**

📌  Conclusion : Since there is no clear advantage in deploying the new page, it's recommended to **experiment with other variables** such as call-to-action buttons, promotional strategies, and user engagement techniques to improve conversions.

📌 **Future Scope**:

- Conduct **multivariate A/B tests** by modifying multiple elements simultaneously.
- Include **additional behavioral metrics** (e.g., session duration, bounce rate) to understand user engagement more comprehensively.


