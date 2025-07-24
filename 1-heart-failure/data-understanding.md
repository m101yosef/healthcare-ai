# Data Understanding

This report presents an exploratory analysis of heart disease dataset comprising 918 patient records with 12 features. The target variable, `HeartDisease`, indicates the presence (1) or absence (0) of heart disease. I began the analysis with the dataset's size, structure, and key attributes, then looked at whether 'HeartDisease' cases are balanced or not. After that, I explored how features related to 'HeartDisease' and&mdash;how they correlated with each other.


## Data Overview
The dataset is nearly balanced, with 44.7% of patients not having heart disease and 55.3% having heart disease. There are no missing values, which simplifies the data preparation process. 

<div style="padding-left: 24px">
<img alt="class balance" src="../image/target-balance.png" height="280">
</div>

## Features Relationships

### Categorical features vs Target
Based on our dataset, you have a high chance of having a heart disease if: 
- you are a male, sad short story :), 
- your fasting blood sugar levels above 120mg/dl, 
- you experience a chest pain during physical activity (especially Asymptomatic (ASY) and typical angina (TA) chest pain types)
- the ECG reading is LVH (left ventricular hypertrophy), and 
- your ST slope is going down or flat....... 

<div style="padding-left: 24px">
<img alt="Categorical features relationships with target" src="../image/cat-vs-target.png">
</div>



### Numerical features distribution 
For Cholesterol and Oldpeak, there is a different distribution of values, indicating potential differences in heart stress responses and maybe I need to split these two features into more than one group of values (I will test this assumption later)


<div style="padding-left: 24px">
<img alt="Numerical features distribution" src="../image/num-kde.png">
</div>


### Numerical features vs Target
The heart disease group (almost) has:
- older ages, 
- high blood pressure,  
- lower maximum heart rate, and
- higher old peak values.

<div style="padding-left: 24px">
<img alt="Numerical features relationships with target" src="../image/num-vs-target.png">
</div>


### Features Correlation
MaxHR and Oldpeak show moderate negative and positive correlations with heart disease, respectively, suggesting these features are important predictors. However, the wide spread in cholesterol levels and the slight increase in resting blood pressure in the disease group indicate that these features may have a less direct impact on heart disease risk.

<div style="padding-left: 24px">
<img alt="Numerical features relationships with target" src="../image/features-corr.png">
</div>

<br>

## Key Takeaways


<div style="margin-top: 1em; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 12px rgba(0,0,0,0.08);">
<table style="border-collapse: collapse; width: 100%; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; font-size: 15px; background: white;">
    <thead>
    <tr style="background: linear-gradient(135deg, crimson, #2c3e50); color: white;">
        <th style="padding: 14px 16px; text-align: left; font-weight: 600;">Feature</th>
        <th style="padding: 14px 16px; text-align: left; font-weight: 600;">Risk Indicator</th>
        <th style="padding: 14px 16px; text-align: left; font-weight: 600;">Notes</th>
    </tr>
    </thead>
    <tbody>
    <tr><th>Categorical Features</th></tr>
    <tr style="transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">Sex = M</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; color: #e74c3c; font-weight: 500;">Higher risk</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Males are more prone to heart issues, especially at younger ages</td>
    </tr>
    <tr style="background-color: #f8f9fa; transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">FastingBS = 1</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; color: #e74c3c; font-weight: 500;">Higher risk</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">High fasting blood sugar (likely diabetic) increases heart risk</td>
    </tr>
    <tr style="transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">ExerciseAngina = Y</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; color: #e74c3c; font-weight: 500;">Higher risk</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Indicates chest pain during exertion — often a sign of blocked arteries</td>
    </tr>
    <tr style="background-color: #f8f9fa; transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">ChestPainType = ASY</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; color: #e74c3c; font-weight: 500;">Higher risk</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Asymptomatic patients can still have serious heart conditions</td>
    </tr>
    <tr style="transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">ST_Slope = Flat</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; color: #e74c3c; font-weight: 500;">Higher risk</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Associated with ST depression and reduced blood flow during exercise</td>
    </tr>
    <tr style="background-color: #f8f9fa; transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">RestingECG = LVH</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; color: #f39c12; font-weight: 500;">Moderate risk</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Suggests left ventricular hypertrophy — a possible indicator of strain</td>
    </tr>
    <tr><th>Numerical Features</th></tr>
    <tr style="transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">Age</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 500; color: #e74c3c;">↑ Higher age → ↑ risk</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Cardiovascular vulnerability increases with age</td>
    </tr>
    <tr style="background-color: #f8f9fa; transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">RestingBP</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 500;">Slightly elevated in heart disease</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Limited standalone predictive value due to significant group overlap</td>
    </tr>
    <tr style="transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">Cholesterol</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 500; color: #7f8c8d;">No clear pattern (inconclusive)</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Impact may be better assessed through feature combinations</td>
    </tr>
    <tr style="background-color: #f8f9fa; transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">MaxHR</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 500; color: #e74c3c;">↓ Lower in heart disease</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Reduced peak heart rate indicates impaired cardiac response to stress</td>
    </tr>
    <tr style="transition: background-color 0.2s;">
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 600;">Oldpeak</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1; font-weight: 500; color: #e74c3c;">↑ Higher in heart disease</td>
        <td style="padding: 12px 16px; border-bottom: 1px solid #ecf0f1;">Indicates ST depression, suggesting myocardial ischemia during exercise</td>
    </tr>
    </tbody>
</table>
</div>


