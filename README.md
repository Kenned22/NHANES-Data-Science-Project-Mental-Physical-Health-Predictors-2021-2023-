# NHANES Sleep, Health, and Depression Analysis (2021–2022)

This repository contains cleaned and merged data from the **National Health and Nutrition Examination Survey (NHANES) 2021–2022** public-use files. The project explores relationships between sleep, physical health behaviors, biomarkers, socioeconomic factors, and depression outcomes in U.S. adults.

All data are publicly available and provided by the **U.S. Centers for Disease Control and Prevention (CDC)**.

NHANES Data Portal: https://wwwn.cdc.gov/nchs/nhanes/

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

- **Inflammation (`HSCRP_L`)**
  - High-sensitivity C-reactive protein (CRP)

- **Body Measures (`BMX_L`)**
  - Body Mass Index (BMI)

- **Smoking – Cigarette Use (`SMQ_L`)**
  - Number of cigarettes smoked per day

- **Physical Activity (`PAQ_L`)**
  - Sedentary minutes per day
  - Frequency of physical and moderate activity

- **Occupation (`OCQ_L`)**
  - Hours worked in the past week

---

## Project Focus

This project investigates how sleep, physical activity, BMI, inflammation, smoking, work hours, and socioeconomic status relate to **depression severity (PHQ-9)** using statistical and machine learning methods.

---

## Notes

- Only **public-use NHANES data** were used.
- Invalid PHQ-9 responses (7 = refused, 9 = don’t know) were treated as missing.
- All datasets were merged using `SEQN`.
- This repository is intended for educational and research purposes.

---
## PHQ-9 Depression Scoring

Depression symptoms were assessed using the **Patient Health Questionnaire-9 (PHQ-9)** from the NHANES Mental Health – Depression Screener component (`DPQ_L`). The PHQ-9 is a validated nine-item screening instrument that measures the frequency of depressive symptoms over the past two weeks and is based on DSM-IV diagnostic criteria (Kroenke & Spitzer, 2002).

Each of the nine symptom items (`DPQ010`–`DPQ090`) is scored on a 4-point scale:
- 0 = Not at all  
- 1 = Several days  
- 2 = More than half the days  
- 3 = Nearly every day  

Responses coded as **7 (Refused)** or **9 (Don’t know)** were treated as missing and excluded from scoring.

PHQ‑9 total scores were calculated only for participants with complete responses to all nine symptom items, following NHANES analytic guidelines. Responses coded as ‘Refused’ or ‘Don’t know’ were treated as missing, and participants with incomplete PHQ‑9 data were excluded from depression scoring.

### Total PHQ-9 Score
A total PHQ-9 score was calculated by summing the nine symptom items, yielding a possible range from **0 to 27**. Scores were only computed for participants with complete responses to all nine items, consistent with NHANES analytic guidance.

### Depression Classification
In addition to the continuous total score, a binary depression indicator was created using a standard clinical cutoff:
- **PHQ-9 ≥ 10** indicates moderate to severe depressive symptoms.

This threshold is commonly used in clinical and epidemiological research to identify individuals with clinically meaningful depression.

Only data from participants **aged 18 years and older** were included, as adult PHQ-9 data are publicly available for NHANES 2021–2022. Youth depression data (ages 12–17) are available only through the NCHS Research Data Center and were not used in this project.

### References
Kroenke, K., Spitzer, R. L., & Williams, J. B. (2001). The PHQ-9: Validity of a brief depression severity measure. *Journal of General Internal Medicine*, 16(9), 606–613.  
Kroenke, K., & Spitzer, R. L. (2002). The PHQ-9: A new depression diagnostic and severity measure. *Psychiatric Annals*, 32(9), 509–515.  
Spitzer, R. L., Kroenke, K., & Williams, J. B. (1999). Validation and utility of a self-report version of PRIME-MD. *JAMA*, 282(18), 1737–1744.

---

## Citation

Centers for Disease Control and Prevention (CDC).  
*National Health and Nutrition Examination Survey Data.*  
Hyattsville, MD: U.S. Department of Health and Human Services.  
https://wwwn.cdc.gov/nchs/nhanes/
