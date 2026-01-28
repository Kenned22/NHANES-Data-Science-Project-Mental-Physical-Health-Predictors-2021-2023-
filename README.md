# NHANES Sleep, Health, and Depression Analysis (2021–2023)

This repository contains cleaned and merged data from the **National Health and Nutrition Examination Survey (NHANES) 2021–2023** public-use files. The project explores relationships between **sleep**, **physical health behaviors**, **biomarkers**, **socioeconomic factors**, and **depression severity** in U.S. adults.

All data are publicly available and provided by the **U.S. Centers for Disease Control and Prevention (CDC)**.

NHANES Data Portal: https://wwwn.cdc.gov/nchs/nhanes/

---

## Project Title

**Examining the Potential Mediating Role of Inflammation (CRP) in the Relationship Between BMI and Depression Severity**

---

## Research Question

> **Does inflammation, as measured by C-Reactive Protein (CRP), mediate the relationship between Body Mass Index (BMI) and depression severity (PHQ-9 score) in U.S. adults?**

---

## Data Variables Included

The following NHANES components were downloaded and merged using the participant identifier `SEQN`:

- **Demographics (`DEMO_L`)**
  - Age, gender, race/ethnicity
  - Household size
  - Income-to-poverty ratio (SES)

- **Sleep (`SLQ_L`)**
  - Weekday and weekend sleep duration
  - Average weekly sleep (derived)

- **Mental Health – Depression Screener (`DPQ_L`)**
  - PHQ-9 items (`DPQ010`–`DPQ090`)
  - Total PHQ-9 depression score
  - Binary depression indicator (PHQ-9 ≥ 10)
  - PHQ-9 severity classification

- **Inflammation (`HSCRP_L`)**
  - High-sensitivity C-reactive protein (CRP)

- **Body Measures (`BMX_L`)**
  - Body Mass Index (BMI)

- **Smoking – Cigarette Use (`SMQ_L`)**
  - Number of cigarettes smoked per day

- **Physical Activity (`PAQ_L`)**
  - Minutes of vigorous activity (`PAD680`)
  - Frequency of moderate activity (`PAD810Q`)
  - Time unit for moderate activity frequency (`PAD810U`) — per day, week, month, or year
  - Duration of moderate activity (`PAD820`)

- **Occupation (`OCQ_L`)**
  - Work status (`OCD150`)

---

## Engineered Variables

During cleaning and preparation, several derived variables were created for analysis:

- `phq9_score`: Total score across 9 PHQ-9 depression items (range: 0–27)
- `phq9_severity`: Categorical label of depression severity (None, Mild, Moderate, etc.)
- `is_depressed`: Binary indicator where 1 = PHQ-9 ≥ 10
- `sleep_avg`: Weighted average sleep duration over a full week
- `bmi`, `crp`, `age`: Renamed variables for clarity in modeling
- `cigarettes_per_day`: Cleaned version of raw smoking variable; excludes invalid codes
- `vigorous_activity_minutes`: Cleaned self-reported minutes of vigorous activity
- `vigorous_activity_category`: Categorized activity level: None / Low / Moderate / High
- `moderate_activity_frequency`: Frequency of moderate physical activity sessions
- `moderate_activity_units`: Unit for frequency (e.g., per week, per day)
- `moderate_activity_minutes`: Duration of each moderate activity session
- `employment_status`: Simplified from NHANES employment codes (Working vs. Not Working)

---

## Project Focus

This project investigates how BMI, inflammation, sleep, physical activity, smoking, and employment status relate to **depression severity (PHQ-9)** using statistical and machine learning methods.

A specific focus is placed on whether **CRP mediates the relationship between BMI and depression**, which could offer insight into possible inflammatory pathways underlying comorbidity.

---

## Planned Methods

At least 3 empirical/statistical learning (ESL) methods were applied:

- **Linear regression** to estimate total and direct effects (BMI → CRP, CRP → depression)
- **Mediation analysis with bootstrapping** to estimate indirect effects and test the mediation pathway
- **Generalized Additive Models (GAMs)** to explore non-linear effects (e.g., BMI on PHQ-9)
- **Regression trees** to explore interaction effects and nonlinear variable splits

---

## Missing Values Handling

- PHQ-9 responses coded as `7` (Refused) or `9` (Don’t know) were excluded.
- Special codes for missing data (e.g., 7777, 9999) were converted to `NA` in smoking, CRP, and activity variables.
- All datasets were merged using `SEQN`, and rows with incomplete core variable data were dropped.
- Final dataset includes **adults aged 18+** with valid depression screening and covariates.

---

## PHQ-9 Depression Scoring

Depression symptoms were assessed using the **Patient Health Questionnaire-9 (PHQ-9)** from the NHANES Mental Health – Depression Screener component (`DPQ_L`). The PHQ-9 is a validated nine-item screening instrument that measures the frequency of depressive symptoms over the past two weeks and is based on DSM-IV diagnostic criteria (Kroenke & Spitzer, 2002).

Each of the nine symptom items (`DPQ010`–`DPQ090`) is scored on a 4-point scale:
- 0 = Not at all  
- 1 = Several days  
- 2 = More than half the days  
- 3 = Nearly every day  

Responses coded as **7 (Refused)** or **9 (Don’t know)** were treated as missing and excluded from scoring.

PHQ‑9 total scores were calculated only for participants with complete responses to all nine symptom items, following NHANES analytic guidelines.

### Total PHQ-9 Score
A total PHQ-9 score was calculated by summing the nine symptom items, yielding a possible range from **0 to 27**.

### Depression Classification
In addition to the continuous total score, a binary depression indicator was created using a standard clinical cutoff:
- **PHQ-9 ≥ 10** indicates moderate to severe depressive symptoms.

| Severity Level        | Score Range |
|-----------------------|-------------|
| None / Minimal        | 0–4         |
| Mild                  | 5–9         |
| Moderate              | 10–14       |
| Moderately Severe     | 15–19       |
| Severe                | 20–27       |

Only data from participants **aged 18 years and older** were included, as adult PHQ-9 data are publicly available for NHANES 2021–2023. Youth depression data (ages 12–17) are available only through the NCHS Research Data Center and were not used in this project.

### References
Kroenke, K., Spitzer, R. L., & Williams, J. B. (2001). The PHQ-9: Validity of a brief depression severity measure. *Journal of General Internal Medicine*, 16(9), 606–613.  
Kroenke, K., & Spitzer, R. L. (2002). The PHQ-9: A new depression diagnostic and severity measure. *Psychiatric Annals*, 32(9), 509–515.  
Spitzer, R. L., Kroenke, K., & Williams, J. B. (1999). Validation and utility of a self-report version of PRIME-MD. *JAMA*, 282(18), 1737–1744.

---

## Included Files

- `nhanes_cleaned_2021_2023.csv` – Final cleaned and merged dataset with derived variables.
- `variable_legend.xlsx` – Description of variables used and engineered for analysis.

---

## Citation

Centers for Disease Control and Prevention (CDC).  
*National Health and Nutrition Examination Survey Data.*  
Hyattsville, MD: U.S. Department of Health and Human Services.  
https://wwwn.cdc.gov/nchs/nhanes/
