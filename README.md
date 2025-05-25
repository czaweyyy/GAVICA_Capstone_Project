# 🎓 TEECE 2 Capstone Project  
## 🧠 *Lifestyle and Learning: Predicting Student Performance*

---

### 👥 Group Members
- **Ma. Charina O. Gavica**
- **Ma. Crista F. Jara**
- **Khryzelle Trisha L. Suyat**

---

## I. Introduction

This project utilizes a simulated dataset of 1,000 student records sourced from Kaggle. Each record captures key lifestyle habits—such as study hours, sleep patterns, screen time, diet, and mental health—and relates them to academic performance, specifically the final exam score. The dataset is ideal for educational machine learning applications, enabling learners to perform data preprocessing, visualization, clustering, regression, and classification.

The primary goal is to analyze how these lifestyle factors affect student performance and to build predictive models based on the insights derived.

---

## II. Project Goals

- Determine relationships between lifestyle habits and final exam scores  
- Discover meaningful student groupings based on lifestyle through clustering  
- Build and evaluate models that predict academic performance  
- Summarize and communicate findings through data storytelling  

---

## III. Project Components

### 1. Problem Definition

**Research Questions:**
- How do various lifestyle habits such as study hours, sleep patterns, screen time, diet quality, and mental health influence student performance?
- Can these factors be used to accurately predict academic performance?
- What distinct types of students emerge based on their habits and lifestyle, and how do these groups differ in academic performance?

---

### 2. Data Understanding and Preprocessing

- **Importing Necessary Libraries**
- **Loading and Inspecting the Dataset**
- **Handling Missing Data**: Handled using median and mode imputation  
- **Categorical Encoding**: Label encoding, binary mapping, and ordinal encoding  
- **Feature Scaling**: Standardization with `StandardScaler`  
- **Feature Engineering**: Created new features like `study_efficiency` and `sleep_quality_score`

---

### 3. Exploratory Data Analysis (EDA)

- **Histograms** to visualize distributions  
- **Scatter Plots**: Comparing habits to exam scores  
- **Box Plots**: To compare score distributions across categories  
- **Correlation Heatmap**: To reveal multicollinearity and relationships  
- Key Insight: Study time and sleep quality positively correlate with scores, while excessive screen time negatively correlates.

---

### 4. Clustering (Unsupervised Learning)

- **KMeans Clustering** on lifestyle features (excluding target variable `exam_score`)
- **Elbow Method**:
  - Inertia decreases rapidly from K=1 to K=3
  - The curve forms an "elbow" at K=3 → **Optimal number of clusters = 3**
- **Silhouette Score** also confirmed K=3
- **Cluster Interpretation**:
  - **Cluster 0**: High Screen Time & Low Sleep
  - **Cluster 1**: Balanced Lifestyle & High Efficiency
  - **Cluster 2**: Well-Rested & Active

---

### 5. Regression Analysis (Supervised Learning)

Trained and compared three regression models:

**Models:**
- Linear Regression  
- Decision Tree Regressor  
- Random Forest Regressor  

**Evaluation Metrics:**
- Mean Absolute Error (MAE)  
- Root Mean Square Error (RMSE)  
- R² Score  

**Validation:**
- 80/20 Train-Test Split  
- 5-Fold Cross-Validation  

**Findings:**
- **Random Forest Regressor** achieved the best accuracy.
- Decision Tree performed decently but risked overfitting.
- Linear Regression was simplest but less accurate.

---

### 6. Optional Classification Task

Converted continuous exam scores into three performance categories:

**Class Encoding:**
- **Low Performer**: Bottom 33%  
- **Average Performer**: Middle 34%  
- **High Performer**: Top 33%

**Models Used:**
- Logistic Regression  
- Decision Tree Classifier
- Random Forest 

**Evaluation:**
- Confusion Matrix  
- Accuracy  
- F1-Score

**Insight:** Logistic Regression performed best for distinguishing High vs. Low performers. Decision Tree was useful but needed pruning to generalize well.

