# assignment-1
This is the first assignment of the semester for HES 505. 

The first part of the course was designed to introduce some of the foundations of working in R, developing programming workflows, and getting help. These topics are important for building robust spatial workflows, but their utility extends beyond that to most things you'll do in R during the course of your graduate research. This homework is meant to help reinforce those concepts and identify any gaps that I need to fill in as we go. By the end of this assignment you should be able to:

* Use `read.***` and `read_***` to bring data into your R environment and determine the data type using `class` and `str`.

* Access and manipulate subsets of the data using standard and tidyverse approaches.

* Demonstrate the use of pseudocode to outline the steps in a function or analysis.

* Build several custom functions to automate repetitive tasks.

* Integrate code and text into a quarto document to facilitate sharing.

You'll need to accept the link to access the questions. 

## Instructions

1. After you've joined the assignment repository, you should have this file (named Readme.md) inside of a R project named assignment-1-xx where xx is your github username (or initials).

2. Once you've verified that you've correctly cloned the assignment repository, create a new Quarto document. Name this file assignment-1-xxx.qmd and give it a title (like M Williamson Assignment 1). Make sure that you select the html output option (Quarto can do a lot of cool things, but the html format is the least-likely to cause you additional headaches). We'll be using Quarto throughout the course so it's worth checking out the other tutorials in the getting started section.

3. Copy the questions below into your document and change the color of their text.

4. Save the changes and make your first commit!

5. Answer the questions making sure save and commit at least 4 more times (having 5 commits is part of the assignment).

6. Render the document to html (you should now have at least 3 files in the repository: Readme.md, assignment-1-xx.qmd, and assignment-1-xx.html). Commit these changes and push them to the repository on GitHub. You should see the files there when you go to github.com.

## The assignment
### R Basics
These first questions are designed to help get you familiar with creating your own data within R, manipulating those data, and using the helpfiles. Show your code (using code chunks in your qmd document).

1. Write a R program to create a vector which contains 25 random values between -50 and +50 and assign it to an object named `firstvector` in your `R` environment. What class is your vector?

2. Set the 5th, 12th, and 23rd elements to `NA`. 

3. Take the mean of `firstvector`. What does `R` return? 

4. Look at the helpfile for the `mean` function (using `?mean`), how might you adjust your code so that it returns the mean of all values that aren't `NA`? Try that and show your code.

5. Replace the NAs in your vector with 3 new numbers of your choosing by combining brackets with the `is.na()` function.

6. Write a R program to create a 5 x 4 matrix and assign it to an object. Then create a 3 x 3 matrix with labels and fill the matrix by rows and assign it to a separate object. Finally, create a 2 × 2 matrix with labels and fill the matrix by columns and assign it to a 3rd object. Use the `matrix` helpfile to see how this works.

7. Combine your vector and the 3 matrices into a single object (`hint: this should be a list`)

8. Create a logical vector with length = 25 and assign it to an object.

9. What is the `mean` of your logical vector?

10. Calculate the number of `TRUE` entries using a single line of code.

11. Replace the 3rd element of your list with the logical vector you just created.

### Reading, identifying, and manipulating data
Between the introductory readings and the little bit of practice in the first part of this assignment, you should have some experience with creating and manipulating data within `R`. Reading external data into `R` from spreadsheets or other files is much more commong. We'll practice that a bit here.

12. List all of the files in the `assignment01' directory. How might you change your call to `list.files()` to restrict the result to only the CSV files?

13. Use `read.csv()` to bring in the `TemoraBR.CSV` file and assign it to an object. What `class` is the resulting object? What about each column within the object?

14. Now use `read_csv()` from the `tidyverse` package to read in the same file. Do you notice any differences? 

15. Look at the helpfiles for both functions and explain why `read_csv` behaves the way that it does. Modify your call to `read.csv()` to try to get it to return the same kind of object as `read_csv()`. (`hint: you can use identical() to see whether the two dataframes are the same`)

16. Get the summary statistics (mean, median, min, max, and quartiles) for all of the columns in `TemoraBR`.

17. Use `read.table()` to read in the `smoking.txt` dataset. What is the structure of the resulting data?

18. Now use `read_table()` to read in the `smoking.txt` dataset. What is different? After looking at the helpfile for `read.table`, how might you adjust the code you used in #17 so that the two functions produce the same objects?

19. Use the `tidyverse` to read in the `smoking.txt` file, create a new column called rate whose value is mortality/smoking, and a column for country where you assign "US", "CAN", or "MEX" to each observation, and assign it to a single object. `(hint: you'll need to use a pipe and mutate; rep can help you with the country column)`

20. Take the dataframe you created in #19 and subset it so that it only contains entries from the US and the rate value that you just calculated

21. Now let's use a similar approach to what you did in #19 and read in the data, create the country and rate columns, group it by country, and create columns that provide the mean, min, and max for smoking, mortality and rate for each country. (`hint:` you'll need summarize`)


### Using the helpfiles to understand what R expects

22. Examine the helpfile for `read_table`. What are the arguments that it accepts? What are the defaults that are used when you don't supply values for the arguments?

23. Look at the helpfile for `cumsum`. What does it return when you provide a vector of numbers? 

24.  Look at the helpfile for `vector`. What are the primary functions for managing vector data in `R`?

25.  Run `mean(c("a","b", "c"))` in your console. What does it return? What does the warning message mean? 

### Using pseudocode and building custom functions

26. Imagine that you are trying to write a function that reads in all of the txt files in our `assignment01` directory, gives them a new column with the filename, and combines them into a single dataframe. Write out the psuedocode that describes each step that the function should take, what you expect it to do, and why.

27. Now that you have your pseudocode, try to add the appropriate `R` functions that correspond to each step.

28. Finally, wrap the important parts in a funciton and use `lapply` to complete the task described in #26.

### Finding help
29. Run the following code the R prompt. What error does this produce? What does this error typically mean? Provide 3 sources (weblinks are fine) that helped you diagnose this error. Provide code that fixes (i.e., results in the expected behavior without errors or warnings) the error.
```
testlist <- c(1,2,3)
testlist$s
```

30. What are the key elements of a "good" question when trying to get help from online sources like StackOverflow.

31. Try to combine the `TemoraBR.CSV` and `prawnGR.CSV` datasets into a single dataframe (ignore the fact that these datasets reflect slightly different things). What error do you get? Create a reproducible example that would allow others to reproduce the problem you are having and describes what you'd like to have happen if the code was working. 

### Rendering a complete document

Once you've gotten all of the answers and code chunks to work, hit the "Render" button and push your complet qmd and html documents to your assignment repo.
