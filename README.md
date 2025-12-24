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

` Grade =    
SWITCH (   
TRUE (),    
[Score] >= 95, "O",    
[Score] >= 81, "A",    
[Score] >= 71, "B",    
[Score] >= 61, "C",    
[Score] >= 51, "D",    
[Score] >= 41, "E",    
"F"      
) `


### 🧬Data Modelling  




