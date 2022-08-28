# Which health factors increase the risk for having a stroke?

## General:
### Communication Protocols:
Slack messenger, Discord, and Zoom were used to keep each other updated on parts of the project that have been completed and committed. 


## Outline:
* Selected topic:
    * Which health factors increase the risk for having a stroke?
* Reason why the topic was selected:
    * Strokes are one of the top leading causes of death in the world. Even if someone does not die from a stroke, it can leave the patient with long lasting effects that greatly impact the quality of their life. If there are simple lifestyle changes people can make to decrease their risk of having a stroke, it is worth the sacrifices to prevent this life altering ailment.  
* Description of data source:
    * The dataset is from kaggle, posted by user fedesoriano.
* Questions the dataset hopes to answer:
    * Which stress factors increase risk for having a stroke?
    * Which health factors increase the risk for having a stroke?
      * Hypertension? Age? BMI? 
    * Which demographic group is most at risk for a stroke?
    * With the dataset, the hope is to predict which individuals will be more at risk to have a stroke based on their age, gender, work type, marital status, residence type, average glucose levels, bmi, smoking status, and blood pressure. 
    * Being knowledgable about the at-risk populations can help implement tests and health coaching programs to focus on these groups. If enough research is done, it is the hope for health care practicioners to gain insight as to which tests should be given to prevent strokes. 




### Data Exploration

The dataset has 9 health or demographic attributes that could possible lead to the target variable: having a stroke or not. 
These attributes include:
* Gender: male, female, or other
* Marital Status: Is the patient married? yes or no
* Work: What does the patient do for work? Private, self-employed, government job, children, unemployed (note: the values "children" and "unemployed" were joined to make the   value "no_work")
* Smoking status: Does the patient smoke? Never smoked, formerly smoked, smokes, unknown
* Residence: What kind of community does the patient live in? Urban or rural
* Hypertension: Does the patient have high blood pressure? yes or no
* Heart Disease: Does the patient have a heart disease? yes or no
* Average glucose level: Integer answer 
    * A glucose level of above 126 mg/dL indicates the patient may have diabetes. Does the patient have a healthy average glucose level? 
    * Data was binned to reduce noise and visualize low glucose level: '<70', normal level: '70-100', pre-diabetic glucose level: '101-125', diabetic glucose level: '>126'.
* Body mass index: Integer answer
    * A BMI over 25 indicates the patient may be overweight; a BMI under 19 indicates the patient may be underweight. This value is dependent on their height and weight. 
* Stroke: Has the patient had a stroke? yes or no

For data exploration, rows with null values were dropped to keep the amount of information for each patient consistent. 


### Data Analysis


### Machine Learning Model:
* preliminary data preprocessing 
    * Any columns with null values were dropped to eliminate incorrect view of data. The 9 columns came with a mixture of values: binary, string and integer. For the model to be able to process the data easily, all columns with yes or no answers were changed to binary values. The columns that had more complex data were mapped with a dictionary of integers from 0-3 or 4.   
* preliminary feature engineering and preliminary feature selection, including their decision-making process 
    * 
* Training and testing
    * The data was split 80% in training and 20% in testing. In recent studies, it has been shown that this split avoids overfitting. Overfitting is an issue where the model will learn from the training data so well, it will not be able to work on data the model has not seen before.   
* Explanation of model choice
    * Benefits
        * Since predictions on health care data need to be precise and accurate, Random Forest was used as the machine learning model. The dataset has multiple features and a clear target variable. By using Random Forest instead of another model, we are preventing the risk of overfitting because there are multiple trees being used instead of one tree. Random Forest can handle up to 60 variables, so it was able to handle the 9 variables in this dataset with no issues. 
    * Limitations
        * Limitations of using the Random Forest model include difficult interpretation, speed issues on real-time data, and ineffective for linear data. 


Database Integration:
* ERD and Query folders
* Stroke_Data_transfer.ipynb

Dashboard:
* Storyboard on a Google Slide(s)
    * https://docs.google.com/presentation/d/1wtpTPGUZmihYq6xbEQ2ToIgmghP479mctH30H1Amqxs/edit?usp=sharing
* Description of the tool(s) that will be used to create the final dashboard
	* Tableau
* Description of interactive element(s)
	* Be able to input your info on a sliding scale and gain insight into your stroke risk level 

## Resources:
https://www.cdc.gov/stroke/facts.htm
