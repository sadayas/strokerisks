# Which health factors increase the risk for having a stroke?

## General:
### Communication Protocols:
Slack messenger was used to keep each other updated on parts of the project that have been completed and committed.
Zoom
Emails

## Presentation:
* Selected topic:
   * Which people are at risk for having a stroke?
* Reason why the topic was selected:
    * Strokes are one of the top leading causes of death in the world. Even if someone does not die from a stroke, it can leave the patient with long lasting effects that greatly impact the quality of their life. If there are simple lifestyle changes people can make to decrease their risk of having a stroke, it is worth the sacrifices to prevent this life altering ailment.  
* Description of data source:
    * The dataset is from kaggle, posted by user fedesoriano.
* Questions the dataset hopes to answer:
    * Which health factors increase the risk for having a stroke?
      * Hypertension? Age? BMI? 
    * Which demographic group is most at risk for a stroke?
    * With the dataset, the hope is to predict which individuals will be more at risk to have a stroke based on their age, gender, work type, marital status, residence type, average glucose levels, bmi, smoking status, and blood pressure. 
    * Being knowledgable about the at-risk populations can help implement tests and health coaching programs to focus on these groups. If enough research is done, it is the hope for health care practicioners to gain insight as to which tests should be given to prevent strokes. 

* Description of the data exploration phase of the project 
* Description of the analysis phase of the project

## Resources:
https://www.cdc.gov/stroke/facts.htm


Segment 2 Rubric:

Presentation:
* Description of the data exploration
phase of the project 

The dataset has 9 health or socioeconomic attributes that could possible lead to the target variable: having a stroke or not. 
These attributes include:
Gender: male, female, or other
Hypertension: Does the patient have high blood pressure? yes or no
Heart Disease: Does the patient have a heart disease? yes or no
Marital Status: Is the patient married? yes or no
Work: What does the patient do for work? Private, self-employed, government job, children, unemployed (note: the values "children" and "unemployed" were joined to make the value "not working")
Residence: What kind of community does the patient live in? Urban, suburban, or rural
Average glucose level: A glucose level of above ### indicates the patient may have diabetes. Does the patient have a healthy average glucose level? Integer answer
Body mass index: A BMI over ___ indicates the patient may be overweight; a BMI under ___ indicates the patient may be underweight. Integer answer
Smoking status: Does the patient smoke? Never smoked, formerly smoked, smokes, unknown
Stroke: Has the patient had a stroke? yes or no

For the data exploration, rows with null values were dropped to keep the amount of information for each patient consistent. 



* Description of the analysis phase of
the project

GitHub: 
README.md:
* Outline of the project (this may include
images, but should be easy to follow and
digest)
Note: The descriptions and explanations
required in all other project deliverables
should also be in your README.md as
part of your outline, unless otherwise
noted.

MLM:
* Description of preliminary data
preprocessing 
* Description of preliminary feature
engineering and preliminary feature
selection, including their decision-making
process 
* Description of how data was split into
training and testing sets 
The data 
* Explanation of model choice, including
limitations and benefits

A supervised, classification model was chosen because the dataset had clear labels. 
When new data is given, based on demographic factors and health factors, the model is able to predict whether or not the person has had a stroke or not.

Database Integration:
✓ Database stores static data for use during the project
✓ Database interfaces with the project in some format (e.g., scraping updates the database)
✓ Includes at least two tables (or collections, if using MongoDB)
	done
✓ Includes at least one join using the database language (not including any joins in Pandas)
	done, sql
✓ Includes at least one connection string (using SQLAlchemy or PyMongo)
	done, transfer code
If you use a SQL database, you must provide your ERD with relationships.
	done, query folder

Dashboard:
Storyboard on a Google Slide(s)
Description of the tool(s) that will be used to create the final dashboard
	tableau
Description of interactive element(s)
	be able to input your info and gain insight into your stroke risk level 