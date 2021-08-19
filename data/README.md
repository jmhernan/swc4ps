# Data directory 
The files are not being tracked through `git` but are the files that are being used to test a SQL database (postgres).  
Files:
|File|Description|Course Relevance|Location|
|---|---|---|---|
LEA Characteristics.csv| US school district directory with personnel contact information | Various data type columns that can be tricky (e.g. address fields, phone numbers)| `2017-18-crdc-data-corrected-publication 2/2017-18 Public-Use Files/Data/LEA/CRDC/CSV/LEA/`
Enrollment.csv| Enrollment numbers by school. | Numbers are broken up into race by gender columns + other categories. | `2017-18-crdc-data-corrected-publication 2/2017-18 Public-Use Files/Data/SCH/CRDC/CSV/`                                
School Characteristics.csv| Various school charecteristic `yes/no` flag columns| Text used instead of boolean or `1/0` encoding. | `2017-18-crdc-data-corrected-publication 2/2017-18 Public-Use Files/Data/SCH/CRDC/CSV/`         
School Expenditures.csv| School expenditures broken up by various categories | Might need to sum up various columns to make sense of a "total expenditure" by school. | `2017-18-crdc-data-corrected-publication 2/2017-18 Public-Use Files/Data/SCH/CRDC/CSV/`            
School Support.csv| School teacher FTE supports and certification. | More column manipulations to get total numbers. | `2017-18-crdc-data-corrected-publication 2/2017-18 Public-Use Files/Data/SCH/CRDC/CSV/`
Suspensions.csv| Number of suspensions by school. | Broken up by Race x Gender columns! Aggregation needed for totals. | `2017-18-crdc-data-corrected-publication 2/2017-18 Public-Use Files/Data/SCH/CRDC/CSV/`  