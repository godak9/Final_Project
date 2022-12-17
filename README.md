# Final Project: Predicting Fatal Shark Bites
Team Member Names:
- Gaby Odak
- Eric Bartlow
- Florian Boyaka

## Selected Topic
Experiencing a shark bite is considered a random occurrence [and, unfortunately, not often explainable](https://stories.uq.edu.au/contact-magazine/2019/fear-versus-reality/index.html). We want to dive deeper into the randomness of shark bites and explore the possibility of predicting shark bite fatalities by using extracted global shark bite data and creating classifier machine learning models. Are certain features invovlved in a shark bite situation associated with more fatality? 

Using Python's Scikit-learn library we created various machine learning models to explore predicting scenarios where a shark bite is fatal. We extracted data for the machine learning models from the Shark Research Institute's website and put it through extensive preprocessing and cleaning by way of curated categorization. The transformed data was hosted as a database and accessed using SQL Alchemy. 
 
Finally, we used Tableau to create data visualizations and a dashboard to explore the data trends in connection to feature importances of the machine learning model.

### Highlight of Technologies Used
- Python 3.7, Jupyter Notebook 1.0
  - pandas 1.4.2
  - scikit-learn 1.0
- SQL, pgAdmin 4
  - psycopg2 2.9.5
  - sqlalchemy 1.4
  - 
### Reasons for Selecting Topic
We found an interesting dataset on shark bite instances that is described further in the _Description of Data_ section below. Getting bit by a shark is a completely based fear becasue of its unpredictability and its potential lethality. Anyone would feel a sense of unease if they encountered a shark. Can we narrow down features frequently involved in fatal shark bites and predict what situations are more deadly with these creatures using machine learning?
### Questions to Answer
#### Main Questions
- Can we use machine learning models to predict fatal shark bites based on the where, when, how, and who features of the shark bite occurance?
- Do certain features have a greater impact when it comes to predicting a fatal shark bite?
#### Supporting Questions
- Is one species of shark more deadly than the others?
- Do certain ocean activities lead to more fatal shark bites?
- Does the time of year contribute to more fatal shark bites?
- Are men or women more susceptible to a fatal injury?
- Are individuals or groups more susceptible to a fatal injury?
- Does the type of bite(i.e., provoked, unprovoked) play a role in fatality?
- Is there a geographic association with fatal shark bites? 

## Accessing Associated Project Presentations 
- [Slideshow presentation](https://docs.google.com/presentation/d/1D5jMEY6qLNIQtL0yeWbthlBPU3TV16M7XuY5U8JGtFo/edit#slide=id.p) containing a description of the project process and in depth project insights. 
- [Tableau story of exploratory analysis](https://public.tableau.com/app/profile/gabrijela.odak/viz/SharkBiteExploratoryAnalysis/ExploratoryAnalysis).
- [Tableau story of machine learning analysis](https://public.tableau.com/app/profile/gabrijela.odak/viz/SharkBiteMachineLearningAnalysis/MachineLearningStory)

## Running Project Code
The requirements for the environment in which the project code was ran can be found in the [requirements.txt file](requirements.txt).

## Analysis Roadmap
This project was broken down into three main parts:
1. Data Cleaning
   - Data ETL
     - Technology/Language used: Python (mainly Pandas) in Jupyter Notebook
     - [Raw data files](Data_Cleaning/Raw_Data_Files) can be found in the  Data_Cleaning/Raw_Data_Files/ folder.
     - [Code for cleaning the dataset](Data_Cleaning/Data_Cleaning_Code) can be found in the Data_Cleaning/Data_Cleaning_Code/ folder.
     - [Cleaned data files](Data_Cleaning/Clean_Data_Files) can be found in the Data_Cleaning/Clean_Data_Files/ folder.
   - Database creation
     - Technology/Language used: PostgreSQL in pgAdmin
     - [Code for database creation](Database_Creation/SQL_Code/SQL_Commands_For_completedata.txt) can be found in the Database_Creation/SQL_Code/ folder.
     - [Notes on database creation and importing/exporting files](Database_Creation/SQL_Code/Data_Notes.txt) can be found in the Database_Creation/SQL_Code/ folder.
     - [Imported files](Database_Creation/Imported_Files) and [exported files](Database_Creation/Exported_Files) can be found in the Database_Creation/Imported_Files/ and Database_Creation/Exported_Files/ folders, relatively.
2. Machine Learning
   - Exploratory analysis
     - Technology/Language used: Tableau Public
     - A [Shark Bite Exploratory Analysis story](https://public.tableau.com/app/profile/gabrijela.odak/viz/SharkBiteExploratoryAnalysis/ExploratoryAnalysis) can be found on Tableau Pubic.
   - Data encoding
     - [Code for encoding data for machine learning](Machine_Learning/Machine_Learning_Data_Encoding.ipynb) can be found in the Machine_Learning folder and at the top of files where mahcine learning models were ran.
   - Comparing validation of machine learning models
     - Technology/Language used: Python (Scikit-learn) in Jupyter Notebook
     - [Code for comparing machine learning models](Machine_Learning/Comparing_ML_Models.ipynb) can be found in the Machine_Learning folder.
   - Choosing a machine learning model
     - [Code for the selected machine learning model](Machine_Learning/Chosen_Model.ipynb) can be found in the Machine_Learning folder.
3. Presentation
   - Technology used: Google Slides and Tableau Public
   - [Slideshow presentation](https://docs.google.com/presentation/d/1D5jMEY6qLNIQtL0yeWbthlBPU3TV16M7XuY5U8JGtFo/edit?usp=sharing)
   - A [Fatal Shark Bites story](https://public.tableau.com/app/profile/gabrijela.odak/viz/SharkBiteMachineLearningAnalysis/MachineLearningStory) exploring the machine learning model features can be found on Tableau Public.

## Description of Data
The [dataset was originally sourced](https://www.sharkattackfile.net/incidentlog.htm) from the Shark Research Institute's website. We came across the [dataset on Kaggle](https://www.kaggle.com/datasets/thedevastator/shark-attacks-the-risks-of-coastal-water-activit) where someone had already extracted the dataset and created a new file from it. However, even the extracted dataset still required a lot of cleaning before we could fit the data to any machine learning models.

The [Kaggle data](Data_Cleaning/Raw_Data_Files/shark_bite_data_raw.csv) showed 6,462 instances of reported shark bites. 
### Inital Data Cleaning 
First, we removed columns not relevant to our analysis. We removed Unamed Columns 22-255 because there are no values in these columns. We also removed the Investigator or Source, pdf, href formula, and href columns becasue these columns contained only source data. Further removed were Case Number 1 and Case Number 2 because they contained a lot of rows with empty values, and the values that were present were duplicates of the original Case Number column. 

When looking through the data, we discovered that not all instances were shark bites (i.e., misreporting or the reported shark bite was from a different sea creature). This information was found in the Species column of the extracted dataset. When these rows were removed, the dataset was narrowed down to 5,935 instances.

We exported the dataframe created after this [initial cleaning](Data_Cleaning/Data_Cleaning_Code/intial_cleaning.ipynb) as a csv file and used this as the [confirmed dataset for all other data cleaning](Data_Cleaning/Raw_Data_Files/shark_bite_confirmed.csv).
#### Description of columns in the [inital cleaned dataset](Data_Cleaning/Raw_Data_Files/shark_bite_confirmed.csv)
- _Index_: Retained because we believed it was a necessary for unqiue identification, but we decided on a different unique identifier to avoid any problems that could arise with index resetting. We removed this column from the final cleaned dataset.
- _Case Number_: This column contained the unqiue identifier for each row and was used to join cleaned data in the database. We also used this column to generate the _Day_, _Month_, _Year_ columns since the Case Number values contained this date information.
- _Date_: Retained becasue we used this column as a cross reference for the generated Day, Month, and Year. We removed this column from the final cleaned dataset.
- _Year_: Retained becasue we used this column as a cross reference for the extracted _Year_ column described below.
- _Type_: Contained information on the type of shark bite incident, including Invalid and Questionable incidents. 
- _Country_: Contained information on the country where the shark bite occurred.
- _Area_: Contained information on the area where the shark bite occurred. We removed this column from the final cleaned dataset because it contained too much missing information. 
- _Location_: Contained information on the beach where the shark bite occurred. We removed from the final cleaned dataset because it contained too much missing information. 
- _Activity_: Contained information the activity being performed when the shark bite occurred.
- _Name_: Contained the name of the victim(s) involved in the shark bite occurrence. Renamed _Original Name_. We used this column to fill in missing values in the _Sex_ column. However, we removed this column in the final cleaned dataset because it was otherwise irrelevant for our analysis.
- _Unnamed 9_: This appeared to be a column was contained information on the sex of the victim(s) involved in the shark bite occurrence, but the majority of the values in this column were missing and needed to be filled.
- _Age_: Contained information on the age of the victim(s) involved in the shark bite occurrence. We removed this column from the final cleaned dataset because there were a great number of missing values and the missing information could only be obtained through internet searches.
- _Injury_: Contained information on the injury of the victim(s) involved in the shark bite occurrence. We used this column to fill in missing values in the _Fatal (Y/N)_ column, but we removed it from the final cleaned dataset because it was otherwise irrelevant for our analysis.
- _Fatal (Y/N)_: Contained information on the outcome for the victim(s) involved in the shark bite occurrence. 
- _Time_: Contained information on the time of day when the shark bite instance occurred. We removed this column from the final cleaned dataset because there were a great number of missing values.
- _Species_: Contained information on the shark involved in the bite incident. 
### Data ETL
We split the [data extraction and transformation code](Data_Cleaning/Data_Cleaning_Code) into seperate files for readability reasons. This code can be found in the Data_Cleaning/Data_Cleaning_Code/ folder. Each file contained code to create a dataframe with the column(s) cleaned in the code and the unique identifier column, Case Number, which remained unchanged. We exported the [datafames as csv files](Data_Cleaning/Clean_Data_Files) which can be found in the Data_Cleaning/Clean_Data_Files/ folder.
#### Database Creation
We made [minor changes](Database_Creation/SQL_Code/Data_Notes.txt) to the cleaned data files before loading them into pgAdmin for formatting reasons. The [final cleaned data files](Database_Creation/Imported_Files) loaded into the database can be found in the Database_Creation/Imported_Files/ folder. We used postgreSQL to [create tables to hold the imported data and join the tables](Database_Creation/SQL_Code/SQL_Commands_For_completedata.txt) The joined table was exported as a csv file and used as the [final cleaned dataset](Database_Creation/Exported_Files/completedata.csv) during exploratory analysis and machine learning analysis. 
#### Description of columns in the final cleaned dataset
- _Case Number_: Described above.
-_Year_: Extracted from the values in the _Case Number_ column. However, we decided not to use this in the machine learning model.
- _Day_: Extracted from the values in the _Case Number_ column. However, we decided not to use this in the machine learning model. 
- _Month_: Extracted from the values in the _Case Number_ column.
- _Country_: Transformed so that each row contained a value that was a three letter country code. The countries with >20 instances were labeled and the rest were labeled as OTH, meaning Other.
- _Activity_: Tranformed so that each row contained a value that was one of 24 labeled activities. There was also a label for Unknown activity, and a label for Miscellaneous activity if the activity did not belong to one of the 24 labeled activities.
- _Species_: Transformed so that each that each row contained a value that was one of 47 labeled species. There was also a label for Unknown species. 
- _Type_: Transformed so that each row contained a value that was one of 5 labeled types (e.g Provoked, Unprovked, Boating). There was also a label for Unknown type.
- _People Involved_: Extracted from the _Original Name_ column and the _Sex_ column. It contained the values I for individual, M for multiple, or U for unknown. If a row in the _Sex_ column contained the value M or F, the _People Involved_ column was labeled I. If a row in the _Sex_ column contained the value S the _People Involved_ column was labeled M.  If a row in the _Sex_ column contained the value U the _People Involved_ column was labeled U.
- _Sex_: Rennamed from Unnamed: 9 in the initial cleaned dataset. We extracted missing values from information contained in the _Name_ column in the intial cleaned dataset and cross referenced on the internet. It contained the values M for male, F for female, U for unknown or S for several, if there were several people involved. 
- _Species_: Transformed so that each row contained a value that was one of 47 labeled species. There was also a label for Unknown species.
- _Fatal_: Renamed from _Fatal (Y/N)_ in the initial cleaned dataset. This was the target column in the machine learning model. Transformed so that each row contained a value either Y for fatal or N for non-fatal. Missing values were extracted from information contained in the _Injury_, _Type_, and _Name_ columns in the initial cleaned dataset dataset and cross referenced on the internet.

## Machine Learning
Before creating any machine learning models, we began with [an exploratory analysis of the cleaned data](https://public.tableau.com/app/profile/gabrijela.odak/viz/SharkBiteExploratoryAnalysis/ExploratoryAnalysis) in Tableau. After exploration, we decided to drop the Day, Year, and Name columns becasue they proved irrelevant to answering our inital questions. Then, we loaded the joined cleaned data table from pgAdmin into a Pandas dataframe where we dropped all rows that contained null values. With no null rows, we [encoded the data](Machine_Learning/Machine_Learning_Data_Encoding.ipynb) using the Pandas .get_dummies() method.

_The encoded machine learning dataset contained 5,056 shark bite instances, 126 feature columns, and the _Fatal_ target column_.

This data was split into training (75%) and testing(25%) sets. 
### Comparing Classification Models
From the beginning of the project we realized predicting a fatal shark bite is a classification problem. We [compared four classification models using Python's Scikit-learn library modules](Machine_Learning/Comparing_ML_Models.ipynb) where we consistently kept the random_state=1:
   1. Simple Logistic Regression using SMOTEENN resampling
   2. Easy Ensemble AdaBoost Classifier Model
   3. Random Forest Classifier Model
   4. Gradient Boosting Model
### Choosing the Best Model
When deciding on the best model we judged two validation scores: Accuracy and Recall. We looked for a model with output sensitive predictions that could cover false negatives. We thought that it was better to label a non-fatal shark bite as fatal than labeling a fatal shark bite as non-fatal. After judging accuracy and recall scores across models we decided the Gradient Boosting Model worked best for prediciting outcomes for our problem. However, we gained valuable insights from the Random Forest Classifier Model after generating a list of feature importances and seeing which import features had the largest effects on the classifier when predicting a certain variable.
#### Gradient Boosting Model
We tried various combinations of n_estimators, learning_rates, and max_features until we landed on the combination that generated the highest accuracy and recall score. Below is the code for our model instance: 
```
GB_classifier = GradientBoostingClassifier(n_estimators=100,
                                        learning_rate=0.25,
                                        max_features=60,
                                        max_depth=3,
                                        random_state=1)
```
The [chosen model](Machine_Learning/Chosen_Model.ipynb) generated an almost 84% accuracy score and a 84% recall score.

![Screen Shot 2022-11-12 at 2 46 36 AM](https://user-images.githubusercontent.com/104794100/201463433-8f0ee1a0-88a8-42b2-a79a-fa1e6e81c7ba.png)

## Project Insights
Although our machine learning model was not perfect, we can say that fatal shark attacks are far from simply random. There are certain factors that contribute to the predictability of fatal shark bites. We used the list of feature importances generated from the Random Forest model to pin-point features with the greatest effect on the model. 

![Screen Shot 2022-11-12 at 1 02 11 PM](https://user-images.githubusercontent.com/104794100/201488281-5dbf1a49-0d16-4685-8565-e9be734bb019.png)

However, one drawback of using feature importance is that the function does not specify which varaible the feature has an effect on the model predicitng. So, we used Tableau Public to visual the outcomes and determine if the features had more effect on the model predicitng Y, fatal attacks, or N, non-fatal attacks. Follow the link to our [Fatal Shark Bites Tableau story](https://public.tableau.com/app/profile/gabrijela.odak/viz/SharkBiteMachineLearningAnalysis/MachineLearningStory) to see which features have the greatest effect on the model and predicitng fatal shark bites.
                                        
