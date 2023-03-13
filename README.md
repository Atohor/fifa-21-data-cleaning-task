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





However to sort Diacritic names, like spanish names with accent  , The player url was used to extract those names to get a cleaner version. 
Filter to see places with Diacritics for the first letter of the alphabet and replace with clean version. If this is not done, during visualization, sorting the names in alphabetical order, ascending or descending will result in those names appearing last after Z.

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224684006-6287fa7c-6d31-408c-99bd-95125ad152d5.png)|![image](https://user-images.githubusercontent.com/99989624/224684358-ea94ad53-b786-43db-8d29-38e647689471.png)



finally Names like C. Ronaldo , A. Benjamin , G. Paiva were standardized to reflect the full first name

<div align="center">
    <h2>Percentages</h2>
</div>

As advised by the Data Dictionary , the columns OVA and POT were reformatted to reflect percentages.
Column from example was used to add % to the end of the row figures ,then the data type was changed to percentage

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224689449-f6a490f1-e016-4058-9373-71487095283d.png)|![image](https://user-images.githubusercontent.com/99989624/224689726-1884d63f-e22e-4b70-8a67-3dbead6aa4ed.png)

<div align="center">
    <h2>Clubs</h2>
</div>
Some club names started with 1. examples 1.fc koln , 1. fc union Berlin these were normalised . Also some other club names contained diacritic first letters and as previously explained, this makes alphabetical sorting to flop during visualiization

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224834902-356b3ed5-c7e0-489c-87d2-b3602bc91364.png)|![image](https://user-images.githubusercontent.com/99989624/224835627-e81bbc9a-7c95-41e9-a1e3-5be5cef1ac2c.png)


<div align="center">
    <h2>Contract</h2>
</div>

This column contained inconsistent data type and format, hence this was reguarized using a combination of 3 columns , namely; Contracts , Joined , and Loan end date
The filter view reveals players whose contract column specify they are on loan tally with the year on the Loan end date column.
while players whose contract indicate free transfer tally with those clubless players with no wage or earnings . this were replaced with null as there is no specified loan end date since they're not on contract and have no recorded wages. These players should therefore be dropped during visualization.

At the end of the cleaning, splitting and merging of columns we arrived at two columns : contract start and contract end which displays only the year info as lack of more data prevented further date drill down

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224838470-25cd2741-d7bf-479b-8ff7-14d2917f498c.png)|![image](https://user-images.githubusercontent.com/99989624/224838770-df41bf1a-5391-4bdd-8a17-99c4a7da1cb5.png)

Notice the data type of the contract start and contract end data type is ABC text because formating it as a date column will lead to incorrect months and day values. As the first day of the first month is automatically assigned for all rows. Thus During visualization, when formatted as date , only the year drill down should be used. 


<div align="center">
    <h2>Positions</h2>
</div>
 
 **Split ? Or ignore:** 
 This column contains the position the player has ever played and some had 2 or more positions assigned to them using comma seperated values. Initial thought was to split the column by delimiter to reflect all positions however since this will lead to creating too many irrelevant data occupying memory space,a decision was reached to drop the column for the best position column as best position column contains complete information suitable for analysis

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224841755-aac24509-7c26-40e5-b46b-4cdc8ddca9e7.png)|![image](https://user-images.githubusercontent.com/99989624/224841978-f61c750b-4ae4-40fe-9af7-8f7208547b2b.png)


<div align="center">
    <h2>Height</h2>
</div>

The majority of values in this column displays height in centimeter. while a few others uses feet and inches for example 6'2" . Initial thought was just to split by the delimiter ' " and multiply by 30.48 which is the standard conversion of feet to cm . However a quick google search reveals this formula only accounts for feet and not inches hence to resolve this after splitting, the feet column was multplied by 30.48 and the inches column by 2.48. then both columns were merged using addition and rounded up to the nearest whole number. then the cm text value was dropped from the other rows to successfully change the data type to numeric

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224844971-31f4648e-2b1f-42d8-99b7-84e1a376a428.png)| ![image](https://user-images.githubusercontent.com/99989624/224845368-72935580-ede4-44b1-94bd-d5db1d4866e8.png)


<div align="center">
    <h2>Weight</h2>
</div>
About 60% of the data values in this column contains weight in lbs (pounds) and the other 40% in Kg . After splitting the column using Digits to non-digits function,  A decision was made to unify all data values as lbs 
and the standard conversion rate of 2.205 was used to multiply the weight in Kg value to give the equivalent in lbs and rounded up.

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224845690-2cb91c6f-bcf9-478f-b1d7-0dc5cc0e8b76.png)|![image](https://user-images.githubusercontent.com/99989624/224846437-d180ffa8-277e-400c-aa69-a2051aed01f5.png)


<div align="center">
    <h2>Value , Wage and release clause</h2>
</div>
These three columns contains euro values in shortenend format where 1,500 euros was written as 1.5k and one million ,five hundred euros as 1.5m.
The goal is to standardise the columns and convert to US dollars
Hence the approach used was to dropped the euro symbol from all rows using find and replace, then split columns by m and k 

first step was to create a New column which If column 1 contains m multiplies the figure by 100000 then if column 1 contains k multiply by 1000 else return the figure on the original column , this else function handles the values , or wages in hundreds having no K or M attached .

this approach gives the full numeric form of the value , wage or release clause but wait! we are not done yet .
To convert this full numeric digits to USD , the average euro to USD exchange rate of 1.183 was used as this was the average exchange rate as at 2021 which our data is based on.

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224848874-1db3b234-8f91-4a58-8aa8-62e4db072d38.png)|![image](https://user-images.githubusercontent.com/99989624/224849112-0e74cdb0-ceb6-4a38-bc4d-4efc3f9ccf43.png)

<div align="center">
    <h2>W/F , SM , IR</h2>
</div>
These three columns contains player ratings in different aspect with a ranking of 1-5 . However a star symbol was attached to each row and this was removed using the replace function and the data type was changed to numeric.

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224855858-546c4bdf-adb2-421a-a459-f799a7f1a241.png)|![image](https://user-images.githubusercontent.com/99989624/224855981-166a7132-bbb1-4451-89e5-62f9b43d66dd.png)

<div align="center">
    <h2>Hits</h2>
</div>
The filter pane reveals some figures in this column were coded in the shortened version, such as 1500 written as 1.5k. These were regularized using a similar approach as previously used and explained for the values and wages column.

| Before | After |
|--------|-------|
![image](https://user-images.githubusercontent.com/99989624/224856470-037630d2-1429-4644-b107-d5b88323fa32.png)|![image](https://user-images.githubusercontent.com/99989624/224856581-0ff90894-e6da-4edc-b25a-850a3b59e966.png)



