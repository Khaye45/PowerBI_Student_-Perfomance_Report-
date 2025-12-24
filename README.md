# PowerBI_Student_ Perfomance_Report   
A comprehensive PowerBI dashboard to help analyze student perfomance  in an academic year.  
## OVERVIEW  
This 2 -paged Students' Performance Power BI PBIX File is an essential tool for educators, school administrators, and data analysts aiming to monitor and improve academic outcomes. Perfect for schools, education departments, and learning institutions, this interactive dashboard offers a scalable, visually engaging solution to uncover trends, analyze performance by demographics, and identify areas needing support.  
### ☑️ Data Cleaning and Preparation   

I imported the [Excel file](https://github.com/Khaye45/PowerBI_Student_-Perfomance_Report-/blob/main/StudentsPerformance.xlsx)  into Power BI and launched the dataset in Power Query Editor. My data cleaning process involved checking out for:      

✍️Missing or inconsistent data in key columns using column quality and column distribution features.   

⏬Duplicate rows (none was found).    

✔️Ensured columns had the correct data types for analysis.   

⚙️Renamed columns to proper case.    

➗Added a calculated column for the student Score    

🧮 Created a conditional column to assign grades based on their scores  

``` Grade =    
SWITCH (   
TRUE (),
[Score] >= 95, "O",    
[Score] >= 81, "A",    
[Score] >= 71, "B",    
[Score] >= 61, "C",    
[Score] >= 51, "D",    
[Score] >= 41, "E",    
"F"      
) 
```

### 🧬Data Modelling  

I calculated the following measures   
#### 💼 Base Measures
+ Total Number Of Students    
 `No Of Students = DISTINCTCOUNT (StudentsPerformance[Student  ID]`  

+ Average Score  
  `Average Score = AVERAGE(StudentsPerformance[Score])`  

+ Average Score for each Subject
  ```
  Avearge Writing = AVERAGE(StudentsPerformance[Writing Score])
  Average Math = AVERAGE(StudentsPerformance[Math Score])  
  Average Reading = AVERAGE(StudentsPerformance[Reading Score])
  ```
+ Percentage Number of Students that are Male and Female
```
Male Students = 
VAR MaleCount =CALCULATE([No Of Students],StudentsPerformance[Gender] = "male")
VAR TotalCount = [No Of Students]
VAR MalePercent = DIVIDE( MaleCount, TotalCount, 0)
RETURN
FORMAT(MalePercent,"0.0%")

Female Students = 
VAR FemaleCount =CALCULATE([No Of Students],StudentsPerformance[Gender] = "female")
VAR TotalCount = [No Of Students]
VAR FemalePercent = DIVIDE( FemaleCount, TotalCount, 0)
RETURN
 FORMAT(FemalePercent,"0.0%")
```

#### 💼 Box Plot Measures   

+ Min Score

  ```
  Min Score = MIN(StudentsPerformance[Score])
  Max Score = MAX(StudentsPerformance[Score])  
  Median Score = MEDIAN(StudentsPerformance[Score])
  Score IQR = [Score Pctile 75] -[Score Pctile 25]
  Score IQR 25-50 = [Median Score] - [Score Pctile 25]
  Score IQR 50-75 = [Score Pctile 75] - [Median Score]
  Score Pctile 25 = PERCENTILE.INC(StudentsPerformance[Score],0.25)
  Score Pctile 75 = PERCENTILE.INC(StudentsPerformance[Score], 0.75)
  Y axis max = [Max Score] * 1.1

  ```
 

  
  
  
  




