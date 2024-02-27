# Doctors As Data Scientists

*Dr. Harry Green (h.d.green@exeter.ac.uk)*
 
## Introduction

Data science has become increasingly important in modern medical research, which is often done using large databases of millions of people. As computing facilities become better and we move towards a "Digital NHS", the amount of data available for medical research will only increase. Data science is about gaining insights from large data. Most medical guidelines that inform your practice will have been informed by data science, so having some experience in the field will help understand where these insights come from.

As a junior doctor, you will also be expected to be auditing your own practice. You may also become involved in research using data from either your own practice or larger, external databases. Efficient and accurate data-handling skills can make these processes a lot easier.

We will be using the R programming language through a piece of software called RStudio, hosted on a website called Posit Cloud, which is free to use. R is used widely for data analyses and statistics in medical research and it is free to download and very flexible in what you can use it for.  In comparison to using something like Excel, R is better able to work with 100,000s of records, is easier to automate and can easily allow steps in your analyses to be shared with others.

## Before the Course

You will need to register on Posit Cloud

https://posit.cloud 

## Session 1

_Aim: learn some efficient and reproducible ways of working with data that will help you in your future careers._

### Loading and using RStudio

On the website https://posit.cloud, create a new RStudio project called Doctors as Data Scientists. This project is where you will be running the workshop commands, and saving your work.

1. Select “New RStudio Project” from the menu: 

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/116f2fe3-2f50-4aeb-b3b1-4a18bec55315)

2. You will get a message saying “Deploying project”
  
3. You will see the following window – image

### Command line vs script window

4. First, create a new "R script" file.

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/47198d65-22af-4f60-bdf5-30de1f7cf7e4)

Your window should now look something like this.

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/87374858-6099-48f5-86d8-d3ee324e8576)


There are two ways to run code in R. The script window ( top left bit) allows you to write and save multiple lines of code to be executed in one batch. The console (bottom left bit) is useful for experimenting with code if you're not sure it will work. Put all of your answers in the script window so you can save a file called `week1.R` with this session's code.

### Simple commands

5. You can use R like a calculator.

To check R is running properly, in the console, type the following and press enter:

``` 40+30 ```

6. Try doing the same in the script window. What happens?
 
7. To run the command in the script window, click at the end of the line and then click the “Run” icon
 
8. Try adding these calculations to the script window. 

```40*30```
```40-30```
```40/30 ```

You can run all these at once by highlighting and clicking "Run".

Q1: From your answers, what do the symbols mean? 

### Saving your Script

### Variable Types

A variable is an object in R that stores some information. This could be a number, a name, a list of numbers, a date, etc. This course covers three basic variable types.

* **numeric**, for example a person’s BMI.
* **character**, for example a person’s name.
* **logical**, which is a TRUE/FALSE variable, e.g. whether a person has cancer or not. This is stored as a 1 for TRUE and 0 for false.
  
There are other variable types too, such as date, time, and factors, but we will not go into these in this course.

### Assigning Variables

The power of R comes in being able to save lots of things in variables to perform tasks. 

```
height=1.7
weight=75
```

These should now be stored in R as numeric variables, and you can see them in the workspace on the top right. You can then perform calculations on these variables. For example:

```BMI=weight/(height^2)```

To see the results of your calculation type ```print(BMI)```.

You can also store character variables in this way, but they require quotation marks around them. Try storing your name in a character variable.

```
first_name='your_name'
surname='your_name'
```

Note that a character variable, which can essentially store any kind of text, needs quotation marks around it. If you try ```first_name=Harry```, then it will trigger an error.

Q: Add commands to your script to print the name variables you have created. 

Note that these quotation marks MUST be 'and'. Not ‘and’. If your keyboard is adding these 'smart quotes', you'll need to disable these using Settings > general > keyboard on an ipad.

### Comparing variables

It is often useful to be able to compare two numbers. Since = is used for assigning variables, testing if two things are equal to each other is done using ==. You can also use < or > for other types of comparisons. The output will always be a logical variable.

For example, ```comp=5==7``` will create a logical variable called comp with the value FALSE.

Compare 5 with 7 using the following operators: <, >, <=, >=, ==, and !=.

Q: What is each of these comparisons doing?

### Vectors
A vector is a variable type that stores a list of values under one name. This is done using ```c```, an R function that combines things together. For example,

```v=c(5,6,7,8)```

will store ```v``` as a vector which contains the 4 numbers. You can then operate on these at once.

Q: Try running ```v*2```, ```v-4```, and ```v>6```. Give your answers.

### Functions, arguments and outputs

A series of commands can be pre-packaged into a function to allow common tasks to be run quicker and easier.
A function can have one or more arguments. Sometimes, these additional arguments control how the function works.

