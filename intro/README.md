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

Basic Building Blocks. In this lesson, we will explore some basic building blocks of the R programming language.

- ?func
- c()

Workspace and Files. In this lesson, you'll learn how to examine your local workspace in R and begin to explore the relationship between your workspace and the file system of your machine.

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

Sequences of Numbers. In this lesson, you'll learn how to create sequences of numbers in R.

- 1:20
- seq()
- seq(along.with = my_seq)
- seq_along(my_seq)
- rep() |  times = 10, each = 10

Vectors. The simplest and most common data structure in R is the vector.

- tf <- c(0.5, 55, -10, 6) < 1
TRUE FALSE  TRUE FALSE
- paste(my_char, collapse = " ")
- paste("Hello", "world!", sep = " ")
- paste(1:3, c("X", "Y", "Z"), sep="")
- paste(LETTERS, 1:4, sep = "-")
- c(c(1,2,3), 4)

Missing Values. Missing values play an important role in statistics and data analysis. Often, missing values must not be ignored, but rather they should be carefully studied to see if there's an underlying pattern or cause for their missingness.

- NA
- c(44, NA, 5, NA) * 3
- rnorm(1000)
- sample(c(y, z), 100)
- is.na()
- sum(is.na(my_data))
- NaN = 'not a number'
- 0 / 0
- Inf - Inf

Subsetting Vectors. In this lesson, we'll see how to extract elements from a vector based on some conditions that we specify.

- x[1:10]
- x[!is.na(x) & x > 0]
- x[c(2, 10)]
- x[c(-2, -10)], x[-c(2, 10)]
- vect <- c(foo = 11, bar = 2, norf = NA)
- names(vect) <- c("foo", "bar", "norf")
- identical()

Matrices and Data Frames. In this lesson, we'll cover matrices and data frames. Both represent 'rectangular' data types, meaning that they are used to store tabular data, with rows and columns.

- dim()
- attributes()
- class()
- matrix()
- cbind()
- data.frame(patients, my_matrix)
- colnames(my_data) <- cnames

Logic. This lesson is meant to be a short introduction to logical operations in R.

- isTRUE()
- identical()
- xor()
- which()
- any()
- all()

9. Functions. Functions are one of the fundamental building blocks of the R language. They are small pieces of reusable code that can be treated like any other R object.

John Chambers, the creator of R once said:

To understand computations in R, two slogans are helpful: 

1. Everything that exists is an object.
2. Everything that happens is a function call.

- Sys.Date()
- mean(c(2, 4, 5))
- If you want to see the source code for any function, just type the function name without any arguments or parentheses.
- args()
- evaluate(function(x){x+1}, 6)
- paste
- func(arg1, arg2 = TRUE, ...).  
- paste (..., sep = " ", collapse = NULL). All arguments after an ellipses must have default values
- "unpack" arguments from an ellipses:
- - args <- list(...)
- - alpha <- args[["alpha"]]
- creating new binary operators: %[whatever]%
"%p%" <- function(left, right){ # Remember to add arguments!
  return(paste(left, right))
}
'I' %p% 'love' %p% 'R!'

10. Lapply and sapply. In this lesson, you'll learn how to use lapply() and sapply(), the two most important members of R's *apply family of functions, also known as loop functions.

Split-Apply-Combine strategy:

- lapply(list, func) -- takes a list as input, applies a function to each element of the list, then returns a list of the same length as the original one. Data frame is a list of vectors. The 'l' in 'lapply' stands for 'list'.
- sapply() -- allows you to automate process by calling lapply(), but then attempting to simplify (hence the 's' in 'sapply') the result for you. In general, if the result is a list where every element is of length one, then sapply() returns a vector. If the result is a list where every element is a vector of the same length (> 1), sapply() returns a matrix. If sapply() can't figure things out, then it just returns a list, no  different from what lapply() would give you.
- vapply()
- tapply()

Each of the *apply functions will SPLIT up some data into smaller pieces, APPLY a function to each piece, then COMBINE the results. More details in Hadley Wickham's Journal of Statistical Software paper titled 'The Split-Apply-Combine Strategy for Data Analysis'

- head()
- dim()
- viewinfo()
- class()
- range()
- unique()

- as.character(cls_list) -- since every element of the list returned by lapply() is a character vector of length one, cls_list can be simplified to a character vector.

- sum(flags$orange)
- flag_colors <- flags[, 11:17]
- sapply(flag_colors, sum)
- shape_mat <- sapply(flag_shapes, range)
- lapply(unique_vals, function(elem) elem[2])



