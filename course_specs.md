# Software Carpentry for Public Sector Professionals

## Step 1: Brainstorming (The What?)

1. What problem(s) will participants learn how to solve?
  * *Example: They'll learn the generative models behind several stochastic process models, and understand to simulate them with R functions.*
2. What techniques or concepts will participants learn?
  * *Example:In learning three new distributions, the **exponential**, **gamma**, and **uniform**, they'll reinforce the concept that (unlike the binomial) distributions can be continuous*
  * *They'll become more familiar with the use of simulation to understand probability models and answer questions about them.*
3. What technologies, packages, or functions will participants use?
  * *The distribution-related functions around the exponential, gamma, and uniform functions*
  * *The `sample`, `cumsum`, `replicate`, and `accumulate` functions*
4. What terms or jargon will you define?
  * *Random walk, Markov chain, transition matrix, waiting time, Poisson process, Poisson point process*
5. What analogies will you use to explain concepts?
  * Two people gambling repeatedly with a coin for a random walk
  * Randomly generated text in a Markov chain
  * A light bulb burning out for an exponential variable/Poisson process
  * Simulating trees in a forest for a spatial Poisson process

## Step 2(a): Who is this course for?

Link to [Learner profiles](https://cdh.carpentries.org/deciding-what-to-teach.html#learner-profiles). 

* **Learner-1**: Learner-1 is the only data analyst in a government organization and wants to leverage open source tools to conduct their work...
* **Learner-2**: Learner-2 is a data manager in theor organization...
* ...
## Step 2(b): Audience Definition Questions?
Link to [audience definition questions](https://cdh.carpentries.org/deciding-what-to-teach.html#audience-definition-questions)

*  What type of exposure do your audience members have to the technologies you plan to teach?
* What types of tools do they already use? 
* What are the pain points they are currently experiencing?
* What types of data does your target audience work with? What are the commonalities in the datasets your target audience will encounter?

## Step 3: How far will this course get its participants?

This could be similar to the last exercise of the course or a last exercise in a chapter.

**Last exercise in Chapter 2**: Write a function that simulates 100 steps from a Markov chain of words, given a `transition_matrix` with row and column names.

**Skills**: [Use this for reference](https://cdh.carpentries.org/deciding-what-to-teach.html#skills-list) 

* writing for loops (to create parameter lists)
* writing data to a file (e.g. parameter lists)
* writing reusable scripts
* creating a specific type of graphic programmatically
* customizing graphics to label them appropriately for a particular data set
* creating a version controlled repository for storing his parameter and output files
* pushing output files to his lab’s website programatically

**Last exercise in the course**: Write a function that, given a number of points, the width of a region, and the height of a region, generate that many points in a Poisson point process.

Use it to plot 50 points in the space of 10 x 10.

**Skills required**: 
**What will the participants need to have in order to be successful**
* Begginers course! Low entry-bar
* Install appropriate software on local machine.

## Step 4: What will the participants do along the way?

**Middle of chapter 2**: Generate three steps in a Markov chain given a transition matrix and starting state.

**Solution**:

```{r}
step2 <- sample(nrow(transition_matrix), 1, transition_matrix[state, ])
step3 <- sample(nrow(transition_matrix), 1, transition_matrix[state2, ])
step4 <- sample(nrow(transition_matrix), 1, transition_matrix[state3, ])
```

**Middle of chapter 4**: Randomly generate 100 events in a one-dimensional Poisson process with a rate of 3 per second by simulating exponential waiting times. Find the distribution of how many events happen in the first 2 seconds.

**Solution**:

```{r}
cumsum(rexp(100, 3))

replicate(1000, sum(cumsum(rexp(100, 3)) <= 2))
```

## Step 5: How are the concepts connected? (Curriculum outline)

**Change to Episodes and Lesson formulation as [seen here.](https://cdh.carpentries.org/our-curriculum-structure.html#episodes)

### Lesson 1: Random walks

* Episode 1.1 - **Random walks**: Imagine you were gambling with a friend, and betting on a coin. Each time you either lose one dollar or gain one dollar. This is a random walk: at any moment, it could go up or down one step.
  * You can simulate a step with `sample()`, and find the cumulative position with `cumsum()`.
  * You can plot this with `plot()`, which looks a bit like a stock price graph.
* Episode 1.2 - **Biased random walk**: So far the random walk has been symmetrical, with an equal probability of gaining or losing.
  * What if the game were a bit rigged: each time, you had a 51% chance of losing? This is similar to playing in a casino, where the casino has an advantage we call the "house edge".
  * Try a very large number of steps: watch it "plummet". In terms of casino games, this proves the old expression that "the house always wins".
* Episode 1.3 - **Properties of a random walk**: Where will a random walk end up after 10 steps? 100 steps?
  * Introduce `replicate()` for simulating it.
  * The end position looks like a normal distribution (bell curve), because of a mathematical result called the central limit theorem.
  * Mean and variance of the end position.
  
  ### Lesson 2: Markov chains

* Episode 2.1 - **Transition matrices**
  * A random walk is one case of a Markov chain: a process where the next step depends only on the current state. Example we'll return to: Markov chain of words.
  * Creating a transition matrix, here's what it means: each cell has probability of going from a particular state to another state
  * Two multiple choice questions: what is the probability of going from state 1 to 2 with this matrix?
* Episode 2.2 - **One step in a Markov chain**
  * `sample(2, 1, prob = transition_matrix[state, ])` lets you randomly step
  * Try it three times in a row
  * Introduce an "absorbing" state
* Episode 2.3 - **Accumulating steps in a chain**
  * Using the `purrr` accumulate function to add up states into a chain.
  * Notice how an absorbing state works.
* Episode 2.4 - **Example: Markov chain of words**
  * We're giving you a transition matrix of words. These were determined based on a set of newspapers
  * Simulate a series of words.

### Lesson 3: ...

### Lesson 4: ...

## Step 6: Curriculum overview

**Curriculum Description**

*Example: Whether it's prices in the stock market, the number of visitors to a website, or the population of rabbits in a forest, many phenomena that we'd like to model with statistics involved numbers tracked over time. In this course, you'll be introduced to the field of stochastic processes, an area of probability studying systems that change over time. You'll learn about common statistical models such as random walks, Poisson processes, and Markov chains, as well as being introduced to the exponential and gamma distributions. These provide the fundamentals for many statistical methods common in finance, biology, and many other fields.*

**Learning Objectives**

* Be introduced to statistical models often used to represent a system changing over time: **random walks**, **Poisson processes**, and **Markov chains**
* Learn about two new statistical distributions, the exponential and the gamma, that are important in modeling .
* Gain experience with probability concepts such as random variables, distributions, expected value, and variance
* Practice using simulation to understand and answer probability problems

**Prerequisites**

* If any link to SWC courses.