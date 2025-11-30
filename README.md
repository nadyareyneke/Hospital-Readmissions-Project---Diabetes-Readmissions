# Hospital-Readmissions-Project---Diabetes-Readmissions


                              1. Project Overview - Hospital Readmissions Analysis & Prediction (Diabetes Readmissions)
                        

This project is based on the UCI Diabetes 130-US Hospitals Readmission Dataset containing diabetes-specific statistics.

Hospital readmissions are a significant burden on healthcare systems, contributing to added clinical workload, higher costs, and poor patient outcomes.
This project aims to:
    (i) Identify key predictors of 30-day readmissions
    (ii) Build a predictive model to generate actionable insights
    
The final output will produce a decision-support framework for healthcare providers.



                                                                2. Dataset Overview
                                                                

This dataset provided valuable information regarding patient admissions including the following variables:
- Patient demographics (age)
- Details of hospital stay (length of stay, lab procedures, medications)
- Visit history (inpatient, outpatient, emergency)
- Medical specialty and test specifics (admitted ward, glucose and A1C tests)
- Outcome (if patient was readmitted or not readmiited)

A target variable (readmitted_bin) will be created where 0 = Not readmitted, 1 = Readmitted.


A dataset inspection will be completed to ensure the data set is clean and ready for analysis (as below):

KPI Overview:
Readmission Rate:  47.0 %
Average Length of Hospital Stay:  4.5 days
Average Number of Lab Procedures:  43.2
Average Number of Medications:  16.3
Number of Patients of Diabetes Medication:  19228



                                                            3. Data Cleaning
                                                            


The following were completed during the data cleaning process to ensure unbiased estimated and support accurate ML:
- Column names were verified and the first few rows were displayed.
- Duplicate data and irrelevant fields were removed.
- Standardised numeric values.
- Standardised string values.
- Converted target variable into a binary label. 
- Calculated mean values for missing data.
- Calculated KPIs.
- Removed potential data leaks.
- Missing lab tests were treated as 'not performed'.
- Missing categorical data was labelled 'Unknown'.



Findings from the data clean include:
- Readmission rates were high - at 47%
    Almost half of all patients return to hospital within 30 days - this may indicate that the patient cohort is very high-risk, there are issues within
    the hospital's discharge processes, or coding in the data set marks every return as visit as "readmitted" (Further investigation  will be 
    conducted below to correct this/ rule this out).

- Average length of inpatient hospital stays was 4.5 days
    This is expected/normal. No further investigation will be required for this project.

- An average of 43 lab procedures were performed on each patient during their stay
    This may include repeated lab monitoring, especially in cases of diabetic patients. This is consistent with inpatient disease management and does 
    not require further investigation in this project.
    
- Patients took an average of 16 medications
    May reflect multiple comorbidities per single patient. No further investigation is significant for this project.

- 19, 228 patients were taking diabetic medication
    Indicates that most patients in this dataset take diabetic medication - this is expected within a diabetes readmission dataset.
    

These initial findings indicate the following key areas that require further investigation in the Exploratory Data Analysis:
(1) High readmission rate (47%) - Analysis required to determine whether due to data errors, clinical procedure, or if as expected 
(2) Which wards drive the highest rates of readmission?
(3) What are the top risk factors driving readmission?

                                      4. Exploratory Data Analysis (High Readmission Rate)
                        (1) High readmission rate (47 %) - Is this due to data errors, clinical procedure, or is expected?

Figure 1.
![Figure 1](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%201%20_%20Proportion%20of%20Readmitted%20vs%20Non-Readmitted%20Patients.png)

Figure 2.
![Figure 2](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%202%20_%20Readmissions%20by%20Number%20of%20Medications.png)

The analysis assessed the data for a potential leakage to ensure that the readmission rate is accurate and that predictive modeling is based only
on data at the time of discharge.

The analysis confirmed that numeric variables showed reasonable correlations and no obvious data entry issues were detected, therefore a readmission  
rate of 47% is accurate. Visual and statistical checks support that this dataset is consistent and as expected.

However, a risk of data leakage was observed in categorical data columns 'change' and 'diabetes_med' as the variables may inflate prediction in a 
predictive model. These variables will be excluded from ML.

Figure 2 shows that the median number of medications is similar between both readmitted and not-readmitted cohorts, suggesting that medication counts 
are consistent and reliable, and that no further analysis as a contributing factor is required.


                                           4. Exploratory Data Analysis (Wards Driving Readmissions)
                                            (2) Which wards drive the highest rates of readmission?

Figure 3.                                            
![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%203%20_%20Readmissions%20Rate%20by%20Ward.png)