---
## Interpretation and Insights

### A. Feature Importance

**Key Findings from Decision Tree and Random Forest:**

- **Most Important Feature:**  
  `study_hours_per_day` — Dominant across both models  
  ➤ Daily study time is the strongest predictor of academic performance.

- **Moderately Important:**  
  `total_well-being` — Second highest in both models  
  ➤ Well-being (sleep, exercise, mental health) contributes positively.

- **Lower Importance:**  
  `total_screen_time` — Some impact, more in Decision Tree  
  ➤ Higher screen time may reduce focus and rest.

- **Least Important:**  
  `social_media_hours` — Nearly no predictive power  
  ➤ Social media use alone is not strongly tied to performance.

**Linear Regression Coefficient Insights:**

- **Top Positive Influencers:**
  - study_hours_per_day
  - study_efficiency
  - mental_health_rating
  - total_well-being
  - attendance_percentage

- **Top Negative Influencers:**
  - total_screen_time
  - social_media_hours
  - netflix_hours

- **Minimal Impact Features:**
  - gender, age, exercise_frequency, internet_quality, parental_education_level

---

### B. Cluster Profiling (K-Means Clustering)

Using lifestyle features (excluding `exam_score`), we identified 3 distinct behavioral clusters:

| Cluster | Profile | Avg Exam Score | Key Traits |
|--------|---------|----------------|------------|
| 0 | High Screen & Low Sleep | -0.28 | High screen time, low well-being, poor study habits |
| 1 | Balanced & High Efficiency | 0.50 | High study efficiency, balanced well-being, low screen time |
| 2 | Well-Rested & Active | 0.42 | Good sleep & health, moderate study effort, low screen time |

**Key Patterns:**
- Screen Time ↑ → Scores ↓  
- Efficiency + Attendance ↑ → Scores ↑  
- Well-Being ↑ → Higher Resilience & Performance  

---

### C. Model Performance (Regression)

We evaluated five models for predicting exam scores:

| Model | Mean R² | Mean MAE | Mean RMSE |
|-------|--------:|---------:|----------:|
| Linear Regression (CV) | 0.90 | 0.25 | 0.31 |
| Decision Tree Regressor (CV) | 0.71 | 0.41 | 0.53 |
| Decision Tree (Tuned) | 0.92 | 0.21 | 0.28 |
| Random Forest Regressor (CV) | 0.87 | 0.28 | 0.35 |
| Random Forest (Tuned, Test Set) ✅ | 0.98 | 0.10 | 0.12 |

**Summary:**
- **Best Model:** Random Forest (Tuned)
- **Most Interpretable:** Linear Regression
- **Best Trade-off:** Decision Tree (Tuned)

---

### D. Optional Classification Task

Scores were classified into:
- Low (bottom 33%)
- Average (middle 34%)
- High (top 33%)

Classification models trained (Logistic Regression, Decision Tree) showed:
- Moderate performance
- Best used for broad performance categorization

---

## Final Recommendations

### Study Consistently
study_hours_per_day is the top predictor.  
📌 Daily study beats cramming.

### Attend Classes
study_efficiency = Time + Attendance  
📌 Presence matters.

### Prioritize Wellness
total_well-being has a major impact.  
📌 Sleep, exercise, and mental health support learning.

###  Manage Screen Time
total_screen_time inversely correlates with scores.  
📌 Limit distractions and bedtime browsing.

### Strive for Balance
The "Balanced & High Efficiency" cluster had the highest average score.  
📌 Balance study, rest, and health — don’t overdo any one area.

---

## Notable Observations

- **Social Media Alone ≠ Failure**  
  It only becomes harmful when combined with poor well-being.

- **Mental Health Matters**  
  Not the top-ranked, but tied to academic resilience.

- **Random Forest = Accuracy, Not Clarity**  
  For maximum accuracy, use forests.  
  For understanding, go with linear or decision trees.
