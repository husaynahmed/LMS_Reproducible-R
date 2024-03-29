Introduction to R, Session 1
========================================================
author: MRC LMS Bioinformatics Core
date: https://lmsbioinformatics.github.io/MRCLMSBioinfo/LMStraining.html
width: 1440
height: 1100
autosize: true
font-import: <link href='http://fonts.googleapis.com/css?family=Slabo+27px' rel='stylesheet' type='text/css'>
font-family: 'Slabo 27px', serif;
css:style.css

Overview
========================================================

- [Background to R](#/background)
- [Data types in R](#/datatypes)
- [Reading and writing data in R](#/reading)
- [Loading libraries](#/libraries)

Materials.
========================================================
id: materials

All prerequisites, links to material and slides for this course can be found on github.
* [Reproducible-R](https://lmsbioinformatics.github.io/LMS_Reproducible-R/)

Or can be downloaded as a zip archive from here. 
* [Download zip](https://lmsbioinformatics.github.io/LMS_Reproducible-R/zipball/master)

Materials. - Presentations, source code and practicals.
========================================================

Once the zip file in unarchived. All presentations as HTML slides and pages, their R code and HTML practical sheets will be available in the directories underneath.

* **presentations/slides/**
Presentations as an HTML slide show.
* **presentations/singlepage/** 
Presentations as an HTML single page.
* **presentations/rcode/**
R code in presentations.
* **exercises/**
Practicals as HTML pages. 
* **answers/**
Practicals with answers as HTML pages and R code solutions. 

Set the Working directory
========================================================

Before running any of the code in the practicals or slides we need to set the working directory to the folder we unarchived. 

You may navigate to the unarchived Reproducible-R folder in the Rstudio menu

**Session -> Set Working Directory -> Choose Directory**

or in the console.


```r
setwd("/PathToMyDownload/Reproducible-R")
# e.g. setwd("~/Downloads/Reproducible-R")
```


Background to R
===============
type:section
id: background

What is R?
========================================================

**R** is a scripting language and environment for **statistical computing**.


Developed by [Robert Gentleman](https://gist.github.com/colliand/d6d4ff42a9124ca38bed8d90136f70f5) and [Ross Ihaka](https://www.stat.auckland.ac.nz/~ihaka/). 


Inheriting much from **S** (Bell labs).

- Suited to high level data analysis
- Open source & cross platform
- Extensive graphics capabilities
- Diverse range of add-on packages
- Active community of developers
- Thorough documentation

What is R to you?
========================================================

**R** comes with excellent "out-of-the-box" statistical and plotting capabilities.


**R** provides access to 1000s of packages ([CRAN](http://cran.r-project.org/)/[MRAN](http://mran.revolutionanalytics.com/)/[R-forge](https://r-forge.r-project.org/)) which extend the basic functionality of R while maintaining high quality documentation.


In particular, [Robert Gentleman](http://www.gene.com/scientists/our-scientists/robert-gentleman) developed the **[Bioconductor](http://bioconductor.org/)** project where 100's of packages are directly related to computational biology and analysis of associated high-throughput experiments.
***

![alt text](imgs/RCitations.jpeg)

How to get R?
========================================================
left: 50%

Freely available from [R-project website](http://cran.ma.imperial.ac.uk/).

RStudio provides an integrated development environment (IDE) which is freely available from [RStudio site](http://www.rstudio.com/)


***We will be using RStudio and R already installed on your machines.***

***
![alt text](imgs/cran.jpeg)
![alt text](imgs/rstudio.jpeg)

A quick tour of RStudio
========================================================
left: 30%
Four main panels
- Scripting panel
- R interface
- Environment and history
- Files, directories and help


**Let's load RStudio and take a look**
***

![alt text](imgs/rstudioBlank.jpeg)


Data types in R
========================================================
id: datatypes
type: section

- Simple calculations
- Variables
- Vectors
- Lists
- Matrices
- Data frames



Simple Calculations 
========================================================
type: subsection
id:simplecalc
At its most basic, **R** can be used as a simple calculator.

```r
> 3+1
```

```
[1] 4
```

```r
> 2*2
```

```
[1] 4
```

```r
> sqrt(25)-1
```

```
[1] 4
```

Using functions.
========================================================

The **sqrt(25)** demonstrates the use of functions in R. A function performs a complex operation on it's arguments and returns the result.

In R, arguments are provided to a function within the parenthesis -- **( )** -- that follows the function name. So **sqrt(*ARGUMENT*)** will provide the square root of the value of ***ARGUMENT***.

Other examples of functions include **min()**, **sum()**, **max()**. 

Note multiple arguments are separated by a comma.


```r
min(2,4,6)
```

```
[1] 2
```

```r
sum(2,4,6)
```

```
[1] 12
```

```r
max(2,4,6)
```

```
[1] 6
```

Using functions.
========================================================

R has many useful functions "built in" and ready to use as soon as R is loaded.

An incomplete, illustrative list can be seen [here](http://www.statmethods.net/management/functions.html) 

In addition to R standard functions, additional functionality can be loaded into R using libraries. These include specialised tools for areas such as sequence alignment, read counting etc.

If you need to see how a function works try **?** in front of the function name.

```r
?sqrt
```


Lets run [**?sqrt**](https://stat.ethz.ch/R-manual/R-devel/library/base/html/MathFun.html) in RStudio and look at the help.

Using functions (Arguments have names and order)
========================================================

With functions such as min() and sqrt(), the arguments to be provided are obvious and the order of these arguments doesnt matter.


```r
min(5,4,6)
```

```
[1] 4
```

```r
min(6,4,5)
```

```
[1] 4
```

Many functions however have an order to their arguments.
Try and look at the arguments for the dir() function using [?dir](https://stat.ethz.ch/R-manual/R-devel/library/base/html/list.files.html).

```
?dir
```
Using functions (Setting names for arguments)
========================================================

Often we know the names of arguments but not necessarily their order.
In cases where we want to be sure we specify the right argument, we provide names for the arguments used.


```r
dir()
dir(full.names=T)
```

This also means we don't have to copy out all the defaults for arguments preceeding it.


```r
dir(full.names=T)
# Is equivalent to...
dir(".",NULL,FALSE,T)
```


Variables (1/2)
========================================================

As with other programming languages and even graphical calculators, **R** makes use of **variables**.

A **variable** stores a value as a letter or word.

In **R**, we make use of the assignment operator **<-** 

```r
x <- 10
```
Now **x** holds the value of 10

```r
x
```

```
[1] 10
```

Variables.(2/2)
========================================================


```r
x
```

```
[1] 10
```
Variables can be altered in place

```r
x <- 20
x
```

```
[1] 20
```
Variables can be used just as the values they contain.

```r
x + sqrt(25)
```

```
[1] 25
```
Variables can be used to create new variables

```r
y <- x + sqrt(25)
y
```

```
[1] 25
```

Vectors.(1/15)
========================================================
id:combine
In **R** the most basic variable or data type is a **vector**. A vector is an ordered collection of values. The x and y variables we have previously assigned are examples of a vector of length 1.


```r
x
```

```
[1] 20
```

```r
length(x)
```

```
[1] 1
```

To create a multiple value vector we use the function **c()** to *combine* the supplied arguments into one vector.


```r
x <- c(1,2,3,4,5,6,7,8,9,10)
x
```

```
 [1]  1  2  3  4  5  6  7  8  9 10
```

```r
length(x)
```

```
[1] 10
```

Vectors (2/15) - Creating vectors
========================================================
Vectors of continuous stretches of values can be created by the shortcut - **:**


```r
y <- 6:10
y
```

```
[1]  6  7  8  9 10
```

Other useful function to create stretchs of numeric vectors are **seq()** and **rep()**.
The **seq()** function creates a sequence of numeric values from a specified start and end value, incrementing by a user defined amount. The **rep()** function repeats a variable a user-defined number of times.



```r
seq(from=1,to=5,by=2)
```

```
[1] 1 3 5
```

```r
rep(c(1,5,10),3)
```

```
[1]  1  5 10  1  5 10  1  5 10
```

Vectors(3/15) - Indexing 
========================================================
id:indexingvectors
Square brackets **[]** identify the position within a vector (the **index**).
These indices can be used to extract relevant values from vectors.



```r
x
```

```
 [1]  1  2  3  4  5  6  7  8  9 10
```

```r
x[1]
```

```
[1] 1
```

```r
x[8]
```

```
[1] 8
```
Vectors(4/15) - Indexing 
========================================================

Indices can be used to extract values from multiple positions within a vector.


```r
x[c(1,6)]
```

```
[1] 1 6
```
Negative indices can be used to extract all positions except that specified


```r
x[-5]
```

```
[1]  1  2  3  4  6  7  8  9 10
```


Vectors(5/15) - Indexing and replacement
========================================================

We can use indices to modify a specific position in a vector


```r
x
```

```
 [1]  1  2  3  4  5  6  7  8  9 10
```

```r
x[5] <- -5
x
```

```
 [1]  1  2  3  4 -5  6  7  8  9 10
```

Indices can be specified using other vectors.


```r
y
```

```
[1]  6  7  8  9 10
```

```r
x[y] <- 0
x
```

```
 [1]  1  2  3  4 -5  0  0  0  0  0
```

Remember!
========================================================

Square brackets **[]**  for indexing

```r
x[1]
```

```
[1] 1
```

Parentheses **()**  for function argments.

```r
sqrt(4)
```

```
[1] 2
```

Vectors(6/15) - Arithmetic operations 
========================================================

Vectors in R can be used in arithmetic operations as seen with [variables earlier](#/simplecalc).
When a standard arithmetic operation is applied to vector, the operation is applied to each position in a vector.


```r
x <- c(1,2,3,4,5,6,7,8,9,10)
x
```

```
 [1]  1  2  3  4  5  6  7  8  9 10
```

```r
y <- x*2
y
```

```
 [1]  2  4  6  8 10 12 14 16 18 20
```

Multiple vectors can be used within arithmetic operations. 

```r
x+y
```

```
 [1]  3  6  9 12 15 18 21 24 27 30
```
Vectors (7/15) - Arithmetic operations  
========================================================

When applying an arithmetic operation between two vectors of unequal length, the shorter will be recycled.


```r
x <- c(1,2,3,4,5,6,7,8,9,10)
x
```

```
 [1]  1  2  3  4  5  6  7  8  9 10
```

```r
x+c(1,2)
```

```
 [1]  2  4  4  6  6  8  8 10 10 12
```


```r
x+c(1,2,3)
```

```
 [1]  2  4  6  5  7  9  8 10 12 11
```

Vectors (8/15) - Character vectors.
========================================================
id:namingvectors

So far we have only looked at numeric vectors or variables.

In R we can also create character vectors [again using **c()** function](#/combine). These vectors can be indexed just the same.


```r
y <- c("ICTEM","CommonWealth","Wolfson")
y[2]
```

```
[1] "CommonWealth"
```

Character vectors can be used to assign names to other vectors.


```r
x <- c(1:3)
names(x) <- y
x
```

```
       ICTEM CommonWealth      Wolfson 
           1            2            3 
```
Vectors (9/15) - Character vectors as names.
========================================================

These named vectors maybe indexed by a position's "name".

```r
x[c("ICTEM","Wolfson")]
```

```
  ICTEM Wolfson 
      1       3 
```
Index names missing from vectors will return special value "NA"

```r
x[c("Strand")]
```

```
<NA> 
  NA 
```

A note on NA values
====================

In R, like many languages, when a value in a variable is missing, the value is assigned a **NA** value.

Similarly, when a calculation can not be perfomed, R will input a **NaN** value.

- **NA** - Not Available.
- **NaN** - Not A Number.

**NA** values allow for R to handle missing data correctly but requires different handling than standard numeric or character values. We will illustrate an example handling **NA** values [later](#/nalast).

Vectors (10/15) - The unique() function
====================

The unique() function can be used to retrieve all unique  values from a vector.


```r
geneList <- c("Gene1","Gene2","Gene3","Gene4","Gene5","Gene1","Gene3")
unique(geneList)
```

```
[1] "Gene1" "Gene2" "Gene3" "Gene4" "Gene5"
```


Vectors (11/15). Logical vectors
========================================================

Logical vectors are a class of vector made up of TRUE/T or FALSE/F boolean values.


```r
z <- c(T,F,T,F,T,F,T,F,T,F) 
# z <-  c(TRUE,FALSE,TRUE,FALSE,TRUE,FALSE,TRUE,FALSE,TRUE,FALSE) 
z
```

```
 [1]  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE
```
Logical vectors can be used like an index to specify postions in a vector. TRUE values will return the corresponding position in the vector being indexed.


```r
x <- 1:10
x[z]
```

```
[1] 1 3 5 7 9
```


Vectors (12/15) - The %in% operator
====================

A common task in R is to subset one vector by the values in another vector.

The **%in%** operator in the context **A %in% B** creates a logical vector of whether values in **A** matches any values in of **B**.

This can be then used to subset the values within one character vector by a those in a second. 


```r
geneList <- c("Gene1","Gene2","Gene3","Gene4","Gene5","Gene1","Gene3")
secondGeneList <- c("Gene5","Gene3")
logical_index <- geneList %in% secondGeneList
logical_index
```

```
[1] FALSE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

```r
geneList[logical_index]
```

```
[1] "Gene3" "Gene5" "Gene3"
```

Vectors (13/15). Logical vectors from operators
========================================================

Vectors may be evaluated to produce logical vectors. This can be very useful when using a logical to index.

Common examples are:

- **==**  evaluates as equal.
- **>** and **<** evaluates as greater or less than respectively.
- **>=** and **<=** evaluates as greater than or equal or less than or equal respectively.


```r
x <- 1:10
x > 5
```

```
 [1] FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE
```

```r
x[x > 5]
```

```
[1]  6  7  8  9 10
```

Vectors (14/15). Combining logical vectors.
========================================================

Logical vectors can be used in combination in order to index vectors. To combine logical vectors we can use some common R operators.

- **&** - Requires both logical operators to be TRUE
- **|** - Requires either logical operator to be TRUE.
- **!** - Reverses the logical operator, so TRUE is FALSE and FALSE is TRUE.


```r
x <- 1:10
!x > 4
```

```
 [1]  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
```

```r
x > 4 & x < 7
```

```
 [1] FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE
```

```r
x > 4 | x < 7
```

```
 [1] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
```

Vectors (15/15). Logical vectors continued.
========================================================

Such combinations can allow for complex selection of a vector's values.

```r
x <- 1:10
x
```

```
 [1]  1  2  3  4  5  6  7  8  9 10
```

```r
x[x > 4 & x < 7]
```

```
[1] 5 6
```

```r
x[x > 4 & !x < 7]
```

```
[1]  7  8  9 10
```


Time for an exercise!
========================================================

Exercise on vectors can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/exercises/vector_exercise.html)

Answers to exercise.
========================================================

Answers can be found here  [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/vector_answers.html)

R code for solutions can be found here  [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/vector_answers.R)

Matrices (1/13) - Creating matrices
========================================================

In programs such as Excel, we are used to tables.

All progamming languages have a concept of a table. In **R**, the most basic table type is a **matrix**.

A **matrix** can be created using the ***matrix()*** function with the arguments of **nrow** and **ncol** specifying the number of rows and columns respectively.

```r
narrowMatrix <- matrix(1:10, nrow=5, ncol=2)
narrowMatrix
```

```
     [,1] [,2]
[1,]    1    6
[2,]    2    7
[3,]    3    8
[4,]    4    9
[5,]    5   10
```

```r
wideMatrix <- matrix(1:10, nrow=2, ncol=5)
wideMatrix
```

```
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10
```

Matrices (2/13) - Creating matrices
========================================================

By default when creating a matrix using the **matrix** function, the values fill the matrix by columns. To fill a matrix by rows the **byrow** argument must be set to TRUE.


```r
wideMatrix <- matrix(1:10, nrow=2, ncol=5)
wideMatrix
```

```
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10
```

```r
wideMatrixByRow <- matrix(1:10, nrow=2, ncol=5, byrow=TRUE)
wideMatrixByRow
```

```
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    2    3    4    5
[2,]    6    7    8    9   10
```

Matrices (3/13) - Finding dimensions
========================================================

To find dimensions of a matrix, the **dim()** function will provide dimensions as the row then column number while **nrow()** and **ncol()** will return just row number and column number respectively.

```r
dim(narrowMatrix)
```

```
[1] 5 2
```

```r
nrow(narrowMatrix)
```

```
[1] 5
```

```r
ncol(narrowMatrix)
```

```
[1] 2
```

Matrices (4/13) (Joining vectors and matrices)
========================================================

A matrix can be created from multiple vectors or other matrices.

**cbind()** can be used to attach data to a matrix as columns.

```r
x <- 1:10
y <- 11:20
z <- 21:22
newMatrix <- cbind(x,y)
newMatrix
```

```
       x  y
 [1,]  1 11
 [2,]  2 12
 [3,]  3 13
 [4,]  4 14
 [5,]  5 15
 [6,]  6 16
 [7,]  7 17
 [8,]  8 18
 [9,]  9 19
[10,] 10 20
```

***

**rbind()** functions to bind to a matrix as rows.

```r
newerMatrix <- rbind(newMatrix,z)
newerMatrix
```

```
   x  y
   1 11
   2 12
   3 13
   4 14
   5 15
   6 16
   7 17
   8 18
   9 19
  10 20
z 21 22
```

Matrices (5/13) - Joining incompatable vectors and matrices
========================================================

When creating a matrix using **cbind()** or **matrix()** from incompatable vectors then the shorter vector is recycled. 




```r
recycledMatrix2 <- matrix(1:5,ncol=2,nrow=3)
recycledMatrix2
```

```
     [,1] [,2]
[1,]    1    4
[2,]    2    5
[3,]    3    1
```
***
For **rbind()** function, the longer vector is clipped.

```r
recycledMatrix3 <- rbind(recycledMatrix2,c(1:5))
recycledMatrix3
```

```
     [,1] [,2]
[1,]    1    4
[2,]    2    5
[3,]    3    1
[4,]    1    2
```

Matrices (6/13) - Column and row names
========================================================

[As we have seen with vectors](#/namingvectors), matrices can be named. For matrices the naming is done by columns and rows using **colnames()** and **rownames()** functions.


```r
namedMatrix <- matrix(1:10,ncol=5,nrow=2)
colnames(namedMatrix) <- paste("Column",1:5,sep="_")
rownames(namedMatrix) <- paste("Row",1:2,sep="_")
namedMatrix
```

```
      Column_1 Column_2 Column_3 Column_4 Column_5
Row_1        1        3        5        7        9
Row_2        2        4        6        8       10
```

Information on matrix names can also be retreived using the same functions.

```r
colnames(namedMatrix)
```

```
[1] "Column_1" "Column_2" "Column_3" "Column_4" "Column_5"
```

```r
rownames(namedMatrix)
```

```
[1] "Row_1" "Row_2"
```


Matrices (7/13) - Indexing
========================================================
id:indexingmatrices

Selecting and replacing portions of a matrix can be done by **indexing** using square brackets **[]** much [like for vectors](#indexingvectors).

When indexing matrices, two values may be provided within the square brackets separated by a comma to retrieve information on a matrix position.

The first value(s) corresponds to row(s) and the second to column(s).

- ***myMatrix[rowOfInterest,columnOfInterest]***

```r
narrowMatrix
```

```
     [,1] [,2]
[1,]    1    6
[2,]    2    7
[3,]    3    8
[4,]    4    9
[5,]    5   10
```
Value of first column, second row

```r
narrowMatrix[2,1]
```

```
[1] 2
```

Matrices (8/13) - Indexing 
========================================================

Similarly, whole rows or columns can be extracted. Single rows and columns will return a vector. When multiple columns or row indices are specified, a matrix is returned. 


Values of second column (row index is empty!)

```r
narrowMatrix[,2]
```

```
[1]  6  7  8  9 10
```

Values of third row (column index is empty!)

```r
narrowMatrix[3,]
```

```
[1] 3 8
```

Values of second and third row (column index is empty!)

```r
narrowMatrix[c(2,3),]
```

```
     [,1] [,2]
[1,]    2    7
[2,]    3    8
```

Matrices (9/13) - Indexing by name
========================================================

As with vectors, names can be used for indexing when present


```r
colnames(narrowMatrix) <- paste("Column",1:2,sep="_")
rownames(narrowMatrix) <- paste("Row",1:5,sep="_")
narrowMatrix[,"Column_1"]
```

```
Row_1 Row_2 Row_3 Row_4 Row_5 
    1     2     3     4     5 
```

```r
narrowMatrix["Row_1",]
```

```
Column_1 Column_2 
       1        6 
```

```r
narrowMatrix["Row_1","Column_1"]
```

```
[1] 1
```

Matrices (10/13) Advanced indexing
========================================================

As with vectors, matrices can be subset by logical vectors

```r
narrowMatrix
```

```
      Column_1 Column_2
Row_1        1        6
Row_2        2        7
Row_3        3        8
Row_4        4        9
Row_5        5       10
```

```r
narrowMatrix[,1]
```

```
Row_1 Row_2 Row_3 Row_4 Row_5 
    1     2     3     4     5 
```

```r
narrowMatrix[,1] < 5
```

```
Row_1 Row_2 Row_3 Row_4 Row_5 
 TRUE  TRUE  TRUE  TRUE FALSE 
```
***

```r
narrowMatrix[narrowMatrix[,1] < 5,]
```

```
      Column_1 Column_2
Row_1        1        6
Row_2        2        7
Row_3        3        8
Row_4        4        9
```

Matrices (11/13) - Arithmetic operations.
========================================================

As with vectors, matrices can have arithmetic operations applied to cells,rows, columns or the whole matrix

```r
narrowMatrix
```

```
      Column_1 Column_2
Row_1        1        6
Row_2        2        7
Row_3        3        8
Row_4        4        9
Row_5        5       10
```

```r
narrowMatrix[1,1]+2
```

```
[1] 3
```

```r
narrowMatrix[1,]+2
```

```
Column_1 Column_2 
       3        8 
```

```r
mean(narrowMatrix)
```

```
[1] 5.5
```

Matrices (12/13) - Replacement
========================================================

As with vectors, matrices can have their elements replaced

```r
narrowMatrix
```

```
      Column_1 Column_2
Row_1        1        6
Row_2        2        7
Row_3        3        8
Row_4        4        9
Row_5        5       10
```

```r
narrowMatrix[1,1] <- 10
narrowMatrix[,2] <- 1
narrowMatrix
```

```
      Column_1 Column_2
Row_1       10        1
Row_2        2        1
Row_3        3        1
Row_4        4        1
Row_5        5        1
```
Matrices (13/13) -Matrices can contain only one data type
========================================================
id:onedatatype
Matrices must be all one type (i.e. numeric or character).

Here replacing one value with character will turn numeric matrix to character matrix.


```r
narrowMatrix[,2] *2
```

```
Row_1 Row_2 Row_3 Row_4 Row_5 
    2     2     2     2     2 
```

```r
narrowMatrix[1,1] <- "Not_A_Number"
narrowMatrix
```

```
      Column_1       Column_2
Row_1 "Not_A_Number" "1"     
Row_2 "2"            "1"     
Row_3 "3"            "1"     
Row_4 "4"            "1"     
Row_5 "5"            "1"     
```


```r
narrowMatrix[,2] *2
```

```
Error in narrowMatrix[, 2] * 2: non-numeric argument to binary operator
```

Time for an exercise!
========================================================

Exercise on matrices can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/exercises/matrices_exercise.html)

Answers to exercise.
========================================================

Answers can be found here  [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/matrices_answers.html)

R code for solutions can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/matrices_answers.R)


Factors (1/6) - Creating factors
========================================================

A special case of a vector is a **factor**.

Factors are used to store data which may be grouped in categories (categorical data).
Specifying data as categorical allows R to properly handle the data and make use of functions specific to categorical data.

To create a factor from a vector we use the **factor()** function. Note that the factor now has an additional component called **"levels"** which identifies all categories within the vector.


```r
vectorExample <- c("male","female","female","female")
factorExample <- factor(vectorExample)
factorExample
```

```
[1] male   female female female
Levels: female male
```

```r
levels(factorExample)
```

```
[1] "female" "male"  
```

Factors (2/6) - Summary() function
========================================================

An example of the use of levels can be seen from applying the **summary()** function to the vector and factor examples



```r
summary(vectorExample)
```

```
   Length     Class      Mode 
        4 character character 
```

```r
summary(factorExample)
```

```
female   male 
     3      1 
```


Factors (3/6) - Display order of levels
========================================================
In our factor example, the levels have been displayed in an alphabetical order. To adjust the display order of levels in a factor, we can supply the desired display order to **levels** argument in the **factor()** function call.


```r
factorExample <- factor(vectorExample,levels=c("male","female"))
factorExample
```

```
[1] male   female female female
Levels: male female
```

```r
summary(factorExample)
```

```
  male female 
     1      3 
```


Factors (4/6) - Nominal factors
========================================================
In some cases there is no natural order to the categories such that one category is greater than the other (nominal data).
In this case we can see that R is gender neutral.


```r
factorExample <- factor(vectorExample,levels=c("male","female"))
factorExample[1] < factorExample[2]
```

```
[1] NA
```
Factors (5/6) - Ordinal factors
========================================================

In other cases there will be a natural ordering to the categories (ordinal data). A factor can be specified to be ordered using the **ordered** argument in combination with specified levels argument.


```r
factorExample <- factor(c("small","big","big","small"),ordered=TRUE,levels=c("small","big"))
factorExample
```

```
[1] small big   big   small
Levels: small < big
```

```r
factorExample[1] < factorExample[2]
```

```
[1] TRUE
```

Factors (6/6) - Replacement
========================================================

Unlike vectors, replacing elements within a factor isn't so easy. While replacing one element with an established level is possible, replacing with a novel element will result in a warning.


```r
factorExample <- factor(c("small","big","big","small"))
factorExample[1] <- c("big")
factorExample
```

```
[1] big   big   big   small
Levels: big small
```

```r
factorExample[1] <- c("huge")
factorExample
```

```
[1] <NA>  big   big   small
Levels: big small
```

To add a new level we can use the levels argument.


```r
levels(factorExample) <- c("big","small","huge")
factorExample[1] <- c("huge")
factorExample
```

```
[1] huge  big   big   small
Levels: big small huge
```

Data frames (1/12) - Creating data frames 
=========================================================

[We saw that with matrices you can only have one type of data](#/onedatatype). We tried to create a matrix with a character element and the entire matrix became a character.

In practice, we would want to have a table which is a mixture of types (e.g a table with sample names (character), sample type (factor) and survival time (numeric))

In R, we make use of the **data frame** object which allows us to store tables with columns of different data types. To create a data frame we can simply use the **data.frame()** function.


```r
patientName <- c("patient1","patient2","patient3","patient4")
patientType <- factor(rep(c("male","female"),2))
survivalTime <- c(1,30,2,20)
dfExample <- data.frame(Name=patientName, Type=patientType,Survival_Time=survivalTime)
dfExample
```

```
      Name   Type Survival_Time
1 patient1   male             1
2 patient2 female            30
3 patient3   male             2
4 patient4 female            20
```



Data frames (2/12) - Indexing and replacement
=========================================================

Data frames may be indexed just [as matrices](#/indexingmatrices).


```r
dfExample
```

```
      Name   Type Survival_Time
1 patient1   male             1
2 patient2 female            30
3 patient3   male             2
4 patient4 female            20
```

```r
dfExample[dfExample[,"Survival_Time"] > 10,]
```

```
      Name   Type Survival_Time
2 patient2 female            30
4 patient4 female            20
```
Data frames (3/12) - Using $ to specify columns
=========================================================
Unlike matrices, it is possible to index a column by using the **$** symbol.


```r
dfExample <- data.frame(Name=patientName,Type=patientType,Survival_Time=survivalTime)
dfExample$Survival_Time
```

```
[1]  1 30  2 20
```

```r
dfExample[dfExample$Survival_Time < 10,]
```

```
      Name Type Survival_Time
1 patient1 male             1
3 patient3 male             2
```
Using the **$** allows for R to autocomplete your selection and so can speed up coding.


```r
dfExample$Surv
```

```
[1]  1 30  2 20
```
But this will not work..

```r
dfExample[,"Surv"]
```

Data frames (4/12) - Creating new columns with $
=========================================================

The **$** operator also allows for the creation of new columns for a data frame on the fly.


```r
dfExample
```

```
      Name   Type Survival_Time
1 patient1   male             1
2 patient2 female            30
3 patient3   male             2
4 patient4 female            20
```

```r
dfExample$newColumn <- rep("newData",nrow(dfExample))
dfExample
```

```
      Name   Type Survival_Time newColumn
1 patient1   male             1   newData
2 patient2 female            30   newData
3 patient3   male             2   newData
4 patient4 female            20   newData
```

Data frames (5/12) - Indexing and replacement
=========================================================

Certain columns can not be replaced in data frames. Numeric columns may have their values replaced but columns with character values may not by default. This occurs because character vectors are treated as factors by default.



```r
dfExample[dfExample[,"Survival_Time"] < 10,"Survival_Time"] <- 0
dfExample
```

```
      Name   Type Survival_Time newColumn
1 patient1   male             0   newData
2 patient2 female            30   newData
3 patient3   male             0   newData
4 patient4 female            20   newData
```


```r
dfExample[dfExample[,"Survival_Time"] < 10,"Name"] <- "patientX"
dfExample
```

```
      Name   Type Survival_Time newColumn
1     <NA>   male             0   newData
2 patient2 female            30   newData
3     <NA>   male             0   newData
4 patient4 female            20   newData
```


Data frames (6/12) - Factors in data frames
=========================================================
It is possible to update factors in data frames just as with standard factors.


```r
dfExample <- data.frame(Name=patientName,Type=patientType,Survival_Time=survivalTime)

levels(dfExample[,"Name"]) <- c(levels(dfExample[,"Name"]) , "patientX")
dfExample[dfExample[,"Survival_Time"] < 10,"Name"] <- "patientX"
dfExample
```

```
      Name   Type Survival_Time
1 patientX   male             1
2 patient2 female            30
3 patientX   male             2
4 patient4 female            20
```

Data frames (7/12) - Creating data frames without factors
=========================================================
If you wish to avoid using factors in data frames then the **stringsAsFactors** argument to **data.frame()** function should be set to **FALSE**


```r
dfExample <- data.frame(Name=patientName,
                        Type=patientType,
                        Survival_Time=survivalTime,
                        stringsAsFactors = F)


dfExample[dfExample[,"Survival_Time"] < 10,"Name"] <- "patientX"
dfExample
```

```
      Name   Type Survival_Time
1 patientX   male             1
2 patient2 female            30
3 patientX   male             2
4 patient4 female            20
```

Data frames (8/12) - Ordering with order() function
=========================================================
A useful function in R is **order()**

For numeric vectors, **order()** by default returns the indices of a vector in that vector's increasing order. This behaviour can be altered by using the "decreasing" argument passed to order.


```r
testOrder <- c(2,1,3)
testOrder
```

```
[1] 2 1 3
```

```r
testOrder[order(testOrder)]
```

```
[1] 1 2 3
```

```r
testOrder[order(testOrder,decreasing=T)]
```

```
[1] 3 2 1
```
Data frames (9/12) - Ordering with NA values
=========================================================
id:nalast
When a vector contains NA values, these NA values will, by default, be placed last in ordering indices. This can be controlled by **na.last** argument.


```r
testOrder <- c(2,1,NA,3)
testOrder[order(testOrder,decreasing=T,na.last=T)]
```

```
[1]  3  2  1 NA
```

```r
testOrder[order(testOrder,decreasing=T,na.last=F)]
```

```
[1] NA  3  2  1
```

Data frames (10/12) - Ordering data frames 
=========================================================
Since the order argument returns an index of intended order for a vector, we can use the order() function to order data frames by certain columns

```r
dfExample
```

```
      Name   Type Survival_Time
1 patientX   male             1
2 patient2 female            30
3 patientX   male             2
4 patient4 female            20
```

```r
dfExample[order(dfExample$Surv, decreasing=T),]
```

```
      Name   Type Survival_Time
2 patient2 female            30
4 patient4 female            20
3 patientX   male             2
1 patientX   male             1
```
***
We can also use order to arrange multiple columns in a data frame by providing multiple vectors to order() function. Ordering will be performed in order of arguments.


```r
dfExample[order(dfExample$Type,
                dfExample$Survival,
                decreasing=T),]
```

```
      Name   Type Survival_Time
3 patientX   male             2
1 patientX   male             1
2 patient2 female            30
4 patient4 female            20
```


Data frames (11/12) - Merging data frames
=========================================================

A common operation is to join two data frames by a column of common values.



```r
dfExample <- data.frame(Name=patientName,
                        Type=patientType,
                        Survival_Time=survivalTime)
dfExample 
```

```
      Name   Type Survival_Time
1 patient1   male             1
2 patient2 female            30
3 patient3   male             2
4 patient4 female            20
```
***

```r
dfExample2 <- data.frame(Name=patientName[1:3],
                        height=c(6.1,5.1,5.5))

dfExample2
```

```
      Name height
1 patient1    6.1
2 patient2    5.1
3 patient3    5.5
```

Data frames (12/12) - Merging data frames with merge()
=========================================================

To do this we can use the **merge()** function with the data frames as the first two arguments. We can then specify the columns to merge by with the **by** argument. To keep only data pertaining to values common to both data frames the **all** argument is set to TRUE.


```r
mergedDF <- merge(dfExample,dfExample2,by=1,all=F)
mergedDF
```

```
      Name   Type Survival_Time height
1 patient1   male             1    6.1
2 patient2 female            30    5.1
3 patient3   male             2    5.5
```

Time for an exercise!
========================================================

Exercise on data frames can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/exercises/Dataframes_Exercise.html)

Answers to exercise.
========================================================

Answers can be found here  [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/Dataframes_Answers.html)

R code solutions can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/Dataframes_Answers.R)

Lists (1/7) - Creating lists
=========================================================

Lists are the final data-type we will look at. 

In R, lists provide a general container which may hold any data types of unequal lengths as part of its elements.
To create a list we can simply use the **list()** function with arguments specifying the data we wish to include in the list.


```r
firstElement <- c(1,2,3,4)
secondElement <- matrix(1:10,nrow=2,ncol=5)
thirdElement <- data.frame(colOne=c(1,2,4,5),colTwo=c("One","Two","Three","Four"))
myList <- list(firstElement,secondElement,thirdElement)
myList
```

```
[[1]]
[1] 1 2 3 4

[[2]]
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10

[[3]]
  colOne colTwo
1      1    One
2      2    Two
3      4  Three
4      5   Four
```

Lists (2/7) -  Named lists
=========================================================

[Just as with vectors](#/namingvectors), list elements can be assigned names.


```r
myNamedList <- list(First=firstElement,Second=secondElement,Third=thirdElement)
myNamedList
```

```
$First
[1] 1 2 3 4

$Second
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10

$Third
  colOne colTwo
1      1    One
2      2    Two
3      4  Three
4      5   Four
```
Lists (3/7) - Indexing
=========================================================

List, as [with other data types in R](#/indexingvectors) can be indexed. In contrast to other types, using **[]** on a list will subset the list to another list of selected indices. To retrieve an element from a list in R , two square brackets **[[]]** must be used. 


```r
myList <- list(firstElement,secondElement,thirdElement)
myList[1]
```

```
[[1]]
[1] 1 2 3 4
```

```r
myList[[1]]
```

```
[1] 1 2 3 4
```

As with data.frames, the $ sign may be used to extract named elements from a list


```r
myNamedList$First
```

```
[1] 1 2 3 4
```

Lists (4/7) - Joining lists
=========================================================

Again, [similar to vectors](#/combine), lists can be joined together in R using the c() function 


```r
myNamedList <- list(First=firstElement,Second=secondElement,Third=thirdElement)
myNamedList <- c(myNamedList,list(fourth=c(4,4)))
myNamedList[c(1,4)]
```

```
$First
[1] 1 2 3 4

$fourth
[1] 4 4
```

Lists (5/7) - Joining vectors to lists
=========================================================

Note that on last slide we are joining two lists. If we joined a vector to a list, all elements of the vector would become list elements.


```r
myList <- c(myList,c(4,4))
myList
```

```
[[1]]
[1] 1 2 3 4

[[2]]
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10

[[3]]
  colOne colTwo
1      1    One
2      2    Two
3      4  Three
4      5   Four

[[4]]
[1] 4

[[5]]
[1] 4
```

Lists (6/7) - Flattening lists
=========================================================

Sometimes you will wish to "flatten" out a list. When a list contains compatable objects, i.e. list of all one type, the **unlist()** function can be used. Note the maintenance of names with their additional sufficies.


```r
myNamedList <- list(First=c(1,2,3),Second=c(2,6,7),Third=c(1,4,7))
myNamedList
```

```
$First
[1] 1 2 3

$Second
[1] 2 6 7

$Third
[1] 1 4 7
```

```r
flatList <- unlist(myNamedList)
flatList[1:7]
```

```
 First1  First2  First3 Second1 Second2 Second3  Third1 
      1       2       3       2       6       7       1 
```



Lists (7/7) Flattening lists to matrices
=========================================================
A common step is to turn a list of standard results into matrix. This can be done in a few steps in R.


```r
myNamedList <- list(First=c(1,2,3),Second=c(2,6,7),Third=c(1,4,7))
flatList <- unlist(myNamedList)
listAsMat <- matrix(flatList,
                    nrow=length(myNamedList),
                    ncol=3,
                    byrow=T,
                    dimnames=list(names(myNamedList)))
listAsMat
```

```
       [,1] [,2] [,3]
First     1    2    3
Second    2    6    7
Third     1    4    7
```


Reading and writing data in R
=========================================================
type:section
id: reading


Data IO (1/7) - Data from External sources
=========================================================

Most of the time, you will not be generating data in R but will be importing data from external files.

A standard format for this data is a table


|Gene_Name | Sample_1.hi| Sample_2.hi| Sample_3.hi| Sample_4.low| Sample_5.low| Sample_1.low|
|:---------|-----------:|-----------:|-----------:|------------:|------------:|------------:|
|Gene_a    |    3.746200|    3.941653|    3.794862|     3.633208|     3.713848|     2.292254|
|Gene_b    |    3.175298|    5.248515|    4.758635|     3.849890|     3.503243|     4.728451|
|Gene_c    |    3.048066|    4.183989|    3.846025|     3.444151|     4.262323|     5.213423|
|Gene_d    |    2.111448|    5.074579|    2.854247|     8.214177|     7.638293|     9.512675|
|Gene_e    |    8.590801|   10.667181|    9.839471|     2.374277|     3.007807|     4.503819|
|Gene_f    |   10.574687|    8.534240|   10.774365|     2.786425|     2.225497|     1.908591|
|Gene_g    |    9.335065|    9.503781|   10.730394|     8.714237|     9.338326|     8.916753|
|Gene_h    |   10.760913|   11.993786|    9.847345|    12.268990|     9.031520|    10.040574|

Data IO (2/7) - Data from text file with read.table()
=========================================================

Tables from text files can be read with **read.table()** function


```r
Table <- read.table("data/readThisTable.csv",sep=",",header=T)
Table[1:4,1:3]
```

```
  Gene_Name Sample_1.hi Sample_2.hi
1    Gene_a    4.570237    3.230467
2    Gene_b    3.561733    3.632285
3    Gene_c    3.797274    2.874462
4    Gene_d    3.398242    4.415202
```

Here we have provided two arguments. 
- **sep** argument specifies how columns are separated in our text file. ("," for .csv, "\t" for .tsv)
- **header** argument specifies whether columns have headers.

Data IO (3/7) - Row names in read.table()
=========================================================

read.table() allows for significant control over reading files through its many arguments. Have a look at options by using **?read.table**

The **row.names** argument can be used to specify a column to use as row names for the resulting data frame. Here we use the first column as row names.


```r
Table <- read.table("data/readThisTable.csv",sep=",",header=T,row.names=1)
Table[1:4,1:3]
```

```
       Sample_1.hi Sample_2.hi Sample_3.hi
Gene_a    4.570237    3.230467    3.351827
Gene_b    3.561733    3.632285    3.587523
Gene_c    3.797274    2.874462    4.016916
Gene_d    3.398242    4.415202    4.893561
```

Data IO (4/7) - Setting factors from read.table()
=========================================================

As mentioned, data which is read into R through read.table() will be of data frame class.

To avoid character columns being converted into factors, we can specify the **stringsAsFactors** argument here.


```r
Table <- read.table("data/readThisTable.csv",sep=",",header=T,stringsAsFactors=F)
```

Other very useful functions for read table include:
- **skip** - To set number of lines to skip when reading.
- **comment.char** - To set the start identifier for lines not to be read.

Data IO (5/7) - Data from other sources
=========================================================

The read.table function can also read data from http.


```r
URL <- "http://mrccsc.github.io/readThisTable.csv"
Table <- read.table(URL,sep=",",header=T)
Table[1:2,1:3]
```

```
  Gene_Name Sample_1.hi Sample_2.hi
1    Gene_a    4.111851    3.837018
2    Gene_b    6.047822    5.683518
```
And the clipboard.(This is Windows version)


```r
Table <- read.table(file="clipboard",sep=",",header=T)
```

Data IO (6/7) - Data from file columns
=========================================================

read.table() function will by default read every row and column of a file.

The **scan()** function allows for the selection of particular columns to be read into R and so can save memory when files are large. 



```r
x <- scan("data/readThisTable.csv",sep=",",
what = c(list(""),rep(list(NULL), 6)),skip=1)
x[1:3]
```

```
[[1]]
[1] "Gene_a" "Gene_b" "Gene_c" "Gene_d" "Gene_e" "Gene_f" "Gene_g" "Gene_h"

[[2]]
NULL

[[3]]
NULL
```

Data IO (7/7) - Writing data to file
=========================================================

Once we have our data analysed in R, we will want to export it to a file. 

The most common method is to use the write.table() function


```r
write.table(Table,file="data/writeThisTable.csv",sep=",")
```

Since our data has column names but no row names, I will provide the arguments col.names and row.names to write.table()


```r
write.table(Table,file="data/writeThisTable.csv", sep=",", row.names =F,col.names=T)
```

Time for an exercise!
========================================================

Exercise on reading and writing data can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/exercises/DataInputOutput_Exercises.html)

Answers to exercise.
========================================================

Answers can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/DataInputOutput_answers.html)

R code for solutions can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/answers/DataInputOutput_answers.R)




Statistics in R
=========================================================
type:section
id: stats



Statistics (1/26) - Statistics in R
=========================================================

R has a powerful set of statistical methods.
Including:
- Standard statistical tests
- Statistical modelling
- Further methods available in add on packages

Statistics (2/26) - Tables and Frequencies
=========================================================

One of the simplest statistical tools are **summary()** and **table()**. These functions provide descriptive statistics for data frames and character vectors or factors.


```r
patientName <- c("patient1","patient2","patient3","patient4")
patientType <- factor(rep(c("male","female"),2))
survivalTime <- c(1,30,2,20)
dfExample <- data.frame(Name=patientName,Type=patientType,Survival_Time=survivalTime)
```
The **table()** function provides a breakdown of the frequency of occurrence of all unique values in vector or factor.

```r
table(patientType)
```

```
patientType
female   male 
     2      2 
```

Statistics (3/26) - summary() function  with data frames
=========================================================

**summary()** provides a breakdown of occurrence for all character or factor columns and min,max,mean and quantiles for numeric columns.


```r
summary(dfExample)
```

```
       Name       Type   Survival_Time  
 patient1:1   female:2   Min.   : 1.00  
 patient2:1   male  :2   1st Qu.: 1.75  
 patient3:1              Median :11.00  
 patient4:1              Mean   :13.25  
                         3rd Qu.:22.50  
                         Max.   :30.00  
```

Statistics (4/26) - table() function with data frames
=========================================================

The **table()** function can be used to generate frequency tables across data.frames.

```r
table(dfExample)
```

```
, , Survival_Time = 1

          Type
Name       female male
  patient1      0    1
  patient2      0    0
  patient3      0    0
  patient4      0    0

, , Survival_Time = 2

          Type
Name       female male
  patient1      0    0
  patient2      0    0
  patient3      0    1
  patient4      0    0

, , Survival_Time = 20

          Type
Name       female male
  patient1      0    0
  patient2      0    0
  patient3      0    0
  patient4      1    0

, , Survival_Time = 30

          Type
Name       female male
  patient1      0    0
  patient2      1    0
  patient3      0    0
  patient4      0    0
```

Statistics (5/26) - ftable() function
=========================================================

**ftable()** function provides a method to generate or print the results from table() in a neater format.


```r
ftable(dfExample)
```

```
                Survival_Time 1 2 20 30
Name     Type                          
patient1 female               0 0  0  0
         male                 1 0  0  0
patient2 female               0 0  0  1
         male                 0 0  0  0
patient3 female               0 0  0  0
         male                 0 1  0  0
patient4 female               0 0  1  0
         male                 0 0  0  0
```
Statistics (6/26) - Correlation
=========================================================

A common task in statistical analysis is to investigate the relationship between pairs of numeric vectors.

This can be done by identifying the correlation between numeric vectors using the **cor()** function in R.

In this example we use cor() to identify the Pearson correlation between two variables.  The **method** argument may be set to make use of different correlation methods.

- Perfectly posively correlated vectors will return 1
- Perfectly negatively correlated vectors will return -1
- Vectors showing no or little correlation will be close to 0.

Statistics (7/26) - Correlation between vectors
=========================================================


```r
x <- rnorm(100,10,2)
z <- rnorm(100,10,2)
y <- x
cor(x,y) # 
```

```
[1] 1
```

```r
cor(x,-y)
```

```
[1] -1
```

```r
cor(x,z)
```

```
[1] -0.0744949
```
***
![plot of chunk unnamed-chunk-109](introToR_Session1-figure/unnamed-chunk-109-1.png)


Statistics (8/26) - Correlation over a matrix
=========================================================
left: 70%
Often we wish to apply correlation analysis to all columns or rows in a matrix in a pair-wise manner. To do this in R, we can simply pass the **cor()** function a single argument of the numeric matrix of interest. The **cor()** function will then perform all pair-wise correlations between columns.


| Sample_1.hi| Sample_2.hi| Sample_3.hi| Sample_4.low| Sample_5.low| Sample_1.low|
|-----------:|-----------:|-----------:|------------:|------------:|------------:|
|    3.746200|    3.941653|    3.794862|     3.633208|     3.713848|     2.292254|
|    3.175298|    5.248515|    4.758635|     3.849890|     3.503243|     4.728451|


```r
cor(minRep)[1:2,2:5]
```

```
            Sample_2.hi Sample_3.hi Sample_4.low Sample_5.low
Sample_1.hi   0.9112755   0.9752387    0.2800140    0.1841944
Sample_2.hi   1.0000000   0.9017547    0.4378759    0.3467012
```

Statistics (9/26) - Visualising correlation
=========================================================


```r
image(cor(minRep),axes=F)
axis(1,at=seq(0,1,length.out=6), colnames(minRep))
axis(2,at=seq(0,1,length.out=6), colnames(minRep))
```
***
<img src="introToR_Session1-figure/unnamed-chunk-114-1.png" title="plot of chunk unnamed-chunk-114" alt="plot of chunk unnamed-chunk-114" width="1920px" />

Statistics (10/26) - Distributions
=========================================================

R comes with functions for extracting information from most common distibutions types.
An example of standard R functions for dealing with distibution can be seen here using the normal distributions.

- pnorm - cumulative distribution for x
- qnorm - inverse of pnorm (from probability gives x)
- dnorm - distribution density
- rnorm - random number from normal distribution

***

![alt text](imgs/Dist.jpg)

Statistics (11/26) - Many distributions available.
=========================================================

Similar functions are available for other distibution types including:
- pbinom (binomial)
- pnbinom (negative binomial),
- phyper (hypergeometric)
- pt (T distribution)

Statistics (12/26) - Distribution examples
=========================================================

We can use rnorm to generate random values following a normal distribution. Here we produce 10 normally distributed numeric values with mean 8 and standard deviation of 3

```r
rnorm(10,mean=8,sd=3)
```

```
 [1] 7.774776 9.651483 6.526969 5.031855 8.829963 4.699238 9.295709
 [8] 6.987415 8.046085 3.990670
```
We can also use these functions to interrogate values assuming a normal distribution for the data.

The probablity of a value being exactly 8 for a distribution of mean 8 and standard deviation 3. 


```r
dnorm(8,mean=8,sd=3)
```

```
[1] 0.1329808
```

Statistics (13/26) - Distribution examples 2
=========================================================

The probablity of a value being less than 8 for a distribution of mean 8 and standard deviation 3. 


```r
pnorm(8,mean=8,sd=3)
```

```
[1] 0.5
```

The value for which i have a 50 percent being greater than given a normal distribution of mean 8 and standard deviation 3. 


```r
qnorm(0.5,mean=8,sd=3)
```

```
[1] 8
```

Statistics (14/26) - Statistical tests
=========================================================

On top of descriptive statistics, R has several statistical tests covering a range of problems and data types.

Some common tests include: 

- var.test() - Comparing 2 variances (Fisher's F test)

- t.test() - Comparing 2 sample means with normal errors (Student's t-test)

- wilcox.test() - Comparing 2 means with non-normal errors (Wilcoxon's rank test)

- fisher.test() - Testing for independence of 2 variables in a contingency table (Fisher's exact test)


Statistics (15/26) - T-test example. Reading data.
=========================================================

To perform a t-test we will read in some datasets, test that the variances of the datasets are equal and then perform the actual t-tests.



```r
tTestExample <- read.table("data/tTestData.csv",sep=",",header=T)
tTestExample
```

```
          A        B        C
1  26.03199 40.65549 33.78191
2  27.00897 40.59726 39.48001
3  27.57468 39.86103 34.63261
4  27.15929 39.96254 42.62425
5  25.82156 42.54450 35.48016
6  26.18872 39.31856 40.49148
7  26.30709 40.80434 38.91200
8  26.21609 39.96368 40.74275
9  25.84095 40.08374 34.28705
10 26.86587 40.18931 37.80057
```

Statistics (16/26) - T-test example. Calculating variance
=========================================================

First we can specify the columns of interest using **$** and calculate their variance using **var()**.


```r
var(tTestExample$A)
```

```
[1] 0.367875
```

```r
var(tTestExample$B)
```

```
[1] 0.7614086
```

```r
var(tTestExample$C)
```

```
[1] 9.681179
```

Statistics (16/26) - T-test example. Comparing variance.
=========================================================

Now we can test for any differences in variances between A and B and A and C with an F-test using the **var.test()** function.


```r
var.test(tTestExample$A,tTestExample$B)
```

```

	F test to compare two variances

data:  tTestExample$A and tTestExample$B
F = 0.48315, num df = 9, denom df = 9, p-value = 0.2936
alternative hypothesis: true ratio of variances is not equal to 1
95 percent confidence interval:
 0.1200078 1.9451614
sample estimates:
ratio of variances 
         0.4831506 
```

```r
var.test(tTestExample$A,tTestExample$C)
```

```

	F test to compare two variances

data:  tTestExample$A and tTestExample$C
F = 0.037999, num df = 9, denom df = 9, p-value = 4.092e-05
alternative hypothesis: true ratio of variances is not equal to 1
95 percent confidence interval:
 0.009438411 0.152983699
sample estimates:
ratio of variances 
        0.03799899 
```

R objects (s3 and s4)
=========================================================
Left:30%
The data type holding the result **var.test()** is a little more complex than the data types we have looked. 

In R, special objects (S3 or S4 objects) can be created which have methods associated to them. The result from var.test is an object of class **htest**.

Since we have not come across this before, in order to discover its structure we can use the **str()** function with the object of interest as the argument.
***

```r
result <- var.test(tTestExample$A, tTestExample$B)
str(result)
```

```
List of 9
 $ statistic  : Named num 0.483
  ..- attr(*, "names")= chr "F"
 $ parameter  : Named int [1:2] 9 9
  ..- attr(*, "names")= chr [1:2] "num df" "denom df"
 $ p.value    : num 0.294
 $ conf.int   : num [1:2] 0.12 1.95
  ..- attr(*, "conf.level")= num 0.95
 $ estimate   : Named num 0.483
  ..- attr(*, "names")= chr "ratio of variances"
 $ null.value : Named num 1
  ..- attr(*, "names")= chr "ratio of variances"
 $ alternative: chr "two.sided"
 $ method     : chr "F test to compare two variances"
 $ data.name  : chr "tTestExample$A and tTestExample$B"
 - attr(*, "class")= chr "htest"
```

R objects (s3 and s4)
=========================================================
Now we know the structure and class of the htest object we can access the **slots** containing information we want just as with a named list.

The p-value

```r
result$p.value
```

```
[1] 0.293592
```

The statistic

```r
result$statistic
```

```
        F 
0.4831506 
```

The data used in function call

```r
result$data.name
```

```
[1] "tTestExample$A and tTestExample$B"
```

Statistics (17/26) T-test example. Equal Variance
=========================================================

We have ascertained that GroupA and GroupB have similar variances. We can therefore perform a standard t-test to assess the significance of differences between these groups.


```r
Result <- t.test(tTestExample$A,tTestExample$B,alternative ="two.sided", var.equal = T)
Result
```

```

	Two Sample t-test

data:  tTestExample$A and tTestExample$B
t = -41.353, df = 18, p-value < 2.2e-16
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -14.60253 -13.19051
sample estimates:
mean of x mean of y 
 26.50152  40.39804 
```

Statistics (18/26) T-test example. Unequal Variance
=========================================================

To compare groups of unequal variance then the **var.equal** argument may be set to FALSE (which is the default).


```r
Result <- t.test(tTestExample$A,tTestExample$C,alternative ="two.sided", var.equal = F)
Result
```

```

	Welch Two Sample t-test

data:  tTestExample$A and tTestExample$C
t = -11.294, df = 9.683, p-value = 6.855e-07
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -13.56531  -9.07821
sample estimates:
mean of x mean of y 
 26.50152  37.82328 
```

Statistics (19/26) T-test example. Specifying a formula 
=========================================================

The same result to that shown could be achieved by specifying a formula for the comparison.
Here we wish to compare column A versus B so we could simply specify the formula and the data to be used.


```r
longFrame <- data.frame(Group = c(rep("A",nrow(tTestExample)),rep("B",nrow(tTestExample))), Value=c(tTestExample$A,tTestExample$B))

result <- t.test(Value~Group,longFrame,alternative ="two.sided",
                 var.equal = T)
result
```

```

	Two Sample t-test

data:  Value by Group
t = -41.353, df = 18, p-value < 2.2e-16
alternative hypothesis: true difference in means is not equal to 0
95 percent confidence interval:
 -14.60253 -13.19051
sample estimates:
mean in group A mean in group B 
       26.50152        40.39804 
```


Statistics (20/26) - Regression and linear models
=========================================================

We have seen how we can find the correlation between two sets of variables using cor() function.

R also provides a comprehensive set of tools for regression analysis including the well used linear modeling function lm()

To fit a linear regression we use a similar set of arguments as passed to the t-test fuction in the previous slide.


```r
> lmExample <- read.table("data/lmExample.txt",h=T,sep="\t")
```

```r
> lmResult <- lm(Y~X,data=lmExample)
> plot(Y~X,data=lmExample,main="Line of best fit with lm()",
+      xlim=c(0,150),ylim=c(0,200))
> abline(lmResult,col="red",lty=3,lwd=3)
```

![plot of chunk unnamed-chunk-130](introToR_Session1-figure/unnamed-chunk-130-1.png)

Statistics (21/26) The lm() function
=========================================================

The lm() function fits a linear regression to your data and provides useful information on the generated fit.

In the example below we fit a linear model using  lm() on the lmExample dataset with column Y as the dependent variable and column X as the explanatory variable.


```r
> lmResult <- lm(Y~X,data=lmExample)
> lmResult
```

```

Call:
lm(formula = Y ~ X, data = lmExample)

Coefficients:
(Intercept)            X  
      7.001        1.972  
```

Printing the result from lm() shows the call to lm() and the coefficients including the intercept.

Statistics (22/26) - Plotting line of best fit.
=========================================================

From the previous slides we now know the formula for the line.

**Y = 7.001 + 1.972*X**

We can add the line of best fit using **abline()**


```r
> plot(Y~X,data=lmExample,main="Line of best fit with lm()",
+      xlim=c(0,100),ylim=c(0,200))
> abline(lmResult,col="red",lty=3,lwd=3)
```

![plot of chunk unnamed-chunk-132](introToR_Session1-figure/unnamed-chunk-132-1.png)

Statistics (23/26) - Interpreting output of lm()
=========================================================
As we have seen, printing the model result provides the intercept and slope of line.

To get some more information on the model we can use the summary() function


```r
> summary(lmResult)
```

```

Call:
lm(formula = Y ~ X, data = lmExample)

Residuals:
    Min      1Q  Median      3Q     Max 
-5.0150 -2.3688 -0.2079  2.6068  5.0538 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  7.00053    0.93207   7.511 3.91e-13 ***
X            1.97218    0.01325 148.894  < 2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 2.858 on 398 degrees of freedom
Multiple R-squared:  0.9824,	Adjusted R-squared:  0.9823 
F-statistic: 2.217e+04 on 1 and 398 DF,  p-value: < 2.2e-16
```


Statistics (24/26) - Residuals
=========================================================


```

Call:
lm(formula = Y ~ X, data = lmExample)

Residuals:
    Min      1Q  Median      3Q     Max 
-5.0150 -2.3688 -0.2079  2.6068  5.0538 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  7.00053    0.93207   7.511 3.91e-13 ***
X            1.97218    0.01325 148.894  < 2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 2.858 on 398 degrees of freedom
Multiple R-squared:  0.9824,	Adjusted R-squared:  0.9823 
F-statistic: 2.217e+04 on 1 and 398 DF,  p-value: < 2.2e-16
```

***
The **residuals** are the difference between the predicted and actual values.
To retrieve the residuals we can access the slot or use the resid() function.


```r
> summary(resid(lmResult))
```

```
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
-5.0150 -2.3688 -0.2079  0.0000  2.6068  5.0538 
```

```r
> summary(lmResult$residual)
```

```
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
-5.0150 -2.3688 -0.2079  0.0000  2.6068  5.0538 
```
Ideally you would want your residuals to be normally distributed around 0.

Statistics (25/26) - R-squared
=========================================================


```

Call:
lm(formula = Y ~ X, data = lmExample)

Residuals:
    Min      1Q  Median      3Q     Max 
-5.0150 -2.3688 -0.2079  2.6068  5.0538 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  7.00053    0.93207   7.511 3.91e-13 ***
X            1.97218    0.01325 148.894  < 2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 2.858 on 398 degrees of freedom
Multiple R-squared:  0.9824,	Adjusted R-squared:  0.9823 
F-statistic: 2.217e+04 on 1 and 398 DF,  p-value: < 2.2e-16
```

The **R-squared** value represents the proportion of variability in the response variable that is explained by the explanatory variable.

A high **R-squared** here indicates that the line fits closely to the data.

Statistics (26/26) - F-statistics. 
=========================================================


```r
> summary(lmResult)
```

```

Call:
lm(formula = Y ~ X, data = lmExample)

Residuals:
    Min      1Q  Median      3Q     Max 
-5.0150 -2.3688 -0.2079  2.6068  5.0538 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  7.00053    0.93207   7.511 3.91e-13 ***
X            1.97218    0.01325 148.894  < 2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 2.858 on 398 degrees of freedom
Multiple R-squared:  0.9824,	Adjusted R-squared:  0.9823 
F-statistic: 2.217e+04 on 1 and 398 DF,  p-value: < 2.2e-16
```

The results from linear models also provides a measure of significance for a variable not being relevant.

Statistics (Extra) - A fit line
=========================================================

![alt text](imgs/fittedline.png)

Statistics (Extra) - Calculating R-squared
=========================================================

![alt text](imgs/rsquared.png)

Statistics (Extra) - Calculating R-squared
=========================================================


```r
SSE <- sum(resid(lmResult)^2)
TSS <- sum((lmExample$Y - mean(lmExample$Y))^2)
1- SSE/TSS
```

```
[1] 0.982364
```

```r
summary(lmResult)$r.squared
```

```
[1] 0.982364
```

Statistics (Extra) - Calculating F-stat
=========================================================

![alt text](imgs/fstatistic.png)

Statistics (Extra) - Calculating F-stat
=========================================================


```r
MSE <- mean(lmResult$residuals^2)
RSS <- sum((predict(lmResult) - mean(lmExample$Y))^2)

summary(lmResult)$fstatistic
```

```
   value    numdf    dendf 
22169.41     1.00   398.00 
```


Time for an exercise!
========================================================

Exercise on statistics can be found [here](https://lmsbioinformatics.github.io/LMS_Reproducible-R/r_course/exercises/Statistics_Exercises.html)

Answers to exercise.
========================================================

Answers can be found here  [here](answers/Statistics_Answers.html)

End of Session 1
====