Figure 3 displays substantial variation in readmission rates depending on the ward:
  - Family and General Practice displayed the highest readmission rate (49.5%) - suggests that patients admitted to this ward require more complex
      follow-up care plans or have poorly managed chronic conditions.

  - Emergency and Trauma displayed a similarly high readmission rate (49.4%).

  - Missing ward data indicates a large portion of patient readmissions (48.9%) in which were not assigned to a specific ward. This highlights a 
      potential data quality issue.

Ward-level variation suggests that readmission risk is not uniform. This analysis directly informs operational decisions (e.g. where to target 
interventions in discharge planning, patient education, or follow-up procedures).


                                              4. Exploratory Data Analysis (Top Risk Factors)
                                          (3) What are the top risk factors driving readmission?

Figure 4.
![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%204%20_%20Top%205%20Risk%20Factors%20Driving%20Readmissions.png)

The correlation analysis revealed that previous inpatient stays are the strongest predictor of hospital readmission (r = 0.21). These patients often
have unstable chronic conditions, insufficient discharge planning, or inadequate follow-up care. Actionable strategies to prevent this demographic's 
readmission would include (i) Enhanced discharge planning, (ii) GP follow-up within 7 days of discharge,  (iii) Case management/ long-term care 
coordination.


Patients who were repeat outpatients or visited the emergency department also demonstrated higher readmission probabilities (0.095 and 0.094
respectively). These patterns suggest increased utilisation of healthcare services is an early indicator of worsening health conditions and a need for 
ongoing management of a complex chronic condition. Suggested actionable strategies may include (i) Development of community nursing/ chronic disease 
programs, (ii) Establish an "ED frequent visitor" flag within patient databases.


This analysis that high healthcare utilisation patterns are the strongest drivers of readmission - not treatment actions or patient demographics. 
The key predictors: frequent prior admissisons, multiple outpatient/ED visits, longer stays, intensive clinical monitoring may be beneficial in 
developing an early-warning system.


   
                                                          5. Data Visualisation

 Figure 5.                                                         
![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%205%20_%20Average%20Length%20of%20Hospital%20Stay%20by%20Medical%20Ward.png)




Figure 6.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%206%20_%20Number%20of%20Lab%20Procedures.png)




Figure 8. 

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%208%20_Lab%20Procedures%20vs%20Length%20of%20Stay.png)




Figure 9.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%209%20_%20Patient%20Count%20by%20Medical%20Ward.png)




Figure 10.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%2010_Age%20Distribution%20of%20Patients.png)




Figure 11.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%2011%20_%20Readmission%20Rate%20by%20Ward%20and%20Prior%20Inpatient%20Visits.png)


The average hospital stay duration was compared accross different wards (Figure 5). While most wards display similar stay lengths (4-5 days), 
Emergency/Trauma and Internal Medicine reflect higher averages - this may be reflective of varying case complexity.

Figure 6 displays a smooth, bell-shaped distribution with no extreme outliers of lab procedures per patient indicating diagnostic intensity is 
relatively consistent across all cohorts (thereby, further analysis is insignificant in this project). In Figure 8, a positive trend between
the number of lab procedures and length of stay by ward is evident (patients who have longer stays generally undergo more lab procedures).
This would align with clinical expectations.

A notable portion of patient records fall under 'Missing' ward, indicating poor documentation (Figure 9), this impacts distribution and is thereby
a significant limitation in contextualisisng readmission patterns.

The largest demographic of patients are aged between 70-80 (Figure 10 and 11). This is essential in understanding the age profile 
of at-risk cohorts, indicating older age groups typically experience higher readmission rates.


                                                     6. Machine Learning Model



Figure 12.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%2012%20_%20Top%2010%20Risk%20Factors%20Driving%20Readmissions.png)




Figure 13.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%2013%20_%20Predicted%20Readmission%20Probability%20After%20A%205%20Improvement.png)




Figure 14. 

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%2014%20_Top%203%20Predictors%20Driving%20Readmissions.png)




Figure 15.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%2015%20_%20Drivng%20or%20Protective%20Effect%20on%20Readmission%20Risk.png)




Figure 16.

