# NHANES Sleep, Health, and Depression Analysis (2021–2022)

This repository contains cleaned and merged data from the **National Health and Nutrition Examination Survey (NHANES) 2021–2022** public-use files. The project explores relationships between sleep, physical health behaviors, biomarkers, socioeconomic factors, and depression outcomes in U.S. adults.

All data are publicly available and provided by the **U.S. Centers for Disease Control and Prevention (CDC)**.

🔗 NHANES Data Portal: https://wwwn.cdc.gov/nchs/nhanes/

---

## 📊 Data Sources Included

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

## 🧠 Project Focus

This project investigates how sleep, physical activity, BMI, inflammation, smoking, work hours, and socioeconomic status relate to **depression severity (PHQ-9)** using statistical and machine learning methods.

---

## 📌 Notes

- Only **public-use NHANES data** were used.
- Invalid PHQ-9 responses (7 = refused, 9 = don’t know) were treated as missing.
- All datasets were merged using `SEQN`.
- This repository is intended for educational and research purposes.

---

## 📚 Citation

Centers for Disease Control and Prevention (CDC).  
*National Health and Nutrition Examination Survey Data.*  
Hyattsville, MD: U.S. Department of Health and Human Services.  
https://wwwn.cdc.gov/nchs/nhanes/
