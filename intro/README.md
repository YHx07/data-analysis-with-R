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

11. Vapply and tapply. In this lesson, we'll learn how to use vapply() and tapply(), each of which serves a very specific purpose within the Split-Apply-Combine methodology.

- vapply() -- whereas sapply() tries to 'guess' the correct format of the result, vapply() allows you to specify it explicitly. If the result doesn't match the format you specify, vapply() will throw an error, causing the operation to stop. This can prevent significant problems in your code that might be caused by getting unexpected return values from sapply().

- dim()
- head()
- str()
- summary()

> table(flags$landmass)

 1  2  3  4  5  6 
31 17 35 52 39 20 

> table(flags$animate)

  0   1 
155  39 

- table(flags$landmass)
        1         2         3         4         5         6 
0.4193548 0.1764706 0.1142857 0.1346154 0.1538462 0.3000000 

12. Looking at Data.

- ls()
- read.csv()
- read.table()
- dim()
- nrow()
- ncol()
- object.size()
- names()
- head()
- tail()
- summary()
- table(plants$Active_Growth_Period)
- str()

13. Simulation. One of the great advantages of using a statistical programming language like R is its vast collection of tools for simulating random numbers.

- sample()
- LETTERS
- flips <- sample(x=c(0, 1), size=100, replace=TRUE, prob=c(0.3, 0.7))
- rbinom(n=100, size=1, prob=0.7) -- Each probability distribution in R has an r*** function (for "random"), a d*** function (for "density"), a p*** (for "probability"), and q*** (for "quantile").
- rnorm()
- rpois()
- replicate()
- cm <- colMeans()
- hist(cm)
- rexp()
- rchisq()
- rgamma()

---

1. Manipulating Data with dplyr

| In this lesson, you'll learn how to manipulate data using dplyr. dplyr is a fast and powerful R
| package written by Hadley Wickham and Romain Francois that provides a consistent and concise
| grammar for manipulating tabular data.
| One unique aspect of dplyr is that the same set of tools allow you to work with tabular data from
| a variety of sources, including data frames, data tables, databases and multidimensional arrays.
| In this lesson, we'll focus on data frames, but everything you learn will apply equally to other
| formats.
| As you may know, "CRAN is a network of ftp and web servers around the world that store identical,
| up-to-date, versions of code and documentation for R" (http://cran.rstudio.com/). RStudio
| maintains one of these so-called 'CRAN mirrors' and they generously make their download logs
| publicly available (http://cran-logs.rstudio.com/). We'll be working with the log from July 8,
| 2014, which contains information on roughly 225,000 package downloads.

- tbl_df()

- read.csv()
- dim()
- head()
- library(dplyr) -- load the package
- packageVersion("dplyr")
- rm()
- is.na()

According to the "Introduction to dplyr" vignette written by the package authors, "The dplyr philosophy is to have small functions that each do one thing well." Specifically, dplyr supplies five 'verbs' that cover most fundamental data manipulation tasks: select(), filter(), arrange(), mutate(), and summarize().

Five main data manipulation:

- select(cran, r_arch:country)
- filter()
- arrange() -- order the ROWS of dataframe so that column is in ascending order
- mutate() -- to create a new variable based on the value of one or more variables already in a dataset.
- summarize()

2. Grouping and Chaining with dplyr

- group_by()

- by_package <- group_by(cran, package)

| At the top of the output above, you'll see 'Groups: package', which tells us that this tbl has
| been grouped by the package variable. Everything else looks the same, but now any operation we
| apply to the grouped data will take place on a per package basis.

- summarize(by_package, mean(size))

| Instead of returning a single value, summarize() now returns the mean size for EACH package in
| our dataset.

- n() -- the total number of rows.
- n_distinct() -- the total number of unique rows
- mean() -- the mean value throw rows

- View()

chaining method:

...

- %>% (magrittr package)

cran %>%
  select(ip_id, country, package, size) %>%
  mutate(size_mb = size / 2^20) %>%
  filter(size_mb <= 0.5) %>%
  arrange(desc(size_mb))
  # Your call to arrange() goes here

3: Tidying Data with tidyr
readr, tidyr, dplyr package

The author of tidyr, Hadley Wickham, discusses his philosophy of tidy data in his 'Tidy Data' paper: http://vita.had.co.nz/papers/tidy-data.pdf

| Tidy data is formatted in a standard way that facilitates exploration and analysis and works
| seamlessly with other tidy data tools. Specifically, tidy data satisfies three conditions:
| 
| 1) Each variable forms a column
| 
| 2) Each observation forms a row
| 
| 3) Each type of observational unit forms a table

| The first problem is when you have column headers that are values, not variable names. I've
| created a simple dataset called 'students' that demonstrates this scenario. Type students to take
| a look.

- gather()

> students
  grade male female
1     A    5      3
2     B    4      1
3     C    8      6
4     D    4      5
5     E    5      5

> gather(students, sex, count, -grade)
   grade    sex count
1      A   male     5
2      B   male     4
3      C   male     8
4      D   male     4
5      E   male     5
6      A female     3
7      B female     1
8      C female     6
9      D female     5
10     E female     5

It's important to understand what each argument to gather() means. The data argument, students, gives the name of the original dataset. The key and value arguments -- sex and count, respectively -- give the column names for our tidy dataset. The final argument, -grade, says that we want to gather all columns EXCEPT the grade column (since grade is already a proper column variable.)

The second messy data case we'll look at is when multiple variables are stored in one column. Type students2 to see an example of this.

- separate()

| A third symptom of messy data is when variables are stored in both rows and columns. students3
| provides an example of this. Print students3 to the console.

- spread()

| readr is required for certain data manipulations, such as `parse_number(), which will be used in
| the next question.  Let's, (re)load the package with library(readr).

| The fourth messy data problem we'll look at occurs when multiple observational units are stored
| in the same table. students4 presents an example of this. Take a look at the data now.

> students4
    id  name sex class midterm final
1  168 Brian   F     1       B     B
2  168 Brian   F     5       A     C
3  588 Sally   M     1       A     C
4  588 Sally   M     3       B     C
5  710  Jeff   M     2       D     E
6  710  Jeff   M     4       A     C
7  731 Roger   F     2       C     A
8  731 Roger   F     5       B     A
9  908 Karen   M     3       C     C
10 908 Karen   M     4       A     A

| Our solution will be to break students4 into two separate tables.

| The fifth and final messy data scenario that we'll address is when a single observational unit is
| stored in multiple tables. It's the opposite of the fourth problem.

- bind_rows()
- contains()