Q. Using some of the variables that should be stored from earlier, run the following commands to get a feel for how they work and write down your answers:

```
max(v)
min(v)
mean(v)
length(v)
paste(first_name,surname)
```

You can also store the output of a function in a variable. This is very useful when you have a long series of commands to write.
```full_name=paste(first_name,surname)```

## Exercise 1

You’ve been asked to check how many patients in your clinic have diabetes to compare with a similar clinic at another hospital. These are all patients with diabetes symptoms and according to your guidelines, a single measurement of HbA1c will allow you to make the diagnosis. HbA1c is a measure of the average blood sugar levels over the last 3 months. Note that in real life you would need some additional information and there are exceptions to these rules! You have realised that if you make an R script, you can easily and quickly do this comparison and do this again in the future: 

1. Make a new R script and save it with a name that helps you remember what it does. Your script, should appear in your list of files on the bottom right
2. Make a numerical vector called HbA1c1 that contains the following percent HbA1c measures for the group of patients: 5, 7, 6.5, 9, 8, 7, 5.5, 5.5, 9, 4. 
3. The threshold for diagnosing diabetes is >48 mmol/mol which you can calculate by  subtracting 2.15 from HbA1c1, and then multiplying it by 11. Make a new numerical vector called HbA1c2 which has the values in mmol/mol.
4. What is the highest HbA1c value in mmol/mol? What is the mean?
5. Make a vector variable called “diabetes” that stores the result of checking  if each person has an HbA1c2 greater than 48. 
6. Use your diabetes vector variable and the  sum() function to find how many people have diabetes. What is this function doing?
7. Use the  length() function to find how many people are in your data. Combine the sum() and length() variables to make a variable that contains calculate the percentage of people with diabetes.
8. Your colleague who runs a similar clinic at another hospital sends you a list of the % HbA1c measurements for their patients: 8, 7, 5.5, 7, 6.5, 9, 8, 7, 5.5, 5.5, 9, 4, 7, 5.5, 5. By only changing the command in your script that makes the numerical vector, find the prevalence of diabetes in this patient group.
9. Which hospital has the highest prevalence of diabetes – yours or your colleagues?
10. If your colleague didn’t want to share their data with you, suggest how else you could help them to find the prevalence in their patients?


### Solution


```
HbA1c1=c(5, 7, 6.5, 9, 8, 7, 5.5, 4.5, 9, 4)
HbA1c2=11*(HbA1c1-2.15)
max_HbA1c= max(HbA1c2)
mean_HbA1c= mean(HbA1c2)
diabetes=HbA1c2>48
prevalence=sum(diabetes)/length(diabetes)
```

### Conclusion

In this workshop we've learned how to handle basic variable types in R and run a series of calculations. While everything we did here could be done on a calculator, in the next workshop we will be working with a large dataset of 250,000 people.


## Session 2 - Working with Data


In the last session, we learned how to work with simple variable types in R, and covered assignment, functions, and vectors. In this session, we will move on to studying real healthcare data using R. We will use the diabetes prediction dataset, a collection of healthcare records recorded from multiple healthcare providers. More information can be found here: https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset.

### Packages

When you load up R, you don't typically get any specialist functions to use. To load the data and do anything interesting with it, we need three packages, which first need to be installed. The `dplyr` package is very common in data science, and contains a lot of useful functions for managing data. The others are used for accessing and reading the file.

```
install.packages('readr')
install.packages('knitr')
install.packages('dplyr')
```

A load of red text appears, just ignore it. Then, once the packages are installed, they need to be loaded.

```
library('readr')
library('knitr')
library('dplyr')
```

Now we have our packages loaded, we can read in the data. I've stored this in the github repository along with this course.

```
myfile = "https://raw.github.com/hdg204/DoctorsAsDataScientists/main/diabetes_prediction_dataset.csv"
testdata=read.csv(myfile)
```

Your environment should now look like this

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/546e1357-c3c2-4762-87d9-6d1862fb0e7c)

You can see we have 100,000 observations and 9 variables in a table, which in R is called a dataframe.

### Inspecting Data

You can take a closer look with the following functions

```
dim(testdata)
nrow(testdata)
ncol(testdata)
ls(testdata)
head(testdata)
head(testdata, n= 10) 
```

Run each of them in turn and take some time to work out what each one does.

You can also get a good picture of how the dataframe looks by using ```glimpse(testdata)```, and you can navigate the data interactively using ```View(testdata)```.  

What do the dbl, int and chr mean?

### Subsetting Data

It can be useful to know how to look at a small set of your data at a time, like specific people or specific variables. There are two ways of doing this: using indices and using variable names.

In general, `testdata[row,column]` will give you the data in that row and column of the data. Leaving any of these blank essentially means 'all'.

