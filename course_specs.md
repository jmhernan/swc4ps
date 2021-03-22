# Software Carpentry for Public Sector Professionals

## Step 1: Brainstorming (The What?)

1. What problem(s) will participants learn how to solve (**Core Skills**)?
  * Learn to work with `.csv, .xlsx` and similar raw data files with `python` or `R`.
    * See: (Formating Data in Spreadsheets)[https://datacarpentry.org/spreadsheets-socialsci/] This might provide a clear jump-off location for a more tailored lesson. 
  *  Develop reproducible cleaning scripts. A contrast from the Data Carpentry lesson that uses (Open Refine)[https://datacarpentry.org/openrefine-socialsci/]
  * Exploratory data analysis (Similar to this but tailored to public sector folks?)[https://datacarpentry.org/r-socialsci/]
    * After learning how to work with "common file types", and loading data into preferred software tool, we can:
      * Data wrangling basics in preferred language.
      * Simple Data Viz.
      * Producing figures for reporting.
  * Reporting tools:
    * RMarkdown and Sweave
    * Python notebooks (not very familiar wth these...)
  * **Other Topics:**
    * SQL integration
    * STATA and SPSS support
## Step 2(a): Who is this course for?
1. What is the expected educational level of your audience? 
  * all sorts of levels, targeting data professionals in non-profit and government organizations.  
2. What type of exposure do your audience members have to the technologies you plan to teach?
  * Minimal experience with open source data software tools.
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

Link to [Learner profiles](https://cdh.carpentries.org/deciding-what-to-teach.html#learner-profiles). 

* **Learner-1**: *Anaya Multifocus* recieved an MA in Education Policy Analysis three years ago. She has worked as a data analyst for the past year in the non-profit education space. She has began a self-taught R curriculum and is interested in seeing how it can be incorporated into the work.
In Anaya's current role she is tasked with developing useful insights from education data using whatever tools she is most comfortable with. Anaya's team consists of her supervisor, who has a backgrouns in managing large data systems, and a data engineer who maintains their data warehouse. Historically, their previous work is all done using SQL, excel pivot tables, and Tableau for visualizations.

  When a new request comes in Anaya and the team work together to complete a request:
  1. Extract the right data from their MS-SQL database,
  2. use excel to summarize and explore, and 
  3. design an insightful visualization (if necessary using Tableu)
  4. Exporting the table or visualization as in a format that can be combined with some word processing for minor write-ups (e.g. `.jpg`)

  Anaya knows that `R` can be used to do a lot of these tasks, and has shared this with the team. Her supervisor is completely on-board and wants Anaya to lead and incorporate something that can be version controlled into their work flow. Anaya knows she needs a more formal introduction to `R` with a specific focus on how practitioners (non-researchers) do this on the ground. 

  This iteration of Software Carpentry will teach Anaya the basic workflow to automate these tasks using R by writing simple scripts to use data from SQL, do your analyses tasks using R and output a visualization that can be used directly as a deliverable or a sketch of something you want to do in Tableau. These analysis pipelines can then be used to address similar requests moving forward and you won't have to recreate everything from scratch as was the previous practice. 

* **Learner-2**: *Brin Eager* 

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
* Beginners course! Low entry-bar
* Install appropriate software on local machine.
## Step 4: Designing Challenges

## Step 5: How are the concepts connected? (Content Development)

**Change to Episodes and Lesson formulation as [seen here.](https://cdh.carpentries.org/our-curriculum-structure.html#episodes)

**Curriculum Description**

*Example: Whether it's prices in the stock market, the number of visitors to a website, or the population of rabbits in a forest, many phenomena that we'd like to model with statistics involved numbers tracked over time. In this course, you'll be introduced to the field of stochastic processes, an area of probability studying systems that change over time. You'll learn about common statistical models such as random walks, Poisson processes, and Markov chains, as well as being introduced to the exponential and gamma distributions. These provide the fundamentals for many statistical methods common in finance, biology, and many other fields.*

**Learning Objectives**

* Be introduced to statistical models often used to represent a system changing over time: **random walks**, **Poisson processes**, and **Markov chains**
* Learn about two new statistical distributions, the exponential and the gamma, that are important in modeling .
* Gain experience with probability concepts such as random variables, distributions, expected value, and variance
* Practice using simulation to understand and answer probability problems

**Prerequisites**

* If any link to SWC courses.