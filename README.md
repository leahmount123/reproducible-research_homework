# Reproducible research: version control and R

## Assignment answers

Questions 1-3: https://github.com/leahmount123/logistic_growth

### Question 4

**(a)** This is what the appears when the code is executed:
![image](https://github.com/user-attachments/assets/2b6a1d41-7b0f-47b1-9260-3aad625ed6c7)

- When executed, the code shows 2 similar layout plots next to each other, but the contents are very different
- The code for both is identical, and each time, there are 500 steps in the walk
- Each plot depicts a random walk containing these 500 steps, going from a darker to a lighter blue
  - Each point is equivalent to 1 of the 500 steps
- The plots are very different from one another as the walks are completely random each time
   - Upon re-running the code, the plots completely change again
- Path 1: the walk is almost a spiral shape around the graph
- Path 2: the trajectory seems to increase in y and decrease in x across the walk

**(b)** When random numbers are generated in R, they are often *pseudorandom* numbers; if you set a seed for the random numbers, the output becomes reproducible. This uses the **set.seed()** function. Essentially, this assigns the reproducibility to an arbitrary integer, so when the seed is used, the output is reproducible.

**(c)** The edited code has been pushed to the main branch of this repo. It has updated the R script in the **question-4-code** folder.

**(d)** <img width="1372" alt="Screenshot 2024-12-08 at 20 16 13" src="https://github.com/user-attachments/assets/f390ea05-f829-4512-abbd-229b07699b43">

### Question 5

**Note:** According to the wording of the question, the allometric model says that *L* refers to the genome length **in nucleotides**. The raw data has the genome length in **kilobases**. I did the conversions (x1000) and found that to reach the correct scaling factor, exponent, and plot, it required the genome length to remain in kilobases. For this reason, I have not done the conversions in the questions.

In the case of these questions, the log base will be e.

**(a)** The data has 13 columns and 33 rows.

**(b)** A suitable transformation to fit a linear model for this data would be to log-transform both sides of the allometric equation.
- V = αL<sup>β<sup>
- logV = logαL<sup>β<sup>
- logV = logα + logL<sup>β<sup> 
- logV = βlogL + logα
- This is now a version of y=mx+c, a linear model

These transformations have been applied to the data in the code.

**(c)**

**Scaling factor (α) = exp(7.0748) ≈ 1182**
- In a linear model, logα is equivalent to the y-intercept of the line
- Upon doing a summary of the linear model, I found that logα = 7.0748
- Hence, α ≈ 1182, with a significant p-value of 2.28e-10
- This is the same scaling factor for dsDNA viruses as seen in the original paper

**Exponent (β) = 1.5152 ≈ 1.52**
- In a linear model, β is equivalent to the gradient of the line
- Upon doing a summary of the linear model, I found that β = 1.5152
- This is the same exponent for dsDNA viruses as seen in the original paper

**(d)** This is the figure that I encoded:
![image](https://github.com/user-attachments/assets/fef4faf4-3a79-4d0f-8d9d-ebb7bdac11e7)

The code I used for this plot is in the R script found in this repo.

**(e)** This is how you would find the estimated volume in nm<sup>3<sup>
- V = αL<sup>β<sup>
- V = 1182 * 300<sup>1.52<sup>
- V = 6,884,014.616
- V ≈ 6,884,015nm<sup>3<sup>

## Instructions

The homework for this Computer skills practical is divided into 5 questions for a total of 100 points. First, fork this repo and make sure your fork is made **Public** for marking. Answers should be added to the # INSERT ANSWERS HERE # section above in the **README.md** file of your forked repository.

Questions 1, 2 and 3 should be answered in the **README.md** file of the `logistic_growth` repo that you forked during the practical. To answer those questions here, simply include a link to your logistic_growth repo.

**Submission**: Please submit a single **PDF** file with your candidate number (and no other identifying information), and a link to your fork of the `reproducible-research_homework` repo with the completed answers (also make sure that your username has been anonymised). All answers should be on the `main` branch.

## Assignment questions 

1) (**10 points**) Annotate the **README.md** file in your `logistic_growth` repo with more detailed information about the analysis. Add a section on the results and include the estimates for $N_0$, $r$ and $K$ (mention which *.csv file you used).
   
2) (**10 points**) Use your estimates of $N_0$ and $r$ to calculate the population size at $t$ = 4980 min, assuming that the population grows exponentially. How does it compare to the population size predicted under logistic growth? 

3) (**20 points**) Add an R script to your repository that makes a graph comparing the exponential and logistic growth curves (using the same parameter estimates you found). Upload this graph to your repo and include it in the **README.md** file so it can be viewed in the repo homepage.
   
4) (**30 points**) Sometimes we are interested in modelling a process that involves randomness. A good example is Brownian motion. We will explore how to simulate a random process in a way that it is reproducible:

   a) A script for simulating a random_walk is provided in the `question-4-code` folder of this repo. Execute the code to produce the paths of two random walks. What do you observe? (10 points) \
   b) Investigate the term **random seeds**. What is a random seed and how does it work? (5 points) \
   c) Edit the script to make a reproducible simulation of Brownian motion. Commit the file and push it to your forked `reproducible-research_homework` repo. (10 points) \
   d) Go to your commit history and click on the latest commit. Show the edit you made to the code in the comparison view (add this image to the **README.md** of the fork). (5 points) 

5) (**30 points**) In 2014, Cui, Schlub and Holmes published an article in the *Journal of Virology* (doi: https://doi.org/10.1128/jvi.00362-14) showing that the size of viral particles, more specifically their volume, could be predicted from their genome size (length). They found that this relationship can be modelled using an allometric equation of the form **$`V = \alpha L^{\beta}`$**, where $`V`$ is the virion volume in nm<sup>3</sup> and $`L`$ is the genome length in nucleotides.

   a) Import the data for double-stranded DNA (dsDNA) viruses taken from the Supplementary Materials of the original paper into Posit Cloud (the csv file is in the `question-5-data` folder). How many rows and columns does the table have? (3 points)\
   b) What transformation can you use to fit a linear model to the data? Apply the transformation. (3 points) \
   c) Find the exponent ($\beta$) and scaling factor ($\alpha$) of the allometric law for dsDNA viruses and write the p-values from the model you obtained, are they statistically significant? Compare the values you found to those shown in **Table 2** of the paper, did you find the same values? (10 points) \
   d) Write the code to reproduce the figure shown below. (10 points) 

  <p align="center">
     <img src="https://github.com/josegabrielnb/reproducible-research_homework/blob/main/question-5-data/allometric_scaling.png" width="600" height="500">
  </p>

  e) What is the estimated volume of a 300 kb dsDNA virus? (4 points) 