```testdata[3,4]``` will give you the data in the 3rd row and the 4th column.
```testdata[2,]``` will give you all of the data for person 2.
```testdata[,6]``` will give you all the data in column 6.

What will ```testdata[c(3:9),]``` do? Run c(3:9) on its own to see what this is doing if you aren't sure.

When you have lots of columns, it can be quite hard to remember what all the numbers mean. This is where subsetting using the variable name can be helpful.

```testdata$bmi```

Will give you all the BMI values.

What will ```testdata$bmi[c(4,7,c(10:14))]``` do?

### Calculations and Combining Conditions

Once you've subsetted data, it works the same way as any other vector. This means you can run things like ```sum(testdata$bmi>25)``` to find out how many people have a BMI over 25. the `testdata$bmi>25` bit creates a logical vector of TRUE where bmi>25 and FALSE where it is not. Sum then adds up all the TRUE values. If you're interested in the ratio, you can run ```sum(testdata$bmi>25)/nrow(testdata)```. 

To get the actual values of BMI where it is greater than 25, you'll need testdata$bmi[testdata$bmi>25]. This tells R 'I want the BMI values, but only when the BMI values are over 25.

Multiple conditions can be subsetted at once. sum(testdata$bmi<20 & testdata$hypertension==1) will give you how many people have a BMI of less than 20 and have hypertension.


### Summarising data

We can apply functions to data, and we can use the same functions we used in week 1.

Calculate the mean BMI using ```mean(testdata$bmi)```. Now do the same for the minimum and maximum BMI. What do you think about the maximum BMI value?

Remind yourselves of what the columns are called using the ```ls``` function. Now, calculate the mean HbA1c. What happened?

We need to talk about the scourge of data science: NA.

### Missing data

Anything missing or otherwise invalid will appear as NA in R. This can happen a lot in real healthcare data, when things aren't recorded properly, or they're only recorded in a subset of people. You can read NA as 'I don't know'.

So why was the mean of HbA1c NA? Why not just give us a number? If Alice is 23, Bob is 60, and you don't know the age of Charlie (NA), who is the oldest? NA, because you don't know. What is the average age? Without Charlie's age, the average age is NA, because you don't know. It doesn't matter how much data you have, if you have 1,000,000 data points, but one of them is NA, you don't know the mean, median, minimum, maximum, etc. This is really annoying, but most functions have a workaround.

```mean(testdata$HbA1c_level,na.rm=TRUE)```

The ```na.rm=TRUE``` bit will tell R to ignore the NAs, and give you the mean.

### Basic plots

Visualising data is important to get a bigger picture rather than just looking at individual points.

```hist(testdata$bmi)```

```boxplot(age ~ heart_disease, data = testdata)```

```plot(testdata$age,testdata$bmi)```

### Exercise 2

You're interested in the links between obesity and hpertension. First, find what percentage of the data have hypertension?

How is this different in people with a BMI over or under 25?

Of the people with hypertension, what percentage also have heart disease?

Plot a histogram of the age of people with hypertension. Repeat this for those without. What does the difference between these plots tell you?

How much higher is the average BMI in people with hypertension vs people without hypertension?

Make a boxplot of the BMI levels with and without hypertension.

What do you conclude about the links between BMI and hypertension?

If you have finished, repeat this with HbA1c and diabetes.

### Solutions

*This section is hidden until after the workshop*

```
hypertension_prev=sum(testdata$hypertension==1)/nrow(testdata)
hypertension_u25=sum(testdata$hypertension[testdata$bmi<25]==1)/sum(testdata$bmi<25)
hypertension_o25=sum(testdata$hypertension[testdata$bmi>25]==1)/sum(testdata$bmi>25)
hist(testdata$age[testdata$hypertension==1])
hist(testdata$age[testdata$hypertension==0])
mean(testdata$bmi[testdata$hypertension==1])-mean(testdata$bmi[testdata$hypertension==0])
boxplot(bmi~hypertension,testdata)
prevalence=sum(diabetes)/length(diabetes)
```

## Session 3 - dplyr and basic statistics


In this session, we will introduce two important packages for data science: dplyr and ggplot2. Make sure your data is loaded into R by checking the workspace. If it isn't, load the same data we used in session 3.

`dplyr` has a lot of useful functions for managing complicated datasets, and in this session we'll introduce them one at a time. They all have the same structure: command(dataframe,instructions). The output is always another dataframe, but unless you assign the output to something, it will just print to screen rather than going into the workspace. dataframe2=command(dataframe,instructions) will store the output in an updated dataframe called dataframe2.

This session is light on additional content and contains more exercises for exploring the data. dplyr commands may help you with the exercises and can help you write readable code, but are not always necessary.

Prepare the data by running the following:

