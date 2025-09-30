# Sleep Disorder Prediction 😴

## Overview

The primary aim of this project is to analyze a person's *lifestyle and medical variables* (such as age, BMI, physical activity, sleep duration, and blood pressure) to accurately *predict the presence and type of sleep disorder*. This is a multi-class classification problem.

---

## Dataset Context

The *Sleep Health and Lifestyle Dataset* contains *400 rows* and *13 columns*, covering comprehensive metrics related to sleep and daily habits.

The target variable is **Sleep_disorder**, which has three classes:
1.  *None*: The individual does not exhibit any specific sleep disorder.
2.  *Insomnia*: The individual experiences difficulty falling asleep or staying asleep.
3.  *Sleep Apnea*: The individual suffers from pauses in breathing during sleep.

---

## Data Dictionary

| Column Name | Description |
| :--- | :--- |
| *Person\_ID* | Unique ID assigned to each person |
| *Gender* | The gender of the person (Male/Female) |
| *Age* | Age of the person in years |
| *Occupation* | The occupation of the person |
| *Sleep\_duration* | The duration of sleep in hours |
| *Quality\_of\_sleep* | Subjective rating of sleep quality (1 to 10) |
| *Physical\_activity* | The level of physical activity (Low/Medium/High) |
| *Stress Level* | Subjective rating of stress level (1 to 10) |
| *BMI\_category* | The BMI category (Underweight/Normal/Overweight/Obese) |
| *Blood\_pressure* | The blood pressure in mmHg (e.g., '125/80') |
| *Heart\_rate* | The heart rate in beats per minute |
| *Daily Steps* | The number of steps taken by the person per day |
| *Sleep\_disorder* | The presence or absence of a sleep disorder |

---

## Data Preprocessing Steps

1.  *Handling Missing Values*: The Sleep Disorder column initially contained null/NaN values which were determined to represent *no sleep disorder*. These were filled with the category **'None'**.
2.  *Column Dropping*: The unique identifier column, **Person ID**, was dropped as it's unnecessary for modeling.
3.  *Feature Engineering*: The composite **Blood Pressure** column (e.g., "125/80") was split into two separate numerical columns: **systolic_bp** and **diastolic_bp**. The original Blood Pressure column was then dropped.
4.  *Data Cleaning*: The 'Normal Weight' category in the BMI Category column was standardized to *'Normal'*.
5.  *Label Encoding*: All remaining categorical columns (**Gender**, **Occupation**, **BMI Category**, and the target variable **Sleep Disorder**) were converted to numerical values using **Label Encoding**.

---

## Exploratory Data Analysis (EDA) Highlights

The EDA revealed significant relationships between demographic/lifestyle factors and sleep disorders:

* *Gender and Disorder Type*: **Males** showed more instances of *Insomnia*, while **Females** showed more instances of *Sleep Apnea*.
* *Occupation Impact*: **Occupation** has a huge impact on sleep disorders.
    * *Nurses* are most subjected to *Sleep Apnea*, with very few having no sleep disorder.
    * *Salespersons* are the most affected by *Insomnia*, followed by teachers.
    * Occupations like Engineers, Doctors, Accountants, and Lawyers showed very few instances of sleep disorders.
* *BMI Category*: **BMI** plays a vital role in prediction.
    * People with *Normal BMI* are the *least likely* to suffer from any sleep disorder.
    * People who are *Overweight* are more likely to suffer from sleep disorders than Obese people. *Obese or Overweight* patients are generally more prone to sleep disorders.
* *General Distribution*:
    * The number of males and females is almost equal.
    * The majority of people have an age between 30 and 45 years.
    * Most people have a sleep quality rating greater than 5.

---

## Modeling and Evaluation

Two powerful non-linear classification models were used for prediction:

1.  *Decision Tree Classifier*
2.  *Random Forest Classifier*

The data was split into training and testing sets, and the models were trained to predict the multi-class target variable (Sleep Disorder).

| Model | Training Accuracy | Test Accuracy | Average F1-Score |
| :--- | :--- | :--- | :--- |
| *Random Forest Classifier* | ≈ 93.49% | **89%** | 0.86 |
| *Decision Tree Classifier* | ≈ 93.49% | **87%** | 0.84 |

### Key Metrics from Random Forest Classifier

The *Random Forest Classifier* showed the highest accuracy and the strongest overall performance. The confusion matrix indicated a low number of false positive results, confirming the model's effectiveness at predicting correct results.

| Class (Sleep Disorder) | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| *0 (Insomnia)* | 0.77 | 0.83 | 0.80 |
| *1 (None)* | 0.94 | 0.98 | 0.96 |
| *2 (Sleep Apnea)* | 0.91 | 0.74 | 0.82 |

---

## Conclusion

The project successfully identified key factors influencing sleep disorders and built a highly accurate predictive model:

* *Dominant Predictors*: The presence and type of sleep disorder largely depend on **Gender, Occupation, and BMI**.
* *Best Model*: The **Random Forest Classifier** provided excellent results, achieving a test accuracy of *89%*.
* *Actionable Insight*: Targeted lifestyle and health interventions should be considered for individuals based on the risk factors identified (e.g., gender-specific disorder types, high-risk occupations like nursing, and BMI categories like Overweight/Obese).
