# Final Project: Predicitng Fatal Shark Bites
Team Members Names 
- Eric Bartlow
- Florian Boyaka
- Gaby Odak

## Presentation 
A [slideshow presentation](https://docs.google.com/presentation/d/1D5jMEY6qLNIQtL0yeWbthlBPU3TV16M7XuY5U8JGtFo/edit#slide=id.p) was created using Google Slides and provides a descirption of the project process and project insights. These slides will also contain links to exploratory analysis and a dashboard presentation hosted through Tablaeu Public (also linked below).

## Selected Topic 
The occurances of a shark bite is considered a random event, [and unfortunately not often explainable](https://stories.uq.edu.au/contact-magazine/2019/fear-versus-reality/index.html). This project dives deeper into the above statement and explores and possibility of a shark bite not being a random event at all. Now, predicting if shark bites in general are random events was a very broad topic to take on with just three people. So, we narrowed the scope of this topic to asking whether or not __fatal__ shark attacks are truly random events.

### Reasons for Selecting Topic
We found an interesting dataset on shark bite instances that is described further in the _Description of Data_ section below. Getting bite by a shark is completely based fear becasue of its unpredictability and its potential lethality. We want to quell that that fear in ourselves and others by narrowing down on factors involved in fatal attacks so we can take more caution when we experience those factors in or around the ocean.

### Questions to Answer
#### Main Questions
- Can we use machine learning to predict fatal shark attacks based on the where, when, how, and who?
- Do certain features have a greater impact when it comes to predicting a fatal shark bite?\
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
     - [Code for cleaning](Data_Cleaning/Data_Cleaning_Code) can be found in the Data_Cleaning/Data_Cleaning_Code/ folder.
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
   - Comparing validation of machine learning models
   - Choosing a machine learning model
3. Presentation
   - Slideshow presentation
   - Dashboard presentation



# WE NEED TO CLEAN THIS SECTION UP A BIT
### Description of Data 
From kaggle https://www.kaggle.com/datasets/thedevastator/shark-attacks-the-risks-of-coastal-water-activit
romShark Research Institute's website https://www.sharkattackfile.net/incidentlog.htm
This is data collected on around 6,500 instances of reported shark attacks. Looking through the data, not all instances were actually shark attacks. When these were removed it was narrowed down to 5,935 instances. Right off the bat we removed the Unamed Columns 22-255 because there are no values in these columns. We also removed "Time", "Investigator or Source", "pdf", "href formula", "href", "Case Number 1", "Case Number 2" becasue these columns were not relevant for our analysis. "Area" and "Location" has values that were all over the place so those were also removed. "Age" was removed becasue there were too many missing values 
Columns: 
- Index: We will keep this as the unqiue idnetifier for each row  
- Case Number: We may use this to use this to set up "Month" and "Day" columns and to cross reference the "Date" and "Year" column, but it will not be used in the machine learning model
- Date: We will not be using this in the machine learning model, but it is useful for cross reference when adding data to other columns.
- Day: Present in the mock data, will require manipulation to add this column for the real dataset. Will be used in the machine learning model.
- Month: Present in the mock data, will require manipulation to add this column for the real dataset. Will be used in the machine learning model.
- Year: Needs to be cross referenced with the "Date" and "Case Number" column.  Will be used in the machine learning model.
- Country: Will create labels for the top five countries (USA, AUSTRALIA, SOUTH AFRICA, PAPUA NEW GUINEA, NEW ZEALAND) and the other countries will be grouped under label. We will make dummies from these variables for the machine learning model.
- Activity: This column will need to be cleaned and labels will need to be created for the various different acitvites. We will make dummies from these variables for the machine learning model.
- Name: The original data is being used to fill in "Unnamed 9" which we renmaed "Sex". The "Name" column will be renamed "Number of Victims" and have the label "I" for individual "M" for multiple of "U" for unknown. We will make dummies from these variables for the machine learning model.
- Sex: Rennamed from "Unnamed: 9", either "M" for male, "F" for female, or "U" for unknown. We will make dummies from these variables for the machine learning model.
- Injury: Right now it is a mess and we narrowed it down to either "Y" for injury or "N" for no injury. I think we will change this to be a scale where 0 is no injury, 1 is a mild injury(sratches, bruises), 2 is a moderate injury(lacerations), 3 is a severe injury (limbs bitten off), and 4 is a fatal injury. Clearly, this column is repetative for fatality predicition, but it could contain good data for presentation purposes.
- Fatal(Y/N): This is our target variable. This will be encoded for machine leanring.
- Species: We will make dummies from this column for the machine learning process. I predict that species of shark will have a high impact on fatality. If every specieis is made into its own individual feature we could point to which shark is the most deadly.



