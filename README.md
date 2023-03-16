# FIFA-Data-Cleaning-Challenge

![image](https://www.answerminer.com/static/6892013332458526a092450e12ab191a/d4bc6/data_cleaning.png)

## Introduction
We are given a task to clean the messy FIFA '21 dataset which has 79 columns like ID, Name, Longname, Nationality, PlayerUrl, Age, OVA, POT, Height, Weight, Prefered foot, Value, Wage, Release clause etc and 18,979 rows. The task is to clean the data and make it ready for analysis. The cleaning process involves deleting duplicates, null values, changing datatype, removing extra spaces, special characters, handling missing values, look for the wrong calculations etc.

## Data Cleaning Process
For the analysis of data, the data should be accurate and consistent. With the elimination of irrelevant and duplicate data, one can ensure the raw data is complete and free of errors.

<img  height=400 width=700 src="https://www.tekstream.com/wp-content/uploads/2018/05/data-cleaning1-1.x21717.jpg">

<h2>White Space</h2>
After the data was loaded into power query, the white space removed by unticking the "Show whitespace" in View tab.

<h2>Name and Longname</h2>
Deleted these columns as they have special characters or diacritic accents. The "playerUrl" column is used to extract the names of the players using the formula 
<i><b>Text.BetweenDelimiters([playerUrl],"/","/",4)</b></i>. '-' is replaced with empty space and capitalized the names.

<h2>Age</h2>
It contains the age of the players as of year 2021. As there is no inaccuracy in the column, no need to clean it. So just changed the type to whole number.

<h2>OVA, POT and BOV</h2>
As per data dictionary, these columns were reformatted to show percentages. To do this, first divided the columns by 100 and then changed the type to percentage.

<h2>Club</h2>
As this columns contains the names of the clubs of which some club names have diactitic letters. to get the appropriate names of the clubs, replaced those diacritic letters with the appropriate alphabets.

<h2>Height</h2>
The heights of the players were expressed in two units like 'cm' and 'feet'. To convert into 'cm', multiplied feet by 30.48 and inch by 2.54.

<h2>Weight</h2>
Same as height, weight alse expressed in two units, 'kg' and 'lbs'. To convert the kg into lbs, multiplied the cells which ends with kg by 2.2

<h2>Value, Wage, Release Clause</h2>

These columns gives the us the details of the players worth, their weekly salary and the amount, the player requires to pay to leave the club which are supposed to be in "US Dollars". But given in millions "M" and thousands "K" of Euros. To convert into Dollars, "M" and "K" are replaced by 1000000 and 1000 respectively and multiplied by 1.06

<h2>W/F, SM, IR</h2>
These are the ratings given to the players for their week foot, skill moves and injury rate with a scale of 1-5. Each row ended with a star and was removed by replace function and then changed the type to whole number.

<h2>Hits</h2>
The figures in this column were expressed in thousands "K" format like 1700 as 1.7K. To standardise the column, used the same approach as used for value and wage column.

<h2>Contract</h2>
This column contained the incosistent data type and format. So for the analysis purpose, it is split into three columns namely contract start, contract end and type of  aggrement like loan,contract and free using conditional column in Add Column tab
