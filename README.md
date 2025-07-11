# Healthcare Database Facility Analysis
# DataChallenge
## Introduction 
Data cleaning is a vital process in any database system, especially in healthcare sector, where accurate and reliable data is essential for decision-making and patient care. This project explores an innovative approach to data cleaning tailored to improve database management by identifying and addressing weaknesses in healthcare system process. This project data cleaning was implemented using Microsoft Excel and Power BI.

## Project Objectives
The main goal of the project is to:
- Data Cleaning: Identify and address inconsistencies, missing values, and formatting errors.
- Exploratory Data Analysis: Perform analysis based on trends and patterns and give recommendations.

## Project Overview
### Data Cleaning Challenge
This project is a #DataCleaningChallenge organized by Green Data Solutions. The event is aimed to provide accurate, actionable and accessible environmental and health data for informed decision making and sustainable living. Participants are to work on the provided dataset, share their experiences and insights into the data cleaning process.

The project consists of three main Parts:
-Data Collection/Timeline
-Data Cleaning and Preprocessing
-Exploratory Data Analysis

### Data Collection/Timeline
The dataset provided included a .csv file named dirty_healthcare_data and a data dictionary in .pdf format. The dataset comprised 1,660 rows and 12 columns, with data fields such as ID, Name, Age, Gender, City, Blood Type, Education, Employment Status, Salary, Health Condition, Credit Score and Date of Admission. In order to preserve the original data, a copy was saved as an .xls file for cleaning and analysis.

## Report Timeline
On-boarding session: January 6th, 2025
Challenge Duration: January 7th - 10th, 2025

### Data Cleaning and Preprocessing
The primary objective was to check for inconsistencies in the data, and transform the dataset into a usable format for analysis. The following are the steps I took into cleaning the dataset:
## Duplicates removal: 
I started by inspecting my data by checking duplicated data. This was done by converting the data range into a table format using Ctrl + T or click the home tab>styles menu>click on format as tables. Dataset converted to Table formatAfter converting to table, I then clicked on the add-ins menu bar(Table design)>remove duplicates. There were a total of 3 unique duplicates value found and removed, while 1656 unique columns values remains.

## Dupilicate values found and removedHandling null values and Data type issues:
Nulls values were inspected across all columns. Columns were checked for formatting errors, such as repeated unique numbers from the ID column, unknown details from the Age, and inconsistent cases on the name, Gender, and City column. 

## Column-Specific Cleaning:
- ID-Column- I highlighted the duplicate IDs using conditional formatting. This was done through the new menu add-ins (Table Design)>Conditional Formatting>Highlight Cell Rules>Duplicate Value. A total number of duplicates found revealed 280 records. The majority of the numbers showed twice, while some thrice. These discrepancies likely resulted from entries across different healthcare annexes within this unified system.

- Name Column: Reformatted the column text to a sentence case using the formula =PROPER(B2). I created a new column and typed the formula. After which it was copied and pasted as value, Below is the image showing the formula that was used to convert the text to sentence case:

- -Age Column: The missing values (Unknown) were replaced with the average age of the total patient's age, which was calculated as 32.97807, which was formatted by removing the float numbers to 33. This was calculated using =AVERAGE(). 

- Formatted Average Age Calculated Value: It was observed that there were outliers in the values, meaning that the age data value does not follow a normal distribution. The data values consist of ages under 0- 14 years of age, which I categorize as very young. The data dictionary justified that the minimum educational status of the Patient's record is classified as "High Schooler". This shows that ages 0–14 years are very young individuals who are still in Kindergarten, Nursery, and Basic Classes. This age range has a total of 55 records. I thereafter replaced these values with the median, which was calculated as =MEDIAN():
  
- Median Age Calculated Value: I also observed those over 70 years of age, and their educational details revealed that they are "RETIRED". Hence, their age was retained for the analysis, due to their educational status, which is significant to the the analysis.

- Gender Column: There are missing and inconsistent gender values. I created a column and used a logical function (IFS). =IFS(logical test 1, value if true 1, logical test 2, value if true 2, …..). The formula was used thus; =IFS(D2="M", "Male", D2="F", "Female", D2="Male", "Male", D2= "Female", "Female", TRUE, "Others"). This is because the data dictionary provided revealed that the gender values consist of Male, Female and Others.

- City Column: The city names had few abbreviated values and inconsistent sentence cases. The inconsistent cases were converted to sentence cases using =PROPER(). Abbreviated values were filled forward based on the dataset's context.