![](https://github.com/nadyareyneke/Hospital-Readmissions-Project---Diabetes-Readmissions/blob/main/Figure%2016%20_%20Readmission%20Rate%20by%20Age%20Group.png)




Machine Learning Model - Predicting 30-Day Hospital Readmissions
    A Machine Learning Model was developed to predict the likelihood of patient readmission within 30 days. Logistic Regression was selected due to its
    interpretability and suitability for generating actionable insights.



Feature Selection:
    Categorical variables were One-Hot Encoded and numerical values were passed through (unchanged). Preprocessing was bundled within the model to 
    prevent data leakage and maintain consistent handling of the training and test data.
    The features 'readmitted', 'change', and 'diabetes_med' were excluded to prevent data leakage.
    The target variable was the binary readmitted flag (where 0 = not readmitted, 1 = readmitted).



Data Preprocessing & Pipeline Contruction:
    Pre-processing was from only the training set, ensuring that performance metrics (ROC and AUC, and accuracy) were not inflated.
    Numeric values were passed through unchanged, while Categorical values were One-Hot Encoded.



Model Training & Evaluation:
    An 80/20 train-test split evaluated out-of-sample performance. 
    The model achieved:
    ROC AUC: 0.641
    Accuracy: 0.608
    Recall of Class 0 (not readmitted): 0.79
    Recall of Class 1 (readmitted): 0.40

  This reveals the model is accurate in identifying patients who are not at risk of being readmitted but it is less sensitive to patients who are,
  highlighting that improved recall for Class 1 is required.

    
Key Risk Identification:
    Logistic regression coefficients were ranked in order of highest readmission risk. The top 3 most significant predictors were: 
    1. n_inpatient (coef = +0.386)
        Patients with higher prior inpatient visits are significantly more likely to be readmitted.
    2. A1Ctest_normal (coef = -0.255)
        Normal A1C results are a protective factor in reducing readmission risk.
    3. age_[90-100) (coef = -0.245)
        There is a lower risk of readmission within this age cohort, likely due to specialised monitoring or low intensity treatment approaches.

   These insights highlight where clinical interventions may be targeted.



ML simulated 5% Improvement:
    A simulation was performed where a hypothetical 5% improvement was applied to the top 3 predictors (n_inpatient, A1Ctest_normal, and age_[90-100]). 

  The model estimated a 4.73% reduction in readmission probability (from 0.471 to 0.427).

  There was an overall accuracy of 0.608 and ROC AUC of 0.641.
  The model can identify non-readmissions with a recall of 0.79 however, it was less sensitive in detecting readmissions with a recall of 0.40. This
  suggests that while the model is reliable, improvement in capturing high-risk patients is required.

  The key predictors of readmission  included:
   1. n_inpatient: coef = 0.386 (very strong predictor) 
        Patients with a higher number of inpatient visits are significantly more likely to be readmitted.
        
   2. A1Ctest_normal: coef = -0.255 (strong negative factor) 
        Patients with normal A1C test results have a reduced readmission risk.
        
   3. age_[90-100): coef = -0.245 (negative factor) 
        Patients aged between 90-100 are less likely to be readmitted, likely due to more established monitoring or lower intensity interventions

  This establishes that even modest improvements may produce meaningful reductions.

                                                        7. Limitations and Next Steps

Interpretation of Findings:
    This analysis highlightse several clinical and operational patterns associated with hospital readmissions (for diabetic patients). Readmission rates 
    vary accross wards - where Emergency/Trauma and General Practice show the highest occurrences. This is likely reflective of a difference in case
    complexity, patient comorbidity files, and continuity of care. The exploratory findings further indicate previous inpatient visits and healthcare
    utilisation are stronger drivers of readmission than treatment intensity.

Limitations:
   Despite producing clinically useful findings, this analysis has several limitations:
  1. Limited predictivity
       The model's recall for readmitted patients is low therefore, many readmissions are not counted. Variables such as length of stay and number of 
       inpatient stays are useful in predicting risk but not sufficient for a thorough model.
      
  2. Missing/ Incomplete Data
        A large portion of patient ward records fall under "Missing", reducing the model's ability to learn patterns from clinical data.

  3. Model Choice
        A simple baseline classifier was used due to its interpretability. However, these types of models are not as accurate when dealing with
        non-linear data relationships.

Next Steps:
    The following recommended steps would improve accuracy and generate more significant insights:
  1. Feature Engineering
        Creation of flags for high-risk medication groups that may influence readmissions (e.g. anticoagulants, insulin). Incorporate additional
        important variables such as time since last admission, lab testing trends, procedures per day, medication dosages/intensity.

  2. Improve Model
        Apply class imbalance strategies.
        Utilise more advanced Machine-Learning Models (e.g. Random Forest).

  3. Patient Subgroup Validation
        Clinical patterns may vary significantly throughout wards - perform ward-specific models to evaluate fairness across age and ward cohorts.

Key Stakeholder Takeaways:

Hospital Administrators
   - Readmission risk is concentrated in a few high-volume wards (Emergency/Trauma and Internal Medicine) thereby, targeted interventions could yield
     significantly reduced outcomes.
          
   - Prior inpatient visits are the strongest risk predictor - these patients should be prioritised for ongoing/ transitional care programs.

   - Length of stay is not a significant risk factor - efforts should focus on maintaining patient stability rather than shortening duration of stay.

Clinical Teams
   - Existing dataset variables fail to predict many readmissions, there is a requirement for deeper clinical detail and consistency in 
          documentation (specifically in listing wards).

Data & Analytics Teams
   - Opportunity for predictive improvement through feature engineering and modern ML approaches.
   - Address missing ward data and enhancement on clinical detail.

