# DoctorsAsDataScientists

## Introduction

Some stuff about why R is useful

## Week 1

### Loading and using RStudio

We will be using the R programming language through a piece of software called RStudio, hosted on a website called Posit Cloud, which is free to use.
On the website https://posit.cloud, create a new RStudio project called Doctors as Data Scientists. This project is where you will be running the workshop commands, and saving your work.

### Command line vs script window

There are two ways to run code in R. The script window (top bit) allows you to write and save multiple lines of code to be executed in one batch. The console (bottom bit) is useful for testing individual lines of code if you’re not sure if you want to save them. I generally recommend testing stuff in the console, and once you have it working, saving the working commands in a script

### Simple commands

To check R is running properly, in the console, run

``` 40+30 ```

You should get the answer appearing on screen.

### Variable Types

This course covers three basic variable types.

**numeric**, for example a person’s BMI
**character**, for example a person’s name
**logical**, which is a TRUE/FALSE variable, e.g. whether a person has cancer or not
There are other variable types too, such as date, time, and factors, but we will not go into these in this course.
Saving Variables
The power of R comes in being able to save lots of things in variables to perform tasks. 
height=1.7
weight=75

These should now be stored in R as numeric variables, and you can see them in the workspace on the top right. You can then perform calculations on these variables. For example:
BMI=weight/(height^2)

You can also store character variables in this way, but they require quotation marks around them. Try storing your name in a character variable.
first_name=’your_name’
surname=’your_name’

Comparing variables
It is often useful to be able to compare two numbers. Since = is used for assigning variables, testing if two things are equal to each other is done using ==. You can also use < or >. The output will always be a logical variable.
For example, comp=5==7 will create a logical variable called comp with the value FALSE.
Compare 5 with 7 using the following operators: < > <= >= == and !=.
Vectors
A vector is a list of values, which can be stored under one name. This is done using c. For example,
v=c(5,6,7,8)

will store v as a vector which contains the 4 numbers. You can then operate on these at once.
Try running v*2, v-4, and v>6.
Functions, arguments and outputs
A series of commands can be pre-packaged into a function to allow common tasks to be run quicker and easier.
A function can have one or more arguments. Sometimes, these additional arguments control how the function works.
Using some of the variables that should be stored from earlier, run the following commands to get a feel for how they work:
mean(v)
length(v)
paste(first_name,surname)

You can also store the output of a function in a variable. This is very useful when you have a long series of commands to write.
full_name=paste(first_name,surname)

## Exercise

You have 10 patients, who have HbA1c values, in percent, of 5, 7, 6.5, 9, 8, 7, 5.5, 5.5, 9, 4. Store this as a numerical vector called HbA1c1.

You don’t like working with %. In diabetes class, you were taught mmol/mol. Subtract 2.15 from HbA1c1, and multiply it by 11, to give HbA1c2, which is now in mmol/mol.

What is the highest HbA1c value in mmol/mol? What is the mean?

Check if this is greater than 48, and store the answer in a variable called diabetes. 

Use ```sum()``` to find how many people have diabetes and length() to find how many people are in your data and calculate the prevalence of diabetes.

### Solution:

<!-- 

HbA1c1=c(5, 7, 6.5, 9, 8, 7, 5.5, 4.5, 9, 4)
HbA1c2=11*(HbA1c1-2.15)
max_HbA1c= max(HbA1c2)
mean_HbA1c= mean(HbA1c2)
diabetes=HbA1c2>48
prevalence=sum(diabetes)/length(diabetes)

-->


<!-- 

## Week 2

 Can I put loads of stuff here
 -->
