# PowerBI_Student_ Perfomance_Report   
A comprehensive PowerBI dashboard to help analyze student perfomance  for academic year 2023-2024    

![Dashboard Gif](https://github.com/user-attachments/assets/14ca1926-fb62-4cd8-ba1f-441b28a13511)


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
#### 💼 Custom SVG Measures For  

+ 🧮 Math Donut Chart
  
+ 📚 Reading Donut Chart  
  
+ ✍️ Writing Donut Chart using DAX

+ 🧑‍🎓 Student Score Bar Chart

### Visualization Creation  
1. 📇 Cards : To visualize the important metrics:( Total Number Of Students, Percentage number Of Male Vs Female Students and the average score ).

2. 📊 Clustered Column Chart : To visualize Grade Distribution by Gender.  

3. 📑 Table Visualization :  To visualize the top 5 students based on the average score value.
   
4. 💹 100% Stacked Bar Chart : To visualize the perfomance (Reading , Writing and Maths)  of students of different race and ethnicity.
   
5. 📊 Box Plot Chart  for a statistical overview of the students' perfomance segmented by demographic factors (gender, race/ethnicity) and socioeconomic indicators (parental education, lunch program status, and test preparation).

6. 📊 Scatter Plot to evaluate the correlation between  math and  reading skills while identifying the extent of which socioeconomic factor (lunch) varies with overall student perfomance.

### Insights   

In the academic year 2023 - 2024 , there's a total of 1, 009 students (48.3% Male, 51.7% Female) with an avereage score of 67.8.  The average score for the male gender is 65.9 while that of female gender is 69.6. 

The top performing subject overall  is Reading with a mean of 69. 1%  followed by Writing at 68.1% while Math had a mean of 66. 1% which shows small variance between the mean scores.
Reading and Writing are the top perfoming subjects for the female gender while the male gender perform highly in Maths compared to Reading and Writing. 


 

















  
  




  


 

  
  
  
  




