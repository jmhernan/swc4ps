# Software Carpentry for Public Sector Professionals

## Step 1: Brainstorming (The What?)

1. What problem(s) will participants learn how to solve (**Core Skills**)?

**Reproducible methods to create analysis-ready data:**
  * Learn to work with `.csv, .xlsx` and similar raw data files with `python` or `R`.
    * Reading in data; especially complex Excel files with whitespace layouts and multiple sheets
    * Writing data frames to formatted Excel
    * (I (Carolina) would personally spend less time teaching skills *in Excel* for spreadsheet design such as what is covered in (Formatting Data in Spreadsheets)[https://datacarpentry.org/spreadsheets-socialsci/] -- My experience is that people mostly come in with pretty good Excel skills and need more support leaving Excel for script based data manipulations environments)
  *  Develop reproducible cleaning scripts in `R` or `python`. A contrast from the Data Carpentry lesson that uses (Open Refine)[https://datacarpentry.org/openrefine-socialsci/]
    *  Date management (with `lubridate` in `R`)
    *  String cleaning (with `stringr` in `R`)
    *  Using `dplyr` and `tidyr` functions to modify a dataframe to construct variables and reshape data
    *  Understanding concepts of tidy data - thinking about appropriate dimensionality depending on reporting expectations/unit of analysis
  *  Working with SQL
    * Writing SELECT queries
    * SQL query integration with R using `DBI` (introducing concept of ODBC - not sure how implementing this will work in practice in a lesson context, but for folks working in a Microsoft-centered government office understanding ODBC rather than direct connections to e.g. PostgreSQL is crucial)
  * Bonus topic: Record Linkage - this is a hugely common need in human services at least, introducing increasingly flexible concepts and tools for linking data sets is really important - that said it may be too technically complicated to cover as part of a Software Carpentry lesson.:
    * basic exact joins with `dplyr`
    * fuzzy joins with `fuzzyjoin` (requires introducing basic string distance concepts)
    * "easy" probabilistic matches using `RecordLinkage` - includes introducing concepts of blocking
  
  **Reproducible methods for analysis and reporting**
After learning how to work with "common file types", and loading data into preferred software tool, we can:

  * Data exploration and reporting
    * Basic data summaries - min/max, valid values etc - making sure data has loaded/transformed correctly
    * Aggregate calculations - constructing measures:
      * `dplyr` `group_by` combined with mutate and/or summarize to create numerator/denominator measures and aggregated summary data
      * understanding operations across columns in tidyverse (`across()` functionality)
    * Simple Data Vizualization (with `ggplot`)
    * Writing functions for repeated aggregation actions or visualization functions (reducing copy-paste and improving consistency across reports/measures)
  * Reporting tools:
    * RMarkdown ---and Sweave--- (I don't find Sweave to be as helpful in my work context - typicaly relly on Rmarkdown alone)
    * Flexdashboard and plotly
    * Python notebooks (not very familiar wth these...)
  
  * **Other Topics:**
    * SQL integration
    * STATA and SPSS support
    * 
## Step 2(a): Who is this course for?
1. What is the expected educational level of your audience? 
  * Minimum complete BA, otherwise may be all over the place; many will have at least a master's degree; targeting data professionals in non-profit and government organizations.  
2. What type of exposure do your audience members have to the technologies you plan to teach?
  * Minimal experience with open source data software tools.  Good basic data literacy and numeracy (e.g. competent Excel skills, understands concepts of measurement and reporting)
3. What types of tools do they already use?
  * Works with data at some capacity (excel files --> SQL)
  * Might heavily rely on proprietary software to conduct work.
  * Some R or Python.
4. What are the pain points they are currently experiencing?
  * Unable to reproduce external data requests or ETL procedures currently being used in-house. 
  * Reporting is not reproducible or version controlled. 
  * data tables and figures are not versioned controlled.
5. What types of data does your target audience work with? What are the commonalities in the datasets your target audience will encounter?
  * Administrative data containing user logs. 
  * Programmatic data and logs containing geographical and aggregated information of program and clients. 
  * Large complex administrative data sets containing relational data about programs, users, services, and providers
  * Excel workbooks created or maintained by partners sometimes within and other times outside the target audience organization.

Link to Public Sector [Learner profiles](hhttps://docs.google.com/document/d/18ocOc-QJHneEBk3Y1gs6esFltp4XAP8QI-UuTHmwXAY). 

Link to [audience definition questions](https://cdh.carpentries.org/deciding-what-to-teach.html#audience-definition-questions)

## Step 2(b): Background Knowledge and Goals of Learners?

* What type of exposure do your audience members have to the technologies you plan to teach?
* What types of tools do they already use? 
* What are the pain points they are currently experiencing?
* What types of data does your target audience work with? What are the commonalities in the datasets your target audience will encounter?

## Step 3: Defining the skills that this lesson will focus on.

**Skills**: [Use this for reference](https://cdh.carpentries.org/deciding-what-to-teach.html#skills-list) 

**Skills required**: 
**What will the participants need to have in order to be successful**
* Beginners course! Low entry-bar. Carolina note: I would actually adjust this upward - they should have at least a working knowledge of excel and experience using data to construct measures. It's a beginners course in that they don't need to have any coding experience.
* Install appropriate software on local machine.
## Step 4: Designing Challenges

## Step 5: How are the concepts connected? (Content Development)

**Change to Episodes and Lesson formulation as [seen here.](https://cdh.carpentries.org/our-curriculum-structure.html#episodes)

**Curriculum Description**

*Example: Whether it's prices in the stock market, the number of visitors to a website, or the population of rabbits in a forest, many phenomena that we'd like to model with statistics involved numbers tracked over time. In this course, you'll be introduced to the field of stochastic processes, an area of probability studying systems that change over time. You'll learn about common statistical models such as random walks, Poisson processes, and Markov chains, as well as being introduced to the exponential and gamma distributions. These provide the fundamentals for many statistical methods common in finance, biology, and many other fields.*

**Learning Objectives**


**Prerequisites**

* If any link to SWC courses.