-Blood type Column: The fact column shows 8 blanks, replaced with the the most occurrence categorical value, O+.

- Education Column: There are irregular entries like "High School (Ged)", which were corrected to "High School", "Bachelor" were corrected as "Bachelor's", "Associate" and "PhD" to "Master's" and blank spaces were filled with most frequent categorical value, Master's.

- Employment Status: The data values were categories using the =IFS(), logical functions formula, grouping the related status terms to the right status, such as Freelance is classified as "Employed".
  
- Salary Column: The column is a monetary unit, including text. I performed an operation using text to column to sepeare the text from numbers using delimiter () and I separated to creat another column. The salary has 9 missing values and replaced blanks with 0.

-  Health Condition: The column shows Excellent, Good and Poor from the data dictionary. Data were categorised in this order using the IFS functions. 45 blanks were replaced by the most frequent value.
  
- Credit Score: The column had None and N/A. I replaced the N/A and None to 0, because it a numerical value. I also observed 380(typo) for 9 records. It could have been an error, but bevause the data set is not much I replaced values with average of the entire values in the column.

- Date of Admission: The column was written in a text format, I converted the data type to date format and uploaded to PowerQuery Editor to automatically convert the data type to date.
  
### Exploratory Data Analysis

## Research Questions 
The following are the research questions that guided the exploratory data analysis:
### 1. What is the Patients demographics and financial capabilities? 

Finding the analyis provides insight into further segmentation and analysis. I checked for total number of patients, their average age, average salary, total credit score, and total unique cities(distinct count).
The analysis shows that there are over 1,656 Patients from 3 cities, with an average age of 34. I checked for the average salary and it was $42K, the total credit score was 78K.
Following the analysis, the dataset confirmed 3 Gender categories, which are Male, Female and Others. Most Patients were categorized as "Employed" or "Unemployed", with minimal representation in the "Student Category". This insights helps to identify the average total population of Patients that receives treatment in the healthcare facility. A total of 234 Patients had O+ as their blood types.
Patients Demographic Track Patient's Gender DistributionPatient's Employment StatusPatient's Education StatusPatients Blood types

## 2. What are the possible cause of health conditions across populations?
In Atlanta city, the highest number of Excellent health condition recorded was 293, followed by 458 records of Good health condition, and 222 records of Poor health conditions. In Albuquerque, 114 has Excellent health conditions, 178 had Good health conditions, while 86 was recorded for Poor health condition. In Balitmore, 88 had Excellent health conditions, 147 had Good health condition, while 70 had poor health conditions.
The distribution of health conditions across cities reflects the differences in population size, healthcare infrastructure, and health awareness programs. Cities like Atlanta may have broader access and resources, while Albuquerque and Baltimore with fewer records shows there is an indication for low healthcare availability and infrastructure.
Patient Health Conditions Per CityThe analysis also shows that the Patient health condition Per employment status reveals that majority of the Patients that have Poor health conditions are Unemployed with 72.81% and the implication is that they are not earning a good stable salary, which could affect their health conditions, while 61.82% are Employed having Excellent health conditions. This implies that people with more income tends to cater for their health needs before it fails.

## 3. What is the relationship between Patients age characteristics and credit score?
The above analysis shows the credit score per age analysed using scatter plot to view the propensity of Patient's Ages that earn more credit score, which can improve their spending capabilities of their health. The results shows majority within 20–40 years of ages having more high credit score than the older ones.

- Patients Age by Credit Score: Observe the yearly trends in Patients health condition distributon across cities and employment statutes, identifying the peak period?
From the healthcare database system collated from year 2019 to 2024, the most peak period with the highest health record is in year 2020, the trend has gradually decline till year 2024. This shows that as the year goes by new technological advancement has been utilized tailored to improve Patient's health care within this healthcare facility.

## Patients Health Condition Per Year (2019–2024)Limitations of the Dataset

There are incomplete records with missing values in specific columns, such as age, salary, health conditions, which limits the analysis accuracy.
- The dataset has inconsistent or extreme values (an outliers), like ages.
- The data covers only three cities, which lacks a broader representation of a region, or country.
- The data is limted from year 2019–2024

### Recommendations
It is recommended to invest in healthcare infrastructure, conduct health awareness campaigns in neighbourhood and cities targeted towards health care improvement, inorder to enhance quality healthcare service delivery and Positive Patients health outcomes.

### Data Visualization
I exported the cleaned dataset file>PowerBI for visualization.