```
install.packages('readr')
install.packages('knitr')
install.packages('dplyr')

library('readr')
library('knitr')
library('dplyr')

myfile = "https://raw.github.com/hdg204/DoctorsAsDataScientists/main/diabetes_prediction_dataset.csv"
testdata=read.csv(myfile)
```

Now we will learn three new dplyr commands: `filter`, `mutate`, and `select`.

### Filter

Filter is a useful command for studying a subset of people.

For example, run ```hyperdata=filter(testdata,hypertension==1)```

What happened to your workspace? How many rows are in this dataframe?

You can combine conditions in the same way as before:

```filter(testdata,hypertension==1&bmi<30)```

Take some time to work out what this command is doing.

What does ```nrow(filter(testdata,hypertension==1&bmi<30))``` tell us about the data?

### Mutate

Mutate creates new columns, which could be based on existing columns in your data.

```testdata2=mutate(testdata,obesity=BMI>30)```

Will create a new column, called obesity, which is TRUE when BMI > 30, and FALSE when it isn't. It stores the result in a new dataframe called `testdata2`.

### Select

Select is fairly simple, it just selects individual columns that you want. Useful if your dataset has hundreds of variables and you're only interested in a handful.

```testdata2=select(testdata, gender, age, BMI)```.

When might this be useful?

### Exercise 3

You're interested in the differences between men and women in your data. 

First you check what percentage of your data is Male, and what percentage is Female.

What percentage of males are current smokers? What about females?

Are males more or less likely to have diabetes, heart disease or hypertension than females?

What is the difference in the average BMI between males and females?

Plot a histogram of the BMI in males, and then again for females.

Make a box plot showing this information.

What do you think is driving these results?

### Solutions

*This section is hidden until after the workshop*
 <!-- 
```
nrow(filter(testdata=='Male'))/nrow(testdata)
nrow(filter(testdata=='Male' & smoking_history=='current')) / nrow(filter(testdata=='Male'))
nrow(filter(testdata=='Female' & smoking_history=='current')) / nrow(filter(testdata=='Female'))

mean(testdata$diabetes[testdata$gender=='Male'])
mean(testdata$diabetes[testdata$gender=='Female'])
mean(testdata$hypertension[testdata$gender=='Male'])
mean(testdata$hypertension[testdata$gender=='Female'])
mean(testdata$heart_disease[testdata$gender=='Male'])
mean(testdata$heart_disease[testdata$gender=='Female'])

mean(testdata$bmi[testdata$gender=='Male'])-mean(testdata$bmi[testdata$gender=='Female'])

hist(testdata$bmi[testdata$gender=='Male'])

hist(testdata$bmi[testdata$gender=='Female'])
boxplot(bmi~gender,testdata)
```
-->

### Exercise 4

You're interested in the links between HbA1c and BMI. But your HbA1c column is a bit messed up, it's in %, when we prefer mmol/mol, and it has some missing data. Make a new dataframe where the HbA1c is in mmol/mol, and the missing values are removed (HINT: !is.na() is a command for checking if something isn't NA).

Plot histograms of HbA1c and BMI to remind yourself of the distribution. Looking at data is important.

You have this really long tail in that distribution of BMI. How many are above 60? Make a new dataframe where you exclude those and plot a new histogram of BMI.

In this new dataframe, find the highest BMI value. What is the HbA1c of the person with the highest BMI value?

What percentage of people with a BMI over 25 also have an HbA1c over 48? Is this percentage different in men and women?

### Solutions

*This section is hidden until after the workshop*
 <!-- 
```
testdata2=filter(testdata,!is.na(HbA1c_level))
testdata3=mutate(testdata2,HbA1cmmol=11*(HbA1c_level-2.15))
hist(testdata3$HbA1cmmol)
hist(testdata3$bmi)
testdata4=filter(testdata3,bmi<60)
hist(testdata4$bmi)
maxbmi=max(testdata4$bmi)
testdata4$HbA1cmmol[testdata4$bmi==maxbmi]
nrow(filter(testdata4,bmi>25 & HbA1cmmol > 48)) / nrow(filter(testdata4,bmi>25))
nrow(filter(testdata4,bmi>25 & HbA1cmmol > 48 & gender=='Male')) / nrow(filter(testdata4,bmi>25 & gender=='Male'))
nrow(filter(testdata4,bmi>25 & HbA1cmmol > 48 & gender=='Female')) / nrow(filter(testdata4,bmi>25 & gender=='Female'))
```



### Extension - Linear Regression

If you've made it to the end, congratulations. The R command lm can perform linear regression analysis.

What does the output of ```lm(bmi~age,data=testdata)``` tell you? Wrapping summary() around that gives you even more information.

Explore the data in whichever way you feel is interesting. Let me know if you find anything.
-->
