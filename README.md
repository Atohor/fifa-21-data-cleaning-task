# fifa-21-data-cleaning-task
![image](https://user-images.githubusercontent.com/99989624/224593879-22577651-31b4-46db-9d0d-069a50a29c8c.png)

A dirty data makes a dirty analysis , so take a walk with me


## Introduction
This is a rundown of the cleaning process for FIFA '21 dataset. This data set was provided as part of a challenge #Datacleaningchallenge launched on twitter by data ethusiasts to test the prowess of newbies , intermediate and pro Data analyst alike for a large messy dataset.

The data set contains 18,980 rows and 80 columns of football players statistics and demography in 2021
The dataset is publicly available on [kaggle](https://www.kaggle.com/datasets/yagunnersya/fifa-21-messy-raw-dataset-for-cleaning-exploring)
which contains data scrapped from [sofifa](www.sofifa.com)
The datafile also includes a Data dictionary as well as a column named player url which contains a link to the player profile on sofifa to give the analyst furher insight and full deails of the player in view in case of missing information.

my prefered tool for this Data cleaning challenge based on proficiency is Power Query as available on Power BI

## Data Cleaning process
![image](https://user-images.githubusercontent.com/99989624/224600574-6e1e90ec-4fa6-4dfc-9b8d-976df3ea6981.png)

![image](https://user-images.githubusercontent.com/99989624/224600737-699ff508-da6a-4847-a99d-85496ba052d2.png)


To ensure data quality , the following approach was used 

After loading the data , whitespaces were removed by unticking the button from the viewtab 
 
<div align="center">
    <h2>Whitespaces</h2>
</div>

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224610838-f6b78c4b-b204-42d9-b158-f7aeacb6cda8.png)| ![image](https://user-images.githubusercontent.com/99989624/224610689-763b528d-9eed-431a-8b7d-2d5a54abaa32.png)


**1. Data Auditing**
To ensure data quality, during the auditing stage of understanding the data and identifying any inconsistencies, missing values, or errors that need to be addressed, the following columns were marked for cleaning ; Name, Longname , Age , OVA , POT , Club , Contract , Positions , Height , Weight , Best position , Joined , Loan End date , Value, wage , release clause , W/F , SM , IR , and Hits.


**2. Data enrichment**
This step involves adding additional information to the data,to enhance its value and usefulness. The dataset was collected 2 years ago in 2021 thus the data was modified to reflect their current age. This was made as an additional column to give the Analyst/Visualizer a choice to use or drop either one. 
 
 <div align="center">
    <h2>Age</h2>
</div>

the age column + 2 gives us their age in 2023

| Before | After |
|--------|-------|
|![image](https://user-images.githubusercontent.com/99989624/224671691-bc17297f-d433-42b2-801b-2a5c614b0fff.png)|![image](https://user-images.githubusercontent.com/99989624/224671895-e15292ce-058d-4fa1-a691-7a36ed032e3d.png)|





**3. Data Cleaning and Transformation** 

The previously identified columns were worked on , in an orderly manner

<div align="center">
    <h2>Names</h2>
</div>

The Name and Longname column were Standardised by splitting delimiters and replacing empty rows 
to generate a first name and last name column. Hyphenated or double last names like De Bruyne , Ter stegan , Van Dijk were also kept in the right manner
| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224680924-00835e64-6273-4c6e-aab9-a472fe3cea3b.png)|![image](https://user-images.githubusercontent.com/99989624/224681183-81a31f33-425e-4105-a848-ebf7d3134ecc.png)





However to sort Diacritic names, like spanish names with accent  , The player url was used to extract those names to get a cleaner version 
Filter to see places with Diacritics for the first letter of the alphabet and replace with clean version. If this is not done, during visualization, sorting the names in alphabetical order, ascending or descending will result in those names appearing last after Z.

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224684006-6287fa7c-6d31-408c-99bd-95125ad152d5.png)|![image](https://user-images.githubusercontent.com/99989624/224684358-ea94ad53-b786-43db-8d29-38e647689471.png)







Also some name have only one alphabet 

Like c. Ronaldo , g. Pierre , a.Benjamin 










