# *Feature Engineering in R* by *Jose Hernandez*

- Chapter 1: September 28 
- Chapter 2: October 19
- Chapter 3: November 2
- Chapter 4: November 16 
- Screencasts: December 7 
- Soft launch: December 21 

## Course development resources

You'll work on the `jose` branch which has a pull request already created to the `master` branch. Chester will review updates to the pull request prior to our meetings.

## Step 1: Brainstorming

1. What problem(s) will students learn how to solve?
* Students will learn to create additional features from existing raw features in the data.
* Students will learn how to increase the predictive power of algorithms by creating additional features from existing features in the raw data. 
2. What techniques or concepts will students learn?
* Domain expertise will facilitate the feature engineering discovery process.
* Beyond an ad-hoc process...This work lies between the raw data and modeling phase.
*  Techniques(bucketing, standard statistical transformations? i.e. centering.
3. What technologies, packages, or functions will students use?
* Data manipulation packages and munging, i.e. Tidyverse.
  * mutate() 
  * case_when()
  * etc.
* Logical operators (`ifelse()` statements)
* glm to fit regression models
4. What terms or jargon will you define?
- features
- variable
- one-hot encoding
- dummy-variable 
- mathematical transformations
- binning/bucketing
- feature crossing

5. What analogies or heuristics will you use?
* A cook improves a recipe by adding additional measured ingredients.
* In education data we usually have a grade level indicator by student; it sometimes makes better sense to change that information to ranges, i.e. Elementary, Middle, High School.
* Using census data you might want to predict income for example, you might want to bucket age groups instead of using raw age as a predictor. 
6. What mistakes or misconceptions do you expect?
* Data cleaning is not feature engineering.  
7. What datasets will you use?
* Census , public education data, text-data, UCI-data.
* Simulated data for examples.
## Step 2: Who is this course for?
- **Unaware Umberto**: This course would be dificult for Unaware Umberto without some sort of introductory courses both in R under his belt.
- **Starting Sindhu:** This course would be manageable after her two initial R courses.  In order to get the full benefit of the course it would be recommended that she take for example, "Introduction to Machine Learning in R" first. You need some basic understanding of the model building process.
- **Coder Chen:** This course would be perfect for Chen and her team.  As they try to create insights from a lot of data, creating features from scratch will prove to be a useful skill. In terms of the statistical background, a basic understanding of general statistics is required and the more specific concepts will be discussed within the context of feature engineering.
- **Mathematical Martha:** Martha would enjoy some content of this course (specifically when mathematical transformations are discussed).  This course will be useful as Martha explores statistical modeling and machine learning courses. Feature engineering is a good concept to understand well if you are to become a Data Scientist.  
- **Advanced Alex:** Alex seems to be on a mission to enhance his python skills.  The concepts in general will be program agnostic, so I can totally see someone like Alex take this course (if not available in python) and replicating using python.  If Alex is only interested in courses that use python, then this course might not be the one for him.

**Older**

* Yngve: Yngve is the perfect target student for this course.  It’s a course designed to enhance your model building skills in R, as well as give you hands-on experience with creating features from large datasets.  This course could help Yngve, improve and create actionable insights in his day-today work through feature engineering. 
* Anya: This course would be great for Anya in terms of teaching her how to create features to analyse her telecom traffic data, if she could pair it with an intro to R (which she should grasp quickly) considering her programming background. 
* Thanh: Thanh could leverage this course to help him test and inform the different special education approaches currently being implemented by creating useful features from data.  This course will level-up his everyday use of statistical methods (specifically model building) and introduce him to other uses of R for data analyses.   
* Mohan: This course might not work for Mohan since its intended to build on previous knowledge of Machine Learning and Statistics.
## Step 3: What will learners do along the way?

Exercises should be no more than 12 lines of code (including comments) with no more than 4 bullet point instructions. In addition, exercises should take no more than 5 seconds to run on the DataCamp platform.

### Exercises for chapter 1 - Lesson 1 

### Mapping string/categorical values
Raw data represented in strings can contain rich information.  Imagine you are exploring the data on discipline infractions, along with numerical features like the number of days student was suspended. Machine learning and statistical models can't learn from strings directly, we use feature engineering to convert these string columns to numeric values.
  
**Example 1: Converting string data to numeric: Dummy-coding (one v.s. all others)**

To do most of the data processing steps, we will rely on various libraries from the `tidyverse`, specifically we will be using `dplyr` and its `mutate()` function in combination with R native functions in this example, to do most of our variable manipulations. **Instructions:** Using the discipline log data and the column `infraction`, create a numeric feature that captures only individuals that were "fighting". 

- Import the data + libraries.
- Summarize your new feature in a meaningful way.

**Skills**
- Learn how to convert string data to numeric by using 'one vs all others' encoding. 

 **Solution**
1. Represent the given string column as a binary vector:
- Only one element in the vector (that represents your specific category) is set to the value of `1`.
- All other elements are set to `0`.
2. The length of this new vector has to be equal to the number of elements in the original. 

```r
new.c  <- df %>% 
  mutate(infraction_fighting = ifelse(infraction == 'fighting', 1, 0))

table(new.c$infraction_fighting)

```
**Example 2: Converting string data to numeric: One-hot encoding**

The `infraction` column contains several inputs of categorical data belonging to the different categories of infractions students commit. We want to represent each one as individual columns to use on our model.  This will help us understand the unique contribution of each class of infraction. **Instructions:** Represent *all* categories with one boolean column for each category.

- Add as a new column to existing dataframe.
- The conditional function `ifelse()` might be useful here.
  
**Skills**
- Learn about representing catgories as seperate boolean values. 

**Solution**
- Each new column is it's own boolean repreentation:
  * For "fighting": Was the infraction "fighting"?
  * For "alcohol": Was the infraction "alcohol"?
  * .
  * .
  
```r
new.c  <- df %>% 
  mutate(infraction_fighting = ifelse(infraction == 'fighting', 1, 0),
         infraction_academic = ifelse(infraction == 'academic dishonesty', 1, 0),
         infraction_failure = ifelse(infraction == 'failure to cooperate', 1, 0),
         infraction_disruptive = ifelse(infraction == 'disruptive conduct', 1, 0),
         infraction_minor = ifelse(infraction == 'minor incident', 1, 0),
         infraction_alcohol = ifelse(infraction == 'alcohol', 1, 0)
          )
```   
### Example 3 (with multiple-steps): Converting string/ordinal data to numeric: Binning/Bucketing 
In this exercise we will be grouping ranges of an ordinal variable into meaningful groups that represent different classes. This process can be informed both by doing data exploration or by understanding some nuances unique to what the data represent. For example, in our dta we have an ordinal feature representing the current grade of the student, where `0` represent "kindergarten" and `12` represent high school senior year. 
- We have prior knowledge that the type of school a student goes to (i.e. `"Elementary School"`, `"Middle School"`, and `"High School"`) is more informative than the specific grade a student is in. 

- How could we create a feature that captures the school types (i.e. `"Elementary School"`, `"Middle School"`, and `"High School"`) using the `grade` column?

#### Step 1: Create meaningful groupings using the numeric column `grade` that represent the school type classes.

**Skills**
- Numeric to categorial mappings that are more informative and incorportes data insights not obvious in our data.
 
**Solution**
```r
new.g <- df %>% 
  mutate(sch_level2 = case_when(grade <= 5 & grade >= 0 ~ "elementary_school",
                                grade <= 8 & grade >= 6 ~ "middle_school",
                                grade <= 12 & grade >=  9 ~ "high_school"))
```

#### Step 2: Create separate columns representing the each school type.

**Skills**
- Use previously mastered skill

```r
new.g <- df %>% 
  mutate(elementary = ifelse(sch_level2 == "elementary_school",1,0),
         middle = ifelse(sch_level2 == "middle_school",1,0),
         highschool = ifelse(sch_level2 == "high_school",1,0))
```


### Other exercises

- Grouping Sparse Classes: **Link to Sample Code**
  - Often times when you have categorical data with a large number of potential classes there will be some that will have few observations.  This can be problematic and can potentially lead to over-fitting. 
  - Learn to combine classes with little signal.
  - Learn to combine similar classes. 

- Date and time feature extraction: **Link to Sample Code**
  - Often times you will have time-stamps as variables, although the time-stamp cannot be used directly in a model, useful indicators can be extracted.
  - Using packages like `lubridate` migh be helpful here and student can choose to apply any of the previosly learned methods to create features.

- Feature Crossing: **Link to Sample Code**
  - Often times you will want to combine information from multiple variables.

## Step 4: How are the concepts connected? (Course outline)

A course is made up of four chapters. Each chapter is made up of three or four lessons. A lesson is a short 2-5 minute video
covering the content our students will quiz themselves on in 2-4 multiple choice or interactive exercises to follow. Thus, a lesson is a short video followed by 2-4 exercises. The first chapter is free on all DataCamp courses and is a spot to really sell your course to encourage students to continue on it and finish it. Chapter 1 is also the shortest chapter containing a maximum of 12 exercises (including videos) with Chapters 2, 3, and 4 containing at most 16 exercises (including videos).

### Chapter 1: Introduction to feature engineering

  - Lesson 1.1 - **Introduction to Feature Engineering** 
    - Set the tone for the course and situate where feature engineering lives in the modeling pipeline of projects.  
    - Emphasize the importance of knowing your data or having a link to someone that can help you better understand where your data comes from. 
    - Knowing what *is* and what *is not*, feature engineering.
  - Lesson 1.2 - **Creating meaningful variables that represent some discrete category**
    - This lesson will focus on a common practice in both statistical and machine learning modeling in which you represent discrete categories in a way that can be interpreted by the model.
    - We will introduce bucketing in combination with one-hot encoding to represent several meaningful categories in the model.
  
  - Lesson 1.3 - **How do we know this is a valuable practice**
    - A simple example on how adding more information (in the form of new variables) will improve your model in significant ways.
    - I will use simple linear regression for this example.
    - A simple exercise detailing what other columns of data are available but that are not quite ready to be used as-is in our current model.  For example, can the date/time stamp tell us something informative in this case?
     
### Chapter 2: Mapping/encoding of discrete, or categorical predictors


  - Lesson 2.1 - **Date and time feature extraction**
    - This lesson will focus on leveraging time information and encoding them in meaningful categorical values. For example, we might be able to extract "time of day" from a time-stamp (using something like `lubridate`), but would want to create "morning" "afternoon" and "evening" categories instead of using the numerical information. 
    - Another example, might involve creating a feature `age` using a column that has the participants date of birth.


  - Lesson 2.2 - **Creating dummy variables to capture several categories** 
    - Imagine you have a dicrete value with several classes and you wanted to capture them in some way in your model.
    - This will expand on the simple example used in the introductory chapter when we encoded a specific dicrete value to a binary class `1` representing the class we were interested in and `0` for everything else.  In this example we will create different columns with the `1`,`0` encoding representing each value in the discrete variable.
  
  - Lesson 2.3 - **Handling sparse classes**
    - This lesson will highlight how to determine if a measured variable has sparse calsses by both tabling and visualizing the variable of interest.
    - After that we will determine which classes to combine.
    - The classes will then be encoded to a numerical representation as before.
  
### Chapter 3: Techniques for numerical predictors

  - Lesson 3.1 - **Mathematical transformations 1**
    - This lesson will focus on log-transformations exploring data that is skewed.
    - This is important for modeling using linear functions.
  - Lesson 3.2 - **Mathematical transformations 2**
    - Box-Cox and Yeo Johnson transformation will be used to as a method to handle variables that are not normally distributed. Using the `caret` package.   
  - Lesson 3.3 - **Binning/Bucketing**
    - This chapter will focus on using both external information about the data as well as relying on the data exploration process to inform meaningful variable transformations. 
    - Using external information relevant to the measured variables: *we might have information that a numeric variable can be grouped into meaningful buckets.*
    - Using data exploration:  *we might look at the distribution of a specific variable and determine we only have signal at one of the tails (i.e. all occurances happen after a certain age)*
  ### Chapter 4: Creating new features from a combination of existing variables


  - Lesson 4.1 - **Feature crossing**
    - This lesson will focus on the potential to contribute to the predictive power of a model when you have a combination of two variables vs just having one or both separately.  For example, if we wanted to predict how likely someone would get suspended based on two features:
      - Behavior Type 
      - Time of Day
    - we would create a feature cross using these represent a joint representation of the combined features.   
    - This lesson will also consider cases were you have two numerical features you wish to cross.
  - Lesson 4.2 - **Pricipal Component Analysis (PCA) 1
    - Reasons to use PCA, the value of dimensionality reduction.
    - Exploring variable relationships (correlations via `corrplot`).
  - Lesson 4.3 - **Pricipal Component Analysis (PCA) 2**
    - How to compute PCA in R using `stats` package function `prcomp()`
    - How to/and what to use in your model.
  
The datasets are:

- **Link to Data**: pokemon data that contains pokemon types and various characteristics. Good candidate for feature crossing.
- `https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data`: census adult incomes. Useful for transformations and other feature creation examples. [See documentation](https://archive.ics.uci.edu/ml/datasets/census+income).
- `https://archive.ics.uci.edu/ml/machine-learning-databases/wine/wine.data`: Chemical analysis of wine grown in the same region in Italy, there are 13 variables of the contituents found in three types of wine.  This dataset is useful for the PCA analyses. [See documentation](https://archive.ics.uci.edu/ml/datasets/Wine). 
- **Link to Sample Code** synthetic student discipline log data for introductory examples.

## Step 5: Course overview

**Course Description**
  
Features Engineering helps you better uncover useful insights from your machine learning models. The model building process in Data Science is iterative and often times requires creating new features using existing variables that make your model more efficient. In this course you will explore different data sets to apply a variety of feature engineering techniques on both continuous and discrete variable representations.

**Learning Objectives**

- Learn about feature engineering and where it fits in the modeling pipeline;
- Learn how to create new features using discrete data;
- Learn how to create using new features using continuous data;
- Learn how to create new features using mathematical transformations on variables;
- Learn how to leverage PCA as a feature creation tool.

**DataCamp Course Prerequisites**

- Introduction to Tidyverse
- Supervised Learning in R: Regression
- Supervised Learning in R: Classification
- Correlation and Regression

