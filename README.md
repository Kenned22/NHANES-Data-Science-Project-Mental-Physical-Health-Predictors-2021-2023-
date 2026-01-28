# NHANES 2021–2023: BMI, Inflammation, and Depression Severity

This repository contains cleaned and merged data from the **National Health and Nutrition Examination Survey (NHANES) 2021–2023** public-use files. The project investigates the potential **mediating role of inflammation**—as measured by **C-reactive protein (CRP)**—in the relationship between **Body Mass Index (BMI)** and **depression severity** (PHQ-9 score) among U.S. adults.

All data are publicly available and provided by the **U.S. Centers for Disease Control and Prevention (CDC)**.

🔗 NHANES Data Portal: [https://wwwn.cdc.gov/nchs/nhanes/](https://wwwn.cdc.gov/nchs/nhanes/)

---

## 🎯 Research Question

**Does inflammation, as measured by high-sensitivity C-Reactive Protein (CRP), mediate the relationship between Body Mass Index (BMI) and depression severity (PHQ-9) in U.S. adults?**

---

## 📊 Variables Used

The following NHANES components were downloaded and merged using the participant identifier `SEQN`:

- **Demographics (`DEMO_L`)**
  - Age, gender, race/ethnicity
  - Household size
  - Income-to-poverty ratio (SES)

- **Body Measures (`BMX_L`)**
  - Body Mass Index (BMI)

- **Inflammation Biomarkers (`HSCRP_L`)**
  - High-sensitivity C-reactive protein (CRP)

- **Mental Health – Depression Screener (`DPQ_L`)**
  - PHQ-9 items (`DPQ010`–`DPQ090`)
  - Total PHQ-9 depression score
  - Binary depression indicator (PHQ-9 ≥ 10)

- **Sleep (`SLQ_L`)**
  - Weekday and weekend sleep duration
  - Average weekly sleep (derived)

- **Smoking – Cigarette Use (`SMQ_L`)**
  - Number of cigarettes smoked per day

- **Physical Activity (`PAQ_L`)**
  - Sedentary minutes per day
  - Frequency of physical and moderate activity

- **Occupation (`OCQ_L`)**
  - Hours worked in the past week

---

## 🧪 Planned Methods

We will apply both statistical and machine learning methods to examine the BMI–CRP–depression relationship and test for mediation effects:

1. **Linear Regression**
   - Estimate total and direct effects of BMI on depression severity.
   - Assess the BMI → CRP and CRP → depression pathways.

2. **Mediation Analysis (with Bootstrapping)**
   - Test for a statistically significant **indirect effect** of BMI on depression via CRP.
   - Quantify and test mediation using bootstrapped confidence intervals.

3. **Generalized Additive Models (GAMs)**
   - Visualize and explore potential **non-linear** relationships among BMI, CRP, and depression severity.

4. **Regression Trees**
   - Explore data-driven partitioning of depression severity based on predictors.
   - Use cost-complexity pruning to avoid overfitting.

---

## ⚠️ Expected Challenges

- Missing or incomplete survey and biomarker data
- Non-normality and skewness in CRP distributions
- Measurement limitations due to self-report bias
- Inference limitations due to the cross-sectional nature of NHANES

---

## 📏 PHQ-9 Depression Scoring

Depression symptoms were assessed using the **Patient Health Questionnaire-9 (PHQ-9)**:

- Each item (`DPQ010`–`DPQ090`) scored from 0 (Not at all) to 3 (Nearly every day)
- Responses of **7 (Refused)** or **9 (Don’t know)** were treated as missing
- **PHQ-9 total score** (range: 0–27) was calculated only for complete responses
- **Binary depression indicator**: PHQ-9 ≥ 10 represents moderate to severe depressive symptoms

Only participants **aged 18 and older** were included.

### References

- Kroenke, K., Spitzer, R. L., & Williams, J. B. (2001). *The PHQ-9: Validity of a brief depression severity measure.* Journal of General Internal Medicine, 16(9), 606–613.
- Kroenke, K., & Spitzer, R. L. (2002). *The PHQ-9: A new depression diagnostic and severity measure.* Psychiatric Annals, 32(9), 509–515.
- Spitzer, R. L., Kroenke, K., & Williams, J. B. (1999). *Validation and utility of a self-report version of PRIME-MD.* JAMA, 282(18), 1737–1744.

---

## 📎 Citation

Centers for Disease Control and Prevention (CDC)  
*National Health and Nutrition Examination Survey Data*  
Hyattsville, MD: U.S. Department of Health and Human Services  
[https://wwwn.cdc.gov/nchs/nhanes/](https://wwwn.cdc.gov/nchs/nhanes/)
