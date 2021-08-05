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

Link to [Learner profiles](https://cdh.carpentries.org/deciding-what-to-teach.html#learner-profiles). 

### **Learner-1**: *Anaya* Has 1-2 years of Data Analyst experience in the public sector

Anaya received an MA in Education Policy Analysis three years ago. She has worked as a data analyst for the past year in the non-profit education space. She has began a self-taught R curriculum and is interested in seeing how it can be incorporated into the work. Anaya, has a lot of experience using SPSS and STATA to do statistical analyses and relies on those tools to do basic correlational analyses in her current role.
    
In Anaya's current role she is tasked with developing useful insights from education data using whatever tools she is most comfortable with. Anaya's team consists of her supervisor, who has a background in managing large data systems, and a data engineer who maintains their data warehouse. Historically, their work is all done using SQL, excel pivot tables, SPSS for correlational analyses and Tableau for visualizations.

When a new request comes in Anaya and the team work together to complete a request:
  1. Extract the right data from their MS-SQL database, 
  2. use excel to summarize and explore, and 
  3. design an insightful visualization (if necessary using Tableau)
  4. Exporting the table or visualization in a format that can be combined with some word processing for minor write-ups (e.g. `.jpg`)

Anaya knows that `R` can be used to do a lot of these tasks, and has shared this with the team. Her supervisor is completely on-board and wants Anaya to lead and incorporate something that can be version controlled into their work flow. Anaya knows she needs a more formal introduction to `R` with a specific focus on how practitioners (non-researchers) do this on the ground. 

This iteration of Software Carpentry will teach Anaya the basic workflow to automate these tasks, write reproducible SQL queries, use R to write scripts to do the analyses tasks and output a table or a visualization that can be used directly as a deliverable or a sketch of something you want to do in Tableau. These analysis pipelines can then be used to address similar requests moving forward and you won't have to recreate everything from scratch as was the previous practice. 

### **Learner-2**: *Brian* Entry level data analyst 

Brian received a BS in Sociology four years ago. He is currently working as a data analyst for the local city housing authority.  Brian has been using excel to do most of the data work in his current position.

The housing authorities typically put out seasonal internal reports summarizing their administrative log data of services being provided and who is signing up for them. Brian, provides detailed tables of service providers and user numbers these reports. Brian's supervisor then combines Brian's contributions into a word document and shares out as a PDF.

Their data is usually output by their intake system as very messy `.csv` files that have to be cleaned and processed by brian and his supervisor. Brian does all of the cleanup of the `.csv` files in excel and creates different pivot tables that are then used for the analysis/explore tasks. 

Brian is currently the only data analyst working directly with the supervisor, and is given a lot of autonomy in terms of what tools he uses to complete his work. Brian wants to learn how to use `R` and effectively incorporate it into his work. 

Software Carpentry can help Brian learn how to write scripts to automate some of the cleaning and number summarization tasks, and teach him how to use version control to manage different report iterations of similar data summary tasks. In addition, Brian will be exposed to `RMarkdown` and how the production of simple summary reports can be done in a seamless process, while combining his analysis scripts and his supervisors content knowledge in the write-up stage.   

### **Learner-3**: *Jesse* New "entry level" evaluator  
Jesse recently graduated from the UW with a MPA and has worked for the past year and a half as an evaluator with a medium sized non-profit.  She has good excel skills, and completed research methods training as part of her MPA that included some basic introductions to R, but most of her statistics training practical work was completed with Stata.  She has just been hired into basic evaluator/data analyst role in a local government human services department, where she is expected to work as part of a team partnering with contract officers and community partners to develop performance measures and continuous quality improvement projects for contracted community partners/service providers.

In her new role Jesse needs to use not just her existing well honed critical thinking, evaluation design, and excel skills. She also needs to develop new skills of using SQL to extract relevant data from administrative databases, programmatically read and tidy multiple messy Excel workbooks from providers, calculate performance measures that may have complicated rules defining numerators and denominators and aggregating across multiple dimensions, and finally produce reports, visualizations, or dashboards that can be easily understood by non-technical partners and can be efficiently reproduced on a recurring (daily/monthly/quarterly/yearly basis) and aligned to have stylistic similarities to other reports produced by other members of her team.

Jesse is happy to get in the weeds to talk about the nitty gritty of defining and implementing performance measures, but does not think of herself as a programmer, and doesn’t have a lot experience creating scripted reproducible workflows. She tends to think of coding as “a tech job” and not the kind of thing she set out to do as a career – focusing on community, clients, and improving outcomes is her motivation, learning to be a coder.

Key skills she needs to do her job that Software Carpentry can teach her include: writing readable and efficient SQL queries to create the targeted datasets she needs from large databases, methods to read in and programmatically extract tidy data out of messy excel workbooks, and using core tidyverse packages (`dplyr`, `tidyr`, `stringr`, `lubridate`) to create the aggregated data needed to create dashboards and reports.

A focus of the Software Carpentry training would be reinforcing strategies to improve reproducibility and reusability of code, to save effort for repeated and similar reporting tasks.

### **Learner-4**: *Mel* Data scientist transitioning from academia to human services department
Mel is an early career social scientist who has decided she would prefer to work in a more applied setting working with data closer to where it is created and can have an impact.  She is comfortable with complex and high-dimensional data, working primarily in R with maybe occasional Python to do advanced modeling and inferential statistics on data sets she has created by combining existing large datasets (that have been at least partly cleaned) from other public and private data sources.

In her new role, Mel is expected to help build and improve existing data pipelines within her new organization, support less technical colleagues (like Jesse) and do creative work to identify and develop new data projects that might provide insight for data-driven decision where previously the organization was not able to get high quality data.  In many cases, this work focuses on bringing together data from different data systems in order to provided targeted analysis and more effectively examine the interactions between different program areas.  To do this work, Mel needs to quickly make sense of complex and possibly poorly documented SQL databases, moving smoothly between SQL for data creation and extraction, and the more powerful analytic capabilities of R or Python.  She will likely need to develop efficient and reusable tools for linking records from administrative systems that do not have fixed unique identifiers, as well as also being able to quickly and efficiently parse challenging excel workbooks.  She also needs to be able to create data products (including new tables or views in a database) for colleagues to use as well as creating accessible dashboards and reports to communicate the findings and recommendations from complex data analyses to less technical partners who have extensive subject area expertise.

Mel is used to working independently and within computing and analytic frameworks where she has a lot of control (losing admin rights is a new experience for her!). She’s excited to do work that matters, but is also trying to navigate a world where expertise and priorities take a very different focus than what she was used to in the academic setting.

Key skills Mell needs to do her job that Software Carpentry can teach her include: writing readable and efficient SQL queries to create the targeted datasets she needs from large databases, which may include intermediate steps of creating views, temp tables, and/or stored procedures. She needs skills to link large datasets that require fuzzy or probabilistic linkage, as well as efficient methods to read in and programmatically extract tidy data out of messy excel workbooks.  She likely has the basic data transformation and aggregation skills already, but may be able to use additional support for functional programming and improving the reusability of her code.

### **Learner-5**: *Jackie* Senior level data manager transitioning from a for-profit company
Jackie is a senior level data manager at a for-profit company that has recently transition to the data non-profit sector. She is comfortable guiding a team in developing data warehouses to streamline reporting pipelines of business outcomes and metrics. She works primarily with SQL, is comfortable dealing with large data from various sources and combining them to address business needs. 

In this new role, Jackie is expected to design/build a scalable data infrastructure to address education equity gaps in a specific region using data from several public education clients and community based organizations. She is tasked with identifying data projects that highlight inequities in the system and making sure access to the right data is efficient. Historically, this non-profit has relied on excel to do most of their data work, Jackie will help design/build a relational database and will also be expected to support a group of analysts that range entry level to mid-career PhD level analysts. To provide support, Jackie needs to understand what tools are available to develop efficient analysis pipelines using tools like, `R` or `python` in addition to SQL. Her analysts do have varying exposure to using these tools but Jackie has never really used them for her work. Jackie will need to have a working understanding of how these tools work so that she can incorporate them into the design of the data infrastructure for this org.

Jackie knows the value of incorporating tools like `SQL`, `R` and `python` for indicator development to allow more in depth analysis of the data they have access to and is excited to support her staff in making a transition from relying exclusively on excel.

Key skills Jackie needs to do her job that Software Carpentry can teach her include: Understanding how to leverage tools like `R` or `python` to aid in the messy ETL process that sometimes includes different data formats (excel, csv). Exposure to tools that can help tidy data for the creation of dashboards and reporting.   

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
