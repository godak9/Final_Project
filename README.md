# Final Project: Predicitng Fatal Shark Bites
Team Members Names 
- Gaby Odak
- Eric Bartlow
- Florian Boyaka


## Presentation 
A [slideshow presentation](https://docs.google.com/presentation/d/1D5jMEY6qLNIQtL0yeWbthlBPU3TV16M7XuY5U8JGtFo/edit#slide=id.p) was created using Google Slides and provides a description of the project process and in depth project insights. These slides will also contain links to exploratory analysis and a dashboard presentation hosted through Tablaeu Public (also linked below).

## Selected Topic 
The occurances of a shark bite is considered a random event, [and unfortunately not often explainable](https://stories.uq.edu.au/contact-magazine/2019/fear-versus-reality/index.html). This project dives deeper into the above statement and explores and possibility of a shark bite not being a random event at all. Now, predicting if shark bites in general are random events was a very broad topic to take on with just three people. So, we narrowed the scope of this topic to asking whether or not _fatal_ shark attacks are truly random events. To explore this question, we decided to use a classification machine learning model. 

### Reasons for Selecting Topic
We found an interesting dataset on shark bite instances that is described further in the _Description of Data_ section below. Getting bite by a shark is completely based fear becasue of its unpredictability and its potential lethality. We want to quell that that fear in ourselves and others by narrowing down on factors involved in fatal attacks so we can take more caution when we experience those factors in or around the ocean.

### Questions to Answer
#### Main Questions
- Can we use machine learning to predict fatal shark attacks based on the where, when, how, and who?
- Do certain features have a greater impact when it comes to predicting a fatal shark bite?
#### Supporting Questions
- Is one species of shark more deadly than the others?
- Are you more susceptible susceptible to a fatal injury where performing a certain ocean activity?
- Are men or women more susceptible to a fatal injury?
- Are individuals or groups more susceptible to a fatal injury?
- Do provoked attacks lead to a more fatalities?

## Analysis Roadmap
This project was broken down into three main parts:
1. Data ETL
   - Data cleaning and transformation
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
     - A [storyboard presentation](https://public.tableau.com/app/profile/gabrijela.odak/viz/SharkBiteExploratoryAnalysis/ExploratoryAnalysis) can be found on Tableau Pubic
   - Data encoding
     - [Code for encoding data for machine learning](Machine_Learning/Machine_Learning_Data_Encoding.ipynb) can be found in the Machine_Learning folder and at the top of files where mahcine learning models were ran.
   - Comparing validation of machine learning models
     - [Code for comparing machine learning models](Machine_Learning/Comparing_ML_Models.ipynb) can be found in the Machine_Learning folder.
   - Choosing a machine learning model
     - [Code for the selected machine learning model](Machine_Learning/Chosen_Model.ipynb) can be found in the Machine_Learning folder.
3. Presentation
   - [Slideshow presentation](https://docs.google.com/presentation/d/1D5jMEY6qLNIQtL0yeWbthlBPU3TV16M7XuY5U8JGtFo/edit?usp=sharing)
   - [Fatal Shark Bites Tableau story](link, but we don't have one yet)

## Description of Data
The [dataset was originally sourced](Shark Research Institute's website https://www.sharkattackfile.net/incidentlog.htm) from the Shark Research Institute's website. We came across the [dataset on Kaggle](https://www.kaggle.com/datasets/thedevastator/shark-attacks-the-risks-of-coastal-water-activit) where someone had already extracted the dataset and created a new file from it. However, even the extracted dataset still required a lot of cleaning before any machine learning was conducted. 

The data showed 6,462 instances of reported shark bites. When looking through the data, we discovered that not all instances were actually shark bites (i.e. misreporting or the bite was concluded to be from a differnt sea creature). This information was found in the Species column of the extracted dataset. When these rows were removed, the dataset was narrowed down to 5,935 instances. The dataframe created after this cleaning was exported as a csv file and used as the [confirmed dataset for all other cleaning](

Next, we removed columns not relevant to our analysis. The Unamed Columns 22-255 because there are no values in these columns. We also removed Time, Investigator or Source, pdf, href formula, and href columns becasue this only contained source data. The columns Case Number 1 and Case Number 2 because they contained a lot of rows with empty values, and the values that were present were duplicates of the original Case Number column. The columns Area and Location were also removed because for the geographical factor we decided to use the Country column. Finally, the Age column was removed because there were too many missing values.

### Desciption of columns used for data cleaning and columns used in machine learning models: 
- _Case Number_: This column contained the unqiue identifier for each row and was used to join cleaned data. This column was also used to set up the Day, Month, Year columns since the Case Number contianed this date information. However, this column was not used in the machine learning model.
- _Day_: Extracted from the Case Number column. However, we decided not to use this in the machine learning model. 
- _Month_: Extracted from the Case Number column.
- _Year_: Extracted from the Case Number column. However, we decided not to use this in the machine learning model. 
- _Country_: Transformed so that each row contained a value that was a three letter country code. The countries with >20 instances were labeled and the rest were labeled as OTH, menaing Other.
- _Activity_: Tranformed so that each row contained a value that was one of 24 labeled activities. There was also a label for Unknown activity, and a label for Miscellaneous activity if the activity did not belong to one of the 24 labeled activities.
- _Type_: Transformed so that each row contained a value that was one of 5 labeled types (e.g Provoked, Unprovked, Boating). There was also a label for Unknown type.
- _Original Name_: This column was used to set up the Sex column However, we decided not to use this in the machine learning model.
- _Sex_: Rennamed from Unnamed: 9. Information for this column was extracted from the Name column after being cross referenced on the internet. It contained the values M for male, F for female, U for unknown or S for several, if there were several people involved. 
- _People Involved_: Extracted from the Original Name column and the Sex column. It contained the values I for individual, M for multiple, or U for unknown. If a row in the Sex column contained the value M or F, the People Involved column was labeled I. If a row in the Sex column contained the value S the People Involved column was labeled M.  If a row in the Sex column contained the value U the People Involved column was labeled U.
- _Species_: Transfomed so that each that each row contained a value that was one of 47 labeled species. There was also a label for Unknown species.
- _Injury_: Removed from the final cleaned dataset. However, the information in this column was used to fill in missing values for the Fatal column. 
- _Fatal_: The column was the target column in the machine learning model. Transformed so that each row contained a value either Y for yes or N for N. Missing values were extracted from information contained in the Injury, Type, Name columns after being cross referenced on the internet.

### Database 
The columns above were seperated before being cleaned and saved to csv files with the unqiue identifier column, Case Number. The data was loaded into pgAdmin where we hosted a database and joined the cleaned data on the Case Number column. This table was also exported as a csv file so we could perform exploratory analysis in Tablaeu before the creating machine learning models. 

## Machine Learning
Before creating any machine learning models, we began with an exploratory analysis of the cleaned data in Tablaue. After exploration, we decided to drop the Day, Year, and Name columns becasue they proved irrelevant to answering our inital questions. Then, we loaded the joined cleaned data table from pgAdmin into a Pandas dataframe where we dropped any row that contained null values. With no null rows, we encoded the data using the Pandas .get_dummies() method. _The encoded machine learning dataset contained 5,056 rows of data, 126 feature columns, and the Fatal target column_.
### Comparing Classification Models
From the beginning of the project we realized predicting a fatal shark attack would be a classification problem. We compared four classification models where we consistently kept the random_state=1 :
   1. Simple Logistic Regression using SMOTEENN resampling
   2. Easy Ensemble AdaBoost Classifier Model
   3. Random Forest Classifier Model
   4. Gradient Boosting Model
### Choosing the Best Model
When deciding on the best model we judged two validation scores: Accuracy and Recall. We were looking for a model with output sensitive predictions where we could cover false negatives. We thought that it was better to label a non-fatal shark bite as fatal than labeling a fatal shark bite as non-fatal. Ater judging these scores across models we decided the Gradient Boosting Model worked best for this problem. However, we gained valuable insights from the Random Forest Classifier Model after generating a list of feature importances and seeing which features had the most impact when classifying. 
#### Gradient Boosting Model
We tried various combinations of n_estimators, learning_rates, and max_features until we landed on the combination that generated the highest accuracy and recall score. Below is the code for out model instance: 
```
GB_classifier = GradientBoostingClassifier(n_estimators=100,
                                        learning_rate=0.25,
                                        max_features=60,
                                        max_depth=3,
                                        random_state=1)
```
This model generated an almost 84% accuracy and a 84% recall score.
![Screen Shot 2022-11-12 at 2 46 36 AM](https://user-images.githubusercontent.com/104794100/201463433-8f0ee1a0-88a8-42b2-a79a-fa1e6e81c7ba.png)

## Project Insights
Although our machine learning model was not perfect, we can say that fatal shark attacks are far from simply random. There are certain factors that contribute to the predictability of fatal shark attacks. Follow the link to our [Fatal Shark Bites Tableau story](link, but we don't have one yet) to see what those factors are.
                                        
