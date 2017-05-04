---
title       : Introduction to BigMemeory Package
description : How does the BigMemory Package differ from other Cluster Computing Packages?  When should we use the BigMemory Package?
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:VideoExercise lang:r xp:50 skills:1 key:f83d639107
## What is the `bigmemory` Package?


*** =video_link
//player.vimeo.com/video/154783078

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:66e4d6f467
## Limitations of `R`

What is the key limitation of R that many cluster computing packages aim to solve?

*** =instructions
- Data processing in R is slow on a local machine
- Data size that can be loaded into R is limited by local disk space
- Data processing is limited by the RAM on a local machine
- Data processing on local machines are not suitable for concurrent programming 

*** =hint
Refer to the slides. 

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad_1 <- "Data processing speed is usually limited to the data object and function that is used.  Try again."
msg_bad_2 <- "Disk space is rarely the issue since there are almost no limits to hard disk space nowadays.  Try again."
msg_success <- "That's correct!  RAM is the limiting factor, and cluster computing opens up access to more RAMs, thereby increasing the limilts of data processing load."
msg_bad_4 <- "This is one issue with many cluster computing packages, and not the issue they aim to solve.  Try again."
test_mc(correct = 3, feedback_msgs = c(msg_bad_1, msg_bad_2, msg_success, msg_bad_4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:a8e1a512e4
## `bigmemory` Package: Advantages and Disadvantages

Which one of the following correctly states one advantage and one disadvantage of the BigMemory package over common cluster computing packages?

*** =instructions
- Data processing in R is slow on a local machine
- Data size that can be loaded into R is limited by local disk space
- Data processing is limited by the RAM on a local machine
- Data processing on local machines are not suitable for concurrent programming 

*** =hint
Refer to the slides. 

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad_1 <- "Data processing speed is usually limited to the data object and function that is used.  Try again."
msg_bad_2 <- "Disk space is rarely the issue since there are almost no limits to hard disk space nowadays.  Try again."
msg_success <- "That's correct!  RAM is the limiting factor, and cluster computing opens up access to more RAMs, thereby increasing the limilts of data processing load."
msg_bad_4 <- "This is one issue with many cluster computing packages, and not the issue they aim to solve.  Try again."
test_mc(correct = 3, feedback_msgs = c(msg_bad_1, msg_bad_2, msg_success, msg_bad_4))
```



--- type:VideoExercise lang:r xp:50 skills:1 key:61fabb81d5
## The `big.matrix` Object


*** =video_link
//player.vimeo.com/video/154783078



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:2eb2a76879
## Who wins in data import?

In the lecture, we have seen how the three popular data import functions (`read.table`, `data.table::fread`, `bigmemory::read.big.matrix`) perform against a moderately sized dataset.  Which one is the fastest, and which one uses the least memory?

*** =instructions
- fastest: `read.big.matrix`; least memory: `read.big.matrix`
- fastest: `fread`; least memory: `fread`
- fastest: `read.big.matrix`; least memory: `fread`
- fastest: `fread`; least memory: `read.big.matrix`


*** =hint
Refer to the slides.

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "This is incorrect.  Try again."
msg_success <- "That's correct!"
test_mc(correct = 4, feedback_msgs = c(msg_bad, msg_bad, msg_bad, msg_success))
```


--- type:NormalExercise lang:r xp:100 skills:1 key:5db7dc4c3d
## Creating a `big.matrix` object from scratch

In this exercise, you will create a `big.matrix` object without any data load.  You will also explore the `big.matrix` object.

*** =instructions
1. Import the `bigmemory` library into your workspace.  
2. Create a `big.matrix` object with 20 rows and 8 columns using the `big.matrix` function with the following arguments, keeping the other arguments in their default values.  Make sure you assign it to `bm`: 

        - nrow = 20, 
        - ncol = 8, 
        - type = "integer"  

3. Call `bm`.  
4. Print the structure of `bm` to the console.  
5. Print the summary of `bm` to the console.  
6. Print `bm` using the `print` function.  
7. Print the `head` of `bm`.  

*** =hint
- For (2), make sure to specify only the number of rows, number of columns, and the data type.  


*** =sample_code
```{r}
# 1. Import the `bigmemory` library. 


# 2. Create the `big.matrix` object and assign it as `bm`.  



# 3. Call `bm`.  



# 4. Print the structure of `bm` to the console.  



# 5. Print the summary of `bm` to the console.  



# 6. Print `bm` using the `print` function.  



# 7. Print the `head` of `bm`.  



```

*** =solution
```{r}
# 1. Import the `bigmemory` library. 
library(bigmemory)

# 2. Create the `big.matrix` object and assign it as `bm`.  
bm <- big.matrix(nrow = 20
                 , ncol = 8
                 , type = "integer")


# 3. Call `bm`.  
bm


# 4. Print the structure of `bm` to the console.  
str(bm)


# 5. Print the summary of `bm` to the console.  
summary(bm)


# 6. Print `bm` using the `print` function.  
print(bm)


# 7. Print the `head` of `bm`.  
head(bm)


```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("big.matrix", args = c("nrow"),
              not_called_msg = "You didn't call `big.matrix()`!",
              incorrect_msg = "You didn't call `big.matrix` with the correct arguments: `nrow`.")

test_function("big.matrix", args = c("ncol"),
              not_called_msg = "You didn't call `big.matrix()`!",
              incorrect_msg = "You didn't call `big.matrix` with the correct arguments: `ncol`.")
              
test_function("big.matrix", args = c("type"),
              not_called_msg = "You didn't call `big.matrix()`!",
              incorrect_msg = "You didn't call `big.matrix` with the correct arguments: `type`.")

test_function("print", args = "x",
              not_called_msg = "You didn't call `print()`!",
              incorrect_msg = "You didn't call `print` with the correct arguments: `x`")

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str()` with the correct argument, `object`.")

test_function("sumamry", args = "object",
              not_called_msg = "You didn't call `summary()`!",
              incorrect_msg = "You didn't call `summary()` with the correct argument, `object`.")

test_function("head",
              not_called_msg = "You didn't call `head()`!")


test_object("bm"
            , undefined_msg = "You have not defined `bm`!"
            , incorrect_msg = "Check whether you have called the correct parameters when initializing `bm`, and set the correct seed when assigning values to `bm`!")



test_error()

success_msg("Good work! You have seen that the `big.matrix` object is a pointer, and neither `str` nor `summary` are useful in exploring the `big.matrix` object.  To display the values of a `big.matrix`, we can either use the `print` or `head` function, and `head` is recommended over `print`.")

```


--- type:NormalExercise lang:r xp:100 skills:1 key:5ab4179364
## Assigning values and column names to a `big.matrix` object

In this exercise, you will assign values to an initialized `big.matrix` object.  You will learn additional functions to explore the `big.matrix` object.  

*** =instructions
Note: The `bigmemory` library has been loaded to your workspace.  

1. Run this section as it is.  Note that an additional line to allow row names and column names to be used is activated here.  
2. Set the seed as 0 and assign the values `sample(1:8, 160, replace = TRUE)` to `bm` using `bm[] <- ...`.  
3. Print the `head` of `bm`.  
4. Print the `dim` of `bm`.
5. Print the `colnames` of `bm`.  
6. Assign the vector `letters[1:8]` as the column names of `bm`.  
7. Print the `colnames` of `bm` one more time to verify that the column names are now changed.  



*** =hint
- For (2), did you include `set.seed(0)`?  Also, did you use `bm[] <- ...` to assign the values to `bm`?
- For (6), did you assign the correct vector to `colnames(bm)`?


*** =pre_exercise_code
```{r}
# Clean up the environment
rm(bm)

# Load the library
library(bigmemory)
```

*** =sample_code
```{r}
# 1. Run this section as it is.  Note that an additional line to allow row names and column names to be used is activated here.  
options(bigmemory.allow.dimnames = TRUE)
bm <- big.matrix(nrow = 20
                 , ncol = 8
                 , type = "integer")

# 2. Set the seed as 0 and assign the values `sample(1:8, 160, replace = TRUE)` to `bm` using `bm[] <- ...`.   



# 3. Print the `head` of `bm`.  



# 4. Print the `dim` of `bm`.  



# 5. Print the `colnames` of `bm`.  



# 6. Assign the vector `letters[1:8]` as the column names of `bm`.  



# 7. Print the `colnames` of `bm` one more time to verify that the column names are now changed.  





```

*** =solution
```{r}
# 1. Run this section as it is.  Note that an additional line to allow row names and column names to be used is activated here.  
options(bigmemory.allow.dimnames = TRUE)
bm <- big.matrix(nrow = 20
                 , ncol = 8
                 , type = "integer")


# 2. Set the seed as 0 and assign the values `sample(1:8, 160, replace = TRUE)` to `bm` using `bm[] <- ...`.   
set.seed(0)
bm[] <- sample(1:8, 160, replace = TRUE)



# 3. Print the `head` of `bm`.  
head(bm)



# 4. Print the `dim` of `bm`.  
dim(bm)



# 5. Print the `colnames` of `bm`.  
colnames(bm)



# 6. Assign the vector `letters[1:8]` as the column names of `bm`.  
colnames(bm) <- letters[1:8]



# 7. Print the `colnames` of `bm` one more time to verify that the column names are now changed.  
colnames(bm)


```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("set.seed", args = "object",
              not_called_msg = "You didn't call `set.seed()`!",
              incorrect_msg = "You didn't call `set.seed()` with the correct argument, `seed`.")

test_function("head",
              not_called_msg = "You didn't call `head()`!")

test_function("dim",
              not_called_msg = "You didn't call `dim()`!")

test_function("colnames",
              not_called_msg = "You didn't call `colnames()`!")

test_object("bm"
            , incorrect_msg = "You have not updated `bm` with values and column names!")

test_error()

success_msg("Good work! `dim` is another useful function to explore `big.matrix` objects.  Also, if you wish to assign row and/or column names to a `big.matrix` object, make sure that you set the options as shown in the code.")

```



--- type:VideoExercise lang:r xp:50 skills:1 key:e655e340ab
## Importing data as `big.matrix` objects and operations on `big.matrix` objects


*** =video_link
//player.vimeo.com/video/154783078

--- type:NormalExercise lang:r xp:100 skills:1 key:00c3de9b07
## Importing data as `big.matrix` objects

In this exercise, you will import data directly as a `big.matrix` object.  You will explore learn the functions to check for file-backing and sharing.  

*** =instructions
Note: The `bigmemory` library has been loaded to your workspace.  

1. 



*** =hint
- 


*** =pre_exercise_code
```{r}
# Clean up the environment
rm(bm)

# Load the library
library(bigmemory)
```

*** =sample_code
```{r}



```

*** =solution
```{r}



```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("set.seed", args = "object",
              not_called_msg = "You didn't call `set.seed()`!",
              incorrect_msg = "You didn't call `set.seed()` with the correct argument, `seed`.")

test_object("bm"
            , incorrect_msg = "You have not updated `bm` with values and column names!")

test_error()

success_msg("")

```
--- type:NormalExercise lang:r xp:100 skills:1 key:cd7f15e068
## More movies

In the previous exercise, you saw a dataset about movies. In this exercise, we'll have a look at yet another dataset about movies!

A dataset with a selection of movies, `movie_selection`, is available in the workspace.

*** =instructions
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

*** =pre_exercise_code
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

*** =sample_code
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

*** =solution
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```
