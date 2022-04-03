# Data analysis with R

## Task 1

We start diving into R with https://swirlstats.com

``` r
library("swirl")
swirl()
```

1.  R Programming: The basics of programming in R

    1.  R Programming
    2.  Take me to the swirl course repository!

2.  Regression Models: The basics of regression modeling in R

3.  Statistical Inference: The basics of statistical inference in R

4.  Exploratory Data Analysis: The basics of exploring data in R

5.  Don't install anything for me. I'll do it myself.

R Programming course:

    1: Basic Building Blocks      2: Workspace and Files        3: Sequences of Numbers    
    4: Vectors                    5: Missing Values             6: Subsetting Vectors      
    7: Matrices and Data Frames   8: Logic                      9: Functions               
    10: lapply and sapply         11: vapply and tapply         12: Looking at Data         
    13: Simulation                14: Dates and Times           15: Base Graphics 

In this lesson, we will explore some basic building blocks of the R programming language.

- ?func
- c()

In this lesson, you'll learn how to examine your local workspace in R and begin to explore the relationship between your workspace and the file system of your machine.

- getwd()
- setwd()
- ls()
- dir()
- args()
- dir.create() 
- list.files()
- file.create()
-- dir.create(file.path('testdir2', 'testdir3'), recursive = TRUE)
- file.rename()
- file.copy()
- file.exists()
- file.info()
- file.path()
- You can use the $ operator --- e.g., file.info("mytest.R")$mode --- to grab specific items.

In this lesson, you'll learn how to create sequences of numbers in R.

