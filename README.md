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

**1. Data Auditing**
To ensure data quality, during the auditing stage of understanding the data and identifying any inconsistencies, missing values, or errors that need to be addressed, the following columns were marked for cleaning ; Name, Longname , Age , OVA , POT , Club , Contract , Positions , Height , Weight , Best position , Joined , Loan End date , Value, wage , release clause , W/F , SM , IR , and Hits.

**2. Data Cleaning , Transformation** **and Enrichment**
 
 After loading the data , whitespaces were removed by unticking the button from the viewtab 
 Removed white spaces from view tab 
<div align="center">
    <h2>Whitespaces</h2>
</div>

| Before | After |
|--------|-------|

| ![image](https://user-images.githubusercontent.com/99989624/224610838-f6b78c4b-b204-42d9-b158-f7aeacb6cda8.png)| ![image](https://user-images.githubusercontent.com/99989624/224610689-763b528d-9eed-431a-8b7d-2d5a54abaa32.png)|





















