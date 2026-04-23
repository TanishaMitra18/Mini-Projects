# Heart Disease Risk Factor Analysis — Exploratory Data Analysis (EDA)

## Project Description
Cardiovascular disease remains one of the leading causes of mortality worldwide, yet many cases go undetected until symptoms become severe. Early identification of key risk factors is critical for timely diagnosis and intervention.

This project performs an exploratory data analysis (EDA) on the Cleveland Heart Disease dataset (UCI Repository, via Kaggle) — a dataset of 297 patients with 14 clinical variables including age, gender, cholesterol, chest pain type, and maximum heart rate.

The goal is to identify which factors show the strongest association with heart disease, uncover counterintuitive patterns in the data, and demonstrate how normalized analysis reveals insights that raw counts alone can miss.

---

## Objectives
1. Identify which demographic and clinical factors (age, gender, chest pain type, cholesterol, max heart rate) show the strongest association with heart disease.
2. Examine inter-variable correlations to understand how key risk factors relate to each other beyond their individual relationship with disease outcome.
3. Test initial hypotheses against actual data findings, particularly around chest pain type and cholesterol — where intuitive expectations may not align with clinical reality.
4. Demonstrate the limitations of correlation coefficients in imbalanced datasets, using sex vs condition as a case study where normalized rate analysis provides deeper insight than correlation alone.

---

## Dataset Overview
| Field | Details |
|-------|---------|
| Source | Cleveland Heart Disease Dataset — UCI Machine Learning Repository (via Kaggle) |
| Size | 297 patients, 14 clinical features |
| Target Variable | `condition` (0 = No Disease, 1 = Heart Disease) |
| Key Features | age, sex, cp, chol, thalach + 9 additional clinical markers |
| Class Balance | No Disease 53.9% (n=160), Heart Disease 46.1% (n=137) |
| Missing Values | None — no imputation required |

> Dataset downloaded from Kaggle. Original source: UCI Machine Learning Repository. Used for educational and portfolio purposes only.

---

## Tools Used
| Tool | Purpose |
|------|---------|
| Python 3 | Core programming language |
| Google Colab | Development environment |
| pandas | Data manipulation and aggregation |
| numpy | Numerical operations |
| matplotlib | Base plotting library |
| seaborn | Statistical visualizations |

---

## Key Findings

### 1. Age vs Heart Disease
Heart disease risk increased progressively with age, with a sharp jump after 50. Patients aged 61-75 showed the highest disease rate at **55.8%** — roughly 1 in 2 older patients — compared to just **29.3%** in the 41-50 group. Raw age counts were normalized across groups to avoid sample size bias, revealing a clear age-dependent risk pattern.

### 2. Gender vs Heart Disease
Initial hypothesis assumed no significant gender difference in disease prevalence. However, male patients showed a substantially higher disease rate **(55.7%)** compared to females **(26.0%)** — a 30 percentage point gap. This aligns with estrogen's known cardioprotective role in pre-menopausal women, supported by a secondary age-stratified analysis showing female disease rates jumping sharply from 4.5% (41-50) to 34.3% (51-60) — consistent with the menopausal transition window.

> **Note:** Female sample size (n=96) limits definitive conclusions; findings are directionally supported but not statistically robust.

### 3. Chest Pain Type vs Heart Disease
Asymptomatic patients showed by far the highest disease rate at **72.5%** — nearly 3 in 4 patients with no chest pain were diagnosed with heart disease. This pattern is consistent with **Silent Ischemia**, where absent symptoms delay diagnosis and intervention, allowing cardiovascular disease to progress undetected. Critically, asymptomatic patients also formed the largest group (n=142), suggesting silent heart disease may be significantly underdiagnosed in clinical settings.

### 4. Cholesterol vs Heart Disease
Contrary to the initial hypothesis, cholesterol showed only a marginal difference between diseased (median **253 mg/dl**) and healthy patients (median **235.5 mg/dl**), with a weak correlation coefficient of just **r=0.08**. A notable outlier — one patient with cholesterol of 564 mg/dl yet no heart disease diagnosis — further weakened the cholesterol-disease relationship. This suggests cholesterol alone is a poor individual predictor of cardiovascular risk.

### 5. Max Heart Rate vs Heart Disease
As hypothesised, diseased patients showed significantly lower maximum heart rates (median **142 bpm**) compared to healthy patients (median **161 bpm**) — a 19 bpm gap confirmed by box plot analysis. With a correlation coefficient of **r=-0.42**, max heart rate emerged as one of the strongest individual predictors of heart disease in this dataset.

---

## Limitations

### 1. Cholesterol Outlier
One patient recorded a cholesterol level of **564 mg/dl** — nearly 2.3x the upper normal range — yet showed no heart disease diagnosis. This likely represents either a data entry error or an unrelated condition such as Familial Hypercholesterolemia. The data point was retained but flagged as a potential anomaly.

### 2. Small Female Sample in Younger Age Groups
The 30-40 female age group contained only **5 patients** — too small for reliable interpretation. The 41-50 group (n=22) is borderline. Only the 51-60 (n=35) and 61-75 (n=33) groups provide sufficient sample sizes for directional conclusions.

### 3. Correlation Dilution in Sex vs Condition
The correlation coefficient (r=0.28) understates the true clinical gap of 30 percentage points revealed by normalized rate analysis. This occurs because **89 healthy males** and **25 diseased females** mathematically dilute the correlation signal — highlighting a key limitation of correlation coefficients in imbalanced datasets.

### 4. Limited Generalizability
With only 297 patients from Cleveland, USA (collected in 1988), findings may not generalize to broader populations. Regional lifestyle factors, dietary habits, and genetic backgrounds vary significantly across geographies and time periods.

### 5. Absence of Menopause Data
The estrogen cardioprotection hypothesis cannot be confirmed without explicit menopause status data. Including menopause age, hormone levels, or HRT status would allow direct testing of estrogen's protective role.

---

## Conclusions
This analysis demonstrates that heart disease, while not universally predictable from clinical markers alone, shows strong situational associations with specific factors. **Maximum heart rate (r=-0.42)**, **thalassemia type (r=0.52)**, **number of major vessels (r=0.46)**, and **chest pain type** emerged as the strongest predictors — while asymptomatic patients showed a striking **72.5% disease rate**, confirming that absence of symptoms is itself a critical risk signal.

Perhaps the most counterintuitive finding was **cholesterol's weak predictive power (r=0.08)**, challenging the common assumption that high cholesterol directly indicates heart disease risk. This analysis reinforces that cardiovascular risk is multifactorial and cannot be reduced to any single marker.

Future work should validate these findings on a larger, geographically diverse dataset with additional features including menopause status, hormone levels, and lifestyle factors.

---

## How To Run

**1. Clone this branch:**
```bash
git clone -b heart-disease-eda https://github.com/TanishaMitra18/Mini-Projects.git
```

**2. Download the dataset:**
Download from [Kaggle](https://www.kaggle.com/datasets/cherngs/heart-disease-cleveland-uci) and place in `/data` folder.

**3. Install dependencies:**
```bash
pip install pandas numpy matplotlib seaborn
```

**4. Run the notebook:**
- Open `heart_disease_eda.ipynb` in Google Colab or Jupyter
- Upload dataset to `/content/` if using Colab
- Run cells sequentially or use **Runtime → Run All**

---

## Author
**Tanisha Mitra**
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/tanisha-mitra-38a154254)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black)](https://github.com/TanishaMitra18)