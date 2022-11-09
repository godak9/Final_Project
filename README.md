# Final_Project
Team Members Names 
- Eric Bartlow
- Florian Boyaka
- Gaby Odak
## Presentation 
A [slideshow presentation](https://docs.google.com/presentation/d/1D5jMEY6qLNIQtL0yeWbthlBPU3TV16M7XuY5U8JGtFo/edit#slide=id.p) was created using Google Slides
### Selected Topic 
Finding factors that contribute the most to fatal shark attacks. Creating a machine learning model that can predict fatal shark attacks. I think we should use a Classification model of some sort. I would like to use an ensemble learning model, but this may change. Once the data is cleaned and encoded, we can set up multiple models and compare the results 
### Reasons for Selecting Topic
The data was interesting considering it has records from the B.C era. This could give some insight into beach saftey by avoiding found factors that lead to fatal sharks (like avoiding  the water if a certain type of shark was spotted there recently, take caution when performing certain activities in certain parts of the world).
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
### Questions to Answer
- Is one species of shark more deadly than the others?
- Are you more susceptible susceptible to a fatal injury where performing a certain ocean activity?
- Are men or women more susceptible to a fatal injury?
- Are individuals or groups more susceptible to a fatal injury?
- Do provoked attacks lead to a more fatalities?
I'm sure more questions will come up along the way, and we may find answers to questions that we didn't think to initially ask, but these are the top five questions that come to mind for now. 
## Communication protocols
So far, Florian, Eric and I have done great job keeping in touch and communicating ideas. We primarily use Slack for communication and we have gotten together on Zoom almost every day. There is fluid written and verbal communicaiton between us.
The only protocol we have in place is that if one of us does not answer in Slack for a few days, we will move on without them. Things come up, it is understandable, so we will try our best to fill the person in when they are able to come back. However, we cannot put a hold on the entire project for one person. 


