# 🧠 Exploratory Data Analysis (EDA) Report: Titanic Dataset

## 🧾 Objective:
To explore and understand the patterns, trends, and anomalies in the Titanic dataset, with a focus on identifying the key factors that influenced passenger survival.

---

## 1️⃣ Summary Statistics & Visual Exploration

- **Numerical features** (`Age`, `Fare`, `SibSp`, `Parch`) were summarized using mean, median, standard deviation, min, and max values.
- Visualizations used:
  - **Histograms** and **KDE plots** to understand distribution
  - **Boxplots** to spot outliers
  - **Heatmap** to examine correlation between variables
  - **Pairplot** to identify separable patterns between survival and features

---

## 2️⃣ Chi-Square Tests (Categorical Pattern Significance)

| Feature   | p-value        | Significant? | Conclusion                                 |
|-----------|----------------|--------------|--------------------------------------------|
| `Pclass`  | 2.11e-11       | ✅ Yes        | Survival strongly depended on class        |
| `SibSp`   | 0.0058         | ✅ Yes        | Survival was influenced by family size     |
| `Parch`   | 2.86e-06       | ✅ Yes        | Survival affected by number of dependents  |

> All tested categorical features showed statistically significant associations with survival.

---

## 3️⃣ T-Tests (Numerical Feature Differences)

| Feature   | p-value        | Significant? | Conclusion                                 |
|-----------|----------------|--------------|--------------------------------------------|
| `Fare`    | 7.09e-12       | ✅ Yes        | Survivors paid significantly higher fares  |
| `Age`     | 0.0146         | ✅ Yes        | Survivors were slightly younger on average |

> Both key numerical features showed statistically significant differences between survivors and non-survivors.

---

## 4️⃣ Anomaly Detection (Z-score Method)

- **Fare**: 18 statistical outliers found (Z > 3); valid high-value cases, likely wealthy passengers or group ticket purchases.
- **Age**: 0 outliers found; age values are well-distributed post-cleaning.

> Z-score confirmed that no extreme anomalies remain that would bias the analysis, validating our previous IQR-based cleaning.

---

## 5️⃣ Group-Based Survival Rate Trends

### ➤ By Passenger Class (`Pclass`)

| Pclass | Survival Rate |
|--------|----------------|
| 1      | 56.38%         |
| 2      | 46.58%         |
| 3      | 24.65%         |

> 🎯 **Insight**: Survival rate decreased as passenger class dropped — reflecting a clear socioeconomic bias in lifeboat access.

---

### ➤ By Siblings/Spouses (`SibSp`)

| SibSp | Survival Rate |
|--------|----------------|
| 0      | 30.82%         |
| 1      | 44.73%         |
| 2      | 38.89%         |

> 🎯 **Insight**: People traveling with 1–2 family members had better chances. Those alone had lower survival odds.

---

### ➤ By Parents/Children (`Parch`)

| Parch | Survival Rate |
|--------|----------------|
| 0      | 29.98%         |
| 1      | 60.29%         |
| 2      | 56.67%         |
| 3      | 60.00%         |
| 4+     | ≤ 20.00%       |

> 🎯 **Insight**: Small family units (1–3 dependents) were most likely to survive. Very large families had near-zero survival, likely due to evacuation challenges.

---

## 6️⃣ Feature-Level Inferences from Visuals

### 📊 Fare
- Right-skewed distribution; higher fares had better survival rates.
- Survivors peaked around high fare values in KDE plots.
> 💡 Inference: **Paying more → higher survival odds**, likely tied to class and cabin proximity to lifeboats.

---

### 👤 Age
- Near-normal distribution; no post-cleaning outliers.
- Survivors had a slight peak at lower ages.
> 💡 Inference: **Younger passengers had better survival odds**, possibly due to evacuation prioritization.

---

### 👫 SibSp
- Most passengers had 0 or 1 companion.
- Survival peaked with 1–2 family members.
> 💡 Inference: Small groups increased odds of survival; being alone or in large groups reduced it.

---

### 👨‍👩‍👧 Parch
- Most passengers had 0–2 dependents.
- Survival peaked at Parch = 1–3.
> 💡 Inference: **Moderate family size improved survival**; very large families suffered due to complexity during emergencies.

---

### 🧮 Pclass
- Clear survival gradient from 1st → 3rd class.
- Strong negative correlation with survival.
> 💡 Inference: Class was **the most influential categorical feature** — showing socioeconomic disparity in survival.

---

### 🔗 Correlation Heatmap
- `Fare` had the strongest positive correlation with `Survived`.
- `Pclass` had the strongest negative correlation.
> 💡 Inference: Wealthier, upper-class passengers had both **monetary** and **social advantages** that increased survival.

---

## ✅ Final Comprehensive Insights

- Survival was **not random** — it was systematically influenced by:
  - **Passenger class**
  - **Ticket fare**
  - **Age**
  - **Family size (SibSp + Parch)**
- **First-class passengers and those with smaller family groups had the highest chances of survival.**
- These findings align across visualizations, statistical tests, and grouped survival trends — confirming their reliability and depth.

---

## 📌 Next Steps (Optional)

- Engineer new features (e.g., `FamilySize = SibSp + Parch + 1`)
- Train machine learning models (e.g., Logistic Regression, Decision Tree)
- Deploy as an interactive dashboard using Tableau or Streamlit
