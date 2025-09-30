# Sleep Disorder Prediction 😴

## Overview

[cite_start]The primary aim of this project is to analyze a person's *lifestyle and medical variables* (such as age, BMI, physical activity, sleep duration, and blood pressure) to accurately *predict the presence and type of sleep disorder*[cite: 791]. This is a multi-class classification problem.

---

## Dataset Context

[cite_start]The *Sleep Health and Lifestyle Dataset* contains *400 rows* and *13 columns*, covering comprehensive metrics related to sleep and daily habits[cite: 793].

The target variable is **Sleep_disorder**, which has three classes:
1.  [cite_start]*None*: The individual does not exhibit any specific sleep disorder[cite: 811].
2.  [cite_start]*Insomnia*: The individual experiences difficulty falling asleep or staying asleep[cite: 812].
3.  [cite_start]*Sleep Apnea*: The individual suffers from pauses in breathing during sleep[cite: 813].

---

## Data Dictionary

| Column Name | Description |
| :--- | :--- |
| *Person\_ID* | [cite_start]Unique ID assigned to each person [cite: 801] |
| *Gender* | [cite_start]The gender of the person (Male/Female) [cite: 801] |
| *Age* | [cite_start]Age of the person in years [cite: 801] |
| *Occupation* | [cite_start]The occupation of the person [cite: 801] |
| *Sleep\_duration* | [cite_start]The duration of sleep in hours [cite: 801] |
| *Quality\_of\_sleep* | [cite_start]Subjective rating of sleep quality (1 to 10) [cite: 801] |
| *Physical\_activity* | [cite_start]The level of physical activity (Low/Medium/High) [cite: 801] |
| *Stress Level* | [cite_start]Subjective rating of stress level (1 to 10) [cite: 801] |
| *BMI\_category* | [cite_start]The BMI category (Underweight/Normal/Overweight/Obese) [cite: 801, 859] |
| *Blood\_pressure* | [cite_start]The blood pressure in mmHg (e.g., '125/80') [cite: 801] |
| *Heart\_rate* | [cite_start]The heart rate in beats per minute [cite: 801] |
| *Daily Steps* | [cite_start]The number of steps taken by the person per day [cite: 801] |
| *Sleep\_disorder* | [cite_start]The presence or absence of a sleep disorder [cite: 809] |

---

## Data Preprocessing Steps

1.  *Handling Missing Values*: The Sleep Disorder column initially contained null/NaN values which were determined to represent *no sleep disorder. [cite_start]These were filled with the category **'None'*[cite: 831, 832].
2.  [cite_start]*Column Dropping*: The unique identifier column, **Person ID**, was dropped as it's unnecessary for modeling[cite: 835].
3.  [cite_start]*Feature Engineering*: The composite **Blood Pressure** column (e.g., "125/80") was split into two separate numerical columns: **systolic_bp** and **diastolic_bp**[cite: 855, 856]. [cite_start]The original Blood Pressure column was then dropped[cite: 857].
4.  [cite_start]*Data Cleaning*: The 'Normal Weight' category in the BMI Category column was standardized to *'Normal'*[cite: 859].
5.  [cite_start]*Label Encoding: All remaining categorical columns (*Gender**, **Occupation**, **BMI Category**, and the target variable **Sleep Disorder*) were converted to numerical values using **Label Encoding*[cite: 1054, 1055, 1057].

---

## Exploratory Data Analysis (EDA) Highlights

The EDA revealed significant relationships between demographic/lifestyle factors and sleep disorders:

* [cite_start]*Gender and Disorder Type: **Males* showed more instances of *Insomnia, while **Females* showed more instances of *Sleep Apnea*[cite: 1674].
* [cite_start]*Occupation Impact: **Occupation* has a huge impact on sleep disorders[cite: 1018].
    * [cite_start]*Nurses* are most subjected to *Sleep Apnea*, with very few having no sleep disorder[cite: 1019].
    * [cite_start]*Salespersons* are the most affected by *Insomnia*, followed by teachers[cite: 1020].
    * [cite_start]Occupations like Engineers, Doctors, Accountants, and Lawyers showed very few instances of sleep disorders[cite: 1021].
* [cite_start]*BMI Category: **BMI* plays a vital role in prediction[cite: 1680].
    * [cite_start]People with *Normal BMI* are the *least likely* to suffer from any sleep disorder[cite: 1047].
    * [cite_start]People who are *Overweight* are more likely to suffer from sleep disorders than Obese people[cite: 1049]. [cite_start]*Obese or Overweight* patients are generally more prone to sleep disorders[cite: 1681].
* *General Distribution*:
    * [cite_start]The number of males and females is almost equal[cite: 939].
    * [cite_start]The majority of people have an age between 30 and 45 years[cite: 939].
    * [cite_start]Most people have a sleep quality rating greater than 5[cite: 940].

---

## Modeling and Evaluation

Two powerful non-linear classification models were used for prediction:

1.  *Decision Tree Classifier*
2.  *Random Forest Classifier*

The data was split into training and testing sets, and the models were trained to predict the multi-class target variable (Sleep Disorder).

| Model | Training Accuracy | Test Accuracy | Average F1-Score |
| :--- | :--- | :--- | :--- |
| *Random Forest Classifier* | [cite_start]$\approx 93.49\%$ [cite: 1475] | [cite_start]$89\%$** [cite: 1670] | [cite_start]$0.86$ [cite: 1670] |
| *Decision Tree Classifier* | [cite_start]$\approx 93.49\%$ [cite: 1248] | [cite_start]$87\%$** [cite: 1446] | [cite_start]$0.84$ [cite: 1451] |

### Key Metrics from Random Forest Classifier

[cite_start]The *Random Forest Classifier* showed the highest accuracy and the strongest overall performance[cite: 1641, 1671]. [cite_start]The confusion matrix indicated a low number of false positive results, confirming the model's effectiveness at predicting correct results[cite: 1643].

| Class (Sleep Disorder) | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| *0 (Insomnia)* | [cite_start]$0.77$ [cite: 1669] | [cite_start]$0.83$ [cite: 1669] | [cite_start]$0.80$ [cite: 1669] |
| *1 (None)* | [cite_start]$0.94$ [cite: 1669] | [cite_start]$0.98$ [cite: 1669] | [cite_start]$0.96$ [cite: 1669] |
| *2 (Sleep Apnea)* | [cite_start]$0.91$ [cite: 1669] | [cite_start]$0.74$ [cite: 1669] | [cite_start]$0.82$ [cite: 1669] |

---

## Conclusion

The project successfully identified key factors influencing sleep disorders and built a highly accurate predictive model:

* [cite_start]*Dominant Predictors: The presence and type of sleep disorder largely depend on **Gender, **Occupation, and **BMI*[cite: 1673].
* [cite_start]*Best Model: The **Random Forest Classifier* provided excellent results, achieving a test accuracy of *$89\%$*[cite: 1682, 1670].
* [cite_start]*Actionable Insight*: Targeted lifestyle and health interventions should be considered for individuals based on the risk factors identified (e.g., gender-specific disorder types, high-risk occupations like nursing, and BMI categories like Overweight/Obese)[cite: 1674, 1679, 1681].
