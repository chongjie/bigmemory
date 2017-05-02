---
title       : Introduction to BigMemeory Package
description : How does the BigMemory Package differ from other Cluster Computing Packages?  When should we use the BigMemory Package?
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:VideoExercise lang:r xp:50 skills:1 key:f83d639107
## What is the BigMemory Package?


*** =video_link
//player.vimeo.com/video/154783078

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:66e4d6f467
## Limitations of R

What is the key limitation of R that many cluster computing packages aim to solve?

*** =instructions
- Data processing in R is slow on a local machine
- Data size that can be loaded into R is limited by local disk space
- Data processing is limited by RAM on a local machine
- Data processing on local machines are not suitable for concurrent programming 

*** =hint
Refer to the slides. 

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad_1 <- "Data processing speed is usually limited to the data object and function that is used.  Try again."
msg_bad_2 <- "Disk space is rarely the issue since there are almost no limits to hard disk space nowadays.  Try again."
msg_bad_4 <- "This is one issue with many cluster computing packages, and not the issue they aim to solve.  Try again."
msg_success <- "That's correct!  RAM is the limiting factor, and cluster computing opens up access to more RAMs, thereby increasing the limilts of data processing load."
test_mc(correct = 2, feedback_msgs = c(msg_bad_1, msg_bad_2, msg_success, msg_bad_4))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:5db7dc4c3d
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
