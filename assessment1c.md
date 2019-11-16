HDAT9700: Assessment 1C - Chapters 6, 7 and 8
================
05 November 2019

### Submission instructions

This is an R Markdown document—an example of *literate programming*, an
approach which allows users to interweave text, statistical output and
the code that produces that output.

To complete your assignment:

  - Edit this file directly, interweaving text and R code as appropriate
    to answer the questions below. Remember to `Knit` the file to make
    sure everything is running smoothly. Detailed information on R
    Markdown is available
    [here](https://rmarkdown.rstudio.com/lesson-1.html), and there is a
    useful cheatsheet
    [here](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf).

  - Use git to `commit` changes you make in this repo locally.

  - `Push` the repo, together with this edited file and the
    corresponding `.md` file to GitHub Classroom.

You can `commit` and `push` as often as neccessary—your assessment will
be graded on the most recent version of your repo at the assessment due
date.

Good luck\!

-----

### Overview

In this assignment we are going to analyse the `Orthodont` data,
available in the `nlme` package. These data include longitudinal
information from a study at the University of North Carolina Dental
School. Investigators followed the growth of children from age 8 until
age 14. Every two years they measured the distance between the pituitary
and the pterygomaxillary fissure, two points that are easily identified
on x-ray exposures of the side of the head.

This data frame contains the following four variables:

  - **distance** A numeric vector of distances from the pituitary to the
    pterygomaxillary fissure (measured in mm). These distances are
    measured on x-ray images of the skull

  - **age** a numeric vector of ages of the subject (in years)

  - **Subject** A unique person identifier indicating the subject on
    which the measurement was made. The levels are labelled M01 to M16
    for the males and F01 to F13 for the females.

  - **Sex** a binary variable with levels Male and Female

As the `nlme` package is one of the core R packages, you don’t need to
separately install it. To get started, you just need to load it into the
workspace in R with `library(nlme)` command. We will also use the
function ggplot to produce figures. Load this into the workspace with
`library(gglopt2)`.

Please provide the R code needed to answer the following exercises as
well as your written answers to them.

-----

### Assignment

1.  Familiarise yourself with the Orthodont dataset.
    1.  How many rows (observations) are there in the dataset, and how
        many children are there in the dataset? \[3 marks\]
    2.  Provide frequencies (%) for the categories of the categorical
        variables, and median and 1st and 3rd quartiles for the
        continuous variables. \[3 marks\]
2.  In this assignment, we are interested in modelling the variable
    **distance** as a function of **age** and **sex**.
    1)  What is the multilevel structure of this dataset? \[3 marks\]
    2)  Age will be modelled as a random effect for the analysis. Why
        might this be appropriate? \[5 marks\]
    3)  Use the function `ggplot()` and the following code to produce a
        scatterplot of age by distance, separately for each sex.
        Summarise the relationship between distance, age and sex. \[3
        marks\]
    <!-- end list -->
    ``` r
    scatter <- ggplot(Orthodont, aes(age, distance, color= Sex))
    scatter + geom_point() + geom_smooth(method="lm", se=FALSE) + 
        facet_wrap(~Sex) + 
        labs(x = "Age (years)", y = " Distance (pituitary to pterygomaxillary fissure) (mm) ", colour= "Sex")
    ```
3.  We will now begin to build a regression model to further investigate
    the relationship between **distance**, **age** and **sex**. We would
    like to test the hypothesis that age and sex are significantly
    related to distance.
    1)  Create a single-level intercept-only model for distance. \[3
        marks\]
    2)  Create a variance-components (intercept only) model for distance
        with a random intercept. \[3 marks\]
    3)  Perform a likelihood ratio test to compare the goodness-of-fit
        of the two models in 3i) and 3b). \[3 marks\]
    4)  What proportion of the variation in distance is at the
        individual level? \[3 marks\]
    5)  In this study, is it justified to use a hierarchical model? \[3
        marks\]
4.  We will now incorporate the variable **age** into the model created
    in 3ii) above.
    1)  Create a longitudinal multilevel linear model with random
        intercept only to investigate the effect of age on distance
        (distance ~ age). \[3 marks\]
    2)  Now add a random slope to the variable age in the longitudinal
        multilevel linear model created in 4i). \[3 marks\]
    3)  Perform a likelihood ratio test to compare the goodness-of-fit
        of the two models in 4i) and 4ii). \[3 marks\]
    4)  What is the sign of the estimated covariance parameter from the
        random part of the model, and what does this suggest about the
        relationship between random intercepts and random slopes? \[6
        marks\]
    5)  Draw a plot to help assess whether the posterior estimates of
        the random intercepts and random slopes are normally
        distributed. \[6 marks\]
    6)  In this study, does the use of a random slope for age improve
        the goodness-of-fit of the model? \[3 marks\]
5.  In this exercise, we will test whether the relationship between
    **age** and **distance** is improved by the use of a non-linear
    quadratic function in the regression model (i.e. a growth curve
    model).
    1)  Based on your results in section 4 above, which model will you
        use as the basis for your growth curve model? **Justify your
        choice** \[3 marks\]
          - Random intercept only (4i)?
        
          - Random intercept and slope (4ii)?
    2)  Now perform a growth curve analysis by adding the term `age^2`
        to the model you have selected in 5i). \[3 marks\]
    3)  Use the anova() function to perform a likelihood ratio test to
        compare the goodness-of-fit of the two models: 5ii) and either
        4i) or 4ii). \[3 marks\]
    4)  In this study, does the use of a non-linear quadratic term for
        age improve the goodness-of-fit of the model? \[3 marks\]
6.  For our final model, we will now add the fixed effect **sex** to our
    model of the relationship between distance and age.
    1)  Which model would you choose as your final random effects model?
        \[3 marks\]
          - Random intercept only with no quadratic term (linear model)
          - Random intercept only with quadratic term (growth curve
            model)?
          - Random intercept and slope with no quadratic term (linear
            model)
          - Random intercept and slope with quadratic term (growth curve
            model)?
    2)  Add the fixed effect **Sex** to the model chosen in 6i). Is
        there a significant relationship between distance and sex? \[3
        marks\]
    3)  Add an interaction term between the variables **sex** and
        **age**. Is this interaction significant? What does that mean?
        \[3 marks\]
7.  Based on your final model, write a paragraph to report the main
    findings of your analysis. Include the main statistical results
    supported by key values from the output (hint: use the intervals()
    function to obtain 95% intervals for your regression parameters).
    Provide a very brief clinical interpretation of your findings (hint:
    do the results support the hypothesis that there is a relationship
    between distance, age and sex?). \[20 marks\]

-----

### Student declaration

***Instructions: Indicate that you understand and agree with the
following three statements by typing an x in the square brackets below,
e.g. \[x\].***

I declare that this assessment item is my own work, except where
acknowledged, and has not been submitted for academic credit elsewhere
or previously, or produced independently of this course (e.g. for a
third party such as your place of employment) and acknowledge that the
assessor of this item may, for the purpose of assessing this item: (i)
Reproduce this assessment item and provide a copy to another member of
the University; and/or (ii) Communicate a copy of this assessment item
to a plagiarism checking service (which may then retain a copy of the
assessment item on its database for the purpose of future plagiarism
checking).

  - \[ \] I understand and agree

I certify that I have read and understood the University Rules in
respect of Student Academic Misconduct.

  - \[ \] I understand and agree

I have a backup copy of the assessment.

  - \[ \] I understand and agree
