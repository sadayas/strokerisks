## Can we predict someone having a stroke based on health, stress, and demographic factors?
* Reason why the topic was selected:
    * Strokes are one of the top leading causes of death in the world. Even if someone does not die from a stroke, it can leave the patient with long lasting effects that greatly impact the quality of their life. If there are simple lifestyle changes people can make to decrease their risk of having a stroke, it is worth the sacrifices to prevent this life altering ailment.  
* Description of data source:
    * The dataset is from kaggle, posted by user Lirilkumar Amal.
* Questions
	* Can we predict someone having a stroke based on health, stress, and/or demographic factors?
	* With the dataset, the hope is to predict which individuals will be more at risk to have a stroke based on their age, gender, work type, marital status, residence type, average glucose levels, bmi, smoking status, and blood pressure. 
	* Being knowledgable about the at-risk populations can help implement tests and health coaching programs to focus on these groups. If enough research is done, it is the hope for health care practicioners to gain insight as to which tests should be given to prevent strokes. 

### Data Exploration
[Stroke_Data_Exploration.ipynb](https://github.com/sadayas/strokerisks/blob/main/Stroke_Data_Exploration.ipynb) </br>
The dataset has 10 health or demographic attributes that could possible lead to the target variable: having a stroke or not. 
These attributes include:
* Gender: male, female, or other
* Age: integer answer
* Marital Status: Has the patient ever been married? yes or no
* Work: What does the patient do for work? Private, self-employed, government job, children, unemployed (note: the values "children" and "unemployed" were joined to make the value "Never_worked")
* Smoking status: Does the patient smoke? Never smoked, formerly smoked, smokes, unknown
* Residence: What kind of community does the patient live in? Urban or rural
* Hypertension: Does the patient have high blood pressure? yes or no
* Heart Disease: Does the patient have a heart disease? yes or no
* Average glucose level: Integer answer 
    * A glucose level of above 126 mg/dL indicates the patient may have diabetes. Does the patient have a healthy average glucose level? 
    * Data was binned for visualization to reduce noise and visualize low glucose level: '<70', normal level: '70-100', pre-diabetic glucose level: '101-125', diabetic glucose level: '>126'.
* Body mass index: Integer answer
    * A BMI over 25 indicates the patient may be overweight; a BMI under 19 indicates the patient may be underweight. This value is dependent on their height and weight. 
* Stroke: Has the patient had a stroke? yes or no

During data preprocessing, the 'gender' column had a third variable of 'other'. Due to not knowing what the parameters were when the data was taken, and there were no patients that chose 'other' as their gender who also had a stroke, so that data was dropped. This seemed like an easy decision because there were only 11 values that were omitted. In a different analysis where we had more data for that category, we could explore other identities as part of the project.

The column 'bmi' had 192 null values. Of these 192, 140 of these patients had a stroke. Because of the high yield of strokes from this subset of data, we decided to fill the null values with an average of all the bmi's from the data.

The column 'smoking_status' had 145 null values for patients who had a stroke. Because only 783 people in the dataset had a stroke, we decided to keep the smoking status null values and replace them with a string value of 'unknown'. 

The columns that had yes/no (or 1/0) answers were left as is. Later in machine learning preprocessing, the categorical data will be encoded to binary values.

Data that had numerical values were normalized using the min-max feature scaling formula: (x - xmin) / (xmax - xmin). These columns included 'bmi', 'avg_glucose_level' and 'bmi'. The original data was kept in the .csv file and just added as new columns to prepare for OneHotEncoder. 


### Data Analysis
Of the 43,400 patients, 783 of them had a stroke. 
![work_type stroke](https://user-images.githubusercontent.com/98570777/187815599-bfbf94cb-b8a0-44b8-973c-475c75aa392d.jpg)
</br>
![smoke stroke](https://user-images.githubusercontent.com/98570777/188056311-60349959-7388-440d-9486-2aa0e4a59333.jpg)
</br>

### Machine Learning Model:
[Machine Learning Model](https://github.com/sadayas/strokerisks/blob/main/scaleandmachinelearn-CURRENT.ipynb)</br>
#### Data preprocessing, feature engineering, feature selection
* The 11 columns in the dataset came with a mixture of types of data: binary, categorical, and integer. The package OneHotEncoder reduces bias by assigning a binary value and adding a new categorical column. OneHotEncoder was used to encode the categorical data (work type, residence type, smoking status, gender and marriage status). Encoding data that did not have simple yes/no values was necessary to keep the integrity of the data while also having some algorithm (our case: Random Forest machine learning model) be able to process it. 
* Data that was continuous (average glucose level, age, and bmi), were normalized. The min-max feature scaling method was used to bring values between 0 and 1. Using a range of (0,1) makes it so the normalized value loses the least amount of precision while the model is being processed.  
* These features were added to the data as: average glucose level - normalized, age - normalized, and bmi - normalized. The scaled features were used in the model instead of the raw data.

##### Random Forest model:
* Benefits
	* Since predictions on health care data need to be precise and accurate, Random Forest was used as the machine learning model. The dataset has multiple 		features and a clear target variable. By using Random Forest instead of another model, we are preventing the risk of overfitting because there are 		multiple trees being used instead of one tree. Random Forest can handle up to 60 variables, so it was able to handle the 10 variables in this dataset with 		no issues. 
* Limitations
	* Limitations of using the Random Forest model include difficult to visualize, speed issues on real-time data, and ineffective for linear data. 
* Training and testing
    * The data was split 80% in training and 20% in testing. In recent studies, it has been shown that this split avoids overfitting. Overfitting is an issue where the model will learn from the training data so well, it will not be able to work on data the model has not seen before.   
     * The model has been trained by changing test size and random state. The initial worry was there were no stroke positive patient data going into the training portion, but with continued training, it seems that either the model is not a good fit for the data, or we need to use a dataset with more stroke positive patients in it.  
    * Continued training: removal of low importance features (i.e.: work type, marriage status, smoking status).

![cm_8292022jpg](https://user-images.githubusercontent.com/98570777/187367755-0bae716a-034a-4911-9ee9-cc66c3d641d8.jpg)
* Accuracy score
    * The current accuracy score for the Random Forest model is 98%. Despite the high accuracy score, the model is not condusive to predicting strokes. When predicting or testing health care data, it is important to have a high true positive number and low false negative number. In the confusion matrix shown above, we can see the false negative value (195) is much higher than the true positive number (1). This means 195 strokes happened, but were predicted to not happen. 
    * The sensitivity/recall percentage is 1%. This is the measure of how many people had a stroke and were correctly diagnosed. An effective model should have a very high sensitivity percentage. 
    * In an effective random forest model, we would want a high true positive and low false negative number. 

### Conclusion
We want the model to be able to tell us the people who will have a stroke.  This would require a high number of true positives. A low false negative is desirable because we want less people to have a stroke than were predicted to have one. In our case, we had the opposite. The model was not able to predict that patients will have a stroke. Class imbalance was an issue because only 1.8% of the data were patients who had a stroke. The model was so used to seeing the "no stroke" target, it started to default to that. 



</br>

### Database Integration:
* ERD and Query folders
* [SQL_train_stroke_data.ipynb](https://github.com/sadayas/strokerisks/blob/main/SQL_train_stroke_data.ipynb)

### Dashboard:
* Presentation: https://docs.google.com/presentation/d/1zE9s9woaUK8jBGWjZ1vNgK_S4C8AiLzq2Drq-wwpGeg/edit#slide=id.p
[![Stroke_Risk_Data_Dashboard](https://user-images.githubusercontent.com/98570777/187893540-858bb4bb-448f-4df4-b689-77cc60a250dd.png)](https://public.tableau.com/app/profile/vienna.rynerson/viz/StrokeRisk_16619322782310/StrokeRisk?publish=yes)


## Resources:
https://www.cdc.gov/stroke/facts.htm </br>
https://www.acls.net/stroke-information-and-resources </br>
